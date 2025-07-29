services:
  plume-mainnet:
    image: ghcr.io/conduitxyz/plume-nitro:v3.3.2-celestia
    container_name: plume-mainnet
    restart: unless-stopped
    ports:
      - "8547:8547"
      - "6070:6070"
    command:
      - --chain.id=98866
      - --chain.name=conduit-orbit-deployer
      - --http.addr=0.0.0.0
      - --http.corsdomain=*
      - --http.vhosts=*
      - --ws.expose-all
      - --ws.rpcprefix=/
      - --ws.port=8547
      - --ws.addr=0.0.0.0
      - --ws.origins=*
      - --http.api=net,web3,eth,txpool,debug,admin,arb,arbdebug,arbtrace
      - --ws.api=net,web3,eth,txpool,debug
      - --chain.info-json=[{"chain-id":98866,"parent-chain-id":1,"chain-name":"conduit-orbit-deployer","chain-config":{"chainId":98866,"homesteadBlock":0,"daoForkBlock":null,"daoForkSupport":true,"eip150Block":0,"eip150Hash":"0x0000000000000000000000000000000000000000000000000000000000000000","eip155Block":0,"eip158Block":0,"byzantiumBlock":0,"constantinopleBlock":0,"petersburgBlock":0,"istanbulBlock":0,"muirGlacierBlock":0,"berlinBlock":0,"londonBlock":0,"clique":{"period":0,"epoch":0},"arbitrum":{"EnableArbOS":true,"AllowDebugPrecompiles":false,"DataAvailabilityCommittee":true,"InitialArbOSVersion":32,"InitialChainOwner":"0x5Ec32984332eaB190cA431545664320259D755d8","GenesisBlockNum":0}},"rollup":{"bridge":"0x35381f63091926750F43b2A7401B083263aDEF83","inbox":"0x943fc691242291B74B105e8D19bd9E5DC2fcBa1D","sequencer-inbox":"0x85eC1b9138a8b9659A51e2b51bb0861901040b59","rollup":"0x35c60Cc77b0A8bf6F938B11bd3E9D319a876c2aC","validator-utils":"0x84eA2523b271029FFAeB58fc6E6F1435a280db44","validator-wallet-creator":"0x0A5eC2286bB15893d5b8f320aAbc823B2186BA09","deployed-at":21887008}}]
      - --node.celestia-cfg.enable=true
      - --node.celestia-cfg.url=http://celestia-server:26657
      - --node.data-availability.enable=true
      - --node.data-availability.rest-aggregator.enable=true
      - --node.data-availability.rest-aggregator.urls=https://das-plume-mainnet-1.t.conduit.xyz
      - --execution.forwarding-target=https://rpc.plume.org
      - --execution.caching.archive
      - --parent-chain.connection.url=<ETH_RPC_URL>
      - --parent-chain.blob-client.beacon-url=<ETH_BEACON_RPC_URL>
      - --node.staker.enable=false
      - --node.feed.input.url=wss://relay-plume-mainnet-1.t.conduit.xyz
      - --node.sequencer=false
      - --execution.rpc.tx-fee-cap=100
      - --execution.rpc.gas-cap=500000000
      - --metrics
      - --metrics-server.addr=0.0.0.0
      - --metrics-server.port=6070
      - --metrics-server.update-interval=5s
