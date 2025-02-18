
**Staging Env

```json
NX_REACT_APP_API_URL: 'https://los-api.swiffylabs.stg',
```
### **Endpoint Name**

**Method:** `GET | POST | PUT | DELETE`  
**URL:**

```pgsql
{http-base}/workflow-manager/customer/{$randomInt}/workflow
```


**Query Parameters (For GET requests):**

| Parameter | Type   | Required | Description           |
| --------- | ------ | -------- | --------------------- |
| param1    | string | ❌        | Optional description  |
| param2    | int    | ✅        | Mandatory description |

**Request Body (For POST/PUT requests):**

```json
{   "templateId": "SWIFFY-LAMF-V1" }
```

Template ids
```json
LAMF: SWIFFY-LAMF-V1

PL: SWIFFY-PL-V1

FE Integration: temp-fe-intg-test-pl-001

Local Testing: local-teja-pl, local-teja-mf

FiftyFin: LOCAL-TEST-50FIN, UAT - 50FIN_SWIFFY_LAS

LOCAL-SIMPLE-FLOW-PL

INTG-TEST-PL-LOS-884

WFM-ISSUE-DEBUG-001
```

**Response Example:**  
✔️ **Success (200 OK)**

```json
{
"workflowId": "f4704ad0-db47-464f-9fc5-2a13d202349e"
}
```

https://los-api.swiffylabs.stg
