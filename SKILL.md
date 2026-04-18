---
name: autodl
description: Helps users interact with the AutoDL GPU cloud platform API — managing container instances (Pro), elastic deployments (ESD), checking account balance, and switching file storage. Use this skill whenever the user mentions AutoDL, GPU rental, container instances, elastic deployment, power on/off, releasing instances, replica scaling, scheduling blacklists, or any GPU cloud resource management on AutoDL, even if they don't explicitly say "API" or "AutoDL".
---

# AutoDL API Skill

Generates ready-to-run Python code for managing AutoDL GPU cloud resources via the official REST API.

## Core Info

- **API Host**: `https://api.autodl.com`
- **Auth**: Add `{"Authorization": "<your-token>"}` to every request header
- **Token location**: Console → Account → Settings → Developer Token

Standard response structure:
```json
{"code": "Success", "msg": "", "data": {...}}
```
`code == "Success"` means OK; otherwise `msg` contains the error.

---

## API Categories

### 1. Common API — `references/common_api.md`
- Get account balance
- Switch dedicated NFS / file storage

### 2. Container Instance Pro API — `references/instance_pro_api.md`
For users who need **persistent instances** with pay-as-you-go or prepaid billing.
- Create / list / get status / power on / power off / release instances

### 3. Elastic Deployment API — `references/esd_api_doc.md`
For **auto-scaling and batch job** scenarios (requires enterprise account verification).
- Create / stop / delete deployments, set replica count, query containers, manage scheduling blacklists, check GPU inventory

---

## Quick Reference

### Common Operations

| Task | Endpoint | Method |
|------|----------|--------|
| Check balance | `/api/v1/dev/wallet/balance` | POST |
| Create Pro instance | `/api/v1/dev/instance/pro/create` | POST |
| Get instance status | `/api/v1/dev/instance/pro/status` | GET |
| List Pro instances | `/api/v1/dev/instance/pro/list` | POST |
| Power on | `/api/v1/dev/instance/pro/power_on` | POST |
| Power off | `/api/v1/dev/instance/pro/power_off` | POST |
| Release instance | `/api/v1/dev/instance/pro/release` | POST |
| Create deployment | `/api/v1/dev/deployment` | POST |
| List deployments | `/api/v1/dev/deployment/list` | POST |
| Set replica count | `/api/v1/dev/deployment/replica_num` | PUT |
| Stop deployment | `/api/v1/dev/deployment/operate` | PUT |
| Delete deployment | `/api/v1/dev/deployment` | DELETE |
| List containers | `/api/v1/dev/deployment/container/list` | POST |
| Stop a container | `/api/v1/dev/deployment/container/stop` | PUT |
| Check GPU stock | `/api/v1/dev/machine/region/gpu_stock` | POST |
| Set blacklist | `/api/v1/dev/deployment/blacklist` | POST |

### Region Codes (`dc_list` / `region_sign`)

| Region | Code |
|--------|------|
| Northwest Enterprise (recommended) | `westDC2` |
| Northwest Zone B | `westDC3` |
| Beijing Zone A | `beijingDC1` |
| Beijing Zone B | `beijingDC2` |
| Inner Mongolia Zone A | `neimengDC1` |
| Chongqing Zone A | `chongqingDC1` |

### Pro Instance GPU Spec IDs

| GPU Model | Spec Type | `gpu_spec_uuid` |
|-----------|-----------|----------------|
| H800-80G | General | `h800` |
| 4090-48G | General | `v-48g` |
| PRO6000-96G | Performance | `pro6000-p` |
| 5090-32G | Performance | `5090-p` |
| 3090-48G | General | `v-48g-350w` |

### Unit Conventions

- **Price**: API uses `yuan × 1000` — e.g. `1000 = ¥1.00/hr`, `9000 = ¥9.00/hr`
- **Memory** (deployment list response): bytes — divide by `1024³` to display as GB
- **CUDA version**: integer encoding — `118 = CUDA 11.8`, `120 = CUDA 12.0`, etc.

---

## Common Workflows

### User wants to act on a resource but hasn't provided a UUID

List the resources first so the user can confirm the target:
1. Call the list endpoint (`/pro/list` or `/deployment/list`)
2. Show UUID, name, and status
3. Proceed once the user confirms

### Releasing a Pro instance (order matters)

The instance must be powered off before releasing, or the release may fail:
1. `power_off` → poll status until `shutdown`
2. `release`

### Scaling down an elastic deployment

- **Stop one specific container**: `/container/stop` — optionally pass `decrease_one_replica_num: true` to also reduce the replica count by 1
- **Bulk scale-in**: `/replica_num` — set the new count; the platform stops the excess containers automatically
- **Stop everything**: `/operate` with `{"operate": "stop"}`

---

## Code Generation Guidelines

Always:
- Include the `Authorization` header with a placeholder comment reminding the user to fill in their token
- Print the response for easy debugging: `print(response.json())`
- Use `requests.post` / `requests.put` / `requests.delete` matching the correct HTTP method for each endpoint

For full parameter tables, response schemas, base image UUIDs, and CUDA version mappings, read the relevant reference file before generating code.

---

## Reference Files

| File | Contents |
|------|----------|
| `references/common_api.md` | Balance, NFS switch |
| `references/instance_pro_api.md` | Full Pro instance API with examples |
| `references/esd_api_doc.md` | Full elastic deployment API, region codes, base image UUIDs, CUDA version table |
