# dtool config generator container image

[![Docker Image Version (latest semver)](https://img.shields.io/docker/v/jotelha/dtool-config-generator?label=dockerhub)](https://hub.docker.com/repository/docker/jotelha/dtool-config-generator) [![GitHub Workflow Status](https://img.shields.io/github/workflow/status/livmats/dtool-config-generator-container-image/publish)](https://github.com/livmats/dtool-config-generator-container-image/actions?query=workflow%3Apublish)

Part of https://github.com/livmats/dtool-lookup-server-container-composition.

## Build

Run

    docker build -t jotelha/dtool-config-generator -f compose/production/dtool_config_generator/Dockerfile .

## Run

For overriding default templates and binding

    docker run -it -p 5010:5000 -e FLASK_BINDING="0.0.0.0:5000" -v $(pwd)/compose/production/dtool_config_generator/templates:/templates jotelha/dtool-config-generator

## Environment variables

* `SCRIP_NAME`
* `FLASK_BINDING = 127.0.0.1:5000`
* `SSL_CERT_FILE`
* `SSL_KEY_FILE`

## Flask config

* `USER_CONFIRMATION_EMAIL_SENDER = 'admin@my.domain'`
* `USER_CONFIRMATION_EMAIL_RECIPIENT = 'someone@some.domain'`

* `MAIL_SERVER = 'localhost'`
* `MAIL_PORT = 587`
* `MAIL_USE_TLS = True`
* `MAIL_USE_SSL = False`
* `MAIL_USERNAME = 'admin@my.domain'`
* `MAIL_PASSWORD = 'JeHfVL2XkY4PXzcz'`
* `MAIL_DEFAULT_SENDER = 'admin@my.domain'`

* `LDAP_HOST="ldap://ldap"`
* `LDAP_PORT=1389`
* `LDAP_USE_SSL=False`
* `LDAP_BASE_DN="dc=example,dc=org"`
* `LDAP_USER_DN="ou=users"`
* `LDAP_USER_RDN_ATTR="cn"`
* `LDAP_USER_LOGIN_ATTR="uid"`
* `LDAP_USER_OBJECT_FILTER="(objectclass=*)"`
* `LDAP_SEARCH_FOR_GROUPS=False`
* `LDAP_USER_SEARCH_SCOPE="SUBTREE"`

* `STORAGEGRID_HOST="s3.storagegrid.server"`
* `STORAGEGRID_ACCOUNT_ID = '12345671234567123456'`
* `STORAGEGRID_USERNAME = 'storagegrid_admin'`
* `STORAGEGRID_PASSWORD = 'storagegrid_admin_password'`
`
* `DTOOL_CONFIG_GENERATOR_ADMIN_USER_ID = 12345`
* `DTOOL_CONFIG_GENERATOR_ADMIN_USER_NAME = 'testuser'`

* `DTOOL_README_TEMPLATE = "/templates/dtool_readme.yml"`
* `DTOOL_CONFIG_TEMPLATE = "/templates/dtool.json"`

* `STORAGEGRID_DEFAULT_GROUP_UUID = "00000000-0000-0000-0000-000000000000"`
* `STORAGEGRID_S3_CREDENTIALS_EMBEDDED_IN_CONFIG = True`
* `STORAGEGRID_DEFAULT_S3_ACCESS_KEY_VALIDITY_PERIOD = 86400*365*2  # two years in seconds`
