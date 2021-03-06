Common operations
-----------------

### Listing my 

addresses

Listing the Scash adresses in your wallet is easily done via _listreceivedbyaddress_. It normally lists only addresses which already have received transactions, however you can list all the addresses by setting the first argument to 0, and the second one to true.

Accounts are used to organize addresses.

Full list
---------

Required arguments are denoted inside < and > Optional arguments are inside \[ and \].

Command

Parameters

Description

Requires unlocked wallet? (v0.1.1+)

`addmultisigaddress`

<nrequired> <'\["key","key"\]'> \[account\]

Add a nrequired-to-sign multisignature address to the wallet. Each key is a Scash address or hex-encoded public key. If \[account\] is specified, assign address to \[account\]. Returns a string containing the address.

N

`backupwallet`

<destination>

Safely copies wallet.dat to destination, which can be a directory or a path with filename.

N

`createmultisig`

<nrequired> <'\["key,"key"\]'>

Creates a multi-signature address and returns a json object

`createrawtransaction`

\[{"txid":txid,"vout":n},...\] {address:amount,...}

N

`decoderawtransaction`

<hex string>

N

`dumpprivkey`

<scashaddress>

Reveals the private key corresponding to <scashaddress>

Y

`encryptwallet`

<passphrase>

Encrypts the wallet with <passphrase>.

N

`getaccount`

<scashaddress>

Returns the account associated with the given address.

N

`getaccountaddress`

<account>

Returns the current Scash address for receiving payments to this account. If <account> does not exist, it will be created along with an associated new address that will be returned.

N

`getaddednodeinfo`

<dns> \[node\]

(note that onetry addnodes are not listed here) If dns is false, only a list of added nodes will be provided, otherwise connected information will also be available.

`getaddressesbyaccount`

<account>

Returns the list of addresses for the given account.

N

`getbalance`

\[account\] \[minconf=1\]

If \[account\] is not specified, returns the server's total available balance.  
If \[account\] is specified, returns the balance in the account.

N

`getbestblockhash`

N

`getblock`

<hash>

Returns information about the block with the given hash.

N

`getblockcount`

Returns the number of blocks in the longest block chain.

N

`getblockhash`

<index>

Returns hash of block in best-block-chain at <index>; index 0 is the [genesis block](/wiki/Genesis_block "Genesis block")

N

`getblocknumber`

**Deprecated**. Use getblockcount.

N

`getblocktemplate`

\[params\]

Returns data needed to construct a block to work on. See [BIP_0022] for more info on params.

N

`getconnectioncount`

Returns the number of connections to other nodes.

N

`getdifficulty`

Returns the proof-of-work difficulty as a multiple of the minimum difficulty.

N

`getgenerate`

Returns true or false whether scashd / Scash Desktop Wallet is currently generating hashes

N

`gethashespersec`

Returns a recent hashes per second performance measurement while generating.

N

`getinfo`

Returns an object containing various state info.

N

`getmemorypool`

\[data\]

**Replaced with getblocktemplate, submitblock, getrawmempool**

N

`getmininginfo`

Returns an object containing mining-related information:

*   blocks
*   currentblocksize
*   currentblocktx
*   difficulty
*   errors
*   generate
*   genproclimit
*   hashespersec
*   pooledtx
*   testnet

N

`getnewaddress`

\[account\]

Returns a new scash address for receiving payments. If \[account\] is specified payments received with the address will be credited to \[account\].

N

`getpeerinfo`

Returns data about each connected node.

N

`getrawchangeaddress`

\[account\]

Returns a new scash address, for receiving change. This is for use with raw transactions, NOT normal use.

N

`getrawmempool`

Returns all transaction ids in memory pool

N

`getrawtransaction`

<txid> \[verbose=0\]

Returns [raw transaction](/wiki/Raw_Transactions "Raw Transactions") representation for given transaction id.

N

`getreceivedbyaccount`

\[account\] \[minconf=1\]

Returns the total amount received by addresses with \[account\] in transactions with at least \[minconf\] confirmations. If \[account\] not provided return will include all transactions to all accounts. 

N

`getreceivedbyaddress`

<scashaddress> \[minconf=1\]

Returns the amount received by <scashaddress> in transactions with at least \[minconf\] confirmations. It correctly handles the case where someone has sent to the address in multiple transactions. Keep in mind that addresses are only ever used for receiving transactions. Works only for addresses in the local wallet, external addresses will always show 0.

N

`gettransaction`

<txid>

Returns an object about the given transaction containing:

