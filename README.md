# kms-envelope-encryption-aws
Envelope Encryption with Amazon KMS and Node

# Concepts

- Customer Master Keys (AWS term) (CMKs): Per platform keys eg. {dev|staging|prod}
- Tenant Master Keys (TMKs): Per customer keys eg. {customer1|customer2|customer3}
- Tenant Data Keys (TDKs): Per record keys eg. {field1|field2|field3}

# Demo
**NB: Requires KMS ARN to be the specified  environment var CMKID**

```bash
export CMKID=arn:aws:kms:{yourregion}:{youraccount}:key/{yourkeyId}
npm run demo
```
# Tests
```bash
npm test
```
