# Using RPi3 or 4 to validate wallet address/idenity 

Based on the Methodology proposed by Mangofarmsassets

A. We propose the following methodology to build Address Metadata Tags:

Generate a new Ravencoin address (or use an existing one).

Create an IPFS file with information relevant to the tag, such as the PGP public key for an Encryption Address Metadata Tag under RIP11,
an Address Name Tag under RIP12, or an Address Identity Tag under RIP13 and add the file to IPFS to obtain a hash.

"Tag" the Ravencoin address by issuing and sending a unique asset to the address, adding the IPFS hash from step 2 as the asset metadata
and using the following naming convention (excluding the brackets): MAIN_ASSET#TAG_[address_hash]

“MAIN_ASSET” can be any main asset name no more than 10 characters in length, for a total asset name length of up to 23 characters (the
remaining 7 characters are reserved for potential future functionality). Users, wallet providers and other second layer solutions may
choose to use a single main asset name for all Address Metadata Tags they or their platforms generate. This reduces the cost of 
generating each Address Metadata Tag to the 5 RVN burn fee.

“TAG” is a three-letter identifyer signifying the Address Metadata Tag being used. For example: (1) "PGP" is used in RIP11 to indicate 
that the the unique asset carries a PGP public key for receiving encrypted metadata; (2) “ANT” is used in RIP12 to specify an Address 

Name Tag for the address; and (3) “AIT” is used in RIP13 to specify an Address Identity Tag for the address. Additional applications can 
use any number of tags for this purpose.

“address_hash” is the CRC32 hash of the Ravencoin address. Using this hash in the unique asset name acts as a checksum, allowing any 
sender to confirm that the encryption receiving asset matches the Ravencoin address that holds it. For this purpose, the hash need not 
be cryptographically secure. CRC32 was selected due to its simplicity and short length (8 characters).

B. Lookup Address Name Tag (Sender)

Once created, an Address Name Tag can be located by users or wallet providers and associated in an address book with a particular
address. Users can use "metadata_signature" to validate that the creator of the tag is the owner of the private key associated with
the address.

The owner of the "MAIN_ASSET" can choose what address can create or recieve an Address Name Tag.  

I propose an applicaton for the RPiX that could check a phone wallet or other wirelessly accessable wallet to see if they have the
asset for access to what the owner per determins.  The application could check for the "MAIN_ASSET" with the address hash or for a list
of white/black listed addresses.  

Could Blue Tooth, NFC and/or RFID be used by the RPiX to communicate with device?

Could ledger nano be used via USB to grant access?
