kotlin-examples
===============

Various examples for Kotlin

- flow **createDepositAppianFlow** 
  - set productCode = `payload.Deposit.ProductCode`
  - set account = `payload.Deposit.PayOutAccount`
  - set cif = `payload.Deposit.Cif`          
  - set startDate = `payload.Deposit.StartDate`
  - flow-ref **retrieveDepositModuleSubFlow** (returns `depositModule`)
  - choice `LD or TD`
    - when `vars.depositModule == 'TD'`
      - flow-ref **createTDDepositSubFlow** 
    - when `vars.depositModule == 'LD'`
      - flow-ref **createLDDepositSubFlow** 
    - otherwise
      - set httpStatus = `500`
      - set payload = `transformers/deposit/createDepositAppian/noProductResponse.dwl`
