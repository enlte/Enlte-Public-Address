# Create Enlte address


```
//get first hash using sha256 of privateKey
$publicKeySha1 = hash(sha256, $privateKey);

$publicKey = hash(sha256, $publicKeySha1, $raw_output = null);
$address = substr($publicKey, 4, 24);

$sha1 = hash(sha256, $address, $raw_output = null);
$checkSum1 = substr($sha1, 0, 4);

$sha2 = hash(sha256, $checkSum1, $raw_output = null);
$checkSum2 = substr($sha2, 0, 4);

$addCheckSum = $checkSum1."".$address."".$checkSum2;

$add_64 = base64_encode($addCheckSum);
$extractedStr = substr($add_64, 0, 29);

$address =  "ELT".$checkSum1.$extractedStr.$checkSum2;

```

# Algorithm description

1. create public address using sha256 of hashed private key
2. Extract 20 character from hashed public key and its range is 4 to 24
3. Create first sha256 of 20 character of hashed private key and get 4 digit from first hash of address
4. Create second sha256 of 4 digit of checksum1 and get 4 digit from second hash of checksum1
5. Add both check sum & address and get base64 from addCheckSum. 
6. Create an address in base64check format through base64 encoding & get first 29 charchater from encode string.
7. Add the checksum1 code with ELT prefix to the start of the extracted result and and checkSum2 at the end of extracted result

Here is your final public address to see your balance.
