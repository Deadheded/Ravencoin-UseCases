# Message Board another 1 

Part 1

KAAWWW sign up or any message board

1.	An entity would enter a web form at the RVN foundation web site and create a signature file.  The file would contain as little information as a “handle” and RVN 
wallet address to full demographic information.  

2.	The registering member would then send a 6 RVN transaction to the KAAWWW “membership” address using the contents of the “signature file” to sign the transaction 
from the address the new member wishes to register.  Address would have to be compliant with mangofarmassets RIP 11~14.

3.	The registering member would then enter the transaction ID into a form field on the website.

4.	The web site would verify the signature and transaction.

5.	The web form would create a PGP key pair. (This should be done client side with the client retaining the private key).

6.	A json(a) file with the public PGP key and any “identifiers” is created and published to IPFS. (identifiers: handles, short descriptions other identifying information 
a member may wish to display about themselves).

7.	A unique asset with the registering members hash address is created based on mangofarmassets’ RIP 11~14 and the IPFS hash attached. 

8.	A second json(b) file, used for verification, is created, encrypted with the registering member’s public key and uploaded to the IPFS.

9.	The unique asset is then sent to the registering members address with the json(b) filed IPFS hash in the memo field.

10.	The client reads the decrypts json(b) file and verifies reception and ownership of the asset and address with the web site.

Part 2

Using the IPFS and Brave browser integration.

Create a web form (local if it can be) that will:

1.	 Encrypt multiple files.

2.	Group multiple files, both encrypted and open files.

3.	Generate a json file with “descriptors” for content.

4.	Post all files to a single IPFS hash.

5.	Generate a json file with IPFS hash locations and encryption keys.

6.	Encrypt json file with “recipient” public PGP key and post to IPSF.

7.	Display IPFS hash for use with RVN asset transfer.

This will allow anyone to publish data to IPFS and generate a public PGP key encrypted json.  The sender can post the hash of the encrypted json file to the RVN BC using 
the memo field when transferring an asset.  Anyone can scan the BC and see the IPFS hash but only the owner of the private PGP key can read the published files. 

In order to post to the ravencoin foundation message board a member would follow the above procedures and then send a sat of an asset, with the IPFS hash in the memo field,
to a designated “publishing” address.  The json file would contain descriptors such as if it is a reply, or a re-post or any number of indentifies the web site would use 
for display formatting. The json file would be encrypted with the public key of the foundation’s web site so only the foundation could read and display the data.  

Upon receiving an asset transaction the web site would read the IPFS hash, check that the sending address was registered and contained the proper unique “membership” asset 
at the time of the transaction.  This check would be done by querying the BC.  If all three conditions are met then the web site would display the post for the public.  
Use of a signature might be extra validation of an address transaction. 

This would also allow for the censoring of illegal content only on the foundation web site without touching the data on the BC or taking any ownership of the data.  The 
original publisher of the data to the IPFS retains all ownership.
