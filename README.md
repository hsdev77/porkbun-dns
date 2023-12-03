# porkbun-dns

## About
This is a bash script for updating DNS entries hosted at porkbun.com.  

The information about porkbun.com API can be found at :

- <https://kb.porkbun.com/article/190-getting-started-with-the-porkbun-api>

- <https://porkbun.com/api/json/v3/documentation>

## Requirements/dependency
This script uses below command line tools:

- curl
- dig

and they must be installed manually before using this script.

## Configuration

To specify the API key for calling the API endpoints, a text file named _porkbun_apikey.txt_ is required to be present :

- in the same directory as the _porkbun-dns_ script file, or
- in _/etc/porkbun-dns_ folder that must be created/edited manually

The API key and secret for your porkbun.com account must me generated previously using your porkbun.com account web interface.
  
Below are the format of the _porkbun_apikey.txt_ :
>_apikey=pk1_1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef_
>_secret=sk1_abcdef1234567890abcdef1234567890abcdef1234567890abcdef1234567890_

##Usage

- cli syntax:
>_porkbun-dns --command domain type [name|@] [value|my-public-ip|.]_

- _--command_ will determine the API endpoint command to be called, valid commands are:
>_--create, --update, --delete_ and _--retrieve_

- _domain_ is the domain name, like _example.com_  

- _type_ is the DNS record type, valid record types are:
>_A, MX, CNAME, ALIAS, TXT, NS, AAAA, SRV, TLSA_ and _CAA_

- _name_ is the hostname, like _'www'_ to specify _'www.example.com'_,  
or, use _'@'_ to specify the top entry (no hostname) like _'example.com'_

- value_ is the value for the entry, for example, and IP address 123.45.67.89  
a special string '_my-public-ip_' will be substitued by the global IP address of the host machine that being used to run this script 


example:

- _porkbun-dns --create example.com A @ 123.45.67.89_
- _porkbun-dns --update example.com A www my-public-ip_
- _porkbun-dns --delete example.com TXT \_acme-challenge.www.example.com_


-eof-



