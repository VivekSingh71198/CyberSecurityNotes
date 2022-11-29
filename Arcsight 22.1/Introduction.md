# ArcSight 22.1

* **CDF**: Container Development Framework
* **Kubernetes**: Used to manage docker images

## Products
* Fusion
  * Soar
  * ArcSight Management Center
  * Fusion Dashboard
  * Reporting
  * Admin Capabilities are part of Fusion
  * TH and Database is not required on Fusion.
* Transformation HUB
* Intelligence (require TH and Database). is used for smart log investigation using ML and UEBA.
* Recon (require TH and Database). Use for Reporting and dashboard.
*  ESM 
   * We cannot access full capabilities of ESM from Fusion ESM, That's why we need Separate ESM.
*  Layered Analytics Identity Governance
---
Facts
``` notes
TH is Kafka in backend
ESM soon to be renamed to detect
```
## Connector
It can send logs in 3 languages
* CEF
* AVRO
* Binary


# Installation and Setup
  1. Access [SLD](https://sld.microfocus.com/) Portal
  2. MF Software Passport ID + SAID 
  3. put capabilities in images folder
  4. YAML in config folder 
  5. put metadata in its respective Folder.
  6. Check yaml file for configuration
  ``` bash
   ./arcsight-install --cmd precheck
   ```
   7. check for pre size of required nodes
  ``` bash
  ./arcsight-install --cmd prereq
  ```
  8. preinstall runs both precheck and prereq
  ``` bash
  ./arcsight-install --cmd preinstall
  ```
  9. it will install CDF + Database
  ``` bash
  ./arcsight-install --cmd install
  ```
  Only install database
  ``` bash
  ./arcsight-install --cmd database
  ```
  Install only CDF
``` bash
  ./arcsight-install --cmd cdf
```

## Notes


* namenode-inteligence can only be used on Large Node.

* Zoo Keeper can only be installed on odd number workers

* if property is not defined in yaml file then it will pic config from
``` bash
/opt/installer/installers/cdf/install.property
 ```
* we can use master node as worker if we set 
``` yaml
allow-worker-on-master: true
```
* Access Kubernetes 
``` bash
k9s
```
Display status of kubernetes
``` bash
./kube-status.sh
```
# User Management
**RESET**  User Password

``` bash
/opt/arcsight-nfs/arcsight-volume/investigate/mgmt/db
rm h2.mv.db
k9s

## delete fusion-user-management 
## delete single-sign-on 
```
delete these files to delete database of vertica