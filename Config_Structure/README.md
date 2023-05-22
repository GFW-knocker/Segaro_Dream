
### Config:
- type = {websocket , grpc , reality , ...}
- link = "vmess vless link" with empty UUID and Domain
- DomainOrIP = ""
- SNI = ""
- useCDN = bool
- useRandomSubDomain = bool
- useFragment = bool
- useLoadBalance = bool
- ADSpath = "/ads.txt"  (UUID obtained from Ads so config is not static and cant be stolen)

### DOH:
- format = {wire,json}
- DomainOrIP = ""
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
- ReportPath = "/report?data="
- PackagePath = "/pkg?captcha="  (validate user by captcha then give him 3 config package)
- useCDN = bool
- useRandomSubDomain = bool
- useFragment = bool
- ADSpath = "/ads.txt"




