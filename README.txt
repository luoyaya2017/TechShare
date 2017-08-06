***************************************************************************
 * Copyright 2017 pers:luoyaya
 *
 * 
 * 
 ***************************************************************************

#####RESTful API  documentation

##JDK
*
*run on jdk1.7.0_60
*
*
##Initialise database
*database version:MySQL Server 5.7
*OS:windows 7 x64
*create database called:spring
*use annotaion way to generate table
*run junit test class method:testSchemaExport() to generate department and employee tables
*database username and password can config in resources/jdbc.properties
*

##build deployable .war file
**can use Ant to set up, compile, WAR, and deploy.
**
**<target name="default" depends="setup,compile,buildwar,deploy"></target>
**then execute one click in Eclipse to run that Ant target. Here are examples of each of the steps:
**
**Preconditions
**
**
**
**${basedir}/src: Java files, properties, XML config files
**${basedir}/web: Your JSP files
**${basedir}/web/lib: Any JARs required at runtime
**${basedir}/web/META-INF: Your manifest
**${basedir}/web/WEB-INF: Your web.xml files
**Set up
**
**Define a setup task that creates the distribution directory and copies any artifacts that need to be WARred directly:
**
**<target name="setup">
**    <mkdir dir="dist" />
**    <echo>Copying web into dist</echo>
**    <copydir dest="dist/web" src="web" />
**    <copydir dest="dist/web/WEB-INF/lib" src="${basedir}/../web/WEB-INF/lib" />
**</target>
**Compile
**
**Build your Java files into classes and copy over any non-Java artifacts that reside under src but need to be available at runtime (e.g. properties, XML files, etc.):
**
**<target name="compile">
**   <delete dir="${dist.dir}/web/WEB-INF/classes" />
**    <mkdir dir="${dist.dir}/web/WEB-INF/classes" />
**    <javac destdir="${dist.dir}/web/WEB-INF/classes" srcdir="src">
**        <classpath>
**            <fileset dir="${basedir}/../web/WEB-INF/lib">
**                  <include name="*" />
**           </fileset>
**        </classpath>
**    </javac>
**    <copy todir="${dist.dir}/web/WEB-INF/classes">
**        <fileset dir="src">
**            <include name="**/*.properties" />
**            <include name="**/*.xml" />
**        </fileset>
**    </copy>
**</target>
**Build WAR

**Create the WAR itself:

**<target name="buildwar">
**    <war basedir="${basedir}/dist/web" destfile="My.war"
**     webxml="${basedir}/dist/web/WEB-INF/web.xml">
**        <exclude name="WEB-INF/**" />
**        <webinf dir="${basedir}/dist/web/WEB-INF/">
**            <include name="**/*.jar" />
**        </webinf>
**    </war>
**</target>
**Deploy
**
**Finally, you can set up a task to deploy the WAR directly into your Tomcat deploy location:
**
**<target name="deploy">
**    <copy file="My.war" todir="${tomcat.deploydir}" />
**</target>





