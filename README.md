## StreamingFast Node.js (JavaScript) Example

This simple program demonstrates how easy it is to stream full block details using StreamingFast gRPC
API:

- Request a token from our authentication API
- Creates a gRPC connection with credentials
- Instantiates a BlockStream client
- Start a stream of blocks
- Prints the blocks received

### Requirements

You will need to have Node.js 10+ as well as Yarn or NPM.

#### Quickstart

First of all, visit [https://app.dfuse.io/](https://app.dfuse.io/) to get a free API key for your project.

First, clone this repository to your work folder:

```bash
git clone https://github.com/streamingfast/example-streamingfast-eth-nodejs.git
cd example-streamingfast-eth-nodejs
```

Install all dependencies:

```bash
yarn install
```

Once your environment is setup properly, simply run the `index.js` script:

```bash
node index.js api.streamingfast.io:443 YOUR_API_KEY_HERE
```

By default it prints light details about the blocks, use the `--full` flag to
print the full block in JSON:

```bash
node index.js api.streamingfast.io:443 YOUR_API_KEY_HERE --full
```

**Note** The default `JSON.stringify` will prints the various `bytes` type using `base64` encoding, this is unfortunate as it makes reading it in the JSON harder. If you find a quick option to print it as hexadecimal, open a PR we will be happy to merge it in.

##### Other Networks

Here the list of endpoint to use and the network it serves:

| Network          | Endpoint                     |
| ---------------- | ---------------------------- |
| Ethereum Mainnet | api.streamingfast.io:443     |
| BSC Mainnet      | bsc.streamingfast.io:443     |
| Polygon Mainnet  | polygon.streamingfast.io:443 |
| HECO Mainnet     | heco.streamingfast.io:443    |
| XDAI Mainnet     | xdai.streamingfast.io:443    |

**Important** If you change the endpoint to something else, ensure you also update `index.js` the `start_block_num` and `stop_block_num` to fit the chain you are querying as well as the `include_filter_expr` to ensure to matches at least one transaction in the queried range.
