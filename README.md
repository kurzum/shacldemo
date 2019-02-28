# shacldemo

## install
`sudo apt-get install tomcat8`

edit ~/.m2/settings.xml, add:

```
<server>
    <id>TomcatServer</id>
    <username>admin</username>
    <password>admin</password>
</server>
```


Edit /etc/tomcat8/tomcat-users.xml

```
  <role rolename="tomcat"/>
  <role rolename="manager-gui"/>
  <role rolename="manager-script"/>
  <user username="admin" password="admin" roles="tomcat,manager-gui,manager-script"/>
```


## deploy

```
git clone https://github.com/AKSW/RDFUnit.git
cd RDFUnit
mvn install 
cd rdfunit-shacl-ws
tomcat7:deploy
```
## NOTE
The war is also deployed for webid at 

* http://databus.dbpedia.org:8080/shacl/validate?d=http://kurzum.net/webid.ttl&A&s=https://raw.githubusercontent.com/dbpedia/webid/master/voc/webid-shacl.ttl

## KNOWN ISSUES

* parameter `s` is not working

* Test Case URLs have to be entered hard coded into the:

`nano src/main/java/org/aksw/rdfunit/validate/ws/ShaclWS.java`

```
 .addSchemaURI("none", "https://raw.githubusercontent.com/kurzum/shacldemo/master/test-case1.ttl").build();
```

then recompile and redeploy

```
mvn clean install -DskipTests=true
cd rdfunit-shacl-ws
tomcat7:deploy

```

## Use

* see all parameters:
http://localhost:8080/shacl/validate


* in browser:

http://localhost:8080/shacl/validate?d=https://raw.githubusercontent.com/kurzum/shacldemo/master/test.ttl



or with local file and shacl:
```

curl --data-urlencode d="https://raw.githubusercontent.com/kurzum/shacldemo/master/test.ttl"   "http://localhost:8080/shacl/validate"
```





