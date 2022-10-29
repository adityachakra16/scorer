# Gitcoin Passport SDK: Scorer

Score the contents of a Gitcoin Passport

## Installation

Add to your project...

```bash
yarn add @gitcoinco/passport-sdk-scorer
```

--

Or download this .git repository and install deps manually...

```bash
yarn install
```

Build...

```bash
yarn run webpack
```

## Basic Usage

Firstly, we need to import the library/bundle and construct a `PassportScorer` instance, passing in the scoring criteria, and optionally the ceramic node URL/networkId

```javascript
// import as a module
import PassportScorer from "@gitcoinco/passport-sdk-scorer";


// or import the bundle
<script src="./dist/scorer.bundle.js" type="script/javascript"/>

...

// create a new instance defining the criteria we wish to score against
const scorer = new PassportScorer([
    {
        provider: "BrightID",
        issuer: "did:key:z6MkghvGHLobLEdj1bgRLhS4LPGJAvbMA1tn2zcRyqmYU5LC",
        score: 0.5
    }
]);

// get the score for a specific address
const score = await scorer.getScore("0x0...");

```

<br/>

The `PassportScorer` instance exposes read-only methods to score the content of a Gitcoin Passport:

<br/>

- `getScore` - pass in a wallet address and get back a score based on the instances scoring criteria and any additional checks
```typescript
PassportScorer.getScore(address: string, passport?: Passport, additionalStampCheck?: (stamp: Stamp) => boolean): Promise<number>
```
