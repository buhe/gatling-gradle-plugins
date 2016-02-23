# Install
--------------------------

execute:

	gradle uploadArchives

put lib directory into your project directory,add configuration to your build.gradle

	buildscript {
	    repositories {
	        maven {
	            url 'file:lib'
	        }
	    }
	    dependencies {
	        classpath 'io.buhe.gradle:gatling:0.0.1'
	    }
	}

# Configuration
--------------------------

	apply plugin: 'gatling'
	gatling {
	    exclude = '.*'
	    include = '^io.test.simulations.*'
	    breakOnFailure = false
	}


exclude is black list, include is white list, regular expressions are supported
both exclude and include may contain a multiple comma separated regexps

#Tasks
--------------------------

	:gatling     execute all match gatling script
	:gatling -Dgatling.include=io.test.simulations.TestSimulation execute a particular simulations
