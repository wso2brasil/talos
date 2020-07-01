## DÍA 3
### 1 - Descargar el WSO2 Integration Studio
https://wso2.com/integration/integration-studio/

### 2 - Descargar el repositorio git para ejecutar las aplicaciones tomcat

. Crear dos Service Providers (pickup-dispatch y pickup-manager )
. Inboud Authentication Configuration -> OAuth/OpenID -> Configure
. Guardar los Consumer Key y Secret de los dos Service Providers
> 
. Editar tomcat/webapps/pickup-manager/WEB-INF/classes/manager.properties
. Editar tomcat/webapps/pickup-dispatch/WEB-INF/classes/dispatch.properties
. Iniciar el Tomcat 
```
catalina.sh run (linux / mac)
catalina.bat run (windows)
```
Para poder configurar TOTP es necesario cambiar su deployment para incorporar este nuevo configmap
```
oc create configmap application-authentication --from-file=application-authentication.xml
```
Cambie también el archivo wso2is-as-km-deployment-totp.yaml con su nombre donde está escrito "joao"
```
ej: 
metadata:
  name: wso2is-joao
```


## DÍA 2
### 1 -Por favor, hacer un comentario en este ticket con su cuenta de WSO2
https://support.wso2.com/jira/browse/BANCOPICHINCHASUB-144

### 2 - Desplegar su contenedor de Identity Server con las siguientes instrucciones:
```
git clone https://github.com/wso2brasil/talos.git
```
Entrar en la carpeta talos/openshift
Editar los archivos:
master-datasources.xml
wso2is-as-km-deployment.xml

### 3 - Ejecutar los siguientes comandos:
```
oc create configmap master-datasource-%%NOMBRE-PARTICIPANTE%% --from-file=master-datasources.xml
oc apply -f wso2is-as-km-deployment.yaml
```

### 4 - Probar su despliegue utilizando port forwarding
```
oc get pods | grep wso2is-%%NOMBRE-PARTICIPANTE%% | awk '{print $1}'`
oc port-forward %%POD NAME%% 9443:9443
```
https://localhost:9443/carbon
admin / admin

## DÍA 1

### LOG ROTATION
https://medium.com/@pamodaaw/customizing-wso2-log-files-a338139620fe

### 1 - Crear las tablas
```
oc get pods 
oc rsh mariadb-101-rhel7-1-gwhg2
mysql -u root -h mariadb-101-rhel7-1-gwhg2 -p
use <database_name>;
source /tmp/mysql5.7.sql
source /tmp/apimgt-mysql5.7.sql
```
