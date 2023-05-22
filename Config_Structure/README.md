
### Config:
- Type = {websocket , grpc , reality , ...}
- Link = "vmess vless link" with empty UUID and Domain
- DomainOrIP = ""
- Port = int
- SNI = ""
- useCDN = bool
- useRandomSubDomain = bool
- useFragment = bool
- useLoadBalance = bool
- ADSpath = "/ads.txt"  (UUID obtained from Ads so config is not static and cant be stolen)

### DOH:
- format = {wire,json}
- DomainOrIP = ""
- Port = int
- DohPath = "/dns-query?name="
- useCDN = bool
- useRandomSubDomain = bool
- useFragment = bool
- ADSpath = "/ads.txt"

### CDN:
- name = "cloudflare"
- IPList = [a,b,c,...] (max 10 ip)


### ReportServer:
- DomainOrIP = ""
- Port = int
- ReportPath = "/report?data="
- PackagePath = "/pkg?captcha="  (validate user by captcha then give him 3 config package)
- useCDN = bool
- useRandomSubDomain = bool
- useFragment = bool
- ADSpath = "/ads.txt"


### Settings
- NumFragment = 87
- FragmentSleep = 0.001


### info: (optional)
- pkgVersion = 1.0
- DateCreation = ""
- DateExpire = ""
- CreatorName = ""
- CreatorContact = ""
- Description = "" (100 char max)

### checksum:
- md5 = ""    (md5 hash of b64 encoding of json with all above info without checksum filed - checksum be inserted later)
- sha1 = ""
- InternalHash = ""  concat(md5[0:10] + sha1[0:10]

# --------------------------------------
- packed in json format
- encoded in Base64
- transfered using file *.cfgpkg




