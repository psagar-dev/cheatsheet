### Mysql StatefulSet
```
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: mysql
  namespace: mysql
spec:
  serviceName: "mysql"     # headless service for stable network IDs
  replicas: 3
  selector:
    matchLabels:
      app: mysql
  template:
    metadata:
      labels:
        app: mysql
    spec:
      terminationGracePeriodSeconds: 10
      containers:
      - name: mysql
        image: mysql:latest    # Use official MySQL image, pick your required version
        ports:
        - containerPort: 3306
        volumeMounts:
        - name: mysql-data
          mountPath: /var/lib/mysql   # MySQL data directory
        env:
        - name: MYSQL_ROOT_PASSWORD
          valueFrom:
            secretKeyRef:
              name: mysql-secret
              key: MYSQL_ROOT_PASSWORD
        - name: MYSQL_USER
          valueFrom:
            secretKeyRef:
              name: mysql-secret
              key: MYSQL_USER
        - name: MYSQL_PASSWORD
          valueFrom:
            secretKeyRef:
              name: mysql-secret
              key: MYSQL_PASSWORD
        resources:
          requests:
            cpu: "500m"
            memory: "1Gi"
          limits:
            cpu: "1"
            memory: "2Gi"
        livenessProbe:
          exec:
            command:
              - sh
              - -c
              - "mysqladmin ping -h 127.0.0.1 -uroot -p$MYSQL_ROOT_PASSWORD"
          initialDelaySeconds: 30
          timeoutSeconds: 5
          periodSeconds: 10
        readinessProbe:
          exec:
            command:
              - sh
              - -c
              - "mysqladmin ping -h 127.0.0.1 -uroot -p$MYSQL_ROOT_PASSWORD"
          initialDelaySeconds: 5
          timeoutSeconds: 1
          periodSeconds: 10
  volumeClaimTemplates:
  - metadata:
      name: mysql-data
    spec:
      accessModes: ["ReadWriteOnce"]
      resources:
        requests:
          storage: 1Gi
```

### Mysql Service

```
apiVersion: v1
kind: Service
metadata:
  name: mysql
  namespace: mysql
spec:
  ports:
    - port: 3306
      name: mysql
  clusterIP: None   # Headless
  selector:
    app: mysql
```

### Mysql Secret
```
apiVersion: v1
kind: Secret
metadata:
  name: mysql-secret
  namespace: mysql
type: Opaque
data:
  MYSQL_ROOT_PASSWORD: cm9vdA==        # 'root'
  MYSQL_USER: dXNlcg==                 # 'user'
  MYSQL_PASSWORD: dXNlcnBhc3M=         # 'userpass'
```
