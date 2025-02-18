
**Get next data

```json
{
  "state": "READY",
  "moduleName": "los-kyc-okyc-redirect",
  "data": {
    "requestId": "78eb9e9f-12ea-4698-ad12-5c818170a987",
    "redirectUrl": "https://api.digitallocker.gov.in/public/oauth2/1/authorize?response_type=code&client_id=CLAC218F6B&redirect_uri=https://api.dscoe.jiolabs.com/redirect&state=swiffy:http://product-journey.swiffylabs.stg/los/product-journey/f4704ad0-db47-464f-9fc5-2a13d202349e/kyc-complete&code_challenge=hgWnSSyCQQ0ArDCvBNAKsNLPkXg6-cDot2dpKE7g0PA&code_challenge_method=S256"
  }
}
```

**Signal data

```json
{
  "moduleName": "los-kyc-okyc-redirect",
  "data": {
    "externalRedirectParams": [
      {
        "key": "code",
        "value": "6ee67278e15b1c6d77b0709e679703f308318aa0"
      }
    ]
  }
}
```