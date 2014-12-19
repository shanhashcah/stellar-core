	
Do we allow alternate paths?
	I don't think it is worth the protocol complexity. Clients can just retry if it fails.
	
Do we want to include the public key in the tx or make them look it up in the account?


How do we want to handle retunring payments?
	If a user sends a payment from a gateway and someone needs to return it 
		they can't just send it back since the gateway 
		needs to know who to credit the payment to. 
	source memo that is echod if there is a return payment?
	include the tx id in the return payment?


AccountEntry.ownerCount  do we want this in the ledgerEntry? 
	It is calculateable


Do we keep full entries in the BucketList?


What is the file format for the history?


Are we charging enough for storage?
	Right now you can make a few million offers and greatly increase 
		the ledger size and get it all back at somepoint
	Maybe it should be more than a bond. Like some part is destroyed permanently.


What do we do about tx that make it into the applied txset but have too low a max fee? 
	Do we consume the seq num?
	Do we charge the max fee and not apply them? 
	Do we just ignore them?
	Do we let them get by for free?

What do we want to do instead of STAmount?	
How do we represnt currencies?
	A client should be able to see the code and know if it was 
		something simple like "USD" or "BTC" without doing some lookup
	We should be able to represent more complex things that are interpreted 
		by clients if we want to do demerge or something.
	Do we want to allow longer human readable currency codes?
	options:
		bit packed code ala ripple
		union of string or hash we look up



How does the network start up?
	validator starts with --new
	DB is cleared
	Hash genesis ledger
	Start FBA with empty txSet
	FBA will hang until a quorum is also started with --new