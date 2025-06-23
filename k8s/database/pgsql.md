### Postgres StatefulSet
  
```
  apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: postgres
  namespace: postgres
spec:
  serviceName: "postgres"   # headless service for stable DNS
  replicas: 1
  selector:
    matchLabels:
      app: postgres
  template:
    metadata:
      labels:
        app: postgres
    spec:
      terminationGracePeriodSeconds: 10
      containers:
      - name: postgres
        image: postgres:latest
        ports:
        - containerPort: 5432
        volumeMounts:
        - name: postgres-data
          mountPath: /var/lib/postgresql/data
        env:
        - name: POSTGRES_USER
          valueFrom:
            secretKeyRef:
              name: postgres-secret
              key: POSTGRES_USER
        - name: POSTGRES_PASSWORD
          valueFrom:
            secretKeyRef:
              name: postgres-secret
              key: POSTGRES_PASSWORD
        - name: POSTGRES_DB
          valueFrom:
            secretKeyRef:
              name: postgres-secret
              key: POSTGRES_DB
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
              - pg_isready
              - "-U"
              - "$(POSTGRES_USER)"
          initialDelaySeconds: 30
          timeoutSeconds: 5
          periodSeconds: 10
        readinessProbe:
          exec:
            command:
              - pg_isready
              - "-U"
              - "$(POSTGRES_USER)"
          initialDelaySeconds: 5
          timeoutSeconds: 1
          periodSeconds: 10
  volumeClaimTemplates:
  - metadata:
      name: postgres-data
    spec:
      accessModes: ["ReadWriteOnce"]
      resources:
        requests:
          storage: 2Gi
```

### Postgres Service
```
apiVersion: v1
kind: Service
metadata:
  name: postgres
  namespace: postgres
spec:
  ports:
    - port: 5432
      targetPort: 5432
  clusterIP: None                # This makes it headless
  selector:
    app: postgres
```

### Postgres Secret
```
apiVersion: v1
kind: Secret
metadata:
  name: postgres-secret
  namespace: postgres
type: Opaque
stringData:
  POSTGRES_USER: "root"
  POSTGRES_PASSWORD: "root"
  POSTGRES_DB: "testdb"
```
            
