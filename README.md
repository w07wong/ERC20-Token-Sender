### erc20-mass-sender

## Summary
erc20-mass-sender reads a CSV file and sends tokens from the user's wallets to the accounts specified in the file.

## Installation
### In terminal:
**NodeJS must be installed**
```
npm install
```
### In the config.js file:
Specify your node url under:
```
'gethNode': ''
```

## Running
Running **node index -h** in the src folder will produce usage information
```
$ node index -h
usage: index [-h] [-v] [--conf path] [--wall path] [--csv path]
             [--addr address] [--deci num] [--offs num] [--batc num]
             [--tready string]
             

Test

Optional arguments:
  -h, --help       Show this help message and exit.
  -v, --version    Show program's version number and exit.
  --conf path      Specify configuration file (default: ../resources/config.
                   conf)
  --wall path      Specify file with MyEtherWallet encrypted JSON container
  --csv path       Specify CSV file with Ethereum addresses and amounts. CSV 
                   must be formatted like so: "address,amount,address,amount" 
                   which each amount corresponding to the preceeding address.
  --addr address   Specify ERC20 contract address
  --deci num       Specify ERC20 token decimals
  --offs num       Specify offset in CSV file, to start sendings from 
                   (default: 0)
  --batc num       Specify batch size (how many transactions to send, 
                   default: to the end of CSV file)
  --tready string  Set to true if ready to begin sending: "--tready true"
```
First, specify your configuration file or enter details manaually.  You will need to enter in the path to your ethereum wallet file, the path to your CSV file which contains sending information and your wallet address to successfully run the program.  You may also specify a token decimal, an offset start position and batch size.

Your CSV file will contain addresses and the amounts you want to send.  It must be structured as shown:
```
address,amount,address,amount
```
For example, the following lists two addresses and the corresponding amount of ether to send to each address.  In this case, 0 ether will be sent to both addresses.
```
0x059345dE4c56C80A5d90AD3B170627e2a7339173,0,0x3e390fD69D0D306D5fdd1dF6F266B8e742460cdb,0
```
When you have all the data inputed, or at least the necessary requriements, run
```
node index --tready true
```
This begins the sending process.  You will be prompted for a gas price, gas limit and the private key to your ethereum wallet.  If all data is entered and correct, then tokens will be sent to the addresses specified in the CSV file.  Hashes of the completed transactions will be logged in the console.

## Note:
This program writes data to the config.conf file, running '--tready true' sets the tready value in the config file to true.  If you want to re-run the application make sure to run '--tready false' so you can change arguments.  If you do not, then the application will re-run the transactions when you enter new arguments.

