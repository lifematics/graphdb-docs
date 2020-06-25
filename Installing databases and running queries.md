# Prerequisite
* Ubuntu 18.04
```
sudo apt-get update
sudo apt-get upgrade
sudo apt install default-jdk
```

## Installing graphdb:

* Register for graphdb in https://www.ontotext.com/products/graphdb/
* Download graphdb standalone server from the link mailed to your email address.
* Unzip graphdb folder
* Go to <graphdb_folder>/bin
* Run graphdb workbench using the command sudo ./graphdb
* Open the workbench in the browser by typing in localhost:7200 in the browser window
* Go to Setup->Repositories->Create new repository
* Set Id to any name(example. NewRepo) and create repository
* Go to terminal, type and enter ctrl+c to close workbench
* In terminal type sudo ./loadrdf -f -i NewRepo -m parallel <path to dataset>
* After the dataset is loaded run sudo ./graphdb to open the workbench at localhost:7200 in the browser.
* Click the sparql tab and click the repository
* Perform queries in the query window.

## Installing rdfstorejs:
* sudo npm install npm
* sudo npm install nodejs
* sudo npm install rdfstore
* To test queries on the dataset, create a file test.json and paste in the following code:
```
var rdfstore = require('rdfstore');
var fs = require('fs');

rdfstore.create(function(store){
  var rdf = fs.readReadStream('/path/to/dataset.ttl');
  store.load('text/turtle', rdf, function(s,d){
    console.log(s,d);
    store.execute("SELECT * WHERE { ?s ?p ?o } LIMIT 10", function(success, results){
      console.log(success, results);
    });
  });
});
```
Please update the path to dataset. Information related to the package can be found in this [repository](https://github.com/antoniogarrote/rdfstore-js#store-creation)

## Installing allegrograph:
* Download allegograph.tar file
https://franz.com/franz/agraph/ftp/pri/acl/ag/ag7.0.0/linuxamd64.64/agraph-7.0.0-linuxamd64.64.tar.gz.lhtml?l=agfree

* Follow the instructions in this page:
https://franz.com/agraph/support/documentation/current/agraph-quick-start.html

OR

Follow the instructions:
* Navigate to the directory extracted by typing cd agraph-7.0.0
* sudo ./install-agraph /path/to/installed/directory 
* Click enter to answer yes to all the questions. Note the user to run as field. The default is set to agraph but you can change it to the current user(not root). This username will be needed to load rdf to the database. Set password for user.
* Move dataset to <path to installed directory>/lib
* Run sudo <path of installed directory>/bin/agraph-control --config <path of installed directory>/lib/agraph.cfg start
* Access http://127.0.0.1:10035 in browser to access allegrograph.
* After signing in, create repository. (Example FirstRepo)
* Go back to the terminal. Make sure the current user is the username  specified during the installation. Navigate to bin and then ./agtool load FirstRepo path/to/dataset
* In the browser select queries tab at the top and input the query and execute
* Run sudo <path of installed directory>/bin/agraph-control --config <path of installed directory>/lib/agraph.cfg stop to stop allegrograph
	
## Installing Stardog:

* wget https://downloads.stardog.com/stardog/stardog-latest.zip
* unzip stardog-latest.zip

* Follow the instructions under setting path and running stardog
https://www.stardog.com/docs/#_setting_path

Note: 60 day trial and 1-year academic trial are available. There are no completely free version.
