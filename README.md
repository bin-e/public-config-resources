# spring-config-resources-pub
spring-config-resources-public for [Spring Cloud Config](https://spring.io/projects/spring-cloud-config)

## 설정파일 적용 순서
아래의 순서대로 읽어들이며 없는 이전에 읽은 properties에 없는 값들이 추가된다.
1. {service name}-{profile}.yml
1. application-{profile}.yml
1. {service name}.yml
1. application.yml

## 설정파일 작성 방법
기본설정파일은 로컬개발 환경에서 모든 서비스(config,discovery,gateway,sub-system ...)를 구동하는 상황을 기준으로 한다.
'*-local.yml'은 gitignore로 지정되어 있다. 로컬개발시에는 이 repo를 clone하여 config서버가 local repogitory에서 설정을 읽어들이도록 한다.

* application.yml: 모든서비스에 적용되는 공통항목을 작성한다.
* application-dev.yml: 모든서비스에 적용되는 공통항목 중 __개발 환경__에서 달라지는 부분만을 작성한다. (development)
* application-prod.yml: 모든서비스에 적용되는 공통항목 중 __운영 환경__에서 달라지는 부분만을 작성한다. (production)
* application-{profile}.yml: 모든서비스에 적용되는 공통항목 중 특정 환경(eg, local:로컬개발)에서 달라지는 부분만을 작성한다.
* {service name}.yml: 로컬개발 환경에서 구동될 때 필요한 사항중 application.yml에 포함되지 않는 __이 서비스만의 설정__을 작성한다.
* {service name}-dev.yml: 이 서비스가 __개발 환경__에서 구동될 때 달라지는 부분을 작성한다.
* {service name}-prod.yml: 이 서비스가 __운영 환경__에서 구동될 때 달라지는 부분을 작성한다.
* {service name}-{profile}.yml: 해당 환경(eg, local:로컬개발)에서 해당 서비스에 적용될 항목만 작성한다.
