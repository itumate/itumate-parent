# itumate-parent

**itumate-parent** 作为根依赖并没有直接引入 `Eureka` 相关依赖。

Spring Boot 默认输出为 `JSON` 格式, 直接引用 `spring-cloud-starter-netflix-eureka-*` 依赖会导致
输出为 `XML` 格式。

所以, 需要在 `Eureka Server Application` 中引入 `spring-cloud-starter-netflix-eureka-server` 依赖。
而在 `Eureka Client Application` 中引入 `spring-cloud-starter-netflix-eureka-client` 依赖。

---

当前跟节点包含依赖:

**Spring Boot** 相关
```xml
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-web</artifactId>
</dependency>
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-test</artifactId>
	<scope>test</scope>
</dependency>

<!--Spring Boot Actuator-->
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-actuator</artifactId>
</dependency>

<!--Spring Boot AOP-->
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-aop</artifactId>
</dependency>
```

**Spring Cloud** 相关
```xml
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-config-server</artifactId>
</dependency>

<dependency>
	<groupId>org.springframework.cloud</groupId>
	<artifactId>spring-cloud-starter-config</artifactId>
</dependency>

<dependency>
	<groupId>org.springframework.cloud</groupId>
	<artifactId>spring-cloud-starter-netflix-hystrix</artifactId>
</dependency>

<!--Spring Cloud Zuul-->
<dependency>
	<groupId>org.springframework.cloud</groupId>
	<artifactId>spring-cloud-starter-netflix-zuul</artifactId>
</dependency>
<!--Spring Cloud Feign-->
<dependency>
	<groupId>org.springframework.cloud</groupId>
	<artifactId>spring-cloud-starter-openfeign</artifactId>
</dependency>

<!--Spring Cloud Config-->
<dependency>
	<groupId>org.springframework.cloud</groupId>
	<artifactId>spring-cloud-starter-config</artifactId>
</dependency>
```

**时间 API**
```xml
<dependency>
	<groupId>joda-time</groupId>
	<artifactId>joda-time</artifactId>
	<version>${joda.time.version}</version>
</dependency>
```

**DB API**
```xml
<dependency>
	<groupId>mysql</groupId>
	<artifactId>mysql-connector-java</artifactId>
	<version>${mysql.version}</version>
	<scope>runtime</scope>
</dependency>
```

**其他**
```xml
<!--Ali-->
<dependency>
	<groupId>com.alibaba</groupId>
	<artifactId>druid</artifactId>
	<version>${ali.druid.version}</version>
</dependency>
<dependency>
	<groupId>com.alibaba</groupId>
	<artifactId>fastjson</artifactId>
	<version>${ali.fastjson.version}</version>
</dependency>

<!--commons3-->
<dependency>
	<groupId>org.apache.commons</groupId>
	<artifactId>commons-lang3</artifactId>
	<version>${common.lang3.version}</version>
</dependency>

<!--swagger2-->
<dependency>
	<groupId>io.springfox</groupId>
	<artifactId>springfox-swagger2</artifactId>
	<version>${swagger2.version}</version>
</dependency>
<dependency>
	<groupId>io.springfox</groupId>
	<artifactId>springfox-swagger-ui</artifactId>
	<version>${swagger2.version}</version>
</dependency>
```

# 问题

引入 `freemarker` 依赖时存在错误或BUG，需要引入 `v2.3.28` 版本或者直接引入 SpringCloud 快速集成 `spring-boot-starter-freemarker` 依赖。

```xml
<dependency>
	<groupId>org.freemarker</groupId>
	<artifactId>freemarker</artifactId>
	<version>2.3.23</version>
</dependency>
```

输出错误日志部分如下：

```
FreeMarker template error (DEBUG mode; use RETHROW in production!): Template importing failed (for parameter value "/spring.ftl"): 
```