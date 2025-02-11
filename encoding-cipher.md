## Base 64
Encode :
echo [string] | base64
Decode :
echo [b64-encoded-string] | base64 -d

## Hex
Encode :
echo [string] | xxd -p
Decode :
echo [hex-encoded-string] | xxd -p -r

## Rot13
Encode / Decode :
echo [string / rot13-encoded-string] | tr 'A-Za-z' 'N-ZA-Mn-za-m'

Cipher Identifier : https://www.boxentriq.com/code-breaking/cipher-identifier
