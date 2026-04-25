# AGENTS.md

## Quick Start

### Start infrastructure
```bash
docker build -t base-service .
docker-compose up -d
```

### Service ports
- Gateway HTTP: `localhost:8001`
- Gateway gRPC: `localhost:9001`
- Operations HTTP: `localhost:8002`
- Operations gRPC: `localhost:9002`
- Mock HTTP: `localhost:8003` (required for tests)
- Mock gRPC: `localhost:9003` (required for tests)
- Kafka: `localhost:9093`
- PostgreSQL: `localhost:5432`

### Run tests
```bash
cd tests && pytest
```

### Rebuild protos
```bash
bash scripts/protos.sh
```

## Key Facts

- Python 3.12, FastAPI, gRPC, Kafka, PostgreSQL
- Tests require mock HTTP (8003) and gRPC (9003) services running
- PostgreSQL credentials: `operations_service_user` / `operations_service_password`
- Database: `operations_service_db`
- PYTHONPATH must include `./:./protos/gen`
- Test env in `tests/.env`