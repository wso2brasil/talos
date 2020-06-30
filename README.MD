oc create configmap master-datasource-joao --from-file=master-datasources.xml
oc create configmap mysql-jdbc-driver-joao --from-file=mysql-connector-java-5.1.46.jar
oc create configmap user-mgt-joao --from-file=user-mgt.xml