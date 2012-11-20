What is wiked!
==============

__Wikis are completely inadequate to support the Knowledge Management of our Entreprise-class projects__ (they are only relevant for collaborative platforms such as wikipedia)

In order __to Keep together what varies together (source, documentation, etc.), let me introduce you__ the wiki killer for your projects: __wiked!__

__wiked! is a web site template to start all your pragmatic (and DRY) project KM with.__
--------------------------------------------------------------------------------------------


Main scenario
=============

1. You store the wiked! web site template next to your source code within your favorite Source Control Management system (SCM)
2. You personalize this site generator template first, with all your project stakes and specificities 
	$ editing whether the site.xml structure, the pom.xml project related informations, or the markdown files content
3. You let your Software Factory (SF) automatically (re)generate __your wiked! project's web site__ every time you change its template markdown content (i.e. any markdown file you add or modify for your project's documentation)
4. You may let your SF publish your updated static project web site whether on a dedicated web server, on hosted within your software factory web server, or simply bundled within the binary packages of your project 

At the end of the day, __wiked!__ is a nice solution to share all your project's domain models, ubiquitous language glossary, dev environments, developer welcome guide, acceptance tests scenarii, etc

[__It was really time for us to DRY our apps' Knowledge Management!__](http://tpierrain.blogspot.fr/2012/11/its-really-time-for-us-to-dry-our-apps.html)
--------------------------------------------------------------------------------

Side notes
==========

+ __wiked! leverages the maven site feature__ (cause I really hate to reinvent the wheel ;-)
    + It speeds up your learning curve of the maven site generation with markdown format
    + It provides you a structure and a nice look n feel for all your agiles & DDD projects web sites
    + the generation of your static web site from your markdown files is achieved via a call to the `mvn site` command-line on the __pom.xml__ for your web site (or your java project).


+ __to understand the wiked! genesis__, you may refer to the post:
    + [__Collaborative Artifacts as Code__](http://cyrille.martraire.com/2012/11/collaborative-artifacts-as-code/)

+ __to understand the maven site implementation used by wiked!, you may refer to the post:
	+ [__maven-sites-reloaded__](http://blog.akquinet.de/2012/04/12/maven-sites-reloaded/)


Many thanks
===========

To my mates:

+ [__Cyrille MARTRAIRE__](http://cyrille.martraire.com/), for having given me the inspiration to finally got rid of wikis for my entreprise-class projects
+ __Christophe LALLEMENT__ and __Alexandre NAVARRO__, for having given me the hint to rely on the existing maven site plugin.
 


wiked! installation guide
==========================

Prerequisites:
--------------
+ Maven 3 (and thus Java) is the only prerequisite for wiked! To install maven 3, you just have to [follow the guide here](http://maven.apache.org/download.html#Installation).


wiked! Installation:
-------------
__TO HAVE A QUICK LOOK ON THE WIKED! WEB SITE DEFAULT CONTENT__
1. Copy the content of the wiked! template somewhere on your disk 
	+ you have to copy the pom.xml but also the entire __src__ sub directories

2. Execute the __`mvn site`__ command-line on your wiked! root pom.xml file in order to generate the web site

__That's it!__ The generated static web site for your project is then browsable from within the file: __`(pom.xml directory)/target/site/index.html`__. 



---------------------	

__TO GENERATE THE FIRST VERSION OF THE WIKED! SITE FOR YOUR PROJECT__

1. Copy the content of the wiked! template on your project SCM working directory 
	+ you have to copy the pom.xml but also the entire __src__ sub directories
	+ For non-java projects, I suggest you to copy the wiked! template in a `documentation` directory at the root of your project SCM directory 


2. Edit the pom.xml file of the wiked! template and set the proper values for the properties:
    + name (name of your project)
    + groupId
    + artifactId
    + version
    + inceptionYear
    
    
3. Set the proper image for your web site banner. You can whether replace/overwrite the `(pom.xml directory)/src/site/resources/BannerImage.jpg` file, or store your own image in the directory `(pom.xml directory)/src/site/resources/` and refer it within the bannerLeft.src__ property of the `(pom.xml directory)/src/site/site.xml` file.


4. Edit the breadcrumbs items of the `(pom.xml directory)/src/site/site.xml` file in order to set the URLs of your software factory, sonar, scm...


5. Execute the __`mvn site`__ command-line on your wiked! root pom.xml file in order to generate a classic and static web site


__That's it! The generated static web site for your project is generated and browsable from within the file: `(pom.xml directory)/target/site/index.html`__. 



wiked! Usage:
------
+ Every developer should now put all the project documentation as markdown files stored within your wiked! web site, just next to your code under the control of your SCM (thus under the `(pom.xml directory)/src/site/markdown/` directory, or under `(pom.xml directory)/src/site/resources/` for images and other referenced files)
+ Make your software factory regenerating the wiked! web site of your project on every change commited/pushed to your SCM. It is simply a call to __`mvn site`__ on your wiked! pom.xml file.
+ __Warning:__ In some cases (like when changing the project name within the pom.xml file), you will have to fully regenerate the web site. In those cases, call `mvn clean` just before the call to `mvn site`. 

