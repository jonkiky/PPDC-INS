# platform-etl-backend

Build Jar without testing. 

Test fails when run sbt assembly

```text
sbt 'set test in assembly := {}' clean assembly
```



```text
    java -server -Xms1G -Xmx6G -Xss1M -XX:+CMSClassUnloadingEnabled \
    -Dlogback.configurationFile=application.xml \
    -Dconfig.file=./application.conf \
    -classpath ./io-opentargets-etl-backend-assembly-0.5.0.jar  io.opentargets.etl.Main "reactome"

```

