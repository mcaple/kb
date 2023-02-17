To get all attributes from a node, change product in the following to be the name you require, taken from [here](https://stackoverflow.com/questions/17735005/how-can-i-return-all-properties-for-a-node-using-cypher)

```
MATCH (p:product) WITH DISTINCT keys(p) AS keys
UNWIND keys AS keyslisting WITH DISTINCT keyslisting AS allfields
RETURN allfields;
```