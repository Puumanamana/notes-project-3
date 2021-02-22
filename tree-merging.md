# Supervised tree merging (in development)

Given a set of trees classifying different sets of species, we want to build a consensus tree for the union of all the species in order to maximize the correlation between the consensus and a trait.

The procedure works in 2 steps:
    - Partioning step: the species are separated along the best performing edge. Species that are not in the tree whose edge is selected are set aside
    - Recruitment step: The species that were not selected are iteratively recruited to one of the 2 partitions based on the information from the other edges
    
These 2 steps are recursively applied to each partition until no further progress can be achieved.

## Example

<img src="img/stm.png" width="800"/>

## Implementation


```python
def make_binary_partition(species, trees):
  	"""
  	1) Prune <trees> with leaves in <species>
  	2) Find edge with best score --> binary partition of species in edge
  	3) Add the remaning species to the partition using a vote among the trees
  	4) Recurse on each set in the partition
  	"""
    # prune tree to only keep relevant species
	trees = [subset(t, species) for t in trees]
	# select partition (=best edge)
    edge_scores = score_edges(trees)
	(v1, v2) = edge_scores.argmax()
    
	# recruit missing species in v1 or v2 using 
    # with a weighted vote among the remaining edges
	recruits = {x: [0, 0] for x in species if x not in set.union(v1, v2)}
        
    for edge, score in edge_scores:
        for spec in recruits:
        # use evidence in edge to recruit spec to either v1 or v2
            vote = recruit_node(edge, spec, (v1, v2))
            recruits[spec][vote] += score
             
    for spec, scores in recruits.items():
        choice = random.choices([0, 1], weight=scores/scores.sum())
        if choice == 0:
            v1.add(spec)
        else:
            v2.add(spec)
                          
    partition = [make_binary_partition(v1, trees), make_binary_partition(v2, trees)]
                                       
    return partition
```
