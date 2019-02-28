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
The war is also deployed at http://databus.dbpedia.org:8080/shacl/validate?d=http://kurzum.net/webid.ttl&A&s=https://raw.githubusercontent.com/dbpedia/webid/master/voc/webid-shacl.ttl


## Use

* see all parameters:
http://localhost:8080/shacl/validate


* in browser:

http://localhost:8080/shacl/validate?d=http://kurzum.net/webid.ttl&A&s=https://raw.githubusercontent.com/dbpedia/webid/master/voc/webid-shacl.ttl

or curl

```
curl --data-urlencode d="http://kurzum.net/webid.ttl" --data-urlencode s="https://raw.githubusercontent.com/dbpedia/webid/master/voc/webid-shacl.ttl"  "http://localhost:8080/shacl/validate"
```

or with local file and online shacl:





