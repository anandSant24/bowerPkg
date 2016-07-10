when I do
$ bower install lodash
bower not-cached    https://github.com/lodash/lodash.git#*
bower resolve       https://github.com/lodash/lodash.git#*
bower checkout      lodash#4.13.1
bower resolved      https://github.com/lodash/lodash.git#4.13.1
bower install       lodash#4.13.1

lodash#4.13.1 bower_components\lodash
---------------------------------------------------------------

it will install loadash
 check in your proj new directory 

bower-components is created.

 and see that loadash is loaded in your proj and inside that there is dist

 2. to remove or uninstall loadash
---------------------------------------------------------------
 you can use cmd line and do
 bower uninstall lodash(you see it got removed)

 3. installing specific version of library
 ---------------------------------------------------------------
 bower install lodash#2.2.1
to know what packages are available do 

3.1 bower info lodash

4. Updating 
---------------------------------------------------------------
bower update
(will update your all libraries to latest version)
to install specific package
bower install underscore

5. listing installed package
$ bower list

bower install backbone
will install backbone and underscore too.

6. searching for package
$ bower search lodash
	o/p all lodash packages
	you can also search in bower.com on web



modulel 2 

===========

bower.json
1.helps to keep track of packages/lib
2.when you publis your own lib

you learn about creating bower.josn

.bowerrc

installing from bower.json
etc...

2.1
---------------------------------------------------------------

	1. bower.json file
	ex: project has 4 packages
	angular
	bootstrap
	jasmine
	jquery

	1. angular's bower.json file
	{
		name:angular
		version: '1.2.4'
		main:"/angular.js"
		dependencies:{}
	}
	---------------------------------------------------------------

	2. jquer's bower.json
	we have list of devDependenc
	Ex:
	{
		name: 'jquery'
		version: 2.1.0,
		main: 'dist/jquery.js',
		license: MIT
		//list of files ignored when bower install these packages
		ignore: [
			"**/.*",
			"build",
			"speed"
		],
		//list of devlopment depen
		devDependencies: {
			"sizzle": "1.10.16",
			"requirejs": "~2.1.8",
			"sinon": "~1.7.3"
		}
		//these keywords are used when searching in bower package list
		"keywords":[
			"jquery",
			"javascript",
			"library"
		]
	}

	---------------------------------------------------------------
	3. bootstarp's bower.json

	{
		name: bootstrap,
		main:[ // main file has list of files
			"/dist/css/bootstrap.css",
			"/dist/js/bootstrap.js",
			"/dist/fonts/glyphicons-regular.eot",
			"/dist/fonts/glyphicons-regular.svg"
			],
		dependencies:{
			jquery: ">=1.9.0"
		}
	}
	//observer the dependecies which say >=1.9.0
	i.e bower install jquery>=1.9.0

	bwoer.json file for our project

	moduleType: "goals"//any type supported by your proj

---------------------------------------------------------------

2.2 Creating bower.json file
bower offers command to create a new json file quickly do this in root directory of proj
$bower init

//Provide the details

2.3 bowerrc
---------------------------------------------------------------
bower always intall packages inside bower_components directories to overcome this restriction i.e we use bowerrc file

just do
.bowerrc

//its format is simple its json file
{
"directory":"js/lib"
}
//now move existing bower packages inside lib directory and now bower treat this lib dir as a repo for all bower packages

2.4 installing from bowere.json file
---------------------------------------------------------------
bower.json will provide meta-data for publishing the package
bower.json package will also provide what 3rd part lib are used by project and using bower we can install all of those packages

$ bower install
// this will install all dependecies declared in bower.json file

*this works same as node work with npm and package.json file

THIS WAS BIG BENIFIT OF USING BOWER.JSON FILE

---------------------------------------------------------------
ADDING PACKAGES TO BOWER.JSON FILE

ex adding new libraries to project
you do 
$bower install jquery
	notice that bower will install jquery.js but not updates the bower.json file's dependencies object.
	inorder to update it you do 

$bower install jquery --save

similarily to install jasmine as devDependencies do 
$bower install jasmine --save-dev 
	o/p bower.json updates
	  "devDependencies": {
	    "jasmine-core": "jasmine#^2.4.1"
	  }



to get rid of dependencies that you no longer need from bower.json file do this
$bower uninstall jquery --save

.boweerrc is used to customize the bower installed directory

Quiz -2
-------
Q) what is purpose of bower.json for published package.

A) it provides information and publishing directions, it lets it know what files to install, what to ignore and what dependencies it can install

Q2) what is purpose of bower.json file for project that will not be published as bower package?

A)easy intallation and update of bower package

Q3) purpose of devDependencies section for non-published project

A) it is just for Organization it has no operation on bower

Q4) purpose of .bowerrc file 

A) it let you change location of installed bower packages(provides you to specify location where package need to be installed)

Q5)how can you add package to bower.json file
add --save flag ex: at end
 	bower install pkg --save

