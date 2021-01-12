	A Block Chain Solution for Twitter, Parler, ect….	

This system is based on: https://github.com/MangoFarmAssets/rips/blob/master/rip-0011.mediawiki

We propose the following methodology, which has been automated in the reference implementation:

<b>A. Address Encryption Tag </b>

Publishers who wish to “post” for public display and discord and 3rd party websites and applications that wish to display encrypted asset metadata information from 
publisher’s “posts”, will create an Address Encryption Tag in the following manner:

1.	Derive a new BIP 44 address using the path m/44'/175'/0'/2/address_index. Constant 2 is used at the change level to facilitate encryption address discovery. 
Users of wallets that do not provide BIP44 functionality may use any Ravencoin address for basic encryption, although this will limit some of the functionality 
outlined in this RIP.

2.	Generate a PGP keypair according to the OpenPGP standard, using the encryption address as the username and a user-generated strong passphrase.

3.	Create a file with the PGP public key block and add the file to IPFS to obtain a hash. A text file can be used, but the JSON file format specified below is 
recommended for this purpose.

4.	Issue a unique asset to the new encryption address, adding the IPFS hash as the asset metadata and using the following naming convention 
(excluding the brackets): MAIN_ASSET#PGP_[address_hash]

“MAIN_ASSET” can be any main asset name no more than 10 characters in length, for a total asset name length of up to 23 characters (the remaining 7 characters 
are reserved for potential future functionality). Users, wallet providers and other second layer solutions may choose to use a single main asset name for all 
Address Encryption Tags they or their platforms generate. This reduces the cost of generating each new encryption address to the 5 RVN burn fee.

“PGP” appears as the first three letters after the unique asset tag # in the unique asset name. This signifies that the unique asset carries a PGP public key 
for receiving encrypted metadata (discussed below) and facilitates protocol-level searching for encryption addresses.

“address_hash” is the CRC32 hash of the encryption address. Using this hash in the unique asset name acts as a checksum, allowing any sender to confirm that the 
encryption receiving asset matches the encryption address that holds it. For this purpose, the hash need not be cryptographically secure. CRC32 was selected due 
to its simplicity and short length (8 characters).

<b>B. Encrypting Asset Metadata (Publisher)</b>

Publishers who want to post encrypted asset metadata for public display can do so in the following manner:

1.	Create a metadata JSON file.

2.	Encrypt the desired files referenced in the metadata JSON (e.g., one or more of the ipfs_attachments) using a cryptographically secure symmetric key algorithm. 
The algorithm chosen is a matter of user preference. The reference implementation for this RIP uses TripleSec, which double-encrypts the data with Salsa 20 and AES.

3.	PGP encrypt the shared symmetric key used in step 2 above, using the PGP public key of each intended 3rd party. This public key can be obtained from the Address 
Encryption Tag associated with each recipient's encryption address.

4.	Add the encryption information for each recipient to the metadata JSON.

This method, which PGP encrypts only the symmetric encryption key, reduces file bloat and eliminates the need to PGP encrypt the entire file multiple times with the 
PGP public key of each additional recipient.

This RIP can be used with any method to generate the JSON file, as long as the relevant encryption information is included within it. For example, RIP14 contains a 
specification for generating the metadata JSON that includes encryption data. Alternatively, if the metadata JSON file is created using the Ravencoin Metadata 
Specification, encryption information for each recipient can be added as a nested object at the end of the metadata JSON to encrypt the contents of contract_url:

{ ...
	"encryption": {
		"algorithm": "<e.g., AES, TripleSec>",
		"recipients": {
			"<recipient 1 encryption address>": "<PGP encrypted symmetric key to recipient 1>",
			"<recipient 2 encryption address>": "<PGP encrypted symmetric key to recipient 2>",
			"<recipient n encryption address>": "<PGP encrypted symmetric key to recipient n>"
		}
  	}
}

This method can also be used with other metadata structures, such as the one being worked on here by adding appropriate version and schema information.

<b>C. Decrypting Asset Metadata (Recipient)</b>

Recipients of assets with encrypted metadata keys can decrypt the ciphertext in the following manner:

1.	Retrieve the JSON metadata file associated with the asset sent to the encryption address. This contains the PGP encrypted symmetric key that is necessary to 
decrypt the file.

2.	Decrypt the ciphertext associated with the user's encryption address in the JSON metadata file with the user's PGP private key. This will reveal the symmetric 
key used to encrypt the metadata file.

3.	Decrypt the encrypted file with the symmetric key using the algorithm specified in the JSON metadata file.

Wallets can use the BIP44 path change=2 specified above to facilitate separate derivation of encryption receiving addresses and the associated JSON file.

Once the 3rd party has the readable data all post are subject to the Terms and Conditions of that party.  In this case the 3rd party can act as “A” publisher and 
manipulate data on their site.  This is differentiated from “The” publisher which is the entity that published the date to the RVN BC and IPFS.

3rd party applications can compete for users and revenue.  While a 3rd party can choose not to display certain content or publisher data, the data posted to the 
RVN BC and IPFS cannot be deleted or taken down.  There is no censoring of the BC.

Through key management the publishers can choose which sites have access to data posted to the RVN BC and IPFS.  The publishers can make one post that is accesses 
by a list of 3rd party applications of their choosing.  One thing to remember is once some is posted to the RVN BC and IPFS, with little exception, it will be there 
forever, no deleting. 

This only addresses one use case for this function.  Multiple other use cases exist and are in the works. 
