
**Get next data

```json
{
  "state": "READY",
  "moduleName": "los-mf-pledge-funds",
  "data": {
    "customerId": "00000097",
    "funds": [
      {
        "portfolioId": 334,
        "folioNo": "19920107056",
        "isin": "INF760K01EI4",
        "scripType": "EQUITY",
        "platform": "KARVY",
        "price": 209.24000549316406,
        "qtyAvailable": 250.0,
        "ltvPerQty": 184.13119506835938,
        "isWhitelisted": true,
        "mfName": "Canara Robeco Emerging Equities  Direct Growth"
      },
      {
        "portfolioId": 335,
        "folioNo": "19920107056",
        "isin": "INF760K01EL8",
        "scripType": "EQUITY",
        "platform": "KARVY",
        "price": 146.25999450683594,
        "qtyAvailable": 20.0,
        "ltvPerQty": 128.70880126953125,
        "isWhitelisted": true,
        "mfName": "Canara Robeco Equity Tax Saver Fund  Direct Growth"
      },
      {
        "portfolioId": 336,
        "folioNo": "79930472341",
        "isin": "INF769K01AX2",
        "scripType": "EQUITY",
        "platform": "KARVY",
        "price": 97.77999877929688,
        "qtyAvailable": 100.0,
        "ltvPerQty": 86.04640197753906,
        "isWhitelisted": true,
        "mfName": "Mirae Asset Large Cap Fund  Direct Plan   Growth"
      },
      {
        "portfolioId": 337,
        "folioNo": "79930472341",
        "isin": "INF769K01DH9",
        "scripType": "EQUITY",
        "platform": "KARVY",
        "price": 500.04998779296875,
        "qtyAvailable": 40.0,
        "ltvPerQty": 440.04400634765625,
        "isWhitelisted": true,
        "mfName": "Mirae Asset Hybrid   Equity Fund  Direct Plan Growth"
      },
      {
        "portfolioId": 338,
        "folioNo": "91028380826",
        "isin": "INF247L01718",
        "scripType": "DEBT",
        "platform": "KARVY",
        "price": 27.709999084472656,
        "qtyAvailable": 67.0,
        "ltvPerQty": 3.7131400108337402,
        "isWhitelisted": true,
        "mfName": "Motilal Oswal Nasdaq 100 Fund of Fund  Direct Plan"
      }
    ],
    "totalPortfolioAmount": 86871.7734375,
    "totalLoanEligibility": 75062.15625,
    "minLoanAmount": 1112.0,
    "maxLoanAmount": 112111.0
  }
}
```

**Signal Data

```json
{
  "moduleName": "los-mf-pledge-funds",
  "data": {
    "portfolioData": [
      {
        "portfolioId": 336,
        //334"quantity": 30
      }
    ],
    "requestId": "{{$guid}}"
  }
}
```

