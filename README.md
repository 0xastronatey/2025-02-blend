# Blend V2 Audit + Certora Formal Verification details
- Total Audit Prize Pool: $125,000 in USDC
  - HM awards: $73,500 in USDC
  - QA awards: $2,800 in USDC
  - Judge awards: $5,000 in USDC
  - Validator awards: $3,200 in USDC 
  - Scout awards: $500 in USDC
  - Mitigation Review: $20,000 in USDC
  - Formal Verification: up to $20,000 in USDC
    - Real Bug Rules: $4,000 in USDC
    - Coverage Rules: $14,000 in USDC
    - Participation Rules: $2,000 in USDC
- [Read our guidelines for more details](https://docs.code4rena.com/roles/wardens)
- Starts February 24, 2025 20:00 UTC
- Ends March 17, 2025 20:00 UTC

**Formal Verification pool is conditional:** If no valid rules are submitted, the Formal Verification awards will be added to the HM award pool. 

ℹ️ This audit includes **deployed code,** and [the "live criticals" exception](https://docs.code4rena.com/awarding/incentive-model-and-awards#the-live-criticals-exception) therefore applies. Please see the section titled "Live/Deployed Code" for details.

**Note re: risk level upgrades/downgrades**

Two important notes about judging phase risk adjustments: 
- High- or Medium-risk submissions downgraded to Low-risk (QA) will be ineligible for awards.
- Upgrading a Low-risk finding from a QA report to a Medium- or High-risk finding is not supported.

As such, wardens are encouraged to select the appropriate risk level carefully during the submission phase.

## Live/Deployed Code

For the purposes of the ["live criticals" exception](https://docs.code4rena.com/awarding/incentive-model-and-awards#the-live-criticals-exception) and [sensitive disclosure process](https://docs.code4rena.com/roles/wardens/submission-guidelines#how-to-submit-zero-day-or-otherwise-highly-sensitive-bugs), contracts in the following directories should be considered live code, as they have only changed incrementally from the V1 code, which is deployed: 
- `./blend-contracts-v2/pool/*`
- `./blend-contracts-v2/pool-factory/*`
- `./blend-contracts-v2/backstop/*`

All other code in scope is _not_ deployed. Vulnerabilities with a root cause in any part of the codebase _except_ the above-listed directories should therefore be submitted via the standard submission form/process.

## Automated Findings / Publicly Known Issues

_Note for C4 wardens: Anything included in this `Automated Findings / Publicly Known Issues` section is considered a publicly known issue and is ineligible for awards._

Any issues that have already been uncovered here at the start of the contest are considered out-of-scope: https://github.com/blend-capital/blend-contracts-v2/issues

The following issues have been uncovered by the Blend team via dedicated issues in their [GitHub page](https://github.com/blend-capital/blend-contracts-v2/issues) and should thus be considered out-of-scope:

- [#18](https://github.com/blend-capital/blend-contracts-v2/issues/18) u64 Optimization
  - The Blend team did not notice any optimizations arising from the type adjustments
- [#11](https://github.com/blend-capital/blend-contracts-v2/issues/11) Remove "spender" and "to" from "submit"
  - The Blend team decided to not implement the relevant `interface` changes as they believe the current approach is more readable and the flash-loan implementation that relied on this change was implemented in a different way
- [#4](https://github.com/blend-capital/blend-contracts-v2/issues/4) Simplify redundent token transfers
  - The issue of redundant token transfers is known and its implementation was considered too complex to implement at this stage

Additionally, the issue outlined below contains a lot of interesting technical information around flash-loans as well as possible known risks considered:

- [#7](https://github.com/blend-capital/blend-contracts-v2/issues/7) Add flash loans 

# Overview

The `blend-contracts-v2` subfolder contains the smart contacts for an implementation of the Blend Protocol. Blend is a universal liquidity protocol primitive that enables the permissionless creation of lending pools.

The `fee-vault` subfolder represents the fee vault for Blend pools. It is used to allow an admin to collect a portion of the interest earned from blend pools by the vault depositors along with all emissions accrued by vault depositors. Wallets and integrating protocols are the entities typically interested in this functionality.

- See the [Formal Verification repo `README`](https://github.com/code-423n4/2025-02-blend-fv) for details about the Formal Verification portion of the competition.

## Links

- **Previous audits:**  https://github.com/blend-capital/blend-contracts/tree/main/audits (V1 Audits)
- **Documentation:** https://docs.blend.capital/
- **Website:** https://www.blend.capital/
- **X/Twitter:** https://x.com/blend_capital
- **Discord:** https://discord.com/invite/a6CDBQQcjW

---

# Scope

The implementations in-scope of the contest may contain unit tests defined within the code of the implementation itself. Those unit tests are clearly annotated via `#[cfg(test)]`, `#[test]`, or any other similar language-supported syntax and are considered out-of-scope for the purposes of the contest.

### Files in scope

| Files | Interfaces | nSLOC |  Libraries used |
| -------- | -------- | -------- |   -------- |
|fee-vault/src/constants.rs | **** | 3 |N/A| 
|fee-vault/src/contract.rs | **** | 147 | N/A | 
|fee-vault/src/errors.rs | **** | 15 | N/A | 
|fee-vault/src/events.rs | **** | 65 | N/A | 
|fee-vault/src/lib.rs | **** | 16 | N/A | 
|fee-vault/src/pool.rs | **** | 42 | N/A | 
|fee-vault/src/reserve_vault.rs | **** | 1178 | N/A | 
|fee-vault/src/storage.rs | **** | 150 | N/A | 
|fee-vault/src/validator.rs | **** | 12 | | N/A
|blend-contracts-v2/backstop/src/backstop/deposit.rs | **** | 203 | N/A | 
|blend-contracts-v2/backstop/src/backstop/fund_management.rs | **** | 225 | N/A | 
|blend-contracts-v2/backstop/src/backstop/mod.rs | **** | 13 | N/A | 
|blend-contracts-v2/backstop/src/backstop/pool.rs | **** | 450 | N/A | 
|blend-contracts-v2/backstop/src/backstop/user.rs | **** | 636 | N/A | 
|blend-contracts-v2/backstop/src/backstop/withdrawal.rs | **** | 403 | N/A | 
|blend-contracts-v2/backstop/src/constants.rs | **** | 6 | N/A | 
|blend-contracts-v2/backstop/src/contract.rs | **** | 150 | N/A | 
|blend-contracts-v2/backstop/src/dependencies/comet.rs | **** | 2 | N/A | 
|blend-contracts-v2/backstop/src/dependencies/mod.rs | **** | 7 | N/A | 
|blend-contracts-v2/backstop/src/dependencies/pool_factory.rs | **** | 2 | N/A | 
|blend-contracts-v2/backstop/src/emissions/claim.rs |  **** | 539 | N/A | 
|blend-contracts-v2/backstop/src/emissions/distributor.rs | **** | 608 | N/A | 
|blend-contracts-v2/backstop/src/emissions/manager.rs | **** | 2137 | N/A | 
|blend-contracts-v2/backstop/src/emissions/mod.rs | **** | 8 | N/A | 
|blend-contracts-v2/backstop/src/errors.rs | **** | 23 | N/A | 
|blend-contracts-v2/backstop/src/events.rs | **** | 67 | N/A | 
|blend-contracts-v2/backstop/src/lib.rs | **** | 16 | N/A | 
|blend-contracts-v2/backstop/src/storage.rs | **** | 349 | N/A | 
|blend-contracts-v2/pool-factory/src/errors.rs | **** | 9 | N/A | 
|blend-contracts-v2/pool-factory/src/events.rs | **** | 8 | N/A | 
|blend-contracts-v2/pool-factory/src/lib.rs | **** | 11 | N/A | 
|blend-contracts-v2/pool-factory/src/pool_factory.rs | **** | 83 | N/A | 
|blend-contracts-v2/pool-factory/src/storage.rs | **** | 58 | N/A | 
|blend-contracts-v2/pool/src/auctions/auction.rs | **** | 1771 | N/A | 
|blend-contracts-v2/pool/src/auctions/backstop_interest_auction.rs | **** | 1296 | N/A | 
|blend-contracts-v2/pool/src/auctions/bad_debt_auction.rs | **** | 2018 | N/A | 
|blend-contracts-v2/pool/src/auctions/mod.rs | **** | 5 | N/A | 
|blend-contracts-v2/pool/src/auctions/user_liquidation_auction.rs | **** | 2587 | N/A | 
|blend-contracts-v2/pool/src/constants.rs | **** | 5 | N/A |  
|blend-contracts-v2/pool/src/contract.rs | **** | 254 | N/A | 
|blend-contracts-v2/pool/src/dependencies/backstop.rs | **** | 2 | N/A | 
|blend-contracts-v2/pool/src/dependencies/mod.rs | **** | 2 | N/A | 
|blend-contracts-v2/pool/src/emissions/distributor.rs | **** | 1404 | N/A | 
|blend-contracts-v2/pool/src/emissions/manager.rs | **** | 530 | N/A | 
|blend-contracts-v2/pool/src/emissions/mod.rs | **** | 4 | N/A |  
|blend-contracts-v2/pool/src/errors.rs | **** | 37 | N/A | 
|blend-contracts-v2/pool/src/events.rs | **** | 144 | N/A | 
|blend-contracts-v2/pool/src/lib.rs | **** | 25 | N/A | 
|blend-contracts-v2/pool/src/pool/actions.rs | **** | 1718 | N/A |  
|blend-contracts-v2/pool/src/pool/bad_debt.rs | **** | 234 | N/A | 
|blend-contracts-v2/pool/src/pool/config.rs | **** | 1066 | N/A |  
|blend-contracts-v2/pool/src/pool/gulp.rs | **** | 213 |N/A |
|blend-contracts-v2/pool/src/pool/health_factor.rs | **** | 287 | N/A | 
|blend-contracts-v2/pool/src/pool/interest.rs | **** | 350 | N/A | 
|blend-contracts-v2/pool/src/pool/mod.rs | **** | 27 | N/A | 
|blend-contracts-v2/pool/src/pool/pool.rs | **** | 680 | N/A | 
|blend-contracts-v2/pool/src/pool/reserve.rs | **** | 589 | N/A | 
|blend-contracts-v2/pool/src/pool/status.rs | **** | 956 | N/A | 
|blend-contracts-v2/pool/src/pool/submit.rs | **** | 1863 | N/A | 
|blend-contracts-v2/pool/src/pool/user.rs | **** | 1004 | N/A | 
|blend-contracts-v2/pool/src/storage.rs | **** | 380 | N/A | 
|blend-contracts-v2/pool/src/validator.rs | **** | 7 | N/A | 
|Totals|  | 27099 |  | 

### Files out of scope

Any file that is not explicitly included in the aforementioned list is to be considered out-of-scope.

## Scoping Q &amp; A

| Question                                | Answer                       |
| --------------------------------------- | ---------------------------- |
| ERC20 used by the protocol              |       [Stellar Asset Contracts (SACs)](https://developers.stellar.org/docs/tokens/token-interface) & Standard [SEP-41](https://github.com/stellar/stellar-protocol/blob/master/ecosystem/sep-0041.md) Soroban Tokens             |
| Test coverage                           | N/A                          |
| ERC721 used  by the protocol            |            N/A              |
| ERC777 used by the protocol             |           N/A                |
| ERC1155 used by the protocol            |              N/A           |
| Chains the protocol will be deployed on | Stellar Network  |

### ERC20 token behaviors in scope

| Question                                                                                                                                                   | Answer |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ |
| [Missing return values](https://github.com/d-xo/weird-erc20?tab=readme-ov-file#missing-return-values)                                                      |   Out of scope  |
| [Fee on transfer](https://github.com/d-xo/weird-erc20?tab=readme-ov-file#fee-on-transfer)                                                                  |  Out of scope  |
| [Balance changes outside of transfers](https://github.com/d-xo/weird-erc20?tab=readme-ov-file#balance-modifications-outside-of-transfers-rebasingairdrops) | Out of scope    |
| [Upgradeability](https://github.com/d-xo/weird-erc20?tab=readme-ov-file#upgradable-tokens)                                                                 |   Out of scope  |
| [Flash minting](https://github.com/d-xo/weird-erc20?tab=readme-ov-file#flash-mintable-tokens)                                                              | Out of scope    |
| [Pausability](https://github.com/d-xo/weird-erc20?tab=readme-ov-file#pausable-tokens)                                                                      | Out of scope    |
| [Approval race protections](https://github.com/d-xo/weird-erc20?tab=readme-ov-file#approval-race-protections)                                              | Out of scope    |
| [Revert on approval to zero address](https://github.com/d-xo/weird-erc20?tab=readme-ov-file#revert-on-approval-to-zero-address)                            | Out of scope    |
| [Revert on zero value approvals](https://github.com/d-xo/weird-erc20?tab=readme-ov-file#revert-on-zero-value-approvals)                                    | Out of scope    |
| [Revert on zero value transfers](https://github.com/d-xo/weird-erc20?tab=readme-ov-file#revert-on-zero-value-transfers)                                    | Out of scope    |
| [Revert on transfer to the zero address](https://github.com/d-xo/weird-erc20?tab=readme-ov-file#revert-on-transfer-to-the-zero-address)                    | Out of scope    |
| [Revert on large approvals and/or transfers](https://github.com/d-xo/weird-erc20?tab=readme-ov-file#revert-on-large-approvals--transfers)                  | Out of scope    |
| [Doesn't revert on failure](https://github.com/d-xo/weird-erc20?tab=readme-ov-file#no-revert-on-failure)                                                   |  Out of scope   |
| [Multiple token addresses](https://github.com/d-xo/weird-erc20?tab=readme-ov-file#revert-on-zero-value-transfers)                                          | Out of scope    |
| [Low decimals ( < 6)](https://github.com/d-xo/weird-erc20?tab=readme-ov-file#low-decimals)                                                                 |   Out of scope  |
| [High decimals ( > 18)](https://github.com/d-xo/weird-erc20?tab=readme-ov-file#high-decimals)                                                              | Out of scope    |
| [Blocklists](https://github.com/d-xo/weird-erc20?tab=readme-ov-file#tokens-with-blocklists)                                                                | Out of scope    |

### External integrations (e.g., Uniswap) behavior in scope:


| Question                                                  | Answer |
| --------------------------------------------------------- | ------ |
| Enabling/disabling fees (e.g. Blur disables/enables fees) | No   |
| Pausability (e.g. Uniswap pool gets paused)               |  Yes   |
| Upgradeability (e.g. Uniswap gets upgraded)               |   No  |


### Walkthrough video of the codebase in transcript

hello everyone and welcome to this week's uh Stella developer meeting today um we have the team from blend joining us uh for a code walkr in support of their exciting news security Initiative for the Stell ecosystem I'm Carson as usual from the SDF Dev team and um and Alex will join us from script 3 and amen from Satur uh to set the stage here uh blend is getting ready to launch their blend V2 and in preparation for that they're opening up that code and for groundbreaking $125,000 in usdc competition focused on securing lend V2 through both a competitive auditing and a formal

verification this is the first ever open competition competitive audit and formal uh verification competition within the Stella ecosystem so it's an amazing opportunity for Stella devs to try their hand on competing to find bugs and write formal verification rules I just get more familiar with blend in general so um I'll post a link to how to sign up for the competition the competition started this Monday so it is open uh but let me now introduce Alex hello thanks for having me welcome Alex um do you just let me know when I am ready to get running go ahead you are

all right perfect your screen all right thank you uh so yeah I am Alex you might see me online as mots2 and I'm the lead developer at script 3 and we developed uh blend which is a universal liquidity protocol primitive uh just a quick overview what we're going to run through we might go a wee bit fast because there's a lot of stuff to cover um but I'll give you guys a quick for those who aren't familiar uh just a quick breakdown of what blend is um how the actual contracts all work together um and then I'll run into the code and kind of the main thing I'll try and focus on uh for those uh doing the auto

competition is really going to be um how we test blend and specifically if there is some kind of bug or thing you found within blend V2 uh kind of some tips and tricks on how you it might be a bit easier to prove um that something is in fact wrong um so yeah blend is a universal liquidity protocol primitive and what does that mean uh basically blend is a tool that allows uh you know companies people who are crypto natives really any entity that wants a lending Market to actually go ahead and have one um so lending markets the crypto are just places where people can uh land in BIO assets from each other and one thing

that blend does is blend basically comes with an automatic back stop module which acts as uh Insurance bad debt protection and also scam protection and and these things these are funded by anyone uh and kind of the way this all works together is the pool will give some portion of the interest it generates out to the back stop module such that it can provide uh that that layer of insurance for the protocol um that's just a really brief intro as to what blend does um I want to touch on first uh actually how the contracts all work together since been looking at this from a security

perspective knowing how uh the main components of blend interact um is pretty vitol so kind of the really like Cornerstone part of blend is the emitter contract uh this doesn't have very many responsibilities it's core one is going to roughly Define the admin protocol token in this case is blend um secondly it's responsible for defining the back stop module now the back stop module is like I said earlier the contract that basically holds all of the insurance funds for the blend pools uh insurance in this case are going to be um blend usdc LP tokens so there is a common amm it's for those familiar with evm it's

basically balancer um but it's just an LP token for blend usdc um its main responsibility is it actually controls the state of the pool so if you have a lending market and there's a back stop module the back stop module actually has the ability to turn the pool on and off so for example if something happens to a pool or it gets exploited some Oracle goes wrong um the back stop module actually has the ability to disable borrowing for the pool um secondly it's also the first less capital in the event of any bad debt and uh those that might not know bad debt is basically the case where um

a user has liabilities and they have no collateral to cover it so the protocol has to take a loss on that debt um secondly it also manages the blend emissions so the protocol basically starting from the emitter blend tokens will get sent to the back stop module and it's the back stop module's responsibility to send it to all of the pools within the blend ecosystem um within the backstop module uh it also defines a pool Factory uh this thing drops pretty simple it's a contract that contains a pool wasum and for any pool that's created uh this is the thing that validates that this is in

fact a blend pool and it is the exact contract that we expect to be deployed um and then the meat and potatoes of the protocol is going to be the actual pool uh this is kind of the sort of a part of the part of the whole protocol um it is the place where people can go and lend and borrow reserves um so there's tons of different ways you can set things up uh but this is kind of the place where um all the lending and borrowing occurs and kind of where most user interaction will end up taking place um so I know that was really fast but hopefully is this is being recorded right

Caren I think it is I'll take that as a yes um y it's recorded perfect so yeah we can go we can go probably go back and watch that over if anything was missed and I'm also available on Discord if uh you want to ask further questions um but we will jump to the actual codes since that's probably what a lot of you all are interested in um so I'll give a quick breakdown of how contracts actually um exist in soron and then we can start trying to dig through some of how this how our codes actually tested um so for those that aren't familiar um The Way We have set up our soron repository is you'll notice that

all of the core contracts that I talked about earlier are located within their own folder so for example all the code for the back stops within the back stop folder pool within the pool pool Factory Etc um each contract has a contract. RS file this is really the entry point and interaction point for the contract so um you'll you you'll notice that in soran there are these macros contract contract client these are really the things that defined how users actually can call into the contract so anything that's public facing um is part of this part of this trait and will be implemented for the

back stop contract stru um this is also the location where where we probably have all of the most user-facing documentation for each of the functions so if you're ever curious about uh what's available on a contract what the arguments mean um this file will be the place where they're documented um so yeah and there's also a contract implementation macro so this will be the place where a a Constructor is defined um so this is basically called when the contract's first deployed and can never be invoked again and there's also the back stop trait implementation for the contract and this is where all of our

code is basically getting defined so everything in here is um exposed for anyone on the blockchain to interact with uh the way we structured things is we generally do all of the authentication that's required to um use the use the contract here and then we actually perform all of the logic in a second helper function so that we can better unit test the code as a whole um so you'll notice if you're ever looking for authentication things um you you'll notice that all of the O actually takes place here um if you are from the evm world o how sorbon does o is probably one of the largest differences um

between the two blockchains um so it is worth looking into it's it's incredibly well documented on sorond uh Sor bonds documentation so I would highly recommend uh reading through how that works um so you and then you'll also notice that for example if I go to where we actually Define the logic um this is pretty common throughout all of our contracts so we we we'll basically try and wrap all all of the logic that's external to authentication and stuff within a function and we actually go through in write unit tests specifically for those functions um so this is a pretty good

place to look if you think something uh might be incorrect or wrong or a bug exists somewhere um this is probably one of the easiest places to start testing that and attempting to find um whether or not something's wrong and you you'll often find that this is like kind of where most of our unit tests actually occur um secondly one thing that we do include within this blend contracts repository is there's mock contracts and there's also a test Suites folder um so one thing that's really nice about interacting with soron is as I'm using tests you'll notice I have rust analyzer installed on

my fsco but you you you have the ability to step through debug so if you're ever curious about um what actual values are within a function you're you can use all the rust internal tools to step through and actually debug it um if you're like most developers in the world you're just going to add a whole bunch of print lines and then run the test that also works fantastic too um but it's it's really nice for example if you do think something's wrong make sure to use the rust tools and use use all the debugging tools to your advantage we've been able to find a lot of things internally um using those those strategies uh but one

really important thing I wanted to touch on especially for L contracts is we have this giant test Suites folder um we use a lot of this for all of the integration testing so for example there is a test fixture um this basically just contains a whole it's it's basically going to deploy from a fresh environment a whole bunch of contracts and things that exist to basically support a pretty standard blend pool um so you'll notice it's going to make tokens uh it adds a whole bunch of users uh it deploys all the contracts out for you and you can basically then start from a really good starting point to actually write an

integration level test um one quick thing to note here is that if you ever see an our test uh the user Bombadil um I'm a bit of a Lord of the Rings nerd so he is the admin and ruler of everything so he has the power to uh basically mint tokens at will he's kind of the admin the super key for roughly all of our tests as well um but how this is actually implemented you'll actually notice if you look back at some of our older audits um we've written integration tests after after basically fixing issues that have been found um one of these was an uh inflation attack that I believe uh C Tor found in the

first audit um but for example this kind of walks you through a really good way if you think something does exist that might have an issue um writing one of these level tests is a really really good way to actually prove whether or not it exists uh since this kind of is what at at this level of test this really is the place where you're going to have the same level of interaction um that someone using the blockchain would um then yeah maybe the last thing to note before I switch over to the fev VA here is you'll notice on the test test fixture when you cre the test picture there's a true false um just so

it's clear uh you have the ability when running rust integration tests to actually deploy the contracts and use WMS um so if you want to use the actual wasm files that are being deployed um that's great we do that in plenty of tests but uh if you do that um rust itself won't actually be able to debug the code within the wasin packages so if you're expecting some of the prit lines or um uh line by line de debugging to work you will need to deploy all of the contracts as rust crates uh that way you can use all the unit testing tools um so yeah that's probably all I'm going to touch on here uh again within

test Suites and test uh this is tons of really good examples on setting up all different kinds of environments um if you want to go through and attempt to prove uh that something is incorrect um lastly I'm going to also run through the Fe Vault contract um this is basically a uh add-on contract that's aimed at wallets uh that will allow users to specify either a fixed rate of return or um excuse me a cap rate of return so for example if a wallet wanted to offer um say 10% on usdc deposits using blend they can deploy one of these Fe volts uh if the blend pools returning

more than 10% they would keep that extra say it's returning 15% they would keep 5% 10% would go to the users um or they can just take a fixed interest take off of all of the interest generated for deposits through this Fe volt um so it it works pretty similar similarly to any uh er uh ERC 4626 function or 4626 Vault token um so those that are familiar or I've looked at those those kinds of protocols in the past um this should feel somewhat familiar to you um I did want to call out one thing you'll also notice some of the implementation patterns we use in blend also come over

here um so the only thing that's maybe a bit different is this contracts a bit simpler so you you'll notice we've kind of there's probably one less layer of abstraction there um for you to have to deal with um most things are documented pretty well in code but if you find anything please please feel free to call it out uh you'll notice that in the test here it's set up a bit differently so for example um this is a very long test but we we we mainly are testing the fee VA through integration testing uh since the contct is a bit similar simpler and it relies heavily on the blend the blend contracts themselves so you'll notice

that we uh we support a blend rust crate um that includes all of the blend contracts themselves uh this has been updated for the exact hash that was pushed for the uh Auto competition um so you'll notice that I believe yeah the version is here um but uh this comes with a very similar deployment script as the one we use within the blend contracts repository for their integration test so um let's see if yeah there's a blend flixer uh uh deploy function that will actually go ahead and create all of the blend contracts needed to interact with um a very similar setup as to what blend

view1 main it is um so if you do run into anything with the F VA um this is kind of a great place to look to go ahead and try and prove that something INF fact is missing or has a bug um so yeah that's probably all I wanted to touch on I wanted to make sure I left a little bit of time for Sor to go through the formal verification portion of the auto competition um but I'll probably leave it there unless there's anything else you want me to touch on Carson great uh let's uh let's wait and see if there's any questions uh at the end but uh thank you for the presentation I'm going to invite

Shandon Armen on the stage welcome both of you hi um Armen are you there okay yep hello uh you have my screen so this is the contest repo um so trra you can let me know yeah we should walk over sure uh yeah you can share and I'll I'll just go over it so um as Alex mentioned in his uh presentation before you know we are doing this audit and formal verification contest for blend and uh while the audit itself you can you know all all of the prog the code bases in scope uh for the verification part we have a smaller

scope because um the the protocol is there's a lot of code and so we decided that it would be more tractable and manageable if we tried to focus on one particular part and in particular we are looking at the back stop crate so if you uh go up a little bit in this uh repository so for what it's worth this is the repository where all the code is so you can uh clone this repository and then you can um check out all the different crates and in particular the one that we are talking about is the back stop as you can see Armen has it here um and I want to show the Sora specific stuff so first

of all uh the the the properties that you're going to be writing are going to be in the seras specs directory where Armen is right now uh I think I have a couple of little uh so well now can you go maybe look at some of the other files there's a few that I provided um just for an example yeah so here's a few examples of things that you um just to give you an idea for what these uh look like um and uh so you can notice here that uh there is this thing called cvlr uncore assert uh in all the rules and so the things that are so that's one uh thing I want to talk about a little bit so if you look at line number five this

is the uh we we call it Cavalier so cavaliere is the specification language that we've built um it's just a rust Library so you can import the library and then you can use the various assertions and there which are just macros uh that we've defined um so assume assert and satisfy I think are probably the most common ones uh and the ones that are I think we recommend using uh the most if you need something more specific then you can always uh reach out and uh we can help you figure out how to how to do that um the other thing uh worth noting here is um can you uh can Arman can you

go down to the the cargo Tomo file at the bottom uh uh yes so uh we are also relying on uh rust features so for example here you can see on line 17 there's this feature called Cur and uh the nice thing about this uh this mechanism is it actually lets you use this feature to selectively uh compile uh the code so for example um you can if you go back Armen to uh let's see um let's go in the back stop yeah and maybe in the withdrawal uh maybe go to deposit actually okay perfect so if you look at the top of this file you'll see that uh

we are using this feature called sora and essentially what this is saying is that when the feature is enabled and I just showed you before that in the cargo TL it is enabled uh then use this mock implementation of the token client and otherwise you can use the whatever default one that blend was using and this is just for verification only right so when you're compiling your code for uh other purposes then you shouldn't be using this uh but when you're doing verification this is helpful because a lot of the times we want to modularize things and so you may not need to include all the code for the token when

you're really just verifying the code uh for the back stop right so that's an interesting feature that I think you'll probably use uh quite a bit and you know always feel free to reach out uh on Discord if you have any questions um the other thing I also want to highlight is uh the con files so on the left you will see that there is this directory called conss and here we have provided some setup and some skeleton for some basic conss so let's look at the one yeah the withdraw one is a good one so what's happening here is uh we have this uh file that has a a build script this is already provided you probably should not

have to modify this at all uh it's just a python script that uh does a bunch of stuff that is necessary for making sure that the reports look nice you know you have all the files uploaded there it calls the right uh build instruction in this case we're using this uh file called uh this build system called just um but other than you should not have to modify that more or less uh then there's a few verification specific things so for example there's this thing called we have this slide called uh optimistic Loop um uh we we don't need to worry about what that is I would leave that there uh there's also this precise

bitwise Ops uh flag which is set to True uh what this is saying is that when you're doing the verification use bit vectors uh you may or may not want it uh it's uh you can if you're facing uh like slow running times I recommend taking it out and seeing what happens and again if you run into any issues uh when you take it out you can reach out and we'll try to help you um and then really the main thing you will have to modify is this rules field so whatever rules you write uh you just have to add them to this file and then you just run this uh San with this configuration file um I one thing I

would recommend so it is very common for users to run the prover with many ruls and that is what you will do in the end but when you're debugging and when you're just you know trying to test things out it is often helpful to just run one rule at a time so you know which rule is problematic or you know which has a Vu problem or all kinds of stuff right so um definitely keep that in mind when you're um just getting started and you know writing these uh as as I can tell you there's a lot of uh excitement already on Discord lots of people have been asking lots of questions um really good questions so it's already really

nice to see the the engagement from the the community so that's that's really cool uh so I think uh let me just think what else I would like to show actually yes uh can you uh Armen if you click on the documentation page that you have open um so yeah here we have some documentation for using Sunbeam so there's the installation guide which I think you probably don't need to worry too much about if you if you if you have installed ctra CLI you should be you should be good to go so I don't think you need anything else so the user guide is the main uh thing you know uh we have some examples of you know what the

different components are so for example here um you know you see this like hash rule thing uh on top of these functions so really what's Happening Here is you're just writing rust functions right so uh Cura is like interpreting those functions separately especially for verification but from your point of view you're just writing rust functions with special macros and special annotation so um that's one of the annotations is this rule uh attribute um and uh I already mentioned the CVL assume assert macros from the Cavalier spec Library another thing that is very useful is uh this notion of

non-determinism so uh oftentimes what happens is when you're doing verification uh you might want to uh sort of summarize some piece of code because you know maybe that's not super relevant for the property you're verifying and all you care about is that that function returns some non-deterministic value right it could be a u64 it could be i1 128 whatever uh it could be a user defined type all kinds of Stu so this nonb gives you a mechanism to do that so Cavalier actually already implements a bunch of non-ets for uh various primitive types um blend has a lot of userdefined

structs right so for example there's the Q4 um Q4 withdrawal uh struct uh you might want to implement that uh uh trade for this uh this truck right so you can do it this way so right like as there's an example here so essentially all you do is um you know you assign non- debt to all the fields of the struct and uh you're good to go so this is something that's really helpful uh for uh for verification uh we often have to do it and I'm imagining other people will have to do this as well we have some very basic examples in the tutorial so we have a Sunbeam tutorial over um over here

uh it gives an example of the token contract so if you've never done verification I think this is a good way to start you can just do the exercises here and uh you know just try to understand like what what's really happening uh when you run the tool and so on um and other than that uh if you go back uh I think I already explained the scripts the build script stuff if you scroll down a little bit more Armen uh yeah I think they these are already covered say so I think the main other thing I would recommend looking at is what

happens when you do run Sunbeam so as I mentioned before and it's actually also uh listed in the readme for the the repo all you do is you just run Cur San proofer and you pass this Con file and you uh you run it and all you get is a link to a run right and this link is going to look something like this right so here you can see um well so here there is no violation so you're fine but if there is a violation you can see a call Trace the call Trace is not super uh easy to read so if you are stuck with problems with the call Trace please post messages on Discord and we'll try to help you as much as possible uh you can

also see the code right so for example here on the left you have this files you can see all the files that you used to run verification all the properties that you ran all the code that you changed or properties you wrote everything is here uh so and I would always encourage you to if you are having any problems you can just send me a link to a run and then I can take a look at the run I can reproduce the Run locally and and help you debug your problems um uh other than that I'm not thinking what else would be useful um I think about that's that might be

all I have like uh oh actually I I would like to mention one other thing so uh we already saw uh the feature CRA feature of mechanism where you can selectively decide what functions to include when you're compiling we also saw the non-dead macro uh another thing that you may have to do is uh summarize various functions so this is something that you know for example here uh the way the best way to do this is the following right so uh in the C specs directory you there is a directory called summaries and in there you can uh so the mod is that's where you um just expose all the summaries that you have

written so here there's you know this file called emissions and in emissions it's possible that depending on the property you're proving you might have to summarize right so for example you can say that I don't really care what emissions does as long as it's returning a Nonet terministic value or you can that well it should be a nondeterministic value but maybe it should be in some range so this kind of stuff right like it really depends on your understanding of protocol and like what you think is necessary for um whoever is calling this function to know about this function Behavior right so

this is actually often very helpful so you can put all your summaries here and then wherever you're calling the function instead of calling the original function you just call this function and um it would be really good if you actually annotate it with this because then you know you're not really changing the semantics of the original program um great I think we need to wrap it up here but uh thank you so much for for this presentation uh I think this was uh very helpful for everyone who's going to participate in the in the competition to get to walk through both of the code and and and uh and the verification here so

thank you all for joining um I didn't see any questions in the chat but yeah feel free to reach out um also in Discord if there's anything I'll post the link again in Discord for the competition so good luck to everyone uh the competition is running until March 17th so still have plenty of time to to dig into it thank you everyone for joining thank you Shandra and Alex for for joining here us thank you everyone thanks everybody

### EIP compliance checklist

N/A

# Additional context

## Main invariants

* User's cannot extract funds (borrow, withdraw) from a pool if they do not meet or exceed the minimum health factor

## Attack ideas (where to focus for bugs)

### Auctions

The protocol conducts auctions to both process liquidations and pay out backstop interest. Anything that can disrupt / block / break the creation or filling of these auctions has potential to impact the health of a pool and/or it's backstop.

The auction creation system was modified in v2 to allow auction creators to specify the assets in the bid/lot. https://github.com/blend-capital/blend-contracts-v2/issues/3

### Flash Loans

Blend v2 introduces a flash loans endpoint. These are slightly different than EVM based flash loans, but still allow external contracts to be invoked. with borrowed funds, and repaid afterwards, or remain borrowed with the appropriate amount of collateral.

## All trusted roles in the protocol

| Role                                | Description                       |
| --------------------------------------- | ---------------------------- |
| Admin                          | Able to add reserves and edit reserve/pool configurations (excluding oracle) |

## Describe any novel or unique curve logic or mathematical models implemented in the contracts:

Interest uses a capped integral controller to adjust the interest rates to help utilization reach the target utilization rate: https://docs.blend.capital/blend-whitepaper#interest-rates

## Running tests

**Building**

[Soroban Setup](https://developers.stellar.org/docs/build/smart-contracts/getting-started/setup) Prerequisites

```bash 
# configure relevant rust target 
rustup target add wasm32-unknown-unknown

# install stellar cli
cargo install --locked stellar-cli@22.2.0 --features opt
```

To compile project (in either folder)

```bash 
make
```

To run tests (in either folder)

```bash 
make test
```

## Miscellaneous

Employees of Blend or Certora, and employees' family members, are ineligible to participate in this audit.

Code4rena's rules cannot be overridden by the contents of this README. In case of doubt, please check with C4 staff.
