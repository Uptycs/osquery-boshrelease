# [Uptycs]((https://www.uptycs.com)) Osquery release for [BOSH](https://bosh.io)

Copy the [osquery.yml](manifests/osquery.yml) manifest file and update it to meet your BOSH environment. Deploy Osquery latest release release:

```sh
bosh -d osquery deploy osquery.yml
```