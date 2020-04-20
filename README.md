# LINKTrader
Repo for LINKTrader

A Simplified Introduction to Chainlink
What is Chainlink?
To understand what Chainlink is, you first need to understand what a smart contract is and what an oracle is. Below, we will cover these in very simplified terms. If you’re already familiar with these concepts, you may prefer to read the Chainlink Whitepaper or see Thomas Hodges’ writeups of the whitepaper sections.

What is a smart contract?
A common analogy for a smart contract is purchasing a drink from a vending machine. Once conditions are met (putting in the money and selecting a drink), an action occurs (a drink is delivered) without any human intervention - you cannot stop it, change it, or back out of the agreement once the action starts.

IF $2 is inserted THEN the drink is released.

Smart contracts, like vending machines, have been around for some time. However so far they have not made the groundbreaking impact to business that they promise and that is because of trust. With the vending machine, all parties must reluctantly trust one another. The customer must trust the owner of the vending machine has not rigged the machine, the owner must trust the customer will not use counterfeit money, and both parties must trust the vending machine will operate without failure. When buying and selling $2 cans of drinks, people are willing to take the risk, but what about when the stakes are higher, like multi-million dollar bonds, mortgage escrow, and insurance policies?

Nick Szabo coined the term smart contract back in the 90s but without the solution to the trust problem, the huge business benefits could not be realised. This changes now. Blockchain, through the Ethereum Project, has proven itself to be able to facilitate smart contracts by making available an environment that solves for the trust issues and can execute the actions too. On the blockchain, smart contracts are like miniature computer programmes; they wait for some input, do some calculation, and then take some action.

An example of a blockchain smart contract in action is AXA’s fizzy service which provides delayed flight insurance.

IF your plane lands over 2 hours late THEN $XXX compensation is paid to your account.

"fizzy uses Ethereum Smart Contracts in order to guarantee the transparency and immutability of your insurance policy. When you subscribe to an insurance policy, the details are registered in fizzy's Smart Contract. Upon the plane landing, the actual landing time is also loaded in the Smart Contract, which compares it with the scheduled landing time and triggers a compensation if you are 2h late or more! fizzy doesn't need your trust: every piece of information and all mechanisms are accessible in the blockchain... ...Last but not least, fizzy doesn't register any of your personal data into the Ethereum blockchain!"

For more information, check out this easy to understand guide written by FreeCodeCamp.

What are some use cases for smart contracts?
There are almost limitless use cases for smart contracts. CapGemini published a report titled Smart Contracts In Financial Services: Getting from hype to reality, in addition to mentioning Chainlink (smartcontract.com) within their document, they provide a list of potential use cases within financial services.

It's important to note that use cases are certainly not limited to just financial services. Norton Rose Fulbright's paper "Smart Contracts: coding the fine print" has two pages on the industries that could be impacted by the rise of smart contracts.

What is an oracle?
To be useful, smart contracts need to be able to interact with the external world (off-chain).

In the flight insurance example, the compensation payout is triggered by your plane landing more than 2 hours late. But how do we know if the plane is 2 hours late and how do we get this off-chain data into the smart contract? And once we have the data, how do we make a payout to a bank account?

The answer to these questions is oracles. An oracle acts as the bridge between the external world and the smart contract. An oracle can query your flight number and landing time using an API (e.g. from FlightRadar24) and then push it into the smart contract. If the plane landed 2 hours after the scheduled landing time, a payment can then be triggered and an oracle used to tell a bank to debit an account and credit another (e.g. a SWIFT message).

Problems with existing oracles
If smart contracts are to be used for high-value agreements (e.g. house purchases), they need to be trusted. The issue of not trusting the middleman to fulfil their obligations is solved by putting the contract on a blockchain, with no middleman, where it is visible and held to account. However, the data that feeds into the smart contract also needs to be trusted.

Current oracles are centralised meaning that only one oracle (also known as a node) queries the data and provides it to a smart contract. However, there are a couple of key issues with centralised oracles:

If the node suffers an outage, the data is no longer being supplied and could lead to the smart contract not being triggered at the correct time.
The node could be tampered with and provide incorrect data to make the smart contract execute to benefit one of the parties. Or the node could be faulty and accidentally provide incorrect information.
So, what is Chainlink?
Chainlink is a decentralised oracle network. This means instead of having just one oracle node query a data source and then pass the data back to the smart contract, multiple nodes query the data (each of these nodes are also known as a Chainlink).

With multiple independent nodes querying the data, all the answers can be aggregated and compared. If all the answers match then it can be assumed that the this is the correct value and can be passed back to the smart contract. If all answers, bar one, match, it could be assumed that this node is misbehaving and the answer provided by it could be dismissed.

Chainlink doesn’t solve the problem of the original source of data being incorrect. If all nodes are querying the same source of data because there is only one source available, and the source is wrong, the incorrect response will be provided to the smart contract. See section 4 of the whitepaper.

Where does the LINK token come in?
For a smart contract owner to take advantage of Chainlink’s network of decentralised oracles, and therefore more reliable data inputs, they will need to pay the node operators in LINK tokens.

LINK is also used to incentivise the good behaviour of nodes. When node operators bid on an assignment they will have to stake (offer as collateral) a number of LINK tokens. If a node fails to provide the data as agreed in the assignment, they will be penalised and lose the staked LINK tokens. See section 5 of the whitepaper.

Who operates the nodes?
Anyone with sufficient hardware can become a node operator. Unlike some other blockchain projects, Chainlink doesn’t have masternodes that allow you to simply stake large amounts of LINK tokens and earn passive income. To be a node operator you must provide connections to external data.

See Thomas Hodges’ Chainlink Node FAQs.

How do I setup a node?
Thomas Hodges (Technical Community Manager) has created a large number of resources for those interested in setting up and running a node:

YouTube Tutorials
ChainLink Alpha Node Setup

ChainLink Node Install Guide

How to create a smart contract with ChainLink

Install and Run a ChainLink Node on VPS

ChainLink Node Architecture

Install ChainLink Node on Amazon AWS Free Tier

Text Guides
Go Implementation Instructions

For those who are not confident with setting up and maintaining a node, or don’t want the hassle, LinkPool may be an alternative option. LinkPool is not part of, or endorsed, by Chainlink.
