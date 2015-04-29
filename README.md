Scaling on OpenShift
=====================

This application helps to visualize what is occurring on your scaled
OpenShift application.  It is an EE6 application that queues and writes
a count of the traffic it is receiving to a Mongo database.  When you
access the application, it uses the d3 javascript libraries to render
a force layout view of your application and the connected gears as
well as the traffic they have served.

https://www.youtube.com/watch?v=ghvofB36PSY

Creating your Own
=====================

If you want to create your own copy of this application, just run the
following command:

    rhc app-create scaleapp jbosseap mongodb-2 -s --from-code https://github.com/trifonnt/scaling-demo.git
  
Then, to add 'hits' to your application, hit the following URL:

    http://YOUR_APP/rest/add
  
To drive some simple traffic, you can run something like:

    for i in {1..10000}; do curl -s http://YOUR_APP/rest/add > /dev/null; usleep 50000; done
