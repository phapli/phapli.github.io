---
layout: post
title: Đặt tên resource xml một cách hiệu quả trong lập trình Android
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