Advanced Topics of bower
---------------------------------------------------------------
---------------------------------------------------------------
--------------------------------------------------------------- 

Bower's:
Cache
install options
help
info
lookup
prune
cmd flags
realistic demo

1. Bower Cache
---------------------------------------------------------------
as you install packages bower creates cache of them, that way if you try to install them again it will install from local cache
	2-cmds
	1. bower cache list
		to look for packages cached in list
	2. bower cache clean
		removes all items from cache
	installing package already in cache

	$ bower install jquery
	bower cached        https://github.com/jquery/jquery-dist.
	git#3.1.0
	bower validate      3.1.0 against https://github.com/jquery/jquery-dist.git#* 

	//notice that bower validate will look onlinr for latest version of jquery to not look on-line or to do offlien use -o command
	
	$ bower install jquery -o
	
	bower cached        https://github.com/jquery/jquery-dist.git#3.1.0
	//observe that it has not looked for online i.e no bower validate and just installed cachec version give great performance benifits

2. bower install options
---------------------------------------------------------------
	installing from local github repo insted of github.com
	(comes handy if you developing locally)
	specify the path to directories

	ex: $ bower install ../bowerFundamentsFiles
	my repo Example:
	// note $ = C:\Users\Aashish\Documents\Aks\GitHub24\bower-basics just for simplicity 
	$ bower install ../src/lib
		bower copy          C:\Uers\Aashish\Documents\Aks\GitHub24\src\lib
		bower resolved      C:\Users\Aashish\Documents\Aks\GitHub24\src\lib
		bower install       lib

		lib bower_components\lib

	we can also specify specific package version online using
	$bower install http://code.jquery.com/jquery-1.11.0.js


--to install only dependencies and not devdependencies
$ bower install --production

--to install lodash but change directory of lodash into another directory
$bower install lo_folder = lodash;
// this will install lodash inside lo_folder

3. Bower help
---------------------------------------------------------------
$ bower help
to get specifi information about command
$bower help install
	provides decripitons

4. Bower info
---------------------------------------------------------------
bower info lodash
	provides block of json file for lodash version

5. Bower lookup
---------------------------------------------------------------

$ bower lookup angular
angular https://github.com/angular/bower-angular.git
	//notice usr is bower instead of angular as it should suppost to be angular.js not bower
	//instead of pointing of angular repo they have their own repo with copy of angular repo and its updated versions
5. bower prune
---------------------------------------------------------------

note that even though we don't have lodash listed as dependencies in bower.json we still have loaded it , when you do 

$ bower list
	bower check-new     Checking for new versions of the project dependencies...
	bower-basics C:\Users\Aashish\Documents\Aks\GitHub24\bower-basics
	├── angular not installed
	├── bootstrap not installed
	├── jasmine-core#2.4.1
	├── lib extraneous
	├── lodash#2.2.1 extraneous (latest is 4.13.1)
	├── myDir#4.13.1 extraneous
	└── sinon#1.14.1 (latest is 2.0.0-pre)

	observer lodash#2.2.1 extraneous
	"extraneous" which indicated that althought it is loaded but it is not part of the dependencies list in bower.json file

So if you use  $bower prune command , this will uninstall those packages

$ bower prune
bower uninstall     lib
bower uninstall     lodash
bower uninstall     myDir


6. Command line flag
------------------------------------------------------------------
observe difference between 
bower install lodash vs bower install lodash -q  
-q is quite flag (this will not list details as bower cached, bower validate, etc...)

-s it installs and doesn't o/p
-v is same as reguar withou flag

-j to output that file to output.json
	$ bower install lodash -j >output.json
this output.json file will have all details about bower output package
 
 *this will be helpful to log the information that will be put on by bower


7.Demo Example:
--------------------------------------------------------------------

1. create .bowerrc file and point it to js/lib
2. create bower.json using cmd bower init or manually
let do manually
	bower.json
	{
		"name": "bower-example"
	}

	Now

	bower install jquery lodash angular angular-resource angular-route --save

To be able to test code install jasmine but they will not part of production code
lets do it inside test/lib

bower doesn't support installing pkg into two differnt directores at same time
let do it this way
	inside test dir create .bowerrc 
	{
	"directory": "lib"
	} 
	and also create bower.json file inside test
	bower.json
		{
			"name": "bower-example-test"
		}

cd test
and do 
bower install jasmine --save

so jasmine will be part of test not js/lib(production)

Quiz3
-----------------------------------------------------------------
Q1. what does the --production flag do when running bower install ?
A. doesn't install devDependencies

Q2. what does bower lookup do
A. Displays url of package

Q3. What does the --o option do when running bower install?
install in offline mode


Part 4 Publishing bower Package
-----------------------------------------------------------------
1. Create & Publish
2. add Package to Github(create client pkg and install and consume pkg)
3. updating Package

1. Create Package
	* create bower.json using init
	* create .js (main app file for our application)
2. Create a repo in github
	* create README file and 
	* create .gitignore file(it need to ignore only one directory i.e .idea dir created by webstrom)

