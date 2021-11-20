# [Uptycs]((https://www.uptycs.com)) Osquery release for [BOSH](https://bosh.io)

Deploy Uptycs Osquery as a BOSH add-on. Copy: [runtime.yml](manifests/runtime.yml)

Replace `version`, `hostname` and `secret`:

```yaml
releases:
- name: osquery
  url: git+https://github.com/Uptycs/osquery-boshrelease
  version: 5.0.2.9-Uptycs-202111112102 # Change to the latest Osquery version

addons:
- name: osquery
  jobs:
  - name: osquery
    release: osquery
    properties:
      uptycs:
        hostname: CHANGE-ME # Change to your Uptycs tenant hostname. Example: tenant.uptycs.io
        secret: CHANGE-ME   # Download the secret from Uptycs SaaS platform
```

Deploy the runtime config with the following command:
```sh
bosh update-runtime-config runtime.yml
```

Verify the addon using the following command:
```sh
bosh runtime-config
```

Create or update BOSH deployments using the following command:
```sh
bosh deploy
```