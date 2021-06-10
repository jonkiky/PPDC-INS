# platform-etl-backend

Build Jar without testing. 

Test fails when run sbt assembly

```text
sbt 'set test in assembly := {}' clean assembly
```

