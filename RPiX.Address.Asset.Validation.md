# Using RPi3 or 4 to validate wallet address/idenity 

Based on the Methodology proposed by Mangofarmsassets

We propose the following methodology to build Address Name Tags:

A. Create Address Name Tag (Recipient)

Users who want to name their Ravencoin addresses can create an Address Name Tag in the following manner:

Generate a new Ravencoin address (or use an existing one).
Create a JSON file with the following information to name the address:

{
	"tag": {
		"tag_type": "ANT",
		"ravencoin_address": "<Ravencoin address from step 1>",
		"address_name": "<name that you want to give to the Ravencoin address>",
		"address_name_mime": "text/x-markdown; charset=UTF-8",
		"icon": "<base64 encoded png image at 64x64>"
	},
	"metadata_signature": {
			"signature_hash": "<SHA256 hash of the immediately preceding metadata JSON object {...}>",
			"signature": "<Ravencoin signed signature_hash>"
	}
}

Add the JSON file to IPFS and obtain an IPFS hash.

Issue a unique asset and send it to the Ravencoin address, adding the IPFS hash from step 3 as the asset metadata and using the
following naming convention (excluding the brackets): MAIN_ASSET#ANT_[address_hash]

“MAIN_ASSET” can be any main asset name no more than 10 characters in length, for a total asset name length of up to 23 characters
(the remaining 7 characters are reserved for potential future functionality). Users, wallet providers and other second layer solutions
may choose to use a single main asset name for all Address Name Tags they or their platforms generate. This reduces the cost of
generating each new Address Name Tag to the 5 RVN burn fee.

“ANT” appears as the first three letters after the unique asset tag # in the unique asset name. This signifies that the unique asset
carries an Address Name Tag and facilitates protocol-level searching for Address Name Tags.

“address_hash” is the CRC32 hash of the Ravencoin address. Using this hash in the unique asset name acts as a checksum, allowing any
sender to confirm that the Address Name Tag matches the address that holds it. For this purpose, the hash need not be cryptographically
secure. CRC32 was selected due to its simplicity and short length (8 characters).

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
