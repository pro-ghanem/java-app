

#  Sample Java App -example
# Big Note
# the artifact-id, group-id and version all those have no effect on the the artifacts, just the name 
# so the based on the name of the app you use it in the browser if the app in pom.xml "java-app-1.0" and in /var/lib//webapps/ is ghanem.war, to access the app u must write : localhost:8080/ghanem , if u want to use the root path remove the ROOT.war and just change the ghanem.war to ROOT.war

 
to Build war with maven and java-app framework

Steps are the following:

1. Clone the repository to your local machine
2. The Dockerfile will do:

        A. Create maven container <br />
        
     * copy pom.xml to /tmp <br />
     * copy folder "src" to /tmp/src <br />
     * Go to /tmp folder then run "mvn package"<br />
      
      The previos command will generate java-app.war<br />
        
        B. Create tomcat container<br />
        
     * Will move the file java-app from maven container to /webapp in tomcat contaner<br />
     * Do health check to make sure that the artifact is deployed

3. Run 'docker build -t java-app .' <br />
    
     * Will create a Docker image called java <br />

4. Run 'docker run -d -p 8080:8080 --name java-app java-app' <br />
     * Will create a container called java-app and will forward the container internal port 8080 to locathost 8080 in the hosted machine

5. Open [http://localhost:8080/
(http://localhost:8080/ in your browser and see the result.

Note : if you will use ansible you could do the following command (Run command as user Ansible )
# sudo runuser -l  ansible  -c 'ansible-playbook deploy-playbook.yml'
