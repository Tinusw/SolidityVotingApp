### Voting Ethereum Contract

Application that allows for voting.

## Lessons

- run `testrpc` in another terminal so we can simulate a blockchain with some ether
- create an instance of the compiled contract using node

## Create an instance of the contract on testrpc []

1. run node in your console
2. Run the following()[]

	```
	Web3 = require('web3')
	//Localhost set by testrpc
	web3 = new Web3(new Web3.providers.HttpProvider("http://localhost:8545"));

	//if correct this command should return all the test accounts
	web3.eth.accounts

	//To compile your contract 
	code = fs.reafFile
	solc = require('solc')
	compiledCode = solc.compile(code)

	// if successfully compiled you should be able to get a response from
	compiledCode.contracts[‘:Voting’].bytecode
	compiledCode.contracts[‘:Voting’].interface

	// to deploy the contract instance
	abiDefinition = JSON.parse(compiledCode.contracts[':Voting'].interface)
	VotingContract = web3.eth.contract(abiDefinition)
	byteCode = compiledCode.contracts[':Voting'].bytecode
	deployedContract = VotingContract.new(['Rama','Nick','Jose'],{data: byteCode, from: web3.eth.accounts[0], gas: 4700000})
	deployedContract.address
	contractInstance = VotingContract.at(deployedContract.address)

	// if successful, you should be able to interface with the contract e.g.
	contractInstance.totalVotesFor.call('Rama')
	contractInstance.voteForCandidate('Rama', {from: web3.eth.accounts[0]})
	contractInstance.totalVotesFor.call('Rama').toLocaleString()
	```
