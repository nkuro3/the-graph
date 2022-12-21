# The Graph
全てのサブグラフの管理レポジトリ
このレポジトリから`graph init`で各サブグラフを作成する。

## tutorial
tutorial - https://github.com/camiinthisthang/thegraph-workshop  
tutorial github - https://github.com/camiinthisthang/fameladysquad-subgraph  
subgraph - https://github.com/nkuro3/thegraph-tutorial  

### refs
Qiita - https://qiita.com/chomado/items/705d0a6d9ce985f1a433  
official ref - https://camiinthisthang.hashnode.dev/the-complete-guide-to-getting-started-with-the-graph  
thegraph - https://thegraph.com/docs/ja/cookbook/quick-start/#heading-8  

### memo
`nkuro3/thegraph-tutorial`に新しいレポジトリが作成される。１つのサブグラフにつき１つのレポジトリを作成する。
```shell
$ graph init ~

✔ Protocol · ethereum
✔ Product for which to initialize · hosted-service
✔ Subgraph name · nkuro3/thegraph-tutorial
✔ Directory to create the subgraph in · thegraph-tutorial
? Ethereum network … 
✔ Ethereum network · mainnet
✔ Contract address · 0xf3E6DbBE461C6fa492CeA7Cb1f5C5eA660EB1B47
✔ Fetching ABI from Etherscan
✔ Contract Name · Token
```

`src/token.ts`を変更する  
https://camiinthisthang.hashnode.dev/the-complete-guide-to-getting-started-with-the-graph  

depolyする
```shell
$ graph auth --product hosted-service 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
Deploy key set for https://api.thegraph.com/deploy/
-> OK

$ graph deploy --product hosted-service nkuro3/thegraph-tutorial
...
Build completed: QmYaXDgBEbPCrEEVZar5nWwuoiJBUcWFN9cztJXdMATFMa
✖ Failed to deploy to Graph node https://api.thegraph.com/deploy/: deployment failure::subgraph validation error: [The feature `ipfsOnEthereumContracts` is used by the subgraph but it is not declared in the manifest.]
```

上記のエラーが出た場合は以下を追加
```yaml
# subgraph.yaml
features:
  - ipfsOnEthereumContracts
```
https://qiita.com/chomado/items/705d0a6d9ce985f1a433  
https://thegraph.com/docs/ja/developing/creating-a-subgraph/#heading-41  

再度deploy
```shell
...
Build completed: Qmeay4Vn8rj8Vho1XhXPn6UsdDf5rVLH2qeDqcscu8uqEq
Deployed to https://thegraph.com/explorer/subgraph/nkuro3/thegraph-tutorial
Subgraph endpoints:
Queries (HTTP):     https://api.thegraph.com/subgraphs/name/nkuro3/thegraph-tutorial
```

上記のリンクを確認するとエラーになっている
```json
{
  "errors": [
    {
      "message": "Store error: query execution failed: Subgraph `Qmeay4Vn8rj8Vho1XhXPn6UsdDf5rVLH2qeDqcscu8uqEq` has not started syncing yet. Wait for it to ingest a few blocks before querying it"
    }
  ]
}
```
サブグラフのページで`Syncing`が確認できる。これが100%になるまで待つ。
https://thegraph.com/hosted-service/subgraph/nkuro3/thegraph-tutorial
