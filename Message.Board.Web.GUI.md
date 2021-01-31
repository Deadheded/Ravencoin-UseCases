<b>Message board w/ Web page GUI</b>

I will not get too deep into the technical details as mush of the audience this is written for will understand them better than I do.

I believe the Ravencoin foundation should use a message board system that utilizes the RVN BC and IPFS.  There could be two ways to interface with the system, 
either via the web site or by an application.  I will talk mostly to the web site interface and leave the creation of an application for another paper. 

Utilizing the procedures laid out in https://github.com/MangoFarmAssets/rips/blob/master/rip-0011.mediawiki through RIP 14, entities that wish to be members of 
the Ravencoin foundation website could create an account and be assigned a wallet.  This can work very similar to https://www.mangofarmassets.com/mangowallet 
with the exception that when performing a transaction the “memo” field for IPFS hashes will be used.

So a member signs up and a wallet is created for them.  They will need to pay for the creation of a unique asset that is assigned to their wallet address.  

The level of KYC can be as anonymous as just an email address or full verification.  The member would decide how much information they wish to provide.  

When a member wishes to make a post or comment they would access a form on the web site, just like any number of current message board solutions.  The “message” 
is composed and is posted to the RVN BC and IPFS by sending an asset to a specific address with the IPFS hash in the “memo” field.  

The Ravencoin foundation web site would then scan the the RVN BC and display any messages as long as it was sent from the proper address and the senders 
address also contained the “membership” asset as outlined in the RIP’s from Mangofarms.  

Although encryption of messages may not be necessary I would suggest that they be encrypted for several reasons.  In the case of encryption the Ravencoin 
foundation web site would receive a PGP key to read each post.  This is outlined in more detail in the Mangofarms RIP’s so I will not re-hash this.
Encryption would keep another 3rd party from reading the data posted to the RVN BC and IPFS and displaying it elsewhere without the author’s knowledge.  
It would also be a system that other 3rd party sights could use simply by creating their own unique “membership” token with a PGP key.  This would allow an 
author to decide between any number of 3rd party applications to display their content. 

This is a quick draft and I will flush this out more and post it to github.  I will also work on a phone application write-up for the same functions. 
