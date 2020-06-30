## LOG ROTATION
https://medium.com/@pamodaaw/customizing-wso2-log-files-a338139620fe

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
oc apply -f wso2is-as-km-deployment.xml
```

### 4 - Probar su despliegue utilizando port forwarding
```
oc get pods | grep wso2is-%%NOMBRE-PARTICIPANTE%% | awk '{print $1}'`
oc port-forward %%POD NAME%% 9443:9443
```
https://localhost:9443/carbon
admin / admin