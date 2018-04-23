# Remarks:

### Start dhlab stack with docker-compose
 - <pre>docker-compose up (in this folder)</pre>

### Installing Knora:

 Run Knora outside of docker container, docker has a bug with Knora for version c6e558e, so we will run it without docker.
 - <pre>git clone https://github.com/dhlab-basel/Knora.git</pre> 
 - <pre>cd Knora && git checkout c6e558e</pre>
 - <pre>sbt</pre>
 - <pre>compile</pre>
 - <pre>reStart</pre>
 
 ### Loading NIE-INE Ontologies
 To import the NIE-INE ontologies do the following:
 - <pre>git clone https://github.com/nie-ine/Ontologies.git</pre>
 - You have to replace some files in the Knora folder that you cloned above with the once from the following repo:
 - <pre>git clone https://github.com/nie-ine/Ontologies</pre>
 - Work is in progress to load the files automatically. You can find out what to replace here, your paths will be different so you can do it manually if you would like, or via shell:
 - <pre>https://github.com/nie-ine/Quick-Installation-Guide---Knora-Salsah-Sipi-GraphDB/blob/master/NIE-INE-Ontologies/Dockerfile</pre>
 - In the same Dockerfile, you can see which script to execute in Knora/Knora/webapi/scripts to import the NIE-INE ontologies.
 
 ### Restart Knora
  - In the terminal where we start Knora don't stop sbt, just type <pre>reStart</pre> Knora will restart.
  
 ### Check if it has succeeded

  -  If Knora says in terminal <pre>webapi Knora API Server using HTTP at http://0.0.0.0:3333</pre>
  there were no reported errors regarding the nie-ontologies. Check at loclahost:4200 if Salsah shows the NIE ontologies.
  
  - Run the import.py script. 
  - With Postman or sth similar, perform the following http request: <pre>localhost:3333/v2/search/resource</pre>
  The word that you search for in this case is "resource, since the given label in import.py is "test resource" it should give the result.
  