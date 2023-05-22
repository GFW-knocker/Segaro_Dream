ADS used by {VPN server , DoH server , Report server} to guarantee investment return

### ADS
- AdsText = "" (max 100 char)
- AdsLink = ""
- AdminLink = "" (optional - page of admin to be contacted for advertisement)
- Domain = "" (optional - change Domain to prevent SNI filtering)
- UUID = "" (used in config - change every 1 hour by VPN server to prevent config stealing)


# -------------------------------------------
- transfered in json format with Base64 encoding
- client check ADS every 15 minutes
- server can change UUID regularly by automated script 
- server must keep old UUID valid for +20 minutes before removing it
