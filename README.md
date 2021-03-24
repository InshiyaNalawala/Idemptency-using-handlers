# Idemptency-using-handlers

We are trying to set up an httpd server using Ansible. We want to automate the restarting of the webserver in case any change occurs in the configuration file. This can be achieved using the template module. We can replace the new version of the configuration file with the old one by using the template module and using the jinja templates to make edits to the file.

Later, the service can be restarted using the service module. The challenge here is that even if no replacement takes place, this conventional approach will still restart the server and it will degrade the performance.

To avoid such issues, we make use of handlers. We can allow some tasks to notify a special block of code in case the execution of the task results in some change. Otherwise, that special code of block can be skipped. 

This special code of block is what we refer to as handlers. The idea is we will allow the task of replacing the configuration file to notify a particular handler if some change is detected. The handler that is notified then restarts the server. In case, no change occurs, the handler is never informed and the unnecessary restart of the server can be avoided. 
 
  


```
ansible-playbook webserver.yml
```
