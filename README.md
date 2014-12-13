tomcat-redis-session-manager
============================

基于redis的tomcat session同步解决方案


##tomcact配置

* 将编译后target/tomcat-redis-session-manager-1.0.zip/lib内一下jar拷贝的tomcat/lib下

* tomcat/conf/server.xml配置

         <Valve className="com.whosenet.tomcat.redissessions.RedisSessionHandlerValve" />
         <Manager className="com.whosenet.tomcat.redissessions.RedisSessionManager"
             host="localhost" <!-- optional: defaults to "localhost" -->
             port="6379" <!-- optional: defaults to "6379" -->
             database="0" <!-- optional: defaults to "0" -->
             maxInactiveInterval="60" <!-- optional: defaults to "60" (in seconds) -->
             sessionPersistPolicies="PERSIST_POLICY_1,PERSIST_POLICY_2,.." <!-- optional -->
             sentinelMaster="SentinelMasterName" <!-- optional -->
             sentinels="sentinel-host-1:port,sentinel-host-2:port,.." <!-- optional --> />

* 项目使用
     session.removeAttribute(key)
     session.setAttribute(key, newAttributeValue)

## license
* [forked from jcoleman/tomcat-redis-session-manager](http://github.com/jcoleman/tomcat-redis-session-manager)
* Licensed under the Apache License 2.0.

修改内容
* 项目构建由gradle改为Maven,适应部分用户项目需要


