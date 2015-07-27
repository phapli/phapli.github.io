---
layout: post
title: Jax-ws Webservice Example
comments: true
---

>[Jax-ws](jax-ws.java.net) (Java API for XML Web Services) is a Java API for developing Web service with XML format (SOAP). 

In this port, I will show you how to create a SOAP Web service in eclipse and build a client to test this service.    

##Create Web service.

1. In Eclipse IDE, menu bar, select "__File__" >> "__New__" >> "__Project__", choose "__Dynamic Web Project__".

	![New Dynamic Web Project](/resources/2015-07-24-jax-ws-webservice-example/1.PNG "New Dynamic Web Project")

2. Follow the instruction and finish.
	
	![New Dynamic Web Project](/resources/2015-07-24-jax-ws-webservice-example/2.PNG "New Dynamic Web Project")
	
3. Create HelloWorld interface with hello method.	
{% highlight java %}
package com.phapli.helloworld;
/*
 * @author: phapli
 */

import javax.jws.WebMethod;
import javax.jws.WebParam;
import javax.jws.WebService;

@WebService
public interface HelloWorld {

	@WebMethod
	public String hello(@WebParam(name = "name") String name);

}
{% endhighlight %}
4. Create HelloWorldImpl class, which is implementation of HelloWorld.
{% highlight java %}
package com.phapli.helloworld;

/*
 * @author: phapli
 */

import javax.jws.WebService;

@WebService(endpointInterface = "com.phapli.helloworld.HelloWorld")
public class HelloWorldImpl implements HelloWorld {

	@Override
	public String hello(String name) {
		return "Hello " + name;
	}

}
{% endhighlight %}
5. In "__WebContent/WEB-INF__" folder, create two files (_sun-jaxws.xml_, and _web.xml_)
{% highlight xml %}
<?xml version="1.0" encoding="UTF-8"?>  
<endpoints xmlns="http://java.sun.com/xml/ns/jax-ws/ri/runtime" version="2.0">  
  <endpoint  
	 name="HelloWorld"  
	 implementation="com.phapli.helloworld.HelloWorldImpl"  
	 url-pattern="/HelloWorld"/>  
</endpoints> 
{% endhighlight %}
{% highlight java %}
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://java.sun.com/xml/ns/javaee" xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd" id="WebApp_ID" version="2.5">
  <display-name>HelloWorld</display-name>
  <listener>
	<listener-class>  
		com.sun.xml.ws.transport.http.servlet.WSServletContextListener  
	 </listener-class>
  </listener>
  <servlet>
	<servlet-name>HelloWorld</servlet-name>
	<servlet-class>  
		com.sun.xml.ws.transport.http.servlet.WSServlet
	</servlet-class>
  </servlet>
  <servlet-mapping>
	<servlet-name>HelloWorld</servlet-name>
	<url-pattern>/HelloWorld</url-pattern>
  </servlet-mapping>
</web-app>
{% endhighlight %}



In Eclipse IDE, menu bar, select "__Help__" >> "__Install New Software...__" , put the Hibernate Url here.

![Install Hibernate Plugin](/resources/2015-07-22-using-hibernate-reverse-engineering-in-eclipse/1.PNG "Install Hibernate Plugin")

Following the instruction to complete installing.
Finally, restart Eclipse to take effect.

##New Hibernate Configuration

1. Open Hibernate Perspective in Eclipse.
 
	Select "__Windows__" >> "__Open Perspective__" >> "__Others...__" , choose "__Hibernate__".
	
2. New a hibernate configuration.

	1. In Hibernate Perspective, right click and select "__Add Configuration...__" or click on "__+__" button.
	
	![New Hibernate Configuration](/resources/2015-07-22-using-hibernate-reverse-engineering-in-eclipse/2.PNG "New Hibernate Configuration")
	
	2. In "__Edit Configuration__" dialog box,
		* In "__Project__" box, click on the "__Browse...__" button to select your project.
		* In "__Database Connection__" box, click "__New...__" button to create your database settings.
		* In "__Configuration File__" box, click "__Setup__" button to create a new or use existing "__Hibernate configuration file__", hibernate.cfg.xml.
		
		![Open Hibernate Perspective](/resources/2015-07-22-using-hibernate-reverse-engineering-in-eclipse/3.PNG "Open Hibernate Perspective")
		
		*hibernate.cfg.xml example for MySql connection*
		
		![hibernate.cfg.xml](/resources/2015-07-22-using-hibernate-reverse-engineering-in-eclipse/4.PNG "hibernate.cfg.xml")
		
		* Refresh to see the result (all tables from your database)
		
		![Tables](/resources/2015-07-22-using-hibernate-reverse-engineering-in-eclipse/5.PNG "Tables")
		
		
3. Run Hibernate Code Generation.
	1. In "__Hibernate Perspective__", click "__Hibernate code generation__" icon (see below figure) and select "__Hibernate Code Generation Configuration__"
	
	![Hibernate Code Generation](/resources/2015-07-22-using-hibernate-reverse-engineering-in-eclipse/6.PNG "Hibernate Code Generation")

	2. Create a new configuration, fill "__name__" field, select "__Console Configuration__" at the configuration which you have created, browse to "__Output directory__" and check option "__Reverse engineer from JDBC Connection__".

	![Input](/resources/2015-07-22-using-hibernate-reverse-engineering-in-eclipse/7.PNG "Input")
	
	3. In "__Exporters__" tab, select options that you want to generate.
	
	![Generate](/resources/2015-07-22-using-hibernate-reverse-engineering-in-eclipse/8.PNG "Generate")

	4. Run, and see the result.
	
	![Result](/resources/2015-07-22-using-hibernate-reverse-engineering-in-eclipse/9.PNG "Result")


##Reference
<http://www.hibernate.org/subprojects/tools.html>

<http://www.jboss.org/tools/download>

<http://www.mkyong.com/hibernate/how-to-generate-code-with-hibernate-tools/>