*   "amount" : total amount of the transaction
*   "confirmations" : number of confirmations of the transaction
*   "txid" : the transaction ID
*   "time" : time associated with the transaction[\[1\]](#cite_note-1).
*   "details" - An array of objects containing:
    *   "account"
    *   "address"
    *   "category"
    *   "amount"
    *   "fee"

N

`gettxout`

<txid> <n> \[includemempool=true\]

Returns details about an unspent transaction output (UTXO)

N

`gettxoutsetinfo`

Returns statistics about the unspent transaction output (UTXO) set

N

`[getwork](/wiki/Getwork "Getwork")`

\[data\]

If \[data\] is not specified, returns formatted hash data to work on:

*   "midstate" : precomputed hash state after hashing the first half of the data
*   "data" : block data
*   "hash1" : formatted hash buffer for second hash
*   "target" : little endian hash target

If \[data\] is specified, tries to solve the block and returns true if it was successful.

N

`help`

\[command\]

List commands, or get help for a command.

N

`importprivkey`

<scashprivkey> \[label\] \[rescan=true\]

Adds a private key (as returned by dumpprivkey) to your wallet. This may take a while, as a [rescan](/wiki/How_to_import_private_keys#Import_Private_key.28s.29 "How to import private keys") is done, looking for existing transactions. Note: There's no need to import public key, as in [ECDSA](/wiki/Elliptic_Curve_Digital_Signature_Algorithm "Elliptic Curve Digital Signature Algorithm") (unlike RSA) this can be computed from private key.

Y

`invalidateblock`

<hash>

Permanently marks a block as invalid, as if it violated a consensus rule.

N

`keypoolrefill`

Fills the keypool, requires wallet passphrase to be set.

Y

`listaccounts`

\[minconf=1\]

Returns Object that has account names as keys, account balances as values.

N

`listaddressgroupings`

Returns all addresses in the wallet and info used for coincontrol.

N

`listreceivedbyaccount`

\[minconf=1\] \[includeempty=false\]

Returns an array of objects containing:

*   "account" : the account of the receiving addresses
*   "amount" : total amount received by addresses with this account
*   "confirmations" : number of confirmations of the most recent transaction included

N

`listreceivedbyaddress`

\[minconf=1\] \[includeempty=false\]

Returns an array of objects containing:

*   "address" : receiving address
*   "account" : the account of the receiving address
*   "amount" : total amount received by the address
*   "confirmations" : number of confirmations of the most recent transaction included

To get a list of accounts on the system, execute scashd listreceivedbyaddress 0 true

N

`listsinceblock`

\[blockhash\] \[target-confirmations\]

Get all transactions in blocks since block \[blockhash\], or all transactions if omitted. \[target-confirmations\] intentionally **does not** affect the list of returned transactions, but only affects the returned "lastblock" value.

N

`listtransactions`

\[account\] \[count=10\] \[from=0\]

Returns up to \[count\] most recent transactions skipping the first \[from\] transactions for account \[account\]. If \[account\] not provided it'll return recent transactions from all accounts.

N

`listunspent`

\[minconf=1\] \[maxconf=999999\]

Returns array of unspent transaction inputs in the wallet.

N

`listlockunspent`

Returns list of temporarily unspendable outputs

`lockunspent`

<unlock?> \[array-of-objects\]

Updates list of temporarily unspendable outputs

`move`

<fromaccount> <toaccount> <amount> \[minconf=1\] \[comment\]

Move from one account in your wallet to another

N

`sendfrom`

<fromaccount> <toscashaddress> <amount> \[minconf=1\] \[comment\] \[comment-to\]

<amount> is a real and is rounded to 8 decimal places. Will send the given amount to the given address, ensuring the account has a valid balance using \[minconf\] confirmations. Returns the transaction ID if successful (not in JSON object).

Y

`sendmany`

<fromaccount> {address:amount,...} \[minconf=1\] \[comment\]

amounts are double-precision floating point numbers

Y

`sendrawtransaction`

<hexstring>

Submits [raw transaction](/wiki/Raw_Transactions "Raw Transactions") (serialized, hex-encoded) to local node and network.

N

`sendtoaddress`

<scashaddress> <amount> \[comment\] \[comment-to\]

<amount> is a real and is rounded to 8 decimal places. Returns the transaction ID <txid> if successful.

Y

`setaccount`

<scashaddress> <account>

Sets the account associated with the given address. Assigning address that is already assigned to the same account will create a new address associated with that account.

N

`setgenerate`

<generate> \[genproclimit\]

<generate> is true or false to turn generation on or off.  
Generation is limited to \[genproclimit\] processors, -1 is unlimited.

N

`settxfee`

<amount>

<amount> is a real and is rounded to the nearest 0.00000001

N

`signmessage`

<scashaddress> <message>

Sign a message with the private key of an address.

Y

`signrawtransaction`

<hexstring> \[{"txid":txid,"vout":n,"scriptPubKey":hex},...\] \[<privatekey1>,...\]

Adds signatures to a [raw transaction](/wiki/Raw_Transactions "Raw Transactions") and returns the resulting raw transaction.

Y/N

`stop`

Stop scash server.

N

`submitblock`

<hex data> \[optional-params-obj\]

Attempts to submit new block to network.

N

`validateaddress`

<scashaddress>

Return information about <scashaddress>.

N

`verifymessage`

<scashaddress> <signature> <message>

Verify a signed message.

N

`walletlock`

Removes the wallet encryption key from memory, locking the wallet. After calling this method, you will need to call walletpassphrase again before being able to call any methods which require the wallet to be unlocked.

N

`walletpassphrase`

<passphrase> <timeout>

Stores the wallet decryption key in memory for <timeout> seconds.

N

`walletpassphrasechange`

<oldpassphrase> <newpassphrase>

Changes the wallet passphrase from <oldpassphrase> to <newpassphrase>.

N

Error Codes
-----------

See [rpcprotocol.h] for the list of error codes and their meanings.
