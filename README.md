ApigeeBundleReaper
===================

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/3ce632f7aa6b417983c464fc3cb99c71)](https://www.codacy.com/app/ssvaidyanathan/ApigeeBundleReaper?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=apigeecs/ApigeeBundleReaper&amp;utm_campaign=Badge_Grade)

Tool to faciliate Apigee Edge Organization maintenance

A  library providing utility to determine the proxies that are not deployed or being used (No Traffic)

A future version will include downloading the proxy bundle to a local directory, delete the bundle from Apigee Edge

Features include:
* Listing API proxies that are not deployed (for a given environment or all environments)
* Listing API proxies that has no traffic for a specified number of days (for a given environment or all environments)
* Delete the APIs that are not deployed. -x is the argument that controls the deletion

## Installation

The only prerequisites not handled during the installation are a functional Node environment, the availability of npm, and sufficient priviledges to run commands as adminstrator. The steps below are applicable to a Mac OS X environment, similar steps work under Linux or Windows. 
	
Clone the bundle-reaper repository to your local machine:

	ApigeeCorporation$ git clone https://github.com/apigeecs/ApigeeBundleReaper.git

Alternatively you can download the zip file via the GitHub home page and unzip the archive.

Navigate to the package directory:

	ApigeeCorporation$ cd path/to/ApigeeBundleReaper/src/package/

Install npm modules:

	ApigeeCorporation$ sudo npm install

## Usage
	
	ApigeeCorporation$ node path/to/ApigeeBundleReaper/src/bundle-reaper.js -h api.enterprise.apigee.com -o <org> -e <all|env> -a "Basic <auth> -d 90 -x yes
	
	where
	-h is the Management API Host
	-o is the Edge Organization
	-e is the Edge Environment (all will fetch all environments for a given Org)
	-a is the Basic auth
	-d is the number of days for which the traffic needs to be fetched
	
	Output:
	-------------------------Undeployed APIs in test-----------------------------
	oauth10a-3legged
	emailer
	authorize
	json-validate
	catchAll
	token_v3_rev3_2016_03_01
	-----------------------------------------------------------------------------
	
	--------------APIs with No Traffic in test in the last 90 days---------------
	java-cookbook
	base64encoder
	jira-release-notes
	ratingsService
	oauth10a-3legged
	response-cache
	oauth-login-app
	oauth-client-credentials
	-----------------------------------------------------------------------------

	-------------------------Undeployed APIs in prod-----------------------------
	json-validate
	catchAll
	token_v3_rev3_2016_03_01
	-----------------------------------------------------------------------------
	
	--------------APIs with No Traffic in prod in the last 90 days---------------
	java-cookbook
	base64encoder
	response-cache
	oauth-login-app
	oauth-client-credentials
	-----------------------------------------------------------------------------


You can also run 

	ApigeeCorporation$ node path/to/ApigeeBundleReaper/src/bundle-reaper.js --help 
	
	Usage: bundle-reaper [options]

  	Options:

    	-h, --help                           output usage information
    	-V, --version                        output the version number
    	-h, --host <host>                    Please provide Management API Host Information [api.enterprise.apigee.com]
    	-o, --organization <organization>    Please provide the Edge Organization Name
    	-e, --environment <environment>      Please provide the Environment name [all | test]
    	-a, --authorization <authorization>  Please provide the Edge Basic auth credentials [Basic <auth>]
    	-d, --axDays <axDays>                Please provide the number of days for Traffic
