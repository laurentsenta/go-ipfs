# Dataset description/sources

- fixtures.car
  - raw CARv1

- record.json
  - ipns record as naive json

generated with:

```sh
# ipfs version 0.18.1
FILE_CID=$(echo "Hello IPFS" | ipfs add --cid-version 1 -q)
IPNS_KEY=$(ipfs key gen ipns-record)

ipfs dag export ${FILE_CID} > fixtures.car

# publish a key valid for a 100 years
ipfs name publish --key=ipns-record --quieter --ttl=876600h /ipfs/${FILE_CID}
ipfs routing get /ipns/${IPNS_KEY} > ${IPNS_KEY}.ipns-record

echo IPNS_KEY=${IPNS_KEY}
echo FILE_CID=${FILE_CID} # A file containing "Hello IPFS"

# IPNS_KEY=k51qzi5uqu5djucgtwlxrbfiyfez1nb0ct58q5s4owg6se02evza05dfgi6tw5
# FILE_CID=bafkreidfdrlkeq4m4xnxuyx6iae76fdm4wgl5d4xzsb77ixhyqwumhz244 # A file containing Hello IPFS
```
