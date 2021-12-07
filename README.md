# IPFS Merkel DAG Tree Visualization

## Table of Contents

- [Install](#install)
- [Usage](#usage)

## Install

To install and run the D3 Tree locally, first [install IPFS](https://dist.ipfs.io/go-ipfs/v0.4.0). Then:


```sh
ipfs daemon
# Open a new terminal window
git clone https://github.com/mohitkh/ipfsDagVis.git
cd ipfsDagVis/webapps/tree-ltr
make
```
Inside ipfsDagVis/webapps/tree-ltr run 'ipfs add -r . '
Now get the hash corresponding to 'ipfsDagVis/webapps/tree-ltr' folder. Lets say it is hash1.

Next, we need to add a folder/directory to ipfs. For that run the command 'ipfs add -r -folder_name'
This folder gets added to ipfs and a hash is generated for each chunk. Lets say hash for root folder -folder_name is hash2.

## Usage
To visualize this folder content in d3, open http://localhost:8080/ipfs/hash1/viz#hash2  <br/>
eg. http://localhost:8080/ipfs/QmPK8rJ5iTYmiMrkm5MXjeqBg3TXZUMQcdyyuoPPZFMTJn/viz#QmXVrwyX5AUx5kWx3e9m49NuKAj57HJYmKbbRvHWMXbUQU
in your browser  <br />
Change the IPFS hash at the end of the URL to see any other IPFS tree. <br />
The first hash is the hash for 'ipfsDagVis/webapps/tree-ltr' folder in ipfs; the second hash is whatever is being visualized. <br />

## Additional feature: Generating static Merkel DAG in pdf/sbg/png format
ipfs cat Qmcd7Sebd46vxDWjbUERK8w82zp8sgWTtHT5c93kzr2v3M  >/usr/local/bin/grapher <br />
chmod +x /usr/local/bin/grapher  <br />

grapher hash2 | dot -Tsvg >graph.svg <br />
grapher hash2 | dot -Tpdf >graph.pdf <br />
grapher hash2 | dot -Tpng >graph.png <br />
 <br />
eg. <br />
grapher QmRCJXG7HSmprrYwDrK1GctXHgbV7EYpVcJPQPwevoQuqF | dot -Tsvg >graph.svg <br />
grapher QmRCJXG7HSmprrYwDrK1GctXHgbV7EYpVcJPQPwevoQuqF | dot -Tpdf >graph.pdf <br />
grapher QmRCJXG7HSmprrYwDrK1GctXHgbV7EYpVcJPQPwevoQuqF | dot -Tpng >graph.png <br />
 <br />
The above lines will generate Merkel DAG in svg, pdf and png format. <br />
The hash2 used is the hash of the folder/data to be visualized <br />
