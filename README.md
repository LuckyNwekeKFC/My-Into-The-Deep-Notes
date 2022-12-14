# Blockchain
My notes, example codes, best practices and sample projects.

## Me
Lucky Nweke ([Linkedin](https://in.linkedin.com/in/luckynwekekfc)).

## Current Status
WIP (Work In Progress)!

## License
Open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT).

-----------

## Important Notes
- [Blockchain Basics](#blockchain-basics)
- [Why Blockchain As Opposed To An Ordinary Database](#why-blockchain-as-opposed-to-an-ordinary-database)
- [Key Concepts](#key-concepts)
    ```diff
    + Blockchain
    + Distributed Ledger
    + Transactions
    + Chaincode
    + Channel Events
    + Chaincode Lifecycle Endorsement Policy Rule
    + Peer Launch Modes
    + Client Side API
    + Arguments Sent To Chaincode
    + Transaction Flow
    + Chaincode Interface
    + The Fabric Model: What makes fabric ideal as an enterprise blockchain solution?
      - Assets
      - Chaincode/Smart Contracts
      - Ledger
      - Privacy
      - Security And Membership Services
      - Consensus
    + Identities
    + Policies
    + Peer
    + Ledger
    + Orderer
    + Channels
    ```
- [Blockchain](#blockchain)
  - [Me](#me)
  - [Current Status](#current-status)
  - [License](#license)
  - [Important Notes](#important-notes)
  - [Blockchain Basics](#blockchain-basics)
  - [Why Blockchain As Opposed To An Ordinary Database](#why-blockchain-as-opposed-to-an-ordinary-database)
  - [Key Concepts](#key-concepts)
  - [Blockchain Technology Benefits](#blockchain-technology-benefits)
  - [Smart Contracts](#smart-contracts)
  - [Development Environment Setup](#development-environment-setup)
  - [CouchDB](#couchdb)
  - [Private Data Collections](#private-data-collections)
  - [Range Queries](#range-queries)
  - [Rich Queries](#rich-queries)
  - [Asset History Logs](#asset-history-logs)
  - [Programmatic Access Control](#programmatic-access-control)
  - [Fabric Node SDK](#fabric-node-sdk)
  - [Common Errors](#common-errors)

-----------

## Blockchain Basics
- It is a decentralized system. Decentralized means the network is **powered by its users (Peers)** without having any third party, central authority or middleman controlling it.
- Every Peer has a record of the complete history of all transactions as well as the balance of every account.
- This bookkeeping is not controlled by one party or a central authority (E.g. Central Bank).
- Its all Public, and available in one digital ledger which is fully distributed across the network. i.e. everybody sees what everybody is doing.
- The Blockchain acts as a public ledger.
- In blockchain all the transactions are logged including:
    * Time
    * Date
    * Participants
    * Amount of every single transaction
- Each node in the network owns the full copy of the blockchain.
- The nodes automatically and continuously agree about the current state of the ledger and every transaction in it.
- If anyone attempts to currupt a transaction, the nodes will not arrive at a **consensus** and hence will refuse to incorporate the transaction in the blockchain.
- So every transaction is public and thousands of nodes unanimously agreed that a transaction has occurred on date X at time Y.
- Everyone has access to shared single public source of truth.
- Blockchain in first instance is all about optimizing **Shared B2B Processes**.

-----------

## Why Blockchain As Opposed To An Ordinary Database
- In a nutshell, a Database solves a Data Problem whereas a Blockchain solves a Digital Asset Problem.
- **Database Solves a Data Problem**:
    * Mature technology exists.
    * Centralized or Distributed.
    * Fit for purpose.
    * **One party governs the data.**
- **Blockchain solves a Digital Asset Problem**:
    * Trade, trust and ownership.
    * Digital Assets.
    * Transactionality.
    * **Multiple parties govern the data.**
    * Remove intermediaries.
    * Solve double spend problem.
    * Need for time and trust in a network.
    * Gives birth to new business models.

-----------

## Key Concepts
- **Blockchain**: It is a shared, replicated transaction system (**Distributed Ledger**) which is updated with the help of **Smart Contracts** and kept consistently synchronized through a process called **Consensus**. It is a append-only transaction system.
    * **Distributed Ledger**: It is a database that is concensually shared and synchronized across multiple sites, institutions or geaographies and it is accessible by multiple people.
    * **Smart Contracts**: It is a self-executing contract with the terms of the agreement between buyer and seller being directly written into lines of codes. The code and the agreement contained therein exists across a distributed, decentralized blockchain network.
    * **Consensus**: The majority of opinion, agreement amoung a group of people.
    * **Private Blockchain vs. Public Blockchain**: In public blockchain, anyone can send a transaction, while in private blockchain, only participants who are approved can send transactions.
    * **Permissioned Blockchain vs. Permissionless Blockchain**: Permissionless blockchain allow people to act anonymously (you do not know their identity), while in permissioned blockchain the identities of participants are known.
    * **Examples of Public and Permissionless Blockchain**: Bitcoin, Etherium.
    * **Examples of Private and Permissioned Blockchain**: Hyperledger Fabric, JP Morgan.
    * **Cryptocurrencies (Bitcoin, Etherium etc.)**: Cryptocurrency is not same as a blockchain. Cryptocurrency use blockchain to store transactions. Most of the cryptocurrencies use their own type of blockchain with some aspects that make them unique and best for their own usecase.
- **Distributed Ledger**:
    * `Distributed Ledger` platforms are used for tracking the `State` of an `Asset`.
    * An `Asset` is a digital representation of any real world thing.
    * So anything in a real world, whether it's a tangible or intangible, that may be digitally represented, can be managed on a `Distributed Ledger`.
    * Tangible assets examples: Cars, Houses, etc.
    * Intangible assets examples: Stocks, Bonds, Certificates and any other kind of financial instruments.
- **Transactions**:
    * The state of an `Asset` on the `Distributed Ledger` is managed by the way of `Transactions`. In other words, `Transactions` manages the `States` of an `Asset`.
    * `Transaction` represents the invocation of business logic that changes or manages the `State` of the `Assets` on the `Distributed Ledger` platform.
    * `Chaincode` encapsulates the business logic.
    * All `Transactions` are recorded in the `Ledger`.
    * The recorded `Transactions` are immutable. i.e. they cannot be updated or deleted.
- **Chaincode**:
    * `Chaincode` implements the business logic and exposes the `State` management features by way of one or more functions.
    * The functions exposed by `Chaincode` are executed from the `Applications` by way of `Transactions`.
    * Not all of the `Transactions` lead to the creation of entry in `Ledger`. Some `Transactions` are performed to read `State` of an `Asset` in the `Ledger`.
    * Fabric Chaincode can be developed in `Golang`, `NodeJS` or `Java`.
    * Any real world asset that can be degitized can be represented as a `Model` in the `Chaincode`.
    * Each of the chaincode in the network is identified by a name which is unique across `Channel`.
    * `Instantiation Policy` determines which `Org` can `Endorse` the `Transaction` for creation of the `Chaincode`.
    * Peers receive the chaincode package in the instantiate transaction and hence the installation of chaincode on peer is automatic: **FALSE**.
    * `Shim API` is used for coding the `Chaincode`.
    * Not all `Orgs` need to install `Chaincode`. Following entities has the `Chaincode`:
        - `Orgs` participating in the `transactions`.
        - `Orgs` that will query the `ledgers`.
        - `Chaincode Endorsers`
    * Important points about `Chaincode`:
        - `Chaincode` may implement multiple `Smart Contracts`.
        - `Chaincode` is packaged in standard `Tar` file format.
        - `Installation` generates the `Package-ID`.
        - Each `Org` approves the specific `Package` for their `Org`.
        - `Package-ID` may be different across `Orgs`.
        - Whenever a `Chaincode` is approved by an `Org`, the `Approval` is added as a `Transaction` into the `Ledger` of that `Org`.
    * By default `State Data` is setup in `LevelDB` but we can configure `Peer` to store `State Data` in `CouchDB` instead of `LevelDB`.
    * `CouchDB` is a `NoSQL` database which can be setup as a `State Data` store for `Peer` node.
    * `CouchDB` allows to execute rich queries against `State Data` whereas `LevelDB` doesn't allow it.
    * Each `Chaincode` owns the `State Data` it manages.
    * Direct access to `State Data` from one `Chaincode` to another is not allowed. However, `Chaincode` can `Invoke` or `Query` other `Chaincode` to access it's `State Data`.
    * Invoke `Chaincode` from another `Chaincode`:
        - Since the `Chaincode` is invoked locally, both the `Chaincodes` (caller and the called `Chaincode`) must be on the same `Peer`.
        - `Transaction` executes in the same `Txn` `Context`.
        - `State` changes on both the caller and the called `Chaincode` take effect only if they share a common `Channel`.
        - No `State` change takes place on the called `Chaincode` if the caller and a called `Chaincodes` are on different `Channels`.
        - `Transaction` message is passed from the caller `Chaincode` to the called `Chaincode`.
        - On **common** `Channel`: `State` changes take effect for both caller and a called `Chaincode`.
        - On **different** `Channel`: `State` changes take effect only for the caller `Chaincode`.
- **Channel Events**:
    * Events are emitted by the `Peers`.
    * Applications may subscribe to the events.
        - **`Subscription` is on `Channel` level**. i.e. `Subscription` requires the specification of the `Channel`.
        - Subscribers can also specify the filter criteria on which the events are evaluated on the `Peer`.
    * There are 3 types of Events:
        - `Block Event`: Emitted by the `Peer` when a new `Block` is added by the `Peer` to the `Ledger`.
        - `Transaction Event`: Emitted by the `Peer` when a specified `Transaction` is received in a `Block`.
        - `Chaincode Event`: Emitted by the `Chaincode`. `Chaincode Events` are generated in response to the `Transactions` against the `Chaincode`.
    * `Chaincode Events` are not received by the subscriber when the `Chaincode` is executed by the `Endorsers`. The events are received by the subscriber when the `Peer` adds the `Transaction` to the `Ledger`.
    * The subscriber can provide the name of the `Event` in which they are interested.
    * The `Transaction Event` and `Chaincode Events` are in the `Block` payload.
- **Chaincode Lifecycle Endorsement Policy Rule**:
    * Network members sets up the `Lifecycle Endorsement Policy`.
    * It decides:
        - How many approvals are needed for a commit to be successful.
        - It may have a rule that says some specific `Organization` must `Endorse` the `Transaction` for it can be committed successfully.
    * This `Policy` is embedded in the `Channel` `Genesis`.
    * `Rules` can be updated with `Channel` update transactions.
    * `Lifecycle Endorsement Policy` can be specified as `ImplicitMeta Policy` or a `Signature Policy`.
    * Default `Policy` is the `Rule = "MEJORITY Endorsement"`. It means that `More than HALF the members of the network MUST approve the Chaincode definition for it to be committed successfully`.
    * The `Policy` rule `Rule = "ANY Endorsement"` requires `Only one approval for committing the Chaincode`.
    * With the help of `Signature Policy`, we can create complex/flexible expressions.
- **Peer Launch Modes**:
    * `Net` mode: `Chaincode` instance launched by `Peer`. This is the **Default** mode.
        - Used in live network.
        - Chaincode Logs are written to the container's file system.
    * `Dev` mode: `Chaincode` instance launched by Developer.
        - Development time only.
        - Chaincode Logs are written to the console.
        - No need to install/upgrade for changes.
        - To launch `Peer` in `Dev` mode:
        ```sh
        # 1. Launch peer in dev mode
        peer node start --peer-chaincodedev
        # 2. Install chaincode to Peer
        # 3. Run chaincode on Terminal/Shell
        # 4. Instantiate the chaincode to Peer
        ```
        - **NOTE:** Chaincode instance is not launched in the Docker container.
        - Helper scripts:
        ```sh
        ##### BOTH COMMANDS USE ENV VARS! #####

        # Builds the Golang chaincode
        /network/bin/cc-build.sh # go build $CC_PATH

        # Runs the Golang chaincode
        /network/bin/cc-run.sh # go run $GOPATH/src/$CC_PATH/*.go
        ```
        - Example commands:
        ```sh
        cd /network/bin/

        # Initialize dev environment in Dev mode.
        # -d: Dev mode
        ./dev-init.sh -d

        # Set env vars for "acme" Org
        source ./set-env.sh acme

        # Check/verify env vars for Org
        ./set-chain-env.sh

        # Package and install chaincode on Peer
        # -p: Package chaincode
        ./chain.sh install -p

        # In new terminal, ssh into vagrant

        # Set Org context in new terminal
        source set-env.sh acme

        # Start chaincode in Terminal mode
        cc-run.sh

        # In other terminal, we can run following commands
        chain.sh instantiate # To instantiate the chaincode
        chain.sh invoke # To invoke chaincode
        chain.sh query # To query chaincode
        ```
- **Client Side API**:
    * `Chaincode` gets deployed on the `Peer`.
    * `Applications` use the `Fabric Client SDK` for interacting with the `Chaincode`.
    * There are 2 APIs that are used by the `Applications`.
        - **Invoke API**: Used for executing the business logic in the `Chaincode` by way of `Transactions`.
        - **Query API**: Used for reading the `State` of the `Assets` from `Distributed Ledger` platform.
    * Both `Invoke API` and `Query API` executes the functions exposed by the `Chaincode`.
- **Arguments Sent To Chaincode**:
    * The `Client Side API` executes the functions by passing data in JSON format to the `Chaincode`.
    * The JSON object has a key called `Args`, which is set to an array of string types. The first element in the `Args` array is the `function name` which will be executed by the `Chaincode` in response of this API invocation on the client side. Rest of the arguments in the `Args` array are the parameters passed to the function called by `Chaincode`.
    ```json
    {
        "Args": ["FunctionName", "Param1", "Param2", "Param..n"]
    }
    ```
- **Transaction Flow**:
    * When client executes an `Invoke` API, the `Transaction Proposal` is created and it is sent to the `Endorsing Peers`. If everything is good with the proposed transaction, the `Endorsing Peers` `Sign` the `Transaction Proposal` and send it back to the client. The client then sends the `Signed Transaction Proposal` to the `Orderer Service` for including the transaction in the `Block`. `Orderer Service` at some point creates the `Block` and sends the `Block` to the `Peers` in the `Network`. Not all of the `Peers` have `Chaincode` installed on them. Those `Peers` will still receive the `Block` sent by `Orderer Service`.
    * When client executes a `Query` API, any of the `Peer` with a `Chaincode` installed on it, will execute the `Chaincode Function` and return response to the client. In this invocation, the client does not go through the `Orderer Service`.
- **Chaincode Interface**:
    * All Golang `Chaincode` must implement following 3 functions:
        - `Init()`: Chaincode initialization logic. Called with `invoke --is-init` flag.
        - `Invoke()`: Contains business logic. Executed on `Query` and `Invoke [Without init flag]`.
        - `main()`: Registers chaincode with the fabric runtime.
- **The Fabric Model**: What makes fabric ideal as an enterprise blockchain solution?
    * **Assets**:
        - Asset definitions enable the exchange of almost anything with monetory value over the network. For e.g. Whole foods, antique cars, currency features, bonds, stocks, digital goods etc.
        - Asset within the network are represented as a collection of key-value pairs with state changes that records the transaction on the ledger or distributed ledger.
        - Assets can be represented in `Binary` and `JSON` format.
        - There are 2 types of Assets viz. `Tangible Assets` and `Intangible Assets`
            * **Tangible Assets**: Tangible assets are typically physical assets or properties owned by a company. For e.g. Computer equipment. Tangible assets are the main type of assets that companies use to produce their product and service.
            * **Intangible Assets**: Intangible Assets don't exists physically, yet they have a monetory value since they represent potential revenue. For e.g. stock, bond, copyright of a song. The record company that owns the copyright would get paid a royalty each time the song is played.
    * **Chaincode/Smart Contracts**:
        - Chaincode contains the smart contracts.
        - Many times chaincodes and smart contracts are used interchangeably because in most cases they mean exactly the same.
        - Chaincode defines the asset and also enforces rules for interacting with the asset or any other information that is stored on the distributed ledger.
        - Chaincode functions execute against the ledger's current state database and are initiated through transaction proposals.
        - Chaincode execution results in a set of key-value pairs which are also called a `Right Set`.
        - `Right Set` can be submitted to the network and thereby append to the ledger.
        - Chaincode execution is partitioned from transaction ordering, limiting the required level of trust and verification across node types, and optimizing network scalability and performance.
        - Chaincode or Smart Contracts define all the business logic.
        - Chaincode/Smart Contracts are stored on `Peer` nodes.
    * **Ledger**:
        - Ledger contains all of the state mutations or transactions. These state changes are produced by the invocation of chaincode.
        - The immutable, shared ledger encodes the entire transaction history for each channel, and includes SQL-like query capability for efficient auditing and dispute resolution.
        - Ledgers store all of the data.
        - Ledgers are stored on `Peer` nodes.
    * **Privacy**:
        - Channels and Private Data Collections enable private and confidential multi-lateral transactions that are usually required by competing businesses and regulated industries that exchange assets on a common network.
    * **Security And Membership Services**:
        - In Fabric Network, all participants have known identities.
        - Public key infrastructure is used to generate cryptographic cenrtificates. These certificates can be tied to an organization, a network component, a user or a client application. These certificates can be used to manage data access control.
        - Role based governing with the help of certificates is the thing which made Fabric `Permissioned`.
        - Permissioned membership provides a trusted blockchain network, where participants know that all transactions can be detected and traced by authorized regulators and auditors.
    * **Consensus**:
        - At a very high level, we can say Consensus Model has something to do with multiple participants agreeing on something.
        - A unique approch to Consensus enables the flexibility and scalability needed for the enterprise.
- **Identities**:
    * Every actor in a network has a digital identity. It is represented by `X-509` certificate.
    * Identities determine resources and access to information for actors.
    * This determination is done based on attribute called `Principals` in certificate.
    * The identity with attribute are called `Principals`. We can think of a `Principal` as some sort of a userid.
    * Identities are created by a trusted **`Certificate Authority`**. In fabric, we can use a `Certificate Authority`.
    * The process of handing out certificates is called **`PKI` (Public Key Infrastructure)**. `PKI` provides a secure way of communication.
    * Just having certificate is not enough for any actor. We also need the network to acknowledge the certificate. For e.g. we need organization to say - "Yes this certificate belongs to my organization". The `Identity` must be registered in the organization's **`MSP` (Membership Service Provider)**.
    * **`MSP` (Membership Service Provider)** turns verifiable identities into members of the blockchain network.
    * **`PKI` (Public Key Infrastructure)** is a collection of internet technologies that provides secure communication in the network.
    * **`PKI` (Public Key Infrastructure)**:
        - Digital Certificates
        - Public and Private Keys
        - Certificate Authorities
        - Certificate Revocation Lists
    * **`MSP`** - For a member to have an access to the network, we need 4 things:
        - Have an identity issued by a CA that is trusted by the network.
        - Become member of an organization that is recognized and approved by the network members.
        - Add the `MSP` to either a consortium on the network or a channel.
        - Ensure the `MSP` is included in the policy definitions on the network.
- **Policies**:
    * A policy is a set of rules that can define how a decision is made.
    * Policies describe a who and a what.
    * In Hyperledger, `Policies` are used for infrastructure management.
    * Uses of `Policies` in Hyperledger network:
        - Adding/Removing members from channel.
        - Change the structure of blocks.
        - Specify count of organizations for endorsement of transactions
    * How do we write `Policy` in Fabric:
        - **Signature Policies**:
            - Turns verifiable identities into members of a blockchain network.
            - `<OR | AND | NOutOf>`
        - **ImplicitMeta Policies**:
            - Only used for channel configuration.
            - `<ANY | ALL | MAJORITY>`
- **Peer**:
    * `Chaincodes/Smart Contracts` and `Ledgers` are stored on `Peer` nodes that are owned by `Organizations` inside the network.
    * `Peer` nodes can host multiple instances of `Chaincodes` and `Ledgers`.
    * End-users communicate with the network by using applications that connect to the `Peer` nodes of their `Organization`.
    * `Peers` use `Channels` to interact with other network components.
    * All `Peers` belong to `Organizations`.
    * `Peers` have an `Identity` assigned to them via a digital certificate (`x.509`).
    * Single Peer itself cannot update information stored in ledger on it. Updating requires a consent of other Peers in network. The update transaction is done in 3 steps:
        - Step #1: `Proposal`.
            * Independently executed by `Peers` and returns `Endorse Proposal` responses.
        - Step #2: `Ordering` and `Packaging` transactions into blocks.
            * `Orderer` receives `Endorsed` transactions and then creates the blocks.
        - Step #3: `Validation` and `Commit` of the transaction.
            * When `Peer` receives a new block from the `Orderer`, the `Peer` processes the block resulting in a new block being added to the `Ledger`.
- **Ledger**:
    * On the ledger, we are recording facts about current state of the object.
    * Change history in ledger is immutable.
    * In Fabric, ledger consists of 2 parts:
        - **`World State`**:
            * It is a database that holds the current value of the object.
            * It can change frequently.
        - **`Blockchain`**:
            * It records all the transactions for the object that together results in a `Current World State`.
            * Transactions are collected inside blocks that are appended to the blockchain.
            * Blockchain data structure is very different from `World State`. It's immutable.
            * Blockchain does not use a database.
            * Blockchain is implemented as a file. The reason for this is because there are just few operations done on a Blockchain.
            * Primary operations of a Blockchain is to append data to it. And a file is perfect for that.
            * First block is called the `Genesis Block`. It does not contain transaction data. It contains configuration of a initial state of a network channel.
            * Blocks are connected together with the `Header` of a block.
            * Each block in blockchain has following structure:
                - **Block Header**: Contains following parts:
                    * **Block Number**: Integer starting at `0` (`Genesis Block`), and increased by 1 for each new block.
                    * **Current Block Hash**: Hash of all the transactions contained in the current block.
                    * **Previous Block Header Hash**: Hash from the previous `Block Header`.
                - **Block Data**: Contains list of transactions arranged in order.
                - **Block Meta-Data**: Contains certificate and the signature of the block creato which is used to verify the block.
- **Orderer**:
    * Orders transactions into blocks.
    * Maintains list of Organizations that can create channels. This list of Organizations is called the `Consortium`. Also, this list is stored in a `System Channel` (Channel for the Orderers).
    * Enforce access control for channels (Application Channels). This way they can restric user from Reading and Writing on a Channel.
    * Manage structure of the blocks.
    * We can tweak the structure of the blocks by setting the `BatchSize` and `BatchTimeout` parameters.
        - **BatchSize**: Maximum transaction count in one block.
        - **BatchTimeout**: Maximum time for a new block creation. This time is measured from the first transaction received in this new block.
    * Ordering service implementations:
        - Kafka (Deprecated since Fabric v2)
        - Solo (Deprecated since Fabric v2)
        - **Raft (Recommended)**: It is a `Crash Fault Tolerant (CFT)` ordering service. It implements `Leader-Follower` model.
    * It is better to have multiple Orderer nodes that are owned by different Organizations. This way we make sure that even the ownership is decentralized.
    * **`Raft` is a protocol for implementing distributed `Consensus`**.
    * In `Raft` there are 2 `timeout` settings which control the elections:
        - **Heartbeat Timeout**
        - **Election Timeout**
    * **Raft Election Process**: It's the amount of time a `Follower` waits until becoming a `Candidate`. After `Election Timeout`, the `Follower` becomes a `Candidate` and starts a new election term, votes for itself and sends out `Request Vote` messages to other nodes. If the receiving node hasn't voted yet in this term then it votes for the `Candidate` and the node resets it's `Election Timeout`. Once the `Candidate` has a majority of votes, it becomes a `Leader`. The `Leader` begins sending out `Append Entries` messages to it's `Followers`. These messages are sent in intervals specified by the `heartbeat timeout`. Followers then respond to each `Append Entries` message. This election term will continue until a follower stops receiving heartbeats and becomes a candidate. If 2 nodes become candidate at the same time then a split vote can occur. Once we have a leader elected, we need to replicate all changes to our system to all nodes. This is done by using the same `Append Entries` message that was used for `heartbeats`. Raft can even stay consistent in the face of network partitions.
- **Channels**:
    * `Channels` are created by creating the first `Transaction` and submitting the `Transaction` to the `Ordering Service`. This `Channel` creation `Transaction` specifies the initial configuration of the `Channel` and it is used by the `Ordering Service` to write the `Channels Genesis Block`.
    * We can use `Configtxgen` tool to create the first `Transaction` which will end up creating `Channel` and writing `Genesis Block` on that `Channel`.
    * The `Configtxgen` tool works by reading the `network/configtx/configtx.yaml` file which holds all of the configurations for the `Channel`. This file uses `Channel Profiles`.
    * `Configtxgen`:
        - Reads from the `network/configtx/configtx.yaml` file.
        - Can create a `Configuration Transaction` for the `Application Channel`.
        - Can create a `Genesis Block` for the `System Channel`.

-----------

## Blockchain Technology Benefits
- **Security**:
    * Since Blockchain is a distributed concensus based architecture, it's eliminates single point of failure and reduces the need for data intermediaries such as transfer agents or messaging system operators.
    * It helps prevent frauds and malicious third parties from doing bad things.
    * Its not fullproof and we do hear about hacks in the box or certainly in cryptocurrency or cryptocurrency exchanges but its very very difficult to hack or manipulate.
- **Transparency**:
    * It provides transparency and in place multialise standards, protocols and shared processes.
- **Trust**:
    * Its transparent and the immutable ledger makes it easy for different parties in a business network to collaborate, manage data and reach agreements.
- **Programmability**:
    * Its programmable, so its able to execute things like **smart contracts** and help be more tamper proof and have deterministic software that automates the business logic.
    * We can code to address many different things from governance to compliance, regulatory compliance, data privacy, identity, looking at things like "know your customer" types things or anti money laundring attributes.
    * It manages that stakeholder participation, like for things like proxy voting.
- **Privacy**:
    * It provides privacy.
- **High-Performance**:
    * It can be a private network of hybrid networks and they are engineered to sustain hundreds/millions of transactions per second and also handle periodic surges in network activity.
- **Scalability**:
    * Its highly scalable.
- **Authenticity and Scarcity**:
    * Digitization really ensures data integrity and enables acid profits. It's really a full transaction history in that single shared source of truth.
- **Streamlined Processes**:
    * Since it can automate almost everything, it can enable some more real time settlements, auditing, reporting and reduces processing times and the potential for error and the delays due to number of steps and intermediaries required to achieve the same level of confidence.
- **Economic Benefits**:
    * Reduced infrastructure, operational and transaction cost.
- **Market Reactivity**:
    * It can be very reactive to market.

-----------

## Smart Contracts
- **Contracts**:
    * A contract is formed when an **offer** by one party is **accepted** by the other party.
    * **Consideration** is the price paid for the promise of the other party. The price may not necessarily involve money.
        - For e.g. If you walk my dog, i will feed your cat.
        - For e.g. If you walk my dog, i will pay you 15 Rs.
- **Smart Contracts**:
    ```go
    Contract terms are agreed to ----> Smart Contract placed on the Blockchain ----> Triggering event causes contract to be automatically executed
    ```
    * **Contract terms are agreed to**: Hard coded and cannot be changed without both parties being aware.
    * **Smart Contract placed on the Blockchain**: Public viewed and verified.
    * **Triggering event causes contract to be automatically executed**: If/then statement coding.

-----------

## Development Environment Setup
- Install `Oracle Virtual Box` [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads).
- Install `Vagrant` [https://www.vagrantup.com/downloads](https://www.vagrantup.com/downloads).
```sh
# Initialize vagrant and create Vagrantfile
vagrant init

# +-+-+-+-+-+-+-+-+ Configure Vagrantfile +-+-+-+-+-+-+-+-+
# Checkout boxes at: https://vagrantcloud.com/search
config.vm.box = "generic/ubuntu2010"

# Setup network
config.vm.network "private_network", ip "192.168.33.10"

# Mount folder
config.vm.synced_folder "./mount", "/home/vagrant/mount"

# Configure memory
config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.memory = "10000" #10 GB
end
# +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+

# Bootup our virtual linux box
vagrant up

# SSH into our running virtual linux box
vagrant ssh

# +-+-+-+-+-+-+- Install HLF Pre-Requisites +-+-+-+-+-+-+-+
# https://hyperledger-fabric.readthedocs.io/en/release-1.4/prereqs.html
# install git
sudo apt install  git -y

# install curl
sudo apt install curl -y

# install docker
sudo apt install build-essential -y
sudo apt install apt-transport-https ca-certificates gnupg-agent software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose -y
sudo usermod -aG docker $USER
newgrp docker

# install go
curl -o "go.tar.gz" https://storage.googleapis.com/golang/go1.17.1.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf "go.tar.gz"

export PATH=$PATH:/usr/local/go/bin
source ~/.bashrc

# install node
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt install nodejs -y

# install ohmyzsh
# NOTE: Default password for root account on ubuntu: vagrant
sudo apt install zsh -y
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
- Install Samples, Binaries and Docker Images:
```sh
# SSH into vagrant
vagrant ssh

# Go to /mount directory
cd mount

# Install samples, binaries and docker images
curl -sSL https://bit.ly/2ysbOFE | bash -s -- 2.2.4 1.5.2
```
- Install `SSH` plugin for VSCode.
- While vagrant machine is up and running, execute following to get location of `IdentityFile`:
```sh
vagrant ssh-config
```
- Add new SSH host into VSCode SSH plugin:
```sh
# Host can be found in Vagrantfile. Look for following line:
# config.vm.network "private_network", ip: "192.168.33.10"
ssh vagrant@192.168.33.10 -i "C:/Aditya/Projects/HLF/.vagrant/machines/default/virtualbox/private_key"
```
- Add `\bin` to path:
```sh
# In vagrant ssh, execute:
export PATH=/home/vagrant/mount/fabric-samples/bin:$PATH
```

-----------

## CouchDB
- We can use CouchDB as out `State Database`.
- `Ledger` contains a `Blockchain` and a `State Database`. Blockchain is implemented as a file and a State Database is implemented as a database.
- By default, we use a `Go Level Database` and this database is implemented in the `Peer` node.
- `LevelDB` stores `Chain Code` data as `key-value` pairs. It supports queries based on `key`, `key range` and `composite key`.
- As an alternative `LevelDB`, we can use `CouchDB` as a `State Database` of the `Ledger`.
- **With CouchDB**:
    * We can store data as `JSON` objects.
    * We can write more complicated queries for retrieving specific data.
    * We can use `Indexes` for more efficient querying at larger data sets.
- We need to decide which database we will be using as a State Database before setting up the network. Otherwise, we have to bring down the network, enable CouchDB and bring the network up again.
- Each `Peer` has its own instance of the `CouchDB`.
- No data replication at the `CouchDB` level.
- Remote access is disabled to `CouchDB`.
- `CouchDB` stores dates in format: `YYYY-MM-DDThh:mm:ss.s`.

-----------

## Private Data Collections
- There are 3 levels of data privacy:
    * Channels
    * Private Data Collections
    * Encryption
- `Private Data Collections` can provide privacy for subsets of `Organizations` within a `Channel`.
- Private data collection consists of:
    * The private data itself
    * Hash of the private data
- The Private data cannot be shared with the `Ordering` service.
- The Private data is stored on a separate database. Nothing is stored in the `State Database`.
- Peers that don't have access to the Private Data Collections, don't have any data on their Peer node.
- `Gossip Protocol` is used for communication between `Peer` nodes. This is a reason why we need to connect at least one `Peer` node of the `Organization` to the `Channel` as an `Anchor Peer`. Because of this, `Peers` know of each other's existence. Thats how we implement Peer to Peer communication using `Gossip Protocol`.
- What can we do with `PDC (Private Data Collection)`:
    * Use a corresponding public key for tracking public state.
    * Chaincode access control.
    * Sharing private data out of band.
    * Sharing private data with other collections.
    * Transferring private data to other collections.
    * Using private data for transaction approval.
    * Keeping transactors private.
- `Members` on the `Channel` can **restrict visibility of data**.
- `Ledger` is **COMMON** so all `Transactions` are still visible to all.
- `Transaction` in `Ledger` has `HASH` of data that is stored in `Private Data Collections`.
- `Private Data Collection` are configured using JSON at the time of `Chaincode` `Instantiate` or `Upgrade`.
- `Peers` manages `PDC` data in a separate set of datastores.
- `PDC` are isolated `namespaces` within `Chaincode`.
- `PDC Key-Values` are accessible within `Chaincode` using `Chaincode Stub API`.
- `Policies` control read access to the `PDC`.

-----------

## Range Queries
- Range Queries require `Start Key` and the `End Key`.
- `Start Key` is included in the result set.
- `End Key` is exluced in the result set.
- If `Start Key` and `End Key` are not specified i.e. Empty strings are provided, then result set will have all the Keys from state data set.
- Keys are indexed in `Lexical Order`.
- Maximum results returned in result set can be restricted by `Peer Config`.
- Commonly used functions from Chaincode Stub API for executing range queries are `GetStateByRange()` and `GetPrivateDataByRange()`.
- `Composite Key`:
    * A key formed by combining 2 or more attributes of the record.
    * Uniqueness is guarenteen only if all parts of the key are used.
    * None of the `Key` attribute values in `Composite Key` can contain a `null` character. i.e. `\0x00`
    * When the `PutState` is executed, the index is created in the `state database`.
    * `GetState()` and `GetStateByRange()` functions do not support `Partial Composite Keys`.

-----------

## Rich Queries
- Requires data to be modeled as `JSON`.
- `Peers` need to use `CouchDB`.
- `Indexes` need to be created for performance.
- Restrictions on CouchDB JSON Documents:
    * Key cannot begin with underscore `_`.
    * Fields beginning with underscore `_` are used internally.
    * `~version` is a reserved field.
- Rich queries for `CouchDB` are created using **`Mango Queries`** language.
- `Mango` query language:
    * Declarative `JSON` query language.
    * Inspired by `MongoDB` query language.
    * Adopted by `Cloudant` and `CouchDB`.
- Rich queries are not executed at the time of `Validation`. This may lead to inconsistent state of chaincode.
- Do not use `Rich Queries` in `Update Transactions (Invoke)` unless we can guarentee `No Phantom Reads`.

-----------

## Asset History Logs
- Fabric manages `Assets` in the `Chaincode`.
- `Invoke Transaction` changes the `State` on per `Key` basis.
- We can use `Queries` to get the `Current State` of the `Asset`.
- `Queries` don't provide history of the `Transactions` on specific `Asset`. i.e. `Queries` cannot get the `Past State`. for e.g. List all previous owners of the vehicle with id `Vin#1000`.
- To get the history of `Transactions` on `Asset`, we use `History Log` and `History API`.
- `Asset History Log` are managed on per `Peer` basis.
- `Peers` on which the `Chaincode` needs access to the `History Log` must be configured to `Create` and `Update` these `History Logs`.
- `Peer` once enabled for managing the `History Logs`, will create the log on per `Chaincode` or per `Asset` basis.
- `Asset History` on `Peer` is managed in a separate datastore.
- Regardless of what database is used as `State Database`, the `Asset History` is always managed in `GoLevelDB` database.
- `History Logs` are setup at `Peer` level. They are not replicated by way of `Gossip`. `Peer` is responsible for managing the `Asset Logs` on it's own.
- `History API` is used from within the `Chaincode` to access history.
- To enable history database, look for following setting in `core.yaml`:
```yml
history:
    enableHistoryDatabase: true
```
- Just like `Rich Query API`, the `History API` is also not re-executed in `Validation` phase of the `Transaction`. This may lead to inconsistent `State` of `Chaincode`.
- Do not use `History API` in `Update Transactions (Invoke)` unless we can guarentee `No Phantom Reads`.

-----------

## Programmatic Access Control
- Fabric uses `PKI (Public Key Infrastructure)` for `Identity Management`.
- All users are issued a `X509` certificate (`Enrollment` certificate). For e.g. Admin and other users in multiple roles.
- All nodes in the network are also issued a `X509` certificate. For e.g. `Orderer`, `Peers`, `Client` etc.
- `Authorization` decision is made by the nodes based on the user's `Role` and the `Policies` that have been set up for the network. For e.g. Only the identities assigned the `Role` of `Admin` can install and instantiate the chaincode.
- At the network level, the `Access` and `Authorization` control is achieved by way of configuration. i.e. we have to declare the `Policies` that will drive the `Access` and `Authorization` at node level.
- For building `Access Control` in `Chaincode`, check the `Client Identity Chaincode Library`: [https://github.com/hyperledger/fabric-chaincode-go/tree/main/pkg/cid](https://github.com/hyperledger/fabric-chaincode-go/tree/main/pkg/cid)
- Custom `Attributes` are added to the `X509` certificates by the `Registrar`.
- `Client Identity Chaincode Library` provides access to the `Attributes` or `Identity` set in `X509` certificates.
- `Cryptogen` tool does not support addition of `Attributes` in the certificates.
- For additional `Attributes` support in `X509` certificates, the `Identities` need to be setup with a `fabric-ca`.

-----------

## Fabric Node SDK
- Module: `fabric-network`:
    * `Gateway Class`: Connection point for accessing the network.
    * `Network Class`: Represents set of `Peers` belonging to a network or the `Application Channel`.
    * `Contract Class` and `Transaction Class`: Exposes APIs (`Invoke` and `Query`) for Chaincode interactions. `Transaction Class` exposes additional APIs for providing finer control over Chaincode interactions.
    * Example flow: Pattern: Invoking and Querying Chaincode:
        - Application creates instance of `Gateway Class` using `new` operator.
        - Application then initializes the `Gateway Instance` with `Wallet` and the `Connection Profile`.
        - `Wallet` holds the credentials information for the user. `Connection Profile` is provided in the form of `YAML` or `JSON` file.
        - After initialization, the Application creates an instance of `Network Class` by invoking a function on `Gateway Class`.
        - Then, Application creates the instance of `Contract Class` by invoking a function on the `Network Class` instance.
        - Functions exposed by the `Contract Class` are then used for executing the `Invoke` and `Query` functions on the `Chaincode`.
    * `fabric-network` module exposes classes for managing `Wallets`.
- **`Wallet`**:
    * A user may participate in multiple networks with different `Roles`.
    * In other words, a user may have multiple `Identity Profiles` to interact with different networks.
    * `Wallet` is construct that is used for managing these `Identity Profiles`.
    * `Wallet` contains one or more user `Identity Context` and each of these `Identity Context` or `Identity Profiles` have `Certificates`, `Private Key` and a `Public Key`.
    * `Identities` in `Wallet` are referred to by a `Label` which is a free format string and it is unique for each of the `Identities` managed in the `Wallet`.
    * `Wallet` interface:
        - `InMemoryWallet`: Manages identities in memory.
        - `FileSystemWallet`: Manages identities on user's filesystem.
        - `CouchDBWallet`: Manages identities in a CouchDB Server.
- Module: `Client Class` API:
    * Provides low level functions (via `Channel Class`) for interacting with the `Peer` and the `Orderer`.
    * Acts as a factory for `Peers`, `Orderer`, `Channel` and `Chaincode` classes.
    * Provides functions for managing the `client instance` configuration.
    * Manage `Channel Update Transactions`.
    * Instance is `Stateful`. i.e. We cannot re-use same instance against multiple `Channel`.
    * `Channel` related updates require multiple `Admin` signatures.
    * `Channel Config` update `Tx` submitted to `Orderer`.
    * Creates instances of `Peer Class` that are used for `Peer` queries.
    * Provides functions for managing `Channel Configuration`.
- Module: `Channel Class` API:
    * Provides API for carrying out `Channel Aware Queries` and `Channel Aware Tasks`.
    * For e.g.
        - Create new `Channel`
        - Update existing `Channel`
        - Access to `Ledger (Blk, Txn)`
        - Joining `Peer` to the `Channel`
        - Instantiation, Invoke and Querying of the `Chaincode`
        - Getting finer control over flow of the `Transaction`
    * Channel class instance is initialized with `Peers` or `Orderer` on `Channel`.
    * Exposes functions for accessing the `Channel Configuration`.

-----------

## Common Errors
- Error:
```sh
zsh: ./networkdown.sh: bad interpreter: /bin/bash^M: no such file or directory
```
- Solution:
```sh
sed -i -e 's/\r$//' networkdown.sh
```
-----------
- Error:
```sh
Docker not installed
# OR
Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/json": dial unix /var/run/docker.sock: connect: permission denied
```
- Solution:
```sh
# ssh into vagrant box
vagrant ssh

# snap install docker
sudo snap install docker

# To fix permission issue
# Change docker.sock file to be owned by "vagrant" user
sudo chown vagrant /var/run/docker.sock
```
-----------
- Minifabric: How to install, approve, commit and initialize chaincode in a single command?
```sh
./minifab install,approve,commit,initialize -n simple -v 2.0 -p '"init","Aditya","35","Nishigandha","30"'
```
-----------
- Minifabric: How to update endorsement policy?
```sh
./minifab anchorupdate
./minifab discover # This will create a folder "discover" at "/vars/discover"
./minifab channelquery # This will create a channel config file at "/vars/channel1_config.json". Make the changes and save this file.

# Do the channel update to apply new changes
./minifab channelsign,channelupdate
```