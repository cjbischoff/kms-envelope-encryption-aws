# kms-envelope-encryption-aws
Envelope Encryption with Amazon KMS and Node

# Concepts

- Customer Master Keys (AWS term) (CMKs): Per platform keys eg. {dev|staging|prod}
- Tenant Master Keys (TMKs): Per customer keys eg. {customer1|customer2|customer3}
- Tenant Data Keys (TDKs): Per datasource eq. {column within database|RDS database|S3 Bucket,}

# Demo
**NB: Requires KMS ARN to be the specified  environment var CMKID**

```bash
export CMKID=arn:aws:kms:{yourregion}:{youraccount}:key/{yourkeyId}
npm run demo
```
Demo will show input of plain text `this is a secret` being enctypyred using the TMK TDK key.

The resultant encrypted envelope values of `[cmkId, tmkCipherText, tdkCipherText, dataCipherText, createdAt]` can all at this point be serialized and stored into your data store of choice.

1. [Create AWS credentials](http://docs.aws.amazon.com/cli/latest/userguide/cli-config-files.html)
2. Create a [KMS (CMK) key](http://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html) that you can generate the ciphertext TMK and TDK with. Add the resultant ARN of the key you’d like to use to the CMKID environment variable (either inline to the command or by exporting).
3. Ensure AWS IAM policy will allow KMS access from laptop
4. Define the AWSREGION environment variable (default is us-west-2)
5. Output should look like this - kinda

```
Plaintext data: this is a secret

Encrypted Envelope:
cmkId:    
tmkCipherText:  
tdkCipherText:
dataCipherText:
createdAt:      

Decrypted Envelope:
cmkId:       
dataPlainText: this is a secret
decryptedAt:   
```

# Tests
```bash
npm test
```
