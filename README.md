# Checks while Hacks
This repository contains my ultimate solidity attack vectors compilation. <br>
I will be compiling all solidity attack vectors that I come across with.<br><br>
thanks to `transmisions11/Solcurity` for a kickstart :)

## To-Do List
- [x] [`Solcurity`](https://github.com/transmissions11/solcurity)
- [x] [Solidity Attack Vectors `Quillhash`](https://github.com/Quillhash/Solidity-Attack-Vectors)
- [x] [Defi Attack Vectors `Quillhash`](https://github.com/Quillhash/DeFi-Attack-Vectors)
- [x] [NFT Attack Vectors `Quillhash`](https://github.com/Quillhash/NFT-Attack-Vectors)
- [x] [smart-contract-vulnerabilities by @0xKaden](https://github.com/kadenzipfel/smart-contract-vulnerabilities)

### Audit Reports : 
- [x] [@code4rena Caviar AMM December 2022](https://code4rena.com/reports/2022-12-caviar)
- [x] [@code4rena Caviar AMM April 2023](https://code4rena.com/reports/2023-04-caviar)
- [x] [@code4rena ENS November 2022](https://code4rena.com/reports/2022-11-ens)
- [x] [@pashovkrum Bloom Protocol Report May, 2023](https://github.com/pashov/audits/blob/master/solo/Bloom-security-review.md)
- [x] [@pashovkrum IPNFT - intellectual properties NFTs & fundraises](https://github.com/pashov/audits/blob/master/solo/IPNFT-security-review.md#l-03-usage-of-address-payables-send-method-is-discouraged)
- [x] [Trust Security AlphaFinanceLab/stella-arbitrum-private- contract](https://github.com/stellaxyz/audits/blob/main/reports/20230529_Trust_Security.pdf) 
- [x] [Olympus Protocol by @zachobront](https://github.com/zobront/audits/blob/main/reports/olympus-lending-amo.md)

# Sections 
1. [Approach](https://github.com/0xprinc/checks-while-hacks#approach) : Contains the general points during auditing.
2. [General Entity](https://github.com/0xprinc/checks-while-hacks#common-questions-to-ask-when-we-come-across-any-general-entity) : Common questions arise while observing specific term in the smart contract.
3. [Variables](https://github.com/0xprinc/checks-while-hacks#variables) : Points related to state variables.
4. [Structs](https://github.com/0xprinc/checks-while-hacks#structs) : Points related to structs.
5. [Functions](https://github.com/0xprinc/checks-while-hacks#functions) : Points related to functions.
6. [Modifiers](https://github.com/0xprinc/checks-while-hacks#modifiers) : Points related to modifiers.
7. [Code](https://github.com/0xprinc/checks-while-hacks#code) : Some good practices to avoid any vulnerability.
8. [Unexpected outputs](https://github.com/0xprinc/checks-while-hacks#unexpected-implementations-and-outputs-from-already-deployed-contracts) : Some unexpected implementations and outputs related to token standards
9. [External Call](https://github.com/0xprinc/checks-while-hacks#external-calls) : Points related to External Call.
10. [Static Call](https://github.com/0xprinc/checks-while-hacks#static-calls) : Points related to Static Call.
11. [Events](https://github.com/0xprinc/checks-while-hacks#events) : Points related to Events.
12. [Contract](https://github.com/0xprinc/checks-while-hacks#contract) : Some points related to the whole contract
13. [Project](https://github.com/0xprinc/checks-while-hacks#project) : Best practices during building a project.
14. [Defi](https://github.com/0xprinc/checks-while-hacks#defi) : Contains some DeFi related vulnerabilities.
15. [After Transaction](https://github.com/0xprinc/checks-while-hacks#after-transaction) : Security issues that can arise after the transaction has been submitted to the mempool.
16. [NFT](https://github.com/0xprinc/checks-while-hacks#nft) : Issues specific to NFTs.

## Approach
- Read the project's docs, specs, and whitepaper to understand what the smart contracts are meant to do.
- Construct a mental model of what you expect the contracts to look like before checking out the code.
- Glance over the contracts to get a sense of the project's architecture.
- Compare the architecture to your mental model. Look into areas that are surprising.
- Identify relevant global and state variables, functions, equations that are involved in the contract.
- List all the invariants related to them and try to find a way to break them to get a loop hole in the implementation.
- Look at areas that interface with external contracts and ensure all assumptions about them are valid.
- Split the contract as the functions and variables interacting with the external contracts or not.
- Try to get what are the possibilities during different states of the contract
    + when it is freshly deployed,
    + when it has high amount of each token and every combination,
    + when it is has some bool value come to true which is changing the state of the contract,
    + try to switch between every if and else condition and also try in all ranges of the variables present
- Do a generic line-by-line review of the contracts.
- Do another review from the perspective of every actor in the threat model.
- Glance over the project's tests + code coverage and look deeper at areas lacking coverage.
- Run static analysers and review their output.
- Look at related projects and their audits to check for any similar issues or oversights.
- Try to figure out as many as expected invariants in the contract after getting its context.
- Try to avoid `transaction order dependence` in the code or find a way to deal with it.
- Try to anticipate what will occur when governance turns evil (this may be the case of the RUG PULL, EXIT SCAMS).
- Comment the "why" as much as possible. 
- Comment the "what" if using obscure syntax or writing unconventional code.
- Comment explanations + example inputs/outputs next to complex and fixed point math.
- Comment explanations wherever optimizations are done, along with an estimate of much gas they save.
- Comment explanations wherever certain optimizations are purposely avoided, along with an estimate of much gas they would/wouldn't save if implemented.
- We should always note all the privileges that are provided to any role and what actually the role can do, any difference in these two will be a vulnerability.
- Also any role should not have the ability to take away all the funds into the contract, or any role that make the protocol centralised.

## Common questions to ask when we come across any general entity
1. Will the contract run the same if this entity is removed?
2. Will this entity be replaced with some alternative code?
3. Will this entity be used by the admin to do some exploit(making the protocol apparently centralised)?
4. Is the entity opening a path for arbitrary interaction with the contract?

## Variables

1. Is the visibility set? Can it be more specific such as `external`, `internal`, `private`? 
2. Can it be `constant`, `immutable`?
3. Is the purpose of the variable and other important information documented using `natspec`?
4. Can it be packed with an adjacent storage variable?
5. Can it be packed in a struct with more than 1 other variable?
6. Use full 256 bit types unless packing with other variables.
7. If it's a public array, is a separate function provided to return the full array?
8. Check that the size of the array to be limited, otherwise it may lead to gas shortage to complete the transaction.
9. Only use `private` to intentionally prevent child contracts from accessing the variable, prefer `internal` for flexibility.
10. Uninitialized local storage variables(variables that take their value from a state variable) can point to unexpected storage locations in the contract, which can lead to intentional or unintentional vulnerabilities, so mark them as memory, calldata and storage as per the requirement.

## Structs

1. Is a struct necessary? Can the variable be packed raw in storage?
2. Are its fields packed together (if possible)?
3. Is the purpose of the struct and all fields documented using natspec?

## Functions

1. Should it be `external` or `internal`?
2. Should it be `payable`?
3. Can the function be front-runned?
4. Can it be combined with another similar function?
5. Validate all parameters are within safe bounds, even if the function can only be called by a trusted users.
6. Always make sure that the argument passed is a valid argument/ behaves as expected in its full range of taking values.
7. Are the multiple arrays taken have same length?
8. Is the `checks` before `effects` pattern followed? (SWC-107)
9. Is the `update` before `call` pattern followed? (Reentrancy) Sometimes even the modifier can not save from reentrancy.
10. Are the correct modifiers applied, such as `onlyOwner`/`requiresAuth`?
11. Are the `modifiers`(if more than one) written in function in correct order, because the change in order will change the code?
12. Write down and test invariants about state before a function can run correctly.
13. Write down and test invariants about the return or any changes to state after a function has run and try to include all edge cases as input.
14. Take care when naming functions, because people will assume behaviour based on the name.
15. If a function is intentionally unsafe (to save gas, etc), use an unwieldy name to draw attention to its risk.
16. Are all arguments, return values, side effects and other information documented using `natspec`?
17. Only use `private` to intentionally prevent child contracts from calling the function, prefer `internal` for flexibility.
18. Use `virtual` if there are legitimate (and safe) instances where a child contract may wish to override the function's behaviour.
19. Are return values always assigned?, sometimes not assigning values is better.
20. Try not to use `msg.value`, after its value has been used as this can cause the loss of funds of the contract. `msg.value` can be used in case of fees payment which is very small and protocol exclusive.
21. `block.timestamp` remains same during a single transaction even if any complex operation is done.
22. Its better to store the values of `state variables` in `local variables` when the state variables are called multiple times, as `MLOAD` is cheaper than `SLOAD`.
23. Try to provide the values of state variables as parameter to internal functions as this will minimize `SLOAD` which is expensive than `CALLDATACOPY`.

## Modifiers

1. Are no storage updates made (except in a reentrancy lock)?
2. Are `external calls` avoided?
3. Is the purpose of the modifier and other important information documented using `natspec`?
4. Always remember that `modifiers` increase the `Codesize` so use them wisely.


## Code

1. Using SafeMath or 0.8 checked math? (SWC-101)
2. Are any storage slots read multiple times?
3. Implementation should be consistent with the documentation, whats written in docs should be implemented in the contract.
4. Are any unbounded loops/arrays used that can cause DoS? (SWC-128)
5. Use `block.timestamp` only for long intervals. (SWC-116)
6. Don't use block.number for elapsed time. (SWC-116)
7. Do not update the length of an array while iterating over it.
8. Don't use `blockhash()`, etc for randomness. (SWC-120)
9. Are signatures protected against replay with a nonce and `block.chainid`? (SWC-121)
10. Ensure all signatures use EIP-712. (SWC-117 SWC-122)
11. Output of `abi.encodePacked()` shouldn't be hashed if using >2 dynamic types. Prefer using `abi.encode()` in general. (SWC-133)
12. Don't use any arbitrary data while using the assembly. (SWC-127)
13. Don't assume a specific ETH balance. (SWC-132)
14. Private data isn't private, it can be accessed. (SWC-136)
15. Updating a struct/array in memory won't modify it in storage.
16. Never shadow state variables. (SWC-119)
17. Try not to mutate function parameters.
18. Is calculating a value on the fly cheaper than storing it?
19. Are all state variables read from the correct contract (master vs. clone)?
20. Are comparison operators used correctly (`>`, `<`, `>=`, `<=`), especially to prevent off-by-one errors?
21. Are logical operators used correctly (`==`, `!=`, `&&`, `||`, `!`), especially to prevent off-by-one errors?
22. Always multiply before dividing, unless the multiplication could overflow.
23. Are magic numbers replaced by a constant with an intuitive name?
24. If the recipient of ETH had a fallback function that reverted, could it cause DoS? (SWC-113)
25. Use SafeERC20 or check return values safely.
26. Don't use `msg.value` if recursive `Delegate Calls` are possible (like if the contract inherits `Multicall`/`Batchable`).
27. Don't assume `msg.sender` is always a relevant user.
28. Don't use `assert()` unless for fuzzing or formal verification. (SWC-110)
29. Don't use `tx.origin` for authorization. (SWC-115)
30. Don't use `address.transfer()` or `address.send()`. Use `.call.value(...)("")` instead. (SWC-134)
31. When using low-level calls, ensure the contract exists before calling.
32. When calling a function with many parameters, use the named argument syntax.
33. Do not use assembly for create2. Prefer the modern salted contract creation syntax.
34. Do not use assembly to access chainId or contract code/size/hash. Prefer the modern Solidity syntax.
35. Use the `delete` keyword when setting a variable to a zero value (`0`, `false`, `""`, etc).
36. Use `unchecked` blocks where overflow/underflow is impossible, or where an overflow/underflow is unrealistic on human timescales (counters, etc). Comment explanations wherever `unchecked` is used, along with an estimate of how much gas it saves (if relevant).
37. Do not depend on Solidity's arithmetic operator precedence rules. In addition to the use of parentheses to override default operator precedence, parentheses should also be used to emphasise it.
38. Expressions passed to logical/comparison operators (`&&`/`||`/`>=`/`==`/etc) should not have side-effects.
39. Wherever arithmetic operations are performed that could result in precision loss, ensure it benefits the right actors in the system, and document it with comments. 
40. Document the reason why a reentrancy lock is necessary whenever it's used with an inline or `@dev` natspec comment.
41. When fuzzing functions that only operate on specific numerical ranges use modulo to tighten the fuzzer's inputs (such as `x = x % 10000 + 1` to restrict from 1 to 10,000).
42. Use ternary expressions to simplify branching logic wherever possible.
43. When operating on more than one address, ask yourself what happens if they're the same.
44. Can someone without spending other then gas fees change the state of the contract.
45. Always check the number of loop iterations should be bounded by a small finite number other wise the transaction will run out of gas.
46. Always check for the return datatype of the called contract function. Example: in ERC20 implementations, the transfer functions are not consistent with             the value they return(some return the bool while others revert which can cause problems)
47. You can always convert `bool` to `revert` by using `require`.
48. Similar to the above, global `transfer` method reverts while the `send` gives the bool value which sometimes causes problems
49. Don't use `extcodesize` to gain the knowledge of whether the `msg.sender` is EOA as any contract calling the function while staying in the constructor can easily act as an EOA.
50. Try to monitor the expected and actual length of the array.
51. Always try to be consistent with the interface contract otherwise the call will lead to the fallback.
52. Making a new owner is a crucial thing, so a new function to accept the ownership should be made so that the ownership don't go in the hands of some wrong person or a smart contract which can not do anything.
53. In Solidity any address can be casted into specific contract, even if the contract at the address is not the one being casted. This can be exploited to hide malicious code.
54. don't use `erecover` and `signature` to verify the user as these cause signature malleability.
55. delete every entry of the mapping before deleting the mapping itself, otherwise the getter function will still work by giving all the mapping values
56. Look out for signature replay attacks.
57. Use underscores or constants for number literals for better readability and also for unexpected human error.
58. Use bytes.concat() instead of abi.encodePacked(), since this is preferred since 0.8.4
59. Any inconsistency in formula for calculation may cause the loss of the funds and also minting additional funds,<br> 
          example can be use of Math.min(a, b) which change suddenly when the condition changes.
60. Don't assume the implementations of ERC20, ERC721 tokens in their contracts, such as decimals, approve functions etc., coding using this assumption will lead to the casting errors
61. Look for the statements that can be skipped and still takes to the same blockchain state, for example some external call without any return values, some non-relevant require statements.
62. Try to read all the ERC20 Implementations in scope as their definitions can be different from what is expected.
63. `Round Up` should be done while taking the tokens in so that no one can be privileged while depositing a lower amount.
64. `Round down` should be done while transferinng tokens from protocol to user so that no user can get the same value while having lower deposit.
65. Use `PULL` over `PUSH` while updating the state variables to mitigate the inclusion of blacklisted entities to become active. This also uses gas only whenever necessary
66. Try not to use the `percentage`, because it introduces the division and then rounding occurs. Also include a 100% cap while including a percentage.
67. It is necessary to make the lines in constructor in proper order, this really affect the initial state of the protocol. Example. a function called inside the constructor takes value of an uninitialized variable, hence will fail to give correct output.
68. A goos practice while dealing with nonReentrant modifier. Try not to make the state variable public, instead make a public getter by yourself with a nonReentrant modifier.
 

## Unexpected implementations and Outputs from already deployed contracts
1. Most price feeds use `Chainlink` as their price feed which sometimes return the values at `8 decimal` numbers, so while scaling the output with a general formula using 1e12 or 1e18 will not be applicable.
2. Some tokens like `PAXG`, `USDT` have fee-on-transfer in-built which makes them transfer less tokens than the argument passed. So to get the exact value of transfer tokens we have to fetch the balance of the receiving contract twice(one before transfer and one after) and also a non-reentrant to protect against ERC-777 tokens
3. Tokens like `USDT`, `KNC` have a approval-race-protection mechanism which uses `allowance` which is either set to `0` or `type(uint256).max`, at any other value, the safe-approval will `revert` instead of giving a `bool`. So we have to use `forceApproval Allowance` to mitigate this problem and to generalize any token approval in our protocol. `USDT` also don't have an `increaseAllowance()` function.
5. Decimals are not fixed to 18 for all ERC20 implementations, such as `GUSD-Gemini Dollar` has only 2 decimals.
6. There are implementations of ERC721 that revert when calling the `setApprovalForAll` function more than one times, this is because the function has a check 
          `require(_tokenOperator[msg.sender][_operator] != _approved)`. Example is `Axie` ERC721 Token.
7. Chainlink's `latestRoundData()` is used, then there should be a check if the return value indicates old data. Otherwise this could lead to old prices according to the [Chainlink documentation](https://docs.chain.link/docs/historical-price-data/#historical-rounds). Also if any variable is used to make sure that the data is not outdated, then while using the two different price feeds, we have to make sure that these two price feeds are updated at comparable amounts of time other wise the difference between their update time will lead to unexpected changes.
8. Different chains have different block mining time which poses a vulnerability when writing the same code for all the chains while relating the number of blocks and the timestamp.
9. Using `solmate safeTransferLib`, one should also make a function to check whether the token contract exist or not, because this is not included in that library
10. A problem with using only `approve` function but not the `increaseAllowance` is that, If A approves B 5 tokens and B don't use them, Now, If A approves B 10 tokens to increase the approve value from 5 to 10 tokens, so that B can spend 10 tokens, now B can front run that 10 token transaction to spend both 5 and 10 tokens.
   

## External Calls

1. Is an external contract call actually needed?
2. Avoid `Delegatecall` wherever possible, especially to external (even if trusted) contracts. (SWC-112)
3. If there is an error, could it cause DoS? Like `balanceOf()` reverting. (SWC-113)
4. Would it be harmful if the call reentered into the current function?
5. Would it be harmful if the call reentered into another function?
6. Is the result checked and errors dealt with? (SWC-104)
7. What if it uses all the gas provided?
8. Could it cause an out-of-gas in the calling contract if it returns a massive amount of data?
9. If you are calling a particular function, do not assume that `success` implies that the function exists (phantom functions).
10. Its best to be stateless while doing an external delegate call.
11. Always assume that the external call will fail, now code accordingly.
12. Try avoiding taking arbitrary input or calldata input for a function that does external call which can make the EOA make the calls in the behalf of the contract.
13. The external calls from a contract can be made to be failed and still be made the function continue if the external call returns a bool, the attacker can just give very enough gas to make the sub-call(call from a contract function to another contract) fail.(Insufficient Gas Greifing)


## Static Calls

1. Is an external contract call actually needed?
2. Is it actually marked as view in the interface?
3. If there is an error, could it cause DoS? Like `balanceOf()` reverting. (SWC-113)
4. If the call entered an infinite loop, could it cause DoS?
5. Is this call supporting Reentrancy? Is this call reading the updated values OR outdated values?

## Events

1. Should any fields be indexed?
2. Is the creator of the relevant action included as an indexed field?
3. Do not index dynamic types like strings or bytes.
4. Is when the event emitted and all fields documented using natspec?
5. `E5` - Are all users/ids that are operated on in functions that emit the event stored as indexed fields?
6. Avoid function calls and evaluation of expressions within event arguments. Their order of evaluation is unpredictable.
7. Events should be made for every important change in state made through the contract, so they can be read off-chain.
8. Avoid event spamming where there are events emitted even when there is e.g. zero claim amount, zero token transfer, as this will affect off-chain event tracking.


## Contract

1. Use an SPDX license identifier.
2. Are events emitted for every storage mutating function?
3. Check for correct inheritance, keep it simple and linear. (SWC-125)
4. Use a `receive() external payable` function if the contract should accept transferred ETH.
5. Write down and test invariants about relationships between stored state.
6. Is the purpose of the contract and how it interacts with others documented using natspec?
7. The contract should be marked `abstract` if another contract must inherit it to unlock its full functionality.
8. Emit an appropriate event for any non-immutable variable set in the constructor that emits an event when mutated elsewhere.
9. Avoid over-inheritance as it masks complexity and encourages over-abstraction.
10. Always use the named import syntax to explicitly declare which contracts are being imported from another file.
11. Group imports by their folder/package. Separate groups with an empty line. Groups of external dependencies should come first, then mock/testing contracts (if relevant), and finally local imports.
12. Summarize the purpose and functionality of the contract with a `@notice` natspec comment. Document how the contract interacts with other contracts inside/outside the project in a `@dev` natspec comment.
13. Malicious actors can use the Right-To-Left-Override unicode character to force RTL text rendering and confuse users as to the real intent of a contract.
14. Try to take into account the c3 linearization when inheriting from two contracts that contain same function with different implementations
          (diamond problem)
15. The callable functions in a contract are not only the ones visible in the contract code but also the ones which are inherited but are not mentioned in the code itself.
16. Its a good practice to include the [headers](https://github.com/transmissions11/headers)
17. The functions should be grouped in the following order as given in the solidity style guide for the auditing process should be smooth <br>
          { constructor, receive function (if exists), fallback function (if exists), external, public, internal, private, view and pure functions last }
18. Always look for making an extra function(claim) if there is possibility of the funds to be stuck in the contract or the contract is having a receive or fallback function. This can be seen in the case of airdrops that are generally landed on the protocol contract and a claim function should be made to retrieve them.
19. In the beginning after deployment of the contract, the state variables are easy to manipulate(especially in defi) since there is not much of the funds locked in the contract, and hence not very much of the funds are required to manipulate the state of the contract, this can lead to the contract being more vulnerable in start
20. If the contract is an implementation of an another protocol, then to maintain the consistency, we should check all the formulas to be same in both. This can happen in the strategy protocols that makes strategy for another defi protocols but lacks giving the users same values or outputs.
21. While using the proxy, Initialize the contract in the same transaction as initialization needs a call to initialixe function.
22. Using same data feed of two related tokens is vulnerable, e.g. using datafeed for `USDC` for `DAI` will be vulnerable as if one depegs, then the other price will also be affected in the protocol.
23. Is the contract upgradeable?  If yes, then are there any storage slots reserved?

## Project

1. Use the right license (you must use GPL if you depend on GPL code, etc).
2. Unit test everything.
3. Fuzz test as much as possible.
4. Use symbolic execution where possible.
5. Run Slither/Solhint and review all findings.
6. The coverage for the tests should be 100%

## DeFi
__`defi has many vulnerabilities outside solidity, so familiarize yourself with the crypto space and its trends`
includes : structuring to avoid AML/CTF, token inflation, fake trends, smurfing, Interlocking Directorate__

1. Check your assumptions about what other contracts do and return.
2. Don't mix internal accounting with actual balances.
3. Don't use spot price from an AMM as an oracle.
4. Do not trade on AMMs without receiving a price target off-chain or via an oracle.
5. Use sanity checks to prevent oracle/price manipulation.
6. Watch out for rebasing tokens. If they are unsupported, ensure that property is documented.
7. Watch out for ERC-777 tokens. Even a token you trust could preform reentrancy if it's an ERC-777. ERC721 are also vulnerable.
8. Watch out for fee-on-transfer tokens. If they are unsupported, ensure that property is documented.
9. Watch out for tokens that use too many or too few decimals. Ensure the max and min supported values are documented.
10. Be careful of relying on the raw token balance of a contract to determine earnings. Contracts which provide a way to recover assets sent directly to them can mess up share price functions that rely on the raw Ether or token balances of an address.
11. If your contract is a target for token approvals, do not make arbitrary calls from user input.
12. Always set a minimum deposit balance to revoke the privilege given to people depositing zero amount
13. One of the best optimisations can be decreasing the impermanent loss(maybe divide the loss among more people since the overall loss can not be decreased as this will affect the price impact on the AMM)
14. Check out for whether governance given to an EOA has infinite minting or approval power(to avoid rug pull, exit scams, circulating price impact)
15. Look out for slippage tolerance in Defi Dex protocol, this saves from unexpected results and even protects from front running
16. There is slippage cap in the functions in AMMs but there should also be the deadline set as the slippage cap gives the person assets in a specified range but the real value of the asset can be changed with time, so even if getting the same amount of token, but not at proper time can lead to bad trade.
17. The main concern while swapping is getting the expected price, so during very high fluctuations, using slippage in form of percentage or deviation from the current price is not a good idea since during high fluctuations, even inside the deadline the price may be very unexpected, so the best way to use swaps is (deadline + expected price) you want rather slippage percentage or absolute difference from the current price.
18. Try not to approve the token contracts which have onlyOwner functions which have the power to move the funds.
19. Watch out what if someone with very much money can do(in cases of auction), in these cases a flashloan attack is likely to happen
20. Functions without any protection(like onlyOwner) are vulnerable to frontrunning so consider what will happen if they are frontrunned.
21. Fees is a part of many protocols, watch out for the `msg.sender`, `fee payer`, `funds` receiver as different users.
22. In general, `Treasury`, `admin`, `manager` are the different entities that can receive the incentives or fees collected, try to differentiate between them.
23. In case of protocols having subscriptions, `unregistered`, `de-registered`, `expired` entries are also different, these should be acting according to the documentation.
24. `Inflation attack` : It is the attack in which the pool is submitted the tokens externally and now the liquidity is very high and the total supply of mint tokens is very low and hence the formula will give the minimum amount to deposit to be very high and hence DOSing for people with low money.
25. `maxSlippage` value should not be fixed, because in case of emergency where the price is constantly dropping or increasing, the withdraw function or swap function will revert due to crossing of the `maxSlippage`. But, at that time the transaction should pass otherwise the funds will be stuck forever as the slippage will never come to low.
26. In a lending and borrowing protocol, this can be a valid finding if at some point of time, the borrower is freeze to borrow the funds or is limited to borrow comparably less funds but is able and have tokens to give collateral, as this will significantly decrease the yield of the lender.
27. Watch out for all entry points for a position in a protocol for example in case of a protocol build on `uniswap` will have two entry points for adding liquidity, one of them is the protocol and another is through the pool. Try to investigate all the entry points and how can an entry points be used for unintended behaviour.
28. Oracle saving `block.timestamp` of every transaction in the pool will be vulnerable since if a smart contract doing multiple operation in the pool in a simgle transaction will result in same timestamp for all of them.
29. FlashLoan protection is done by using the condition `lastTimestamp != block.timestamp`, this reduces multiple calls in a single transaction and even in a single block. But this also makes the protocol vulnerable to `DOS`, since if any valid transaction can be frontrunned, then that transaction can not be included in that block, and multiple attacks of this kind on consecutive blocks will cause `DOS`. So, an extra front-running protection should be there.

    
## After Transaction
1. The transaction data can be seen by anyone reading the mempool, so don't use things like password in the transactions.
2. While auditing measures related to `pre-exploit` and `post-exploit` should be taken since the codebase can not be claimed to be hack proof very easily and hence `post-exploit` measures should also be included inside the codebase, both should count as a valid finding. So, try to think, what will happen if a contract is exploited, how will it affect the whole `DeFi` space.


## NFT
1. Any smart contract using NFT contracts as input should also include a function to blacklist NFTs so that anyone can not use NFT contracts as inputs that are theft in the past
