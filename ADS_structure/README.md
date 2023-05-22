### ADS
- AdsText = "" (max 100 char)
- AdsLink = ""
- AdminLink = "" (optional - page of admin to be contacted for advertisement)
- UUID = "" (used in config - change every 1 hour by server to prevent config stealing)
- Domain = "" (optional - replace Domain inside config)

# -------------------------------------------
- transfered in json format with Base64 encoding
- client check ADS every 15 minutes
- server can change UUID regularly by automated script 
- server must hold old UUID valid for +20 minutes before removing it

