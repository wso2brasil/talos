# TREINAMENTO BASICO WSO2

## OPENSHIFT

### SELECTOR
- oc get all --selector app=wso2is-km -o name
- oc delete all --selector app=wso2is-km


oc new-app -e MYSQL_USER="wso2user" -e MYSQL_PASSWORD="wso2!234" -e MYSQL_DATABASE="wso2" -e MYSQL_ROOT_PASSWORD="rootroot" mysql:5.7


oc new-app docker.wso2.com/wso2is:5.7.0.1591974552018

## MARIA DB (MYSQL)
oc new-app -e MYSQL_USER=wso2 -e MYSQL_PASSWORD=wso21234 -e MYSQL_DATABASE=wso2 -e MYSQL_ROOT_PASSWORD=rootroot registry.access.redhat.com/rhscl/mariadb-101-rhel7

### PORT FORWARDING
_mariadb=`oc get pods | grep mariadb-101-rhel | awk '{print $1}'`
echo $_mariadb
oc port-forward $_mariadb 33006:3306

oc port-forward mariadb-101-rhel7-1-gwhg2 33006:3306

### REMOTE ACCESS
_mariadb=`oc get pods | grep mariadb-101-rhel | awk '{print $1}'`
echo $_mariadb


### WSO2 DATABASES
GRANT ALL ON wso2am.* TO 'wso2'@'%';

## WSO2 IDENTITY SERVER - KM - 5.7.0
oc new-app wso2brasil/bp-wso2is-km:5.7.0

_wso2is=`oc get pods | grep wso2is-joao | awk '{print $1}'`
echo $_wso2is
oc logs -f $_wso2is

oc port-forward $_wso2is 9443:9443

### Exemplo de ConfigMap 
oc create configmap user-mgt-conf --from-file=conf/user-mgt.xml
oc create configmap wso2is-as-km-master-datasources --from-file=master-datasources.xml
oc create configmap wso2is-carbon --from-file=k8s/conf/carbon.xml
