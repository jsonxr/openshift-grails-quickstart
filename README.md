Run Grails on OpenShift
============================

This git repository helps you get up and running quickly w/ a tomcat installation and Grails on OpenShift.
It is based on the tomcat work done here https://github.com/openshift/openshift-tomcat-quickstart


Create a DIY app on OpenShift
----------------------------

Create an account at http://openshift.redhat.com/ , don't forget to create a namespace and install client tools as well.

Contact RedHat and request that they increase your account to allow for medium gear sizes.  Grails requires a medium gear size.

Create a DIY application

    rhc app create -a grailstest -t diy-0.1 -g medium

Get Tomcat and Grails running
----------------------------
Grab this quickstart code and pull it into your repository.

    cd grailstest
    git remote add upstream -m master git://github.com/jasonxrowland/openshift-grails-quickstart.git
    git pull -s recursive -X theirs upstream master
    git push

You can view the grails app at:

    http://grailstest-$yournamespace.rhcloud.com

It may take a while for tomcat to extract the war file.  If you want to watch the progress of the server, you can log into the server and tail the log file:

    tail -f $OPENSHIFT_LOG_DIR/catalina.out

Grails
----------------------------
The deploy command calls "grails prod war".  You will need to modify .openshift/action_hooks/deploy if you would like to deploy to test or dev.