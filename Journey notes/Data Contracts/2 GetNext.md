
**Staging Env

```json
NX_REACT_APP_API_URL: 'https://los-api.swiffylabs.stg',
```
### **Endpoint Name**

**Method:** `GET | POST | PUT | DELETE`  
**URL:**

```pgsql
{{http-base}}/workflow-manager/customer/workflow/{{workflowId}}
```


**Query Parameters (For GET requests):**

| Parameter  | Type   | Required | Description       |
| ---------- | ------ | -------- | ----------------- |
| workflowid | string |          | workflowid        |
| token      | string |          | token of the user |


**Response Example:**  
✔️ **Success (200 OK)**

```json
{
	"state": "READY",
	"moduleName": "los-personalDetails"
	"data":{
	
	}
}
```

