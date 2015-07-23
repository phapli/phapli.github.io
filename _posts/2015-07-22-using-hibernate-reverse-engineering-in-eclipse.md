---
layout: post
title: Using Hibernate Reverse Engineering In Eclipse
comments: true
---

>[Hibernate](http://hibernate.org) (Hibernate ORM) is an object-relational mapping framework, that mapping an object-oriented domain model in Java to a traditional relational database.

There are many ways to use this framework, and in this post, I will show you how using Hibernate Reverse Tool to generate Java object from exist MySql database.   

##Install Hibernate Tool in Eclipse.

Firstly, You must check your version of Eclipse or download [Eclipse here](https://www.eclipse.org/downloads).
After that, searching on the internet to find correct version of Hibernate plugin. Here is for Eclipse Luna 4.4.2: 

```
http://download.jboss.org/jbosstools/updates/stable/luna/
```

In Eclipse IDE, menu bar, select "__Help__" >> "__Install New Software...__" , put the Hibernate Url here.

![alt text](https://cloud.githubusercontent.com/assets/1092116/8832483/8bf21374-30d3-11e5-8a41-26d2467066fd.PNG "Logo Title Text 1")

Following the instruction to complete installing.
Finally, restart Eclipse to take effect.

##New Hibernate Configuration

1. Open Hibernate Perspective in Eclipse.
 
	Select "__Windows__" >> "__Open Perspective__" >> "__Others...__" , choose "__Hibernate__".

2. New a hibernate configuration.

	i. In Hibernate Perspective, right click and select "__Add Configuration...__" or click on "__+__" button.
	2. In "__Edit Configuration__" dialog box,
		* In "__Project__" box, click on the "__Browse...__" button to select your project.
		* In "__Database Connection__" box, click "__New...__" button to create your database settings.
		* In "__Configuration File__" box, click "__Setup__" button to create a new or use existing "__Hibernate configuration file__", hibernate.cfg.xml.
	
		*hibernate.cfg.xml example for MySql connection*
		
		```xml
			<?xml version="1.0" encoding="utf-8"?>
			<!DOCTYPE hibernate-configuration PUBLIC
			"-//Hibernate/Hibernate Configuration DTD 3.0//EN"
			"http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
			<hibernate-configuration>
				<session-factory>
					<property name="hibernate.connection.driver_class">com.mysql.jdbc.Driver</property>
					<property name="hibernate.connection.password">MTIzYWJjISEh</property>
					<property name="hibernate.connection.url">jdbc:mysql://192.168.1.11:3306/Token_DB_FPT?autoReconnect=true</property>
					<property name="hibernate.connection.username">username</property>
					<property name="hibernate.dialect">org.hibernate.dialect.MySQLDialect</property>
					<property name="hibernate.search.autoregister_listeners">false</property>
					<property name="hibernate.show_sql">false</property>
					<property name="hibernate.validator.apply_to_ddl">false</property>
				</session-factory>
			</hibernate-configuration>
		```
		
3. Run Hibernate Code Generation.
	1. In "__Hibernate Perspective__", click "__Hibernate code generation__" icon (see below figure) and select "__Hibernate Code Generation Configuration__"
	












##Reference
<http://www.hibernate.org/subprojects/tools.html>
<http://www.jboss.org/tools/download>