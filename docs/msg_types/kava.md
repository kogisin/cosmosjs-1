# Kava

In this docs, these are supporting message types in Kava.

**_Note:_** At the time of this writing, CDP transactions are NOT available in `kava-2 (mainnet)`. It is only available in `kava-testnet-4000`.

- [Kava testnet link is available here](https://github.com/Kava-Labs/kava-testnets)

Kava is a collateralized debt position built on top of Cosmos SDK. It has pretty much the same message types as Cosmos Hub other than [4 different moduels](https://github.com/Kava-Labs/kava-devnet/blob/master/spec/kava.md) that make up the system.

### Supporting Message Types

- [cosmos-sdk/MsgSend](#msgsend)
- [cosmos-sdk/MsgMultiSend](#msgmultisend)
- [cosmos-sdk/MsgCreateValidator](#msgcreatevalidator)
- [cosmos-sdk/MsgEditValidator](#msgeditvalidator)
- [cosmos-sdk/MsgDelegate](#msgdelegate)
- [cosmos-sdk/MsgUndelegate](#msgundelegate)
- [cosmos-sdk/MsgBeginRedelegate](#msgbeginredelegate)
- [cosmos-sdk/MsgWithdrawDelegationReward](#msgwithdrawdelegationreward)
- [cosmos-sdk/MsgWithdrawValidatorCommission](#msgwithdrawvalidatorcommission)
- [cosmos-sdk/MsgModifyWithdrawAddress](#msgmodifywithdrawaddress)
- [cosmos-sdk/MsgSubmitProposal](#msgsubmitproposal)
- [cosmos-sdk/MsgDeposit](#msgdeposit)
- [cosmos-sdk/MsgVote](#msgvote)
- [cosmos-sdk/MsgUnjail](#msgunjail)
- [cdp/MsgCreateCDP](#msgCreateCDP)
- [cdp/MsgDeposit](#msgDeposit)
- [cdp/MsgWithdraw](#msgWithdraw)
- [cdp/MsgDrawDebt](#msgDrawDebt)
- [cdp/MsgRepayDebt](#msgRepayDebt)

###  MsgSend

```js
// cosmos-sdk/MsgSend
let stdSignMsg = cosmos.newStdMsg({
	msgs: [
		{
			type: "cosmos-sdk/MsgSend",
			value: {
				amount: [
					{
						amount: String(100000), 	// 6 decimal places (1000000 uatom = 1 ATOM)
						denom: "uatom"
					}
				],
				from_address: address,
				to_address: "cosmos18vhdczjut44gpsy804crfhnd5nq003nz0nf20v"
			}
		}
	],
	chain_id: chainId,
	fee: { amount: [ { amount: String(5000), denom: "uatom" } ], gas: String(200000) },
	memo: "",
	account_number: String(data.result.value.account_number),
	sequence: String(data.result.value.sequence)
});
```

###  MsgMultiSend

```js
// cosmos-sdk/MsgMultiSend
let stdSignMsg = cosmos.newStdMsg({
	msgs: [
		{
			type: "cosmos-sdk/MsgMultiSend",
			value: {
				inputs: [
					{
						address: address,
						coins: [
							{
								amount: String(100000),		// 6 decimal places (1000000 uatom = 1 ATOM)
								denom: "uatom"
							}
						]
					}
				],
				outputs: [
					{
						address: "cosmos18vhdczjut44gpsy804crfhnd5nq003nz0nf20v",
						coins: [
							{
								amount: String(100000),
								denom: "uatom"
							}
						]
					}
				]
			}
		}
	],
	chain_id: chainId,
	fee: { amount: [ { amount: String(5000), denom: "uatom" } ], gas: String(200000) },
	memo: "",
	account_number: String(data.result.value.account_number),
	sequence: String(data.result.value.sequence)
});
```

### MsgCreateValidator

```js
// cosmos-sdk/MsgCreateValidator
let stdSignMsg = cosmos.newStdMsg({
	msgs: [
		{
			type: "cosmos-sdk/MsgCreateValidator",
			value: {
				description: {
					moniker: "Test Validator",
					identity: "",
					website: "",
					details: ""
				},
				commission: {
					rate: "0.250000000000000000",	// 25.0%
					max_rate: "1.000000000000000000",
					max_change_rate: "0.100000000000000000"
				},
				min_self_delegation: String(1),
				delegator_address: address,
				validator_address: "cosmosvaloper106kt5cmued596rqusmthfnh39h38k64e73fxce",
				pubkey: "cosmosvalconspub1zcjduepq8ve2hfuvnyhan9tz7vjgstslw7lygnk85sgp3emehtnxjpu3j7gqw5wvcz",
				value: {
					denom: "uatom",
					amount: String(1)
				}
			}
		}
	],
	chain_id: chainId,
	fee: { amount: [ { amount: String(5000), denom: "uatom" } ], gas: String(200000) },
	memo: "",
	account_number: String(data.result.value.account_number),
	sequence: String(data.result.value.sequence)
});
```

### MsgEditValidator

```js
// cosmos-sdk/MsgEditValidator
let stdSignMsg = cosmos.newStdMsg({
	msgs: [
		{
			type: "cosmos-sdk/MsgEditValidator",
			value: {
				Description: {
					moniker: "Best Validator",
					identity: "[do-not-modify]",
					website: "[do-not-modify]",
					details: "[do-not-modify]"
				},
				address: "cosmosvaloper106kt5cmued596rqusmthfnh39h38k64e73fxce",
				commission_rate: "0.220000000000000000",	// 22.0%
				min_self_delegation: null
			}
		}
	],
	chain_id: chainId,
	fee: { amount: [ { amount: String(5000), denom: "uatom" } ], gas: String(200000) },
	memo: "",
	account_number: String(data.result.value.account_number),
	sequence: String(data.result.value.sequence)
});
```

### MsgDelegate

```js
// cosmos-sdk/MsgDelegate
let stdSignMsg = cosmos.newStdMsg({
	msgs: [
		{
			type: "cosmos-sdk/MsgDelegate",
			value: {
				amount: {
					amount: String(1000000),
					denom: "uatom"
				},
				delegator_address: address,
				validator_address: "cosmosvaloper1clpqr4nrk4khgkxj78fcwwh6dl3uw4epsluffn"
			}
		}
	],
	chain_id: chainId,
	fee: { amount: [ { amount: String(5000), denom: "uatom" } ], gas: String(200000) },
	memo: "",
	account_number: String(data.result.value.account_number),
	sequence: String(data.result.value.sequence)
});
```

### MsgUndelegate

```js
// cosmos-sdk/MsgUndelegate
let stdSignMsg = cosmos.newStdMsg({
	msgs: [
		{
			type: "cosmos-sdk/MsgUndelegate",
			value: {
				amount: {
					amount: String(1000000),
					denom: "uatom"
				},
				delegator_address: address,
				validator_address: "cosmosvaloper1clpqr4nrk4khgkxj78fcwwh6dl3uw4epsluffn"
			}
		}
	],
	chain_id: chainId,
	fee: { amount: [ { amount: String(5000), denom: "uatom" } ], gas: String(200000) },
	memo: "",
	account_number: String(data.result.value.account_number),
	sequence: String(data.result.value.sequence)
});
```

### MsgBeginRedelegate 

```js
// cosmos-sdk/MsgBeginRedelegate
let stdSignMsg = cosmos.newStdMsg({
	msgs: [
		{
			type: "cosmos-sdk/MsgBeginRedelegate",
			value: {
				amount: {
					amount: String(1000000),
					denom: "uatom"
				},
				delegator_address: address,
				validator_dst_address: "cosmosvaloper1ec3p6a75mqwkv33zt543n6cnxqwun37rr5xlqv",
				validator_src_address: "cosmosvaloper1clpqr4nrk4khgkxj78fcwwh6dl3uw4epsluffn"
			}
		}
	],
	chain_id: chainId,
	fee: { amount: [ { amount: String(5000), denom: "uatom" } ], gas: String(200000) },
	memo: "",
	account_number: String(data.result.value.account_number),
	sequence: String(data.result.value.sequence)
});
```

### MsgWithdrawDelegationReward

```js
// cosmos-sdk/MsgWithdrawDelegationReward
let stdSignMsg = cosmos.newStdMsg({
	msgs: [
		{
			type: "cosmos-sdk/MsgWithdrawDelegationReward",
			value: {
				delegator_address: address,
				validator_address: "cosmosvaloper1clpqr4nrk4khgkxj78fcwwh6dl3uw4epsluffn"
			}
		}
	],
	chain_id: chainId,
	fee: { amount: [ { amount: String(5000), denom: "uatom" } ], gas: String(200000) },
	memo: "",
	account_number: String(data.result.value.account_number),
	sequence: String(data.result.value.sequence)
});
```

### MsgWithdrawValidatorCommission

```js
// cosmos-sdk/MsgWithdrawValidatorCommission
let stdSignMsg = cosmos.newStdMsg({
	msgs: [
		{
			type: "cosmos-sdk/MsgWithdrawValidatorCommission",
			value: {
				validator_address: "cosmosvaloper1clpqr4nrk4khgkxj78fcwwh6dl3uw4epsluffn"
			}
		}
	],
	chain_id: chainId,
	fee: { amount: [ { amount: String(5000), denom: "uatom" } ], gas: String(200000) },
	memo: "",
	account_number: String(data.result.value.account_number),
	sequence: String(data.result.value.sequence)
});
```

### MsgModifyWithdrawAddress

```js
// cosmos-sdk/MsgModifyWithdrawAddress
let stdSignMsg = cosmos.newStdMsg({
	msgs: [
		{
			type: "cosmos-sdk/MsgModifyWithdrawAddress",
			value: {
				delegator_address: address,
				withdraw_address: "cosmos133mtfk63fuac5e2npfgcktwufnty2536wedfal"
			}
		}
	],
	chain_id: chainId,
	fee: { amount: [ { amount: String(5000), denom: "uatom" } ], gas: String(200000) },
	memo: "",
	account_number: String(data.result.value.account_number),
	sequence: String(data.result.value.sequence)
});
```

### MsgSubmitProposal

```js
// cosmos-sdk/MsgSubmitProposal
let stdSignMsg = cosmos.newStdMsg({
	msgs: [
		{
			type: "cosmos-sdk/MsgSubmitProposal",
			value: {
				title: "Activate the Community Pool",
				description: "Enable governance to spend funds from the community pool. Full proposal: https://ipfs.io/ipfs/QmNsVCsyRmEiep8rTQLxVNdMHm2uiZkmaSHCR6S72Y1sL1",
				initial_deposit: [
                    {
                    	amount: String(1000000),
                        denom: "uatom"
                    }
                ],
                proposal_type: "Text",
                proposer: address
			}
		}
	],
	chain_id: chainId,
	fee: { amount: [ { amount: String(5000), denom: "uatom" } ], gas: String(200000) },
	memo: "",
	account_number: String(data.result.value.account_number),
	sequence: String(data.result.value.sequence)
});
```

### MsgDeposit

```js
// cosmos-sdk/MsgDeposit
let stdSignMsg = cosmos.newStdMsg({
	msgs: [
		{
			type: "cosmos-sdk/MsgDeposit",
			value: {
				amount: [
                    {
                    	amount: String(1000000),
                        denom: "uatom"
                    }
                ],
                depositor: address,
				proposal_id: String(1)
			}
		}
	],
	chain_id: chainId,
	fee: { amount: [ { amount: String(5000), denom: "uatom" } ], gas: String(200000) },
	memo: "",
	account_number: String(data.result.value.account_number),
	sequence: String(data.result.value.sequence)
});
```

### MsgVote

```js
// cosmos-sdk/MsgVote
let stdSignMsg = cosmos.newStdMsg({
	msgs: [
		{
			type: "cosmos-sdk/MsgVote",
			value: {
				option: "Yes",	// Yes, No, NowithVeto, Abstain
				proposal_id: String(1),
                voter: address
			}
		}
	],
	chain_id: chainId,
	fee: { amount: [ { amount: String(5000), denom: "uatom" } ], gas: String(200000) },
	memo: "",
	account_number: String(data.result.value.account_number),
	sequence: String(data.result.value.sequence)
});
```

### MsgUnjail

```js
// cosmos-sdk/MsgUnjail
let stdSignMsg = cosmos.newStdMsg({
	msgs: [
		{
			type: "cosmos-sdk/MsgUnjail",
			value: {
				address: "cosmosvaloper1clpqr4nrk4khgkxj78fcwwh6dl3uw4epsluffn"
			}
		}
	],
	chain_id: chainId,
	fee: { amount: [ { amount: String(5000), denom: "uatom" } ], gas: String(200000) },
	memo: "",
	account_number: String(data.result.value.account_number),
	sequence: String(data.result.value.sequence)
});
```

### MsgCreateCDP

```js
// cdp/MsgCreateCDP
let stdSignMsg = cosmos.newStdMsg({
	msgs: [
        {
            type: "cdp/MsgCreateCDP",
            value: {
                sender: "kava1ztrqwujkdu3dfzqv059vjyw7p879zv87lp5qn6",
                principal: [
                    { 
                        denom: "usdx", 
                        amount: "50000000" 
                    }
                ],
                collateral: [
                    { 
                        denom: "btc", 
                        amount: "1500000" 
                    }
                ]
            }
        }
	],
	chain_id: chainId,
	fee: { amount: [ { amount: String(5000), denom: "ukava" } ], gas: String(200000) },
	memo: "",
	account_number: String(data.result.value.account_number),
	sequence: String(data.result.value.sequence)
});
```

### MsgDeposit
```js
// cdp/MsgDeposit
let stdSignMsg = cosmos.newStdMsg({
	msgs: [
        {
            type: "cdp/MsgDeposit",
            value: {
                owner: "kava1ztrqwujkdu3dfzqv059vjyw7p879zv87lp5qn6",
                depositor: "kava1ztrqwujkdu3dfzqv059vjyw7p879zv87lp5qn6",
                collateral: [
                    { 
                        denom: "btc", 
                        amount: "1500" 
                    }
                ]
            }
        }
	],
	chain_id: chainId,
	fee: { amount: [ { amount: String(5000), denom: "ukava" } ], gas: String(200000) },
	memo: "",
	account_number: String(data.result.value.account_number),
	sequence: String(data.result.value.sequence)
});
```

### MsgWithdraw

```js
// cdp/MsgWithdraw
let stdSignMsg = cosmos.newStdMsg({
	msgs: [
        {
            type: "cdp/MsgWithdraw",
            value: {
                owner: "kava12mhygxvk67n52wzcz0yuunw74xst7jmw2pkql3",
                depositor: "kava10tpyfe03nufsax5g038n287yzn9ldyqc9dvz5j",
                collateral: [
                    { 
                        denom: "btc", 
                        amount: "50000" 
                    }
                ]
            }
        }
	],
	chain_id: chainId,
	fee: { amount: [ { amount: String(5000), denom: "ukava" } ], gas: String(200000) },
	memo: "",
	account_number: String(data.result.value.account_number),
	sequence: String(data.result.value.sequence)
});
```

### MsgDrawDebt

```js
// cdp/MsgDrawDebt
let stdSignMsg = cosmos.newStdMsg({
	msgs: [
        {
            type: "cdp/MsgDrawDebt",
            value: {
                sender: "kava10tpyfe03nufsax5g038n287yzn9ldyqc9dvz5j",
                cdp_denom: "btc",
                principal: [
                    { 
                        denom: "usdx", 
                        amount: "5000" 
                    }
                ]
            }
        }
	],
	chain_id: chainId,
	fee: { amount: [ { amount: String(5000), denom: "ukava" } ], gas: String(200000) },
	memo: "",
	account_number: String(data.result.value.account_number),
	sequence: String(data.result.value.sequence)
});
```

### MsgRepayDebt

```js
// cdp/MsgRepayDebt
let stdSignMsg = cosmos.newStdMsg({
	msgs: [
        {
            type: "cdp/MsgRepayDebt",
            value: {
                sender: "kava10tpyfe03nufsax5g038n287yzn9ldyqc9dvz5j",
                payment: [
                    { 
                        denom: "usdx", 
                        amount: "10000" 
                    }
                ],
                cdp_denom: "btc"
            }
        }
	],
	chain_id: chainId,
	fee: { amount: [ { amount: String(5000), denom: "ukava" } ], gas: String(200000) },
	memo: "",
	account_number: String(data.result.value.account_number),
	sequence: String(data.result.value.sequence)
});
```


