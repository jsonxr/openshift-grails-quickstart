Run Grails on OpenShift
============================

This git repository helps you get up and running quickly w/ a tomcat installation and Grails on OpenShift.
It is based on the tomcat work done here https://github.com/openshift/openshift-tomcat-quickstart

Grails requires medium instance
----------------------------

Contact RedHat and request that they increase your account to allow for medium instances.  Grails will not
run on the small instance.


Create a DIY app on OpenShift
----------------------------

Create an account at http://openshift.redhat.com/ , don't forget to create a namespace and install client tools as well.

Create a DIY application

    rhc app create -a grailstest -t diy-0.1 -g medium

Get Tomcat and Grails running
----------------------------
Grab this quickstart codes and make it working for you!

    cd grailstest
    git remote add upstream -m master git://github.com/jasonxrowland/openshift-grails-quickstart.git
    git pull -s recursive -X theirs upstream master
    git push

You can checkout the grails app at:

    http://grailstest-$yournamespace.rhcloud.com

Grails
----------------------------
The deploy command calls "grails prod war".  You will need to modify .openshift/action_hooks/deploy if you would like to deploy to test or dev.