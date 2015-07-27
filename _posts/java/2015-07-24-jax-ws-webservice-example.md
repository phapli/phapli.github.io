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

6. To generate a jax-ws, we need some libraries. 
	* jaxb-impl.jar
	* jaxws-api.jar
	* jaxws-rt.jar
	* saaj-impl.jar
	* stax-ex.jar
	* streambuffer.jar
	
	Please add them to "__WebContent/WEB-INF/lib__"
	
7. Using wsgen (a tool of JDK) to generate Web service. Open terminal, go to project folder, and run this script.

{% highlight bash %}
wsgen -s src -d build/classes -cp build/classes com.phapli.helloworld.HelloWorldImpl
{% endhighlight %}

	![wsgen](/resources/2015-07-24-jax-ws-webservice-example/3.PNG "wsgen")
	
8. Refresh your eclipse project to see the result. 

	![server project](/resources/2015-07-24-jax-ws-webservice-example/4.PNG "server project")
	
9. Run project in server (such as tomcat, jboss ...). Go to http://localhost:8080/HelloWorld/HelloWorld to access the Web service.

	![wsdl](/resources/2015-07-24-jax-ws-webservice-example/6.PNG "wsdl")
	
## Create Client.

1. In Eclipse IDE, menu bar, select "__File__" >> "__New__" >> "__Project__", choose "__Java Project__".

	![New Java Project](/resources/2015-07-24-jax-ws-webservice-example/5.PNG "New Java Project")
	
2. Use wsimport (a tool of JDK) to generate Stub from wsdl url. Open terminal, go to project folder, and run this script.
	
{% highlight bash %}
wsimport -d src -extension -keep -p com.tomica.coremb -XadditionalHeaders http://localhost:8080/HelloWorld/HelloWorld?wsdl
{% endhighlight %}

	![wsimport](/resources/2015-07-24-jax-ws-webservice-example/7.PNG "wsimport")	

3. Create Client class with main method to test this service.	

{% highlight java %}
package com.phapli.client;

import java.net.MalformedURLException;
import java.net.URL;

import com.phapli.helloworld.HelloWorld;
import com.phapli.helloworld.HelloWorldImplService;

public class Client {

	public static void main(String[] args) {
		try {
			// init webservice port
			HelloWorldImplService service = new HelloWorldImplService(new URL(
					"http://localhost:8080/HelloWorld/HelloWorld?wsdl"));
			HelloWorld port = service.getHelloWorldImplPort();
			
			// call hello method
			String response = port.hello("phapli");

			System.out.println(response);

		} catch (MalformedURLException e) {
			e.printStackTrace();
		}
	}

}
{% endhighlight %}	
 
4. Run this class to see the result.

##Reference
<http://www.mkyong.com/webservices/jax-ws/deploy-jax-ws-web-services-on-tomcat/>