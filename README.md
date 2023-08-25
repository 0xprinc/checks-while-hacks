# Checks while Hacks
This repository contains my ultimate solidity attack vectors compilation. <br>
I will be compiling all solidity attack vectors(the general approach) that I come across with.<br><br>
_inspired from `transmisions11/Solcurity`_

## To-Do List
- [x] [`Solcurity`](https://github.com/transmissions11/solcurity)
- [x] [Solidity Attack Vectors `Quillhash`](https://github.com/Quillhash/Solidity-Attack-Vectors)
- [x] [Defi Attack Vectors `Quillhash`](https://github.com/Quillhash/DeFi-Attack-Vectors)
- [x] [NFT Attack Vectors `Quillhash`](https://github.com/Quillhash/NFT-Attack-Vectors)
- [x] [smart-contract-vulnerabilities by @0xKaden](https://github.com/kadenzipfel/smart-contract-vulnerabilities)
- [ ] [Smart contract Security Artile by Jeffrey Scholz](https://www.rareskills.io/post/smart-contract-security)
- [x] [NFT Attacks by @volodya](https://0xvolodya.hashnode.dev/nft-attacks#heading-erc-777-tokens)
### Audit Reports : 
- [x] [@code4rena Caviar AMM December 2022](https://code4rena.com/reports/2022-12-caviar)
- [x] [@code4rena Caviar AMM April 2023](https://code4rena.com/reports/2023-04-caviar)
- [x] [@code4rena ENS November 2022](https://code4rena.com/reports/2022-11-ens)
- [x] [@pashovkrum Bloom Protocol Report May, 2023](https://github.com/pashov/audits/blob/master/solo/Bloom-security-review.md)
- [x] [@pashovkrum IPNFT - intellectual properties NFTs & fundraises](https://github.com/pashov/audits/blob/master/solo/IPNFT-security-review.md#l-03-usage-of-address-payables-send-method-is-discouraged)
- [x] [Trust Security AlphaFinanceLab/stella-arbitrum-private- contract](https://github.com/stellaxyz/audits/blob/main/reports/20230529_Trust_Security.pdf) 
- [x] [Olympus Protocol by @zachobront](https://github.com/zobront/audits/blob/main/reports/olympus-lending-amo.md)
- [x] [@pashovkrum NFT Loots - ERC721 lootboxes](https://github.com/pashov/audits/blob/master/solo/NFTLoots-security-review.md)
- [x] [@code4rena OpenLeverage](https://code4rena.com/reports/2022-01-openleverage)
- [x] [@code4rena Llama Governance](https://code4rena.com/reports/2023-06-llama)
- [x] [@code4rena Sturdy](https://code4rena.com/reports/2022-05-sturdy)
- [x] [@code4rena AbraNFT](https://code4rena.com/reports/2022-04-abranft)
- [x] [@code4rena Backed Protocol](https://code4rena.com/reports/2022-04-backed)
- [x] [@code4rena Paladin](https://code4rena.com/reports/2022-03-paladin)
- [x] [@code4rena timeswap March 2022](https://code4rena.com/reports/2022-03-timeswap)
- [x] [@code4rena Yield-Convex	](https://code4rena.com/reports/2022-01-yield/)
- [x] [@code4rena Timeswap January 2022](https://code4rena.com/reports/2022-01-timeswap/)
- [x] [@code4rena Swivel](https://code4rena.com/reports/2021-09-swivel)
- [x] [Solodit AMM High findings](https://solodit.xyz)
- [ ] [@code4rena Wild Credit](https://code4rena.com/reports/2021-09-wildcredit/)
- [ ] [@code4rena Yield micro contest #1](https://code4rena.com/reports/2021-08-yield)
- [ ] [@code4rena Wild Credit](https://code4rena.com/reports/2021-07-wildcredit)
- [ ] [@code4rena Yield](https://code4rena.com/reports/2021-05-yield)
- [ ] [@code4rena Yeti Finance](https://code4rena.com/reports/2021-12-yetifinance/)
- [ ] [@code4rena 88mph](https://code4rena.com/reports/2021-05-88mph/)
- [ ] [@code4rena Based Loans](https://code4rena.com/reports/2021-04-basedloans/)
- [ ] [@code4rena Maple Finance](https://code4rena.com/reports/2021-04-maple/)
- [x] [@code4rena Arbitrum Security Council Elections](https://code4rena.com/contests/2023-08-arbitrum-security-council-election-system/)
- [x] [@code4rena Stader Labs](https://code4rena.com/reports/2023-06-stader)
- [ ] [@code4rena JuiceBox Delegate](https://code4rena.com/reports/2023-05-juicebox) 

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
1. Read the project's docs, specs, and whitepaper to understand what the smart contracts are meant to do.
2. Construct a mental model of what you expect the contracts to look like before checking out the code.
3. Glance over the contracts to get a sense of the project's architecture.
4. Compare the architecture to your mental model. Look into areas that are surprising.
5. Identify relevant global and state variables, functions, equations that are involved in the contract.
6. List all the invariants related to them and try to find a way to break them to get a loop hole in the implementation.
7. Look at areas that interface with external contracts and ensure all assumptions about them are valid.
8. Split the contract as the functions and variables interacting with the external contracts or not.
9. Try to get what are the possibilities during different states of the contract
    + when it is freshly deployed,
    + when it has high amount of each token and every combination,
    + when it is has some bool value come to true which is changing the state of the contract,
    + try to switch between every if and else condition and also try in all ranges of the variables present
10. Do a generic line-by-line review of the contracts.
11. Do another review from the perspective of every actor in the threat model.
12. Glance over the project's tests + code coverage and look deeper at areas lacking coverage.
13. Run static analysers and review their output.
14. Look at related projects and their audits to check for any similar issues or oversights.
15. Try to figure out as many as expected invariants in the contract after getting its context.
16. Try to avoid `transaction order dependence` in the code or find a way to deal with it.
17. Try to anticipate what will occur when governance turns evil (this may be the case of the RUG PULL, EXIT SCAMS).
18. Comment the "why" as much as possible. 
19. Comment the "what" if using obscure syntax or writing unconventional code.
20. Comment explanations + example inputs/outputs next to complex and fixed point math.
21. Comment explanations wherever optimizations are done, along with an estimate of much gas they save.
22. Comment explanations wherever certain optimizations are purposely avoided, along with an estimate of much gas they would/wouldn't save if implemented.
23. We should always note all the privileges that are provided to any role and what actually the role can do, any difference in these two will be a vulnerability.
24. Its a centralisation attack when there is given power to the owner to control funds of users in any case.

## Common questions to ask when we come across any general entity
1. Will the contract run the same if this entity is removed?
2. Will this entity be replaced with some alternative code?
3. Will this entity be used by the admin to do some exploit(making the protocol apparently centralised)?
4. Is the entity opening a path for arbitrary interaction with the contract?

## Variables

1. When was the variable initialized and how?
2. Is the visibility set? Can it be more specific such as `external`, `internal`, `private`? 
3. Can it be `constant`, `immutable`?
4. Is the purpose of the variable and other important information documented using `natspec`?
5. Can it be packed with an adjacent storage variable? this is applicable to both local, state and calldata variables.
6. Can it be packed in a struct with more than 1 other variable?
7. Use full 256 bit types unless packing with other variables.
8. If it's a public array, is a separate function provided to return the full array?
9. Check that the size of the array to be limited, otherwise it may lead to gas shortage to complete the transaction.
10. Enums can be used instead of seperate and related constants.
11. Only use `private` to intentionally prevent child contracts from accessing the variable, prefer `internal` for flexibility.
12. Uninitialized local storage variables(variables that take their value from a state variable) can point to unexpected storage locations in the contract, which can lead to intentional or unintentional vulnerabilities, so mark them as memory, calldata and storage as per the requirement.
13. The variables that store value of the past should also have the functionality to have it removed as well otherwise the gas fee for the operations will be increasing as the variable storing values increase in cases of array as we have to traverse all the previous entries also.
14. Variables that need to be very precise(number of months/year elapsed) should not get the precision error(as 1.99 month should not be considered as 1 month although 1.99 day can be considered as 1 because of the time error).
15. Ethereum incentivize the efficient use of storage. When we delete a variable, there is a gas refund that appears in the transaction


## Structs

1. Is a struct necessary? Can the variable be packed raw in storage?
2. Are its fields packed together (if possible)?
3. Is the purpose of the struct and all fields documented using natspec?

## Functions

1. Should it be `external` or `internal`? For instance, the function not called by the same contract should be marked as external.
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
22. Its better to store the values of `state variables` in `local variables` when the state variables are called multiple times, as `MLOAD` is cheaper than `SLOAD`. This process is called `variable caching`.
23. Try to provide the values of state variables as parameter to internal functions as this will minimize `SLOAD` which is expensive than `CALLDATACOPY`.
24. `OnlyOwner` function should be marked as `payable`, this will lower cost for legitimate callers due to avoidance of CALLVALUE, DUP1, JUMPI, REVERT, POP, JUMPDEST. (Practice this iff the security is not sacrificed).

## Modifiers

1. Are no storage updates made (except in a reentrancy lock)?
2. Are `external calls` avoided?
3. Is the purpose of the modifier and other important information documented using `natspec`?
4. Always remember that `modifiers` increase the `Codesize` so use them wisely.
5. Duplicated require/revert statement should be refactored to a modifier or function.
6. Best practice to have the nonReentrant modifier come at the first of all the modifiers.
7. 


## Code

1. Using SafeMath or 0.8 checked math? (SWC-101)
2. Are any storage slots read multiple times?
3. Implementation should be consistent with the documentation, whats written in docs should be implemented in the contract.
4. Are any unbounded loops/arrays used that can cause DoS? (SWC-128)
5. Always remember there is present a discontinuity in the formula for division in solidity.
6. TO avoid division while in an equation, transfer the denominator to the other side to make it a multiplication.
7. Use `block.timestamp` only for long intervals. (SWC-116)
8. Don't use block.number for elapsed time. (SWC-116)
9. Do not update the length of an array while iterating over it.
10. Don't use `blockhash()`, etc for randomness. (SWC-120)
11. Are signatures protected against replay with a nonce and `block.chainid`? (SWC-121)
12. Ensure all signatures use EIP-712. (SWC-117 SWC-122)
13. Output of `abi.encodePacked()` shouldn't be hashed if using >2 dynamic types. Prefer using `abi.encode()` in general. (SWC-133)
14. Don't use any arbitrary data while using the assembly. (SWC-127)
15. Don't assume a specific ETH balance. (SWC-132)
16. Private data isn't private, it can be accessed. (SWC-136)
17. Updating a struct/array in memory won't modify it in storage.
18. Never shadow state variables. (SWC-119)
19. Try not to mutate function parameters.
20. Is calculating a value on the fly cheaper than storing it?
21. Are all state variables read from the correct contract (master vs. clone)?
22. Are comparison operators used correctly (`>`, `<`, `>=`, `<=`), especially to prevent off-by-one errors?
23. Are logical operators used correctly (`==`, `!=`, `&&`, `||`, `!`), especially to prevent off-by-one errors?
24. Always multiply before dividing, unless the multiplication could overflow.
25. Are magic numbers replaced by a constant with an intuitive name?
26. If the recipient of ETH had a fallback function that reverted, could it cause DoS? (SWC-113)
27. Use SafeERC20 or check return values safely.
28. Don't use `msg.value` if recursive `Delegate Calls` are possible (like if the contract inherits `Multicall`/`Batchable`).
29. Don't assume `msg.sender` is always a relevant user.
30. Don't use `assert()` unless for fuzzing or formal verification. (SWC-110)
31. Don't use `tx.origin` for authorization. (SWC-115)
32. Don't use `address.transfer()` or `address.send()`. Use `.call.value(...)("")` instead. As these were used to save from reentrancy attacks since using them gives a constant supply of 2300 gas. But they have a problem that if in future, during some hardfork the gas is decreased then this will lead to the failure of the transaction as if the fallback function is a little bit of gas consuming then this will cause the transaction to fail.
33. It is also recommended to not use the transfer or send for transfering the native ETH while interacting with a smart contract.
34. Prefer using `safeTransferFrom`, `safeMint` for `ERC20` and `ERC721` tokens
35. When using low-level calls, ensure the contract exists before calling.
36. When calling a function with many parameters, use the named argument syntax.
37. Do not use assembly for create2. Prefer the modern salted contract creation syntax.
38. Do not use assembly to access chainId or contract code/size/hash. Prefer the modern Solidity syntax.
39. Use the `delete` keyword when setting a variable to a zero value (`0`, `false`, `""`, etc).
40. Comment explanations wherever `unchecked` is used, along with an estimate of how much gas it saves (if relevant).
41. Do not depend on Solidity's arithmetic operator precedence rules. In addition to the use of parentheses to override default operator precedence, parentheses should also be used to emphasise it.
42. Expressions passed to logical/comparison operators (`&&`/`||`/`>=`/`==`/etc) should not have side-effects.
43. Wherever arithmetic operations are performed that could result in precision loss, ensure it benefits the right actors in the system, and document it with comments. 
44. Document the reason why a reentrancy lock is necessary whenever it's used with an inline or `@dev` natspec comment.
45. When fuzzing functions that only operate on specific numerical ranges use modulo to tighten the fuzzer's inputs (such as `x = x % 10000 + 1` to restrict from 1 to 10,000).
46. Use ternary expressions to simplify branching logic wherever possible.
47. When operating on more than one address, ask yourself what happens if they're the same.
48. Can someone without spending other then gas fees change the state of the contract.
49. Always check the number of loop iterations should be bounded by a small finite number other wise the transaction will run out of gas.
50. Always check for the return datatype of the called contract function. Example: in ERC20 implementations, the transfer functions are not consistent with             the value they return(some return the bool while others revert which can cause problems)
51. You can always convert `bool` to `revert` by using `require` and `revert` to `bool` by using try/catch statement.
52. Similar to the above, global `transfer` method reverts while the `send` gives the bool value which sometimes causes problems
53. Don't use `extcodesize` to gain the knowledge of whether the `msg.sender` is EOA as any contract calling the function while staying in the constructor can easily act as an EOA.
54. Always try to be consistent with the interface contract otherwise the call will lead to the fallback.
55. Making a new owner is a crucial thing, so a new function to accept the ownership should be made so that the ownership don't go in the hands of some wrong person or a smart contract which can not do anything.
56. In Solidity any address can be casted into specific contract, even if the contract at the address is not the one being casted. This can be exploited to hide malicious code.
57. Don't use `ecrecover` and `signature` in general to verify the user as these cause signature malleability.
58. While using `ecrocover`, the return value should also be checked to be non-zero(zero states invalid signature).
59. delete every entry of the mapping before deleting the mapping itself, otherwise the getter function will still work by giving all the mapping values
60. Look out for signature replay attacks.
61. Use underscores or constants for number literals for better readability and also for unexpected human error.
62. Use bytes.concat() instead of abi.encodePacked(), since this is preferred since 0.8.4
63. Any inconsistency in formula for calculation may cause the loss of the funds and also minting additional funds,<br> 
          example can be use of Math.min(a, b) which change suddenly when the condition changes.
64. Don't assume the implementations of ERC20, ERC721 tokens in their contracts, such as decimals, approve functions etc., coding using this assumption will lead to the casting errors
65. Look for the statements that can be skipped and still takes to the same blockchain state, for example some external call without any return values, some non-relevant require statements.
66. Try to read all the ERC20 Implementations in scope as their definitions can be different from what is expected.
67. `Round Up` should be done while taking the tokens in so that no one can be privileged while depositing a lower amount.
68. `Round down` should be done while transfering tokens from protocol to user so that no user can get the same value while having lower deposit.
69. Use `PULL` over `PUSH` while updating the state variables to mitigate the inclusion of blacklisted entities to become active. This also uses gas only whenever necessary
70. Try not to use the `percentage`, because it introduces the division and then rounding occurs. Also include a 100% cap while including a percentage.
71. It is necessary to make the lines in constructor in proper order, this really affect the initial state of the protocol. Example. a function called inside the constructor takes value of an uninitialized variable, hence will fail to give correct output.
72. A good practice while dealing with nonReentrant modifier. Try not to make the state variable public, instead make a public getter by yourself with a nonReentrant modifier.
73. Some good practices to save some gas involve :
    - using ++i instead of i++
    - using calldata to load the info instead of memory
    - not equating with boolean inside the if-else statement
    - use !=0 instead of > while putting non-zero condition to a uint
    - use bytes32 instead of string to declare a string variable
    - use bit manipulation instead of doing operation with the powers of 2
    - use multiple require statements instead of a single require statement containing the conditions seprated with the && operator
    - not use safeMath everywhere as some simple operations like division and multiplication can be done easily without it
    - internal functions not used should be removed before deployment to save some gas
    - don't assign default values to save gas (example: uint i = 0, bool x = false)
    - multiple mapping from same datatype can be then grouped to a single (from first datatype to the struct containing all destination datatypes)
    - revert error(); is better than require(error statement);
    - Try to use the unchecked to increment and decrement to an inrange number
    - Try not to call the full struct if only one or two variables of it are used in the function. Just cache the values of them in a local variable.
    - cheap way to store constants is to store them in library as an internal variable.
74. The constants in solidity when assigned to a mathematical expression have a property to calculate its value everytime they are written to give the value. While the immutables don't have this property so this gives immutables a gas saving advantage while assigned to a mathematical expression e.g. 2*10e12
75. If oracle is accessed using block number(to get historical data), then it should be mandatory to set the values only once per block.
 

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
10. A problem with using only `approve` function but not the `increaseAllowance` is that, If A approves B 5 tokens and B don't use them, Now, If A approves B 10 tokens to increase the approve value from 5 to 10 tokens, so that B can spend 10 tokens, now B can front run that 10 token transaction to spend both 5 and 10 tokens. So use `increaseAllowance`, `decreaseAllowance` instead of `approve` and similiar for `safe` versions of those functions.
12. While receiving arbitrary NFT, extend `ERC721Holder` from OpenZeppelin to handle the case when the NFT contract is using `safeTransferFrom` method as this method checks for `onERC721Received` method present in receiver contract or the reciever is an EOA.
13. While using `transfer` or `transferFrom` to send the arbitrary tokens:
    - Some tokens don't revert on failure, like `ZRX`
    - Some don't return bool value on function call, like `USDT`, `BNB`, `OMG`
    - Even the implementation of `USDT` is different on Polygon and Ethereum.
14. Chain reorgs is another event for rearrangement of transactions and can even removal of transactions. This event is very common in the chains where the time between consecutive blocks is very less and can reach upto high depths of blocks. Mitigation involves waiting for enough blocks after the transaction has become successful, otherwise reorg can remove that transaction.
15. The view functions of `CURVE` price oracle are not locked by the reentrancy modifier, so always check for the reentrancy modifier while using the curve oracle view function.
16. The cost of withdrawing the ether from Arbitrum to Ethereum is very high since Arbitrum uses a rollup architecture, which requires users to pay gas fees to transfer assets between the rollup and the Ethereum mainnet.
17. There are the copies of NFTs in different chains after a hardfork is done. This lead to sometimes double value a single entity when the protocol functions cross-chain.
18. There is no guarantee for no revert of the transaction that is made to get the symbol, decimals for ERC20 if it is not inheriting the `IERC20Metadata.sol`, and tokenURI for ERC721 if it is not inheriting the `IERC721Metadata.sol`
19. Consider supporting old NFTs and tokens before the ERC20 and ERC721 standard arrived. For example ERC20: WETH , ERC721: CryptoPunks, EtherRocks
   

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
13. The external calls from a contract can be made to be failed and still be made the function continue if the external call returns a bool, the attacker can just give very enough gas to make the sub-call(call from a contract function to another contract) fail.(Insufficient Gas Griefing)
14. Always check for the contrat existence before doing a low-level call.
15. Limit the number of iterations in the for-loop if making an external call due to gas shortage.
16. Multiple subsequent(one external call is related to the other external call depending on previous one) external calls should be checked to conserve the `msg.value`.


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
5. Are all users/ids that are operated on in functions that emit the event stored as indexed fields?
6. Avoid function calls and evaluation of expressions within event arguments. Their order of evaluation is unpredictable.
7. Events should be made for every important change in state made through the contract, so they can be read off-chain.
8. Avoid event spamming where there are events emitted even when there is e.g. zero claim amount, zero token transfer, as this will affect off-chain event tracking.
9. Always remember that events also change the state and also can contain state changing functions as their arguments.


## Contract

1. Use an SPDX license identifier.
2. A protocol whose fake code is present online which by mistake gets imported by another protocol can be unexpected. This happend while having duplicate npm packeage names but different code inside.
3. Are events emitted for every storage mutating function?
4. Check for correct inheritance, keep it simple and linear. (SWC-125)
5. Interface contracts generally don't contain the function which is internal as internal functions are made to support the public functions in their logic.
6. Use a `receive() external payable` function if the contract should accept transferred ETH and don't use if the contract don't accept the ether otherwise the funds could be stucted.
7. Write down and test invariants about relationships between stored state.
8. Is the purpose of the contract and how it interacts with others documented using natspec?
9. The contract should be marked `abstract` if another contract must inherit it to unlock its full functionality.
10. Emit an appropriate event for any non-immutable variable set in the constructor that emits an event when mutated elsewhere.
11. Avoid over-inheritance as it masks complexity and encourages over-abstraction.
12. Always use the named import syntax to explicitly declare which contracts are being imported from another file.
13. Group imports by their folder/package. Separate groups with an empty line. Groups of external dependencies should come first, then mock/testing contracts (if relevant), and finally local imports.
14. Summarize the purpose and functionality of the contract with a `@notice` natspec comment. Document how the contract interacts with other contracts inside/outside the project in a `@dev` natspec comment.
15. Malicious actors can use the Right-To-Left-Override unicode character to force RTL text rendering and confuse users as to the real intent of a contract.
16. Try to take into account the c3 linearization when inheriting from two contracts that contain same function with different implementations
          (diamond problem)
17. The callable functions in a contract are not only the ones visible in the contract code but also the ones which are inherited but are not mentioned in the code itself.
18. Its a good practice to include the [headers](https://github.com/transmissions11/headers)
19. The functions should be grouped in the following order as given in the solidity style guide for the auditing process should be smooth <br>
          { constructor, receive function (if exists), fallback function (if exists), external, public, internal, private, view and pure functions last }
20. Always look for making an extra function(claim) if there is possibility of the funds to be stuck in the contract or the contract is having a receive or fallback function. This can be seen in the case of airdrops that are generally landed on the protocol contract and a claim function should be made to retrieve them.
21. In the beginning after deployment of the contract, the state variables are easy to manipulate(especially in defi) since there is not much of the funds locked in the contract, and hence not very much of the funds are required to manipulate the state of the contract, this can lead to the contract being more vulnerable in start
22. If the contract is an implementation of an another protocol, then to maintain the consistency, we should check all the formulas to be same in both. This can happen in the strategy protocols that makes strategy for another defi protocols but lacks giving the users same values or outputs.
23. While using the proxy, Initialize the contract in the same transaction as initialization needs a call to initialize function.
24. Using same data feed of two related tokens is vulnerable, e.g. using datafeed for `USDC` for `DAI` will be vulnerable as if one depegs, then the other price will also be affected in the protocol.
25. Is the contract upgradeable?  If yes, then are there any storage slots reserved?
26. Try not to use the hardcoded address.

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
10. Staking, lending in a protocol is different(even if it seems very same)
11. Always try to see what a dust amount can do, as the dust amount can make anything to non-zero and somethings that work only for absolute zero variable will fail.
12. Be careful of relying on the raw token balance of a contract to determine earnings. Contracts which provide a way to recover assets sent directly to them can mess up share price functions that rely on the raw Ether or token balances of an address.
14. If your contract is a target for token approvals, do not make arbitrary calls from user input.
15. Always set a minimum deposit balance to revoke the privilege given to people depositing zero amount
16. One of the best optimisations can be decreasing the impermanent loss(maybe divide the loss among more people since the overall loss can not be decreased as this will affect the price impact on the AMM)
17. Check out for whether governance given to an EOA has infinite minting or approval power(to avoid rug pull, exit scams, circulating price impact)
18. Look out for slippage tolerance in Defi DEX protocol, this saves from unexpected results and even protects from front running
19. There is slippage cap in the functions in AMMs but there should also be the deadline set as the slippage cap gives the person assets in a specified range but the real value of the asset can be changed with time, so even if getting the same amount of token, but not at proper time can lead to bad trade.
20. The main concern while swapping is getting the expected price, so during very high fluctuations, using slippage in form of percentage or deviation from the current price is not a good idea since during high fluctuations, even inside the deadline the price may be very unexpected, so the best way to use swaps is (deadline + expected price) you want rather slippage percentage or absolute difference from the current price.
21. Try not to approve the token contracts which have onlyOwner functions which have the power to move the funds.
22. Watch out what if someone with very much money can do(in cases of auction), in these cases a flashloan attack is likely to happen
23. Functions without any protection(like onlyOwner) are vulnerable to frontrunning so consider what will happen if they are frontrunned.
24. Fees is a part of many protocols, watch out for the `msg.sender`, `fee payer`, `funds` receiver as different users.
25. In general, `Treasury`, `admin`, `manager` are the different entities that can receive the incentives or fees collected, try to differentiate between them.
26. In case of protocols having subscriptions, `unregistered`, `de-registered`, `expired` entries are also different, these should be acting according to the documentation.
27. `Inflation attack` : It is the attack in which the pool is submitted the tokens externally and now the liquidity is very high and the total supply of mint tokens is very low and hence the formula will give the minimum amount to deposit to be very high and hence DOSing for people with low money.
28. `maxSlippage` value should not be fixed, because in case of emergency where the price is constantly dropping or increasing, the withdraw function or swap function will revert due to crossing of the `maxSlippage`. But, at that time the transaction should pass otherwise the funds will be stuck forever as the slippage will never come to low.
29. In a lending and borrowing protocol, this can be a valid finding if at some point of time, the borrower is freeze to borrow the funds or is limited to borrow comparably less funds but is able and have tokens to give collateral, as this will significantly decrease the yield of the lender.
30. Watch out for all entry points for a position in a protocol for example in case of a protocol build on `uniswap` will have two entry points for adding liquidity, one of them is the protocol and another is through the pool. Try to investigate all the entry points and how can an entry points be used for unintended behaviour.
31. Oracle saving `block.timestamp` of every transaction in the pool will be vulnerable since if a smart contract doing multiple operation in the pool in a single transaction will result in same timestamp for all of them.
32. FlashLoan protection is done by using the condition `lastTimestamp != block.timestamp`, this reduces multiple calls in a single transaction and even in a single block. But this also makes the protocol vulnerable to `DOS`, since if any valid transaction can be frontrunned, then that transaction can not be included in that block, and multiple attacks of this kind on consecutive blocks will cause `DOS`. So, an extra front-running protection should be there.
33. Some protocols give a choice of the withdrawal token but the same value, this actually reduced capital efficiency if there is no proper ratio of all the tokens is maintained, as the ratio will be not equal but the value provided is equal.
34. It is a good practice for having a partial tokens withdrawal as if the contract have not enough funds, then by the margin of a very small amount, the funds of a user can get stuck.
35. Good practice is to give the claim authority to the owner or to the recepient themselves.
36. Some safety factor checks that are included in the protocol during withdrawal, oracle updating, liquidating a position are made to be protected against the flashloan attacks. But they should not be hardcoded as the adverse conditions in the De-Fi can cross the limits and the withdraw function will not work due to the conditions and hence the funds are stuck and the conditions are depleting :(
37. Always check and confirm as the expected behaviour whether the voting power is weighted according to the token holding or uniformly distributed. IMO it should be weighted.
38. Governance protocols should be checked between the clash in the priviledges of two different roles so as to have a race condition. And also what are the perks to open functions(public use)
39. Any extra perk other than the fees for the lender is an opportunity for them to be the borrower themselves as the funds will get returned to them in any case along with those perks.
40. Better to have a view function or the return variable of the deposit function so that the user know how much they will receive. They don't have to calculate by themselves and something unexpected don't happen.
41. `Just-In-Time` is actually doing a transaction not just before but `just before`, which means that the transaction should be just before the transaction of the victim. This can be used during the distribution of the yield to the LPs on the basis of their percent share in the pool. If a whale deposits a very big amount in the pool Just-in-Time before the distribution reward called by the owner, then the whale will have the great yield. But he don't deserve it since his tokens are never used by the protocol to earn the yield. Now, after receiving the yield, he just takes out his liquidity from the pool.
42. Exchanging tokens is not always straight forward(A 🔄 B) either due to lack of the pool between them, or due to the minimization of the overall fees for the exchange(so can go through different path e.g. A 🔄 D 🔄 B), so any protocol fixing a path or the fees will cause a vulnerability.
43. `FlashLoan` can be related to a `zero duration loan in borrowing and lending protocol` if the interest amount is starts from zero, but the collateral will be required to take the loan.
44. Always take care of the dust amount as it can make the equality to inequality and also makes the system DOS while playing around the corners of the inequality. [Example](https://twitter.com/0xprinc/status/1691053853050085376)
45. The receiver of the collateral should not be always same as the recepient of the collateral or not always be specified by the one who pays the loan as this will make any person to pay the debt and take away the collateral as the collateral contains more value.
    
## After Transaction
1. The transaction data can be seen by anyone reading the mempool, so don't use things like password in the transactions.
2. While auditing measures related to `pre-exploit` and `post-exploit` should be taken since the codebase can not be claimed to be hack proof very easily and hence `post-exploit` measures should also be included inside the codebase, both should count as a valid finding. So, try to think, what will happen if a contract is exploited, how will it affect the whole `DeFi` space.


## NFT
1. Any smart contract using NFT contracts as input should also include a function to blacklist NFTs so that anyone can not use NFT contracts as inputs that are theft in the past.
