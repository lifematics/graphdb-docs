# Initialize ubuntu 20.04 lts virtual machine
Initialize with at least 2GB memory and 10GB hard drive space(The more the better, to handle future requirements)

* sudo apt-get update
* sudo apt-get upgrade
* sudo apt-get install
* cd /
* sudo mkdir lifematics (This is the file where all downloads should be stored and programs run)
* sudo chmod 777 lifematics(Give full permissions to lifematics folder)
* sudo apt install default-jdk(Install java environment)


## Installing graphdb:


* Register for graphdb in https://www.ontotext.com/products/graphdb/
* Download graphdb standalone server from the link mailed to your email address.
* Download this sample dataset https://chiba.dbcls.jp/data/taxonomy_2019-05-01.ttl
* Unzip graphdb folder
* Go to <graphdb_folder>/bin
* Run graphdb workbench using the command sudo ./graphdb
* Open the workbench in the browser by typing in localhost:7200 in the browser window
* Go to Setup->Repositories->Create new repository
* Set Id to any name(e.g. NewRepo) and create repository
* Go to terminal, type and enter cntrl+c to close workbench
* In terminal type sudo ./loadrdf -f -i NewRepo -m parallel <path to dataset> . It will take around 40 minutes to load the big dataset. 
To test a smaller sample of the data copy the first 10000 lines from the oriinal dataset and create a new one (head -10000 taxonomy_2019-05-01.ttl > taxonomy10000.ttl) 
* After the dataset is loaded the workbench can be opened and SPARQL queries can be run


(Note: The dataset can be loaded faster using the preload tool instead of the loadrdf tool. 
However I got an error saying the linux instance did not have enough memory even when I set memory size to maximum during initialization. 
Preload works fine in the MacOS system so the system settings of linux needs to be tuned)


## Installing rdfstorejs:
* sudo npm install npm
* sudo npm install rdfstore


## Installing allegrograph:
* Download allegograph.tar file
https://franz.com/franz/agraph/ftp/pri/acl/ag/ag7.0.0/linuxamd64.64/agraph-7.0.0-linuxamd64.64.tar.gz.lhtml?l=agfree

* Follow the instructions in this page:
https://franz.com/agraph/support/documentation/current/agraph-quick-start.html

OR

Follow the instructions:
* Navigate to the directory extracted cd agraph-7.0.0
* sudo ./install-agraph /lifematics/agraph
* Click enter to answer yes to all the questions. Set password for user super
* After installation is complete, access http://127.0.0.1:10035 in browser to access allegrograph.

## Installing Stardog:

* wget https://downloads.stardog.com/stardog/stardog-latest.zip
* unzip stardog-latest.zip

* Follow the instructions under setting path and running stardog
https://www.stardog.com/docs/#_setting_path

Note: 60 day trial version

