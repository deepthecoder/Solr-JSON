# Solr-JSON
This consists of JSON extractor Javascript+HTML file
You might face troubles with the CORS(Cross-Origin Resource Sharing)
I will be sharing my way of resolving the problem. You can come upp with some other way of solving the same. 


Solution:

In the Apache Solr directory in your local system...
Drill down to the following folder(this is with reference to Windows 10)
C:\ccc\cccc\cccc\solr-8.2.0\server\solr-webapp\webapp\WEB-INF

Here in this directory, you can find a web.xml file and you can see the following tag

```<web-app xmlns="http://java.sun.com/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd"
         version="2.5"
         metadata-complete="true">
```
After this piece of code paste the following piece of code mentioned below:

<filter>
  <filter-name>cross-origin</filter-name>
  <filter-class>org.eclipse.jetty.servlets.CrossOriginFilter</filter-class>
  <init-param>
    <param-name>allowedOrigins</param-name>
    <param-value>*</param-value>
  </init-param>
  <init-param>
    <param-name>allowedMethods</param-name>
    <param-value>GET,POST,OPTIONS,DELETE,PUT,HEAD</param-value>
  </init-param>
  <init-param>
    <param-name>allowedHeaders</param-name>
    <param-value>origin, content-type, accept</param-value>
  </init-param>
</filter>

<filter-mapping>
  <filter-name>cross-origin</filter-name>
  <url-pattern>/*</url-pattern>
</filter-mapping>

After pasting the following lines, save the web.cml file and RESTART the Solr Server!!
And you should be good with the code.
