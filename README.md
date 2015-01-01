tomcat-redis-session-manager
============================

基于redis的tomcat session同步解决方案

##tomcact配置

* 将编译后target/tomcat-redis-session-manager-1.0.zip/lib内以下jar拷贝到tomcat/lib下
    - commons-pool2-2.2.jar
    - jedis-2.5.2.jar
    - tomcat-redis-session-manager-1.0.jar

* redis-server自行配置启动

* 配置参数(tomcat7/conf/context.xml文件<Context>节点下增加如下内容)

         <Valve className="com.whosenet.tomcat.redissessions.RedisSessionHandlerValve" />
         <Manager className="com.whosenet.tomcat.redissessions.RedisSessionManager"
             host="localhost" <!-- optional: defaults to "localhost" -->
             port="6379" <!-- optional: defaults to "6379" -->
             database="0" <!-- optional: defaults to "0" -->
             maxInactiveInterval="60" <!-- optional: defaults to "60" (in seconds) -->
             sessionPersistPolicies="PERSIST_POLICY_1,PERSIST_POLICY_2,.." <!-- optional -->
             sentinelMaster="SentinelMasterName" <!-- optional -->
             sentinels="sentinel-host-1:port,sentinel-host-2:port,.." <!-- optional --> />

* 示例配置(tomcat7/conf/context.xml文件<Context>节点下增加如下内容)

          <Valve className="com.whosenet.tomcat.redissessions.RedisSessionHandlerValve" />

          <Manager className="com.whosenet.tomcat.redissessions.RedisSessionManager"
             host="localhost"
             port="6379"
             database="0"
             maxInactiveInterval="60"
        	/>

* 项目使用

    - session.removeAttribute(key)
    - session.setAttribute(key, newAttributeValue)

##修改内容
* 项目构建由gradle改为Maven,适应部分用户项目需要

## license
* [forked from jcoleman/tomcat-redis-session-manager](http://github.com/jcoleman/tomcat-redis-session-manager)
*  Licensed under the Apache License 2.0.


