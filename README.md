# The Graph
全てのサブグラフの管理レポジトリ
このレポジトリから`graph init`で各サブグラフを作成する。

## tutorial
tutorial - https://github.com/camiinthisthang/thegraph-workshop  
subgraph - https://github.com/nkuro3/thegraph-tutorial  

### refs
Qiita - https://qiita.com/chomado/items/705d0a6d9ce985f1a433  
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