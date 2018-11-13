# ethereum_practice
本文主要从代码的角度分析以太坊协议的实现

> tips
目录结构需要重新排版

## 快速浏览

* [简介](README.md)
* [类型](类型/README.md)
  * [CallMsg](类型/callmsg.md)
  * [ChainReader](类型/chainreader.md)
  * [ChainStateReader](类型/chainstatereader.md)
  * [ChainSyncReader ](类型/chainsyncreader.md)
  * [ContractCaller](类型/contractcaller.md)
  * [FilterQuery](类型/filterquery.md)
  * [GasEstimato](类型/gasestimato.md)
  * [GasPricer](类型/gaspricer.md)
  * [LogFilterer ](类型/logfilterer.md)
  * [PendingContractCaller](类型/pendingcontractcaller.md)
  * [PendingStateEventer ](类型/pendingstateeventer.md)
  * [PendingStateReader ](类型/pendingstatereader.md)
  * [Subscription](类型/subscription.md)
  * [SyncProgress](类型/syncprogress.md)
  * [TransactionReader](类型/transactionreader.md)
  * [TransactionSender](类型/transactionsender.md)
* [accounts](accounts/README.md)
  * [accounts/abi](accounts/accountsabi.md)
  * [accounts/abi/bind](accounts/accountsabibind.md)
  * [accounts/abi/bind/backends](accounts/accountsabibindbackends.md)
  * [accounts/keystore](accounts/accountskeystore.md)
  * [accounts/usbwallet](accounts/accountsusbwallet.md)
  * [accounts/usbwallet/internal/trezor](accounts/accountsusbwalletinternaltrezor.md)
* [cmd](cmd/README.md)
  * [cmd/abigen](cmd/cmdabigen.md)
  * [cmd/bootnode](cmd/cmdbootnode.md)
  * [cmd/clef](cmd/cmdclef.md)
  * [cmd/ethkey](cmd/cmdethkey.md)
  * [cmd/evm](cmd/cmdevm.md)
  * [cmd/evm/internal/compiler](cmd/cmdevminternalcompiler.md)
  * [cmd/faucet](cmd/cmdfaucet.md)
  * [cmd/geth](cmd/cmdgeth.md)
  * [cmd/internal/browser](cmd/cmdinternalbrowser.md)
  * [cmd/p2psim](cmd/cmdp2psim.md)
  * [cmd/puppeth    ](cmd/cmdpuppeth.md)
  * [cmd/rlpdump](cmd/cmdrlpdump.md)
  * [cmd/swarm](cmd/cmdswarm.md)
  * [cmd/swarm/mimegen](cmd/cmdswarmmimegen.md)
  * [cmd/swarm/swarm-smoke](cmd/cmdswarmswarm-smoke.md)
  * [cmd/utils](cmd/cmdutils.md)
  * [cmd/wnode](cmd/cmdwnode.md)
* [common](comon/README.md)
  * [common/bitutil](comon/commonbitutil.md)
  * [common/compiler](comon/commoncompiler.md)
  * [common/fdlimit](comon/commonfdlimit.md)
  * [common/hexutil](comon/commonhexutil.md)
  * [common/math](comon/commonmath.md)
  * [common/mclock    ](comon/commonmclock.md)
  * [common/prque](comon/commonprque.md)
* [consensus](consensus/README.md)
  * [consensus/clique](consensus/consensusclique.md)
  * [consensus/ethash](consensus/consensusethash.md)
  * [consensus/misc](consensus/consensusmisc.md)
  * [console](consensus/console.md)
  * [contracts/chequebook](consensus/contractschequebook.md)
  * [contracts/chequebook/contract](consensus/contractschequebookcontract.md)
  * [contracts/ens](consensus/contractsens.md)
  * [contracts/ens/contract](consensus/contractsenscontract.md)
* [core](core/README.md)
  * [core/asm](core/coreasm.md)
  * [core/bloombits](core/corebloombits.md)
  * [core/rawdb](core/corerawdb.md)
  * [core/state](core/corestate.md)
  * [core/types](core/coretypes.md)
  * [core/vm](core/corevm.md)
  * [core/vm/runtime](core/corevmruntime.md)
* [crypto](cryptp/README.md)
  * [crypto/bn256 ](cryptp/cryptobn256.md)
  * [crypto/bn256/cloudflare](cryptp/cryptobn256cloudflare.md)
  * [crypto/bn256/google](cryptp/cryptobn256google.md)
  * [crypto/ecies](cryptp/cryptoecies.md)
  * [crypto/secp256k1](cryptp/cryptosecp256k1.md)
  * [crypto/sha3](cryptp/cryptosha3.md)
* [dashboard](dashboard/README.md)
* [eth](eth/README.md)
  * [ethclient](eth/ethclient.md)
  * [eth/downloader](eth/ethdownloader.md)
  * [eth/fetcher](eth/ethfetcher.md)
  * [eth/filters](eth/ethfilters.md)
  * [eth/gasprice](eth/ethgasprice.md)
  * [ethstats](eth/ethstats.md)
  * [eth/tracers    ](eth/ethtracers.md)
  * [eth/tracers/internal/tracers    ](eth/ethtracersinternaltracers.md)
* [event](event/README.md)
* [internal](internal/README.md)
  * [internal/build](internal/internalbuild.md)
  * [internal/cmdtest](internal/internalcmdtest.md)
  * [internal/debug](internal/internaldebug.md)
  * [internal/ethapi](internal/internalethapi.md)
  * [internal/guide](internal/internalguide.md)
  * [internal/jsre](internal/internaljsre.md)
  * [internal/jsre/deps](internal/internaljsredeps.md)
  * [internal/web3ext](internal/internalweb3ext.md)
* [les](les/README.md)
  * [les/flowcontrol](les/lesflowcontrol.md)
* [light](light/README.md)
* [log](log/README.md)
* [metrics](metrics/README.md)
  * [metrics/exp](metrics/metricsexp.md)
  * [metrics/influxdb](metrics/metricsinfluxdb.md)
  * [metrics/librato](metrics/metricslibrato.md)
* [miner](miner/README.md)
* [mobile](mobile/README.md)
* [node](node/README.md)
* [p2p](p2p/README.md)
  * [p2p/discover](p2p/p2pdiscover.md)
  * [p2p/discv5](p2p/p2pdiscv5.md)
  * [p2p/enode](p2p/p2penode.md)
  * [p2p/enr](p2p/p2penr.md)
  * [p2p/nat](p2p/p2pnat.md)
  * [p2p/netutil](p2p/p2pnetutil.md)
  * [p2p/protocols](p2p/p2pprotocols.md)
  * [p2p/simulations](p2p/p2psimulations.md)
  * [p2p/simulations/adapters](p2p/p2psimulationsadapters.md)
  * [p2p/simulations/examples](p2p/p2psimulationsexamples.md)
  * [p2p/simulations/pipes](p2p/p2psimulationspipes.md)
  * [p2p/testing](p2p/p2ptesting.md)
* [params](params/README.md)
* [rlp](rlp/README.md)
* [rpc](rpc/README.md)
* [signer](signer/README.md)
  * [signer/core](signer/signercore.md)
  * [signer/rules](signer/signerrules.md)
  * [signer/storage](signer/signerstorage.md)
* [swarm](swarm/README.md)
  * [swarm/api](swarm/swarmapi.md)
  * [swarm/api/client](swarm/swarmapiclient.md)
  * [swarm/api/http](swarm/swarmapihttp.md)
  * [swarm/bmt](swarm/swarmbmt.md)
  * [swarm/chunk    ](swarm/swarmchunk.md)
  * [swarm/fuse](swarm/swarmfuse.md)
  * [swarm/log](swarm/swarmlog.md)
  * [swarm/metrics](swarm/swarmmetrics.md)
  * [swarm/multihash](swarm/swarmmultihash.md)
  * [swarm/network](swarm/swarmnetwork.md)
  * [swarm/network/bitvector](swarm/swarmnetworkbitvector.md)
  * [swarm/network/priorityqueue](swarm/swarmnetworkpriorityqueue.md)
  * [swarm/network/simulation](swarm/swarmnetworksimulation.md)
  * [swarm/network/simulations](swarm/swarmnetworksimulations.md)
  * [swarm/network/simulations/discovery    ](swarm/swarmnetworksimulationsdiscovery.md)
  * [swarm/network/stream](swarm/swarmnetworkstream.md)
  * [swarm/network/stream/intervals](swarm/swarmnetworkstreamintervals.md)
  * [swarm/pot](swarm/swarmpot.md)
  * [swarm/pss](swarm/swarmpss.md)
  * [swarm/pss/client](swarm/swarmpssclient.md)
  * [swarm/pss/notify](swarm/swarmpssnotify.md)
  * [swarm/sctx](swarm/swarmsctx.md)
  * [swarm/services/swap](swarm/swarmservicesswap.md)
  * [swarm/services/swap/swap](swarm/swarmservicesswapswap.md)
  * [swarm/spancontext](swarm/swarmspancontext.md)
  * [swarm/state](swarm/swarmstate.md)
  * [swarm/storage](swarm/swarmstorage.md)
  * [swarm/storage/encryption](swarm/swarmstorageencryption.md)
  * [swarm/storage/feed](swarm/swarmstoragefeed.md)
  * [swarm/storage/feed/lookup](swarm/swarmstoragefeedlookup.md)
  * [swarm/storage/mock](swarm/swarmstoragemock.md)
  * [swarm/storage/mock/db    ](swarm/swarmstoragemockdb.md)
  * [swarm/storage/mock/mem](swarm/swarmstoragemockmem.md)
  * [swarm/storage/mock/rpc](swarm/swarmstoragemockrpc.md)
  * [swarm/storage/mock/test](swarm/swarmstoragemocktest.md)
  * [swarm/testutil](swarm/swarmtestutil.md)
  * [swarm/tracing](swarm/swarmtracing.md)
  * [swarm/version](swarm/swarmversion.md)
* [trie](trie/README.md)
* [whisper](wisper/README.md)
  * [whisper/mailserver](wisper/whispermailserver.mdm)
  * [whisper/shhclient](wisper/whispershhclient.md)
  * [whisper/whisperv5](wisper/whisperwhisperv5.md)

