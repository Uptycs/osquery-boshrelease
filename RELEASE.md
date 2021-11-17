## Creating new ew release notes

* Update the version in the following files:
  * packages/osquery/packaging
  * packages/osquery/spec
  * config/blobs.yml
  * manifests/osquery.yml

* Download deb and rpm versions of the package from S3

* Add the blobs using bosh CLI:
  ```sh
  bosh add-blob /tmp/osquery-<VERSION>.rpm osquery/osquery-<VERSION>-202111112102.rpm
  bosh add-blob /tmp/osquery-<VERSION>.rpm osquery/osquery-<VERSION>-202111112102.deb
  ```

* Verify blobs exists:
  ```sh
  bosh blobs
  ```

* Create dev release
  ```sh
  bosh create-release --force
  ```

* Git Commit changes

* Create final release
  ```sh
  bosh create-release --version=<VERSION> --final
  ```