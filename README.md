Install appropriate plugin for spring:
`plugins {
    id 'com.palantir.docker-run' version '0.22.1'
}`

Then put in gradle appropriate configuration:

`dockerRun {
    name 'couchbase'
    image 'adriankubica/couchbase'
    ports '8091:8091', '8092:8092', '8093:8093', '8094:8094', '11210:11210'
    env 'COUCHBASE_ADMINISTRATOR_USERNAME':'admin',
        'COUCHBASE_ADMINISTRATOR_PASSWORD':'secret',
        'COUCHBASE_BUCKET':'fraud-detector-db',
        'COUCHBASE_RBAC_USERNAME':'fraud-detector-db',
        'COUCHBASE_RBAC_PASSWORD':'secret',
        'COUCHBASE_RBAC_NAME':'fraud-detector-db',
        'CLUSTER_NAME':'dev'
    daemonize true
    clean true
}`

Run docker iamge from `gradlew` with command: `dockerRun` 