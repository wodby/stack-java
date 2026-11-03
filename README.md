# Java application stack for Kubernetes on Wodby

Deploy Java applications on Kubernetes with Wodby.

This repository defines the Wodby stack manifests and default service
composition for Java.

<!-- wodby:generated:start -->

## Stack contract

- [Java stack on Wodby](https://wodby.com/stacks/java)
- [Browse Wodby application stacks](https://wodby.com/stacks)
- [Wodby stack documentation](https://wodby.com/docs/2.0/stacks/)
- [Stack manifest reference](https://wodby.com/docs/2.0/stacks/template/)

## Start from a boilerplate

Use one of the compatible boilerplates exposed by this stack's services to
start with Wodby CI build configuration:

- [Java boilerplate](https://github.com/wodby/java-boilerplate)

## Service definitions

- [Java service](https://github.com/wodby/service-java)
- [PostgreSQL service](https://github.com/wodby/service-postgres)
- [Valkey service](https://github.com/wodby/service-valkey)
- [Mailpit service](https://github.com/wodby/service-mailpit)
- [OpenSMTPD service](https://github.com/wodby/service-opensmtpd)
- [Gotenberg service](https://github.com/wodby/service-gotenberg)
- [Cloud PostgreSQL service](https://github.com/wodby/service-cloud-postgres)

## What's included

| Component / service | Default configuration |
| --- | --- |
| Java<br>`java` | required; enabled by default; links: `db` → `postgres`, `redis` → `valkey`, `sendmail` → `mailpit` |
| PostgreSQL<br>`postgres` | optional; disabled by default; volumes: `data` 20 GB |
| Valkey<br>`valkey` | optional; disabled by default |
| Mailpit<br>`mailpit` | optional; disabled by default |
| OpenSMTPD<br>`opensmtpd` | optional; disabled by default |
| Gotenberg<br>`gotenberg` | optional; disabled by default |
| Cloud PostgreSQL<br>`cloud-postgres` | optional; disabled by default |

Enabled optional services are selected by default but can be excluded when an
app is created. Disabled optional services are available but not selected by
default. Required services cannot be excluded.

## Validate the stack manifest

```bash
wodby stack validate-manifest stack.yml --org <org-id>
```

<!-- wodby:generated:end -->

## Choose a stack

This stack fits any Java application that builds into a runnable jar with Maven or a Gradle wrapper, such as one on
Quarkus, Micronaut, Javalin or no framework at all. For Spring Boot applications, the
[Spring Boot stack](https://github.com/wodby/stack-spring-boot) sets Spring Boot's own connection settings; for
Kotlin, use the [Kotlin stack](https://github.com/wodby/stack-kotlin).

## Optional services

The boilerplate needs no other service. PostgreSQL, Valkey and Mailpit are linked but disabled: enable one when the
application uses it, and the link sets its connection variables, such as `DB_HOST`, `DB_PORT`, `DB_NAME`,
`DB_USERNAME` and `DB_PASSWORD` for the database.

## Deploy this stack

Start from [Java boilerplate](https://github.com/wodby/java-boilerplate), or connect your own compatible source
repository.

Review service versions, storage, links, and optional components when creating
the application. The same stack can be reused across development, staging, and
production environments.

## Maintain a custom version

1. Fork this repository.
2. Edit the stack manifest.
3. Import the repository as a [Git-backed stack](https://wodby.com/docs/2.0/stacks/create/#create-a-git-backed-stack).

When replacing or renaming a stack service, update every related link target
and derivative reference. Stack-local names and referenced service names are
distinct identifiers.
