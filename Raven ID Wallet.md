# RVN.ID.Wallet (RIW)

The purpose of this wallet is to give 3rd party software a way to validate identity.  This is based on the Mangofarmsassets RIP 11~14.  A unique asset is generated with a 
hash of the address in the RIW.  If the RIW is queried for an asset the wallet will return true/false and the full name of the asset.  Anyone can query the RVN BC to see 
if the name of the unique asset and the address in which it resides match.  If the local RIW does not hold the asset and/or the asset is not in the correct address, the 
identity is invalid.

A RVN wallet with assets.

Very limited GUI.  Address generation, 12 word backup and recovery

3rd party software interaction. Allow 3rd party software to check for the presence of asset in wallet.  Return true/false and full asset name.  

Example:  “query command”=”Asset” ;  “checkassetname RIP” command would return “True RIP11#PGP_141E7FEC”

At this point the 3rd party knows if the identity is valid and who the “entity” is based on the name of the unique asset and the address matched against the 3rd party’s 
member database. 

The purpose of the RIW is to do away with username and password logins.  A person could sign up for a “web site” and give the unique asset and address to the “web site” 
at time of sign up.  Once the user is validated they simply return to the “web site”, click the login button and the “web site” will query the RIW for the presence of an 
unique asset.  Based on the query return the “web site” will know if the person is validated and who it is.

The ability to query a local wallet for the presence of an unique asset and/or an address presents a number of issues that may go against the ideas of block chain address 
anonymity.  The RVN BC already allows for restricted assets and 3rd parties to KYC address for these restricted assets.  The RIW allows a 3rd party to validate that the 
entity requesting access actually holds the proper asset locally.  

Some advanced functioning for encryption could be added.  The Mangofarmsassets RIP 11~14 allows for the attachment of a PGP key via IPFS to an asset.  This way encrypted 
data can be sent to the holder of an asset and only that holder can access this data.  I propose the following functions be added:

1.	RIW can generate PGP key pair, create unique asset (might have to access central party), and post pubic PGP key to IPFS
2.	RIW would hold private PGP key with only access via CLI and 12 words.
3.	Encrypted data posted to IPFS would have a special header identifying it as RIW access data.
4.	Any 3rd party application could browse to the IPFS data and send it to the RIW to read and return the data to the 3rd party application.
5.	RIW holds private key, accesses the data and delivers readable data to the 3rd party application.


This wallet will be designed for minimum end user interaction.  There is no need for most end users to know or understand Block chains, PGP encryption or assets in order 
to use the functions.

By having a set of APIs that any 3rd party could access many different types of use cases are opened up.

Private messaging

Application and web site access

Subscription services

Private sales of digital content

Command sets for IoT

Validated software updates

And many many more…… 
