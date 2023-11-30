# Nextstrain lab

## Introduction and background
In this lab, you will be using Nextstrain to examine a set of phylogenetic trees of sequences sampled from H3Nx influenza viruses in animals. In human populations, H3N2 and H1N1 circulate via seasonal epidemics, and were originally introduced into humans via cross-species transmission from animals. The 1968 H3N2 influenza pandemic was caused by a reassortment event in which HA and PB1 genes from an avian influenza virus reassorted with the H2N2 seasonal virus that was circulating in humans at the time. The introduction of a novel H3 HA gene, against which humans did not have pre-existing immunity, caused widespread transmission and a pandemic. Following initial transmission in humans, H3N2 continued to circulate seasonally, evolving yearly in a process of continual immune selection. The H1N1 virus that circulates in humans today is the result of the 2009 swine flu pandemic. 

Like all influenza viruses, H3 viruses naturally circulate in wild birds. It is thought that frequent reassortment in wild birds continually shuffles viral diversity and generates new subtypes. In addition to humans, avian origin H3 viruses have repeatedly spilled over into other host species, resulting in long-term transmission in pigs, horses, and dogs. However, surprisingly little is understood about how these viruses evolve in these other host species, and how the cross-species transmission has occurred in the past. In this tutorial, we will build phylogenetic trees using H3Nx sequences (meaning viruses with H3 HAs, packaged with any NA) sampled from a variety of host species to reconstruct the history of H3Nx evolution and cross-species transmission. We will investigate the following questions: 

1. How many times have H3 viruses been introduced into new species? 
2. When did these events occur? 
3. Does reassortment contribute to patterns of circulation in different hosts? 
4. How have these viruses spread geographically? 
5. What roles do different hosts play in H3 transmission and evolution? 


## Activity 1: Using Nextstrain commands to generate an H3Nx HA phylogeny. 


### Visualizing results
Now that we have a tree, let's take a look! The Nextstrain interface has a lot of fun and useful features. We'll walk through a few of them, and then you should take some time to explore. 

1. First, let's check out the clock rate. One the lefthand panel of the screen, you'll see lots of options for how to visualize the tree. Under the "Tree Options" -> "Layout", you should see a "Clock" option. Click on that option, and take a look. What is the estimated clock rate for these viruses? Do these viruses exhibit "clock-like" evolution? 

2. One interesting question is whether these viruses might evolve at different rates in different host species. One way we can take a look at that question is by comparing the clock rates by host. We can look at this visually, but it is a little challenging to see. So now let's try filtering the data by host. In the lefthand panel, under "Filter Data", click in the box. You should see some options auto-fill. Select `Host -> Equine` and `Host -> Swine`. Is there any noticeable difference in clock rates among these hosts? How about other combinations of hosts? Now try filtering on `Host -> Canine`. What is different about canine evolution?  

3. Now, let's go back to the tree view. Under "Tree Options" -> "Layout", click on "Rectangular". We now get to choose whether we want to view the tree with branch lengths scaled by Time or Divergence. Toggle between the divergence tree and the timetree. Do they look different? If so, how? If not, why would that be? 

4. Look at the tree, colored by host. You'll notice that we have inferred "host" traits onto internal nodes on the phylogeny. We can infer host switches on the tree by looking at the internal nodes at the which a host switch occurred. How many host switch events have there been over the history of this tree? Which host groups are major donors and which hosts are recipients? Which host switches have been the most successful, i.e., circulated for the longest or with the most diversity? Do different avian orders play different roles in H3 evolution and transmission? Which host order (anseriformes, galliformes, or neoaves) act more frequently as sources? 

4. As part of our reconstruction, we also inferred nucleotide and amino acid mutations on the internal nodes of the phylogeny. Zoom in on different branches of the tree by clicking on them. Take a look at some of the branches leading to host switches. We see that many of these host switch branches have amino acid changing mutations. If we want to filter the tree to color by mutations, under "Color By", select "Genotype" -> "HA", then the amino acid. Take for example site 179. Look at this site in the tree view and the scatterplot view. We can see that it is highly polymorphic in different host species. Without further data on phenotype, it is impossible to know whether this illicits an important change evolutionarily, but it is an interesting hypothesis that could be tested. 

5. Now let's look at geographic regions. Change the colorby view to "region" and take a look at the tree. How geographically structured are these populations? Are particular host groups restricted to particular geographic regions? Which host groups circulate the most widely across geographic space? As another fun way to visualize this, play around with the scatterplot view of the tree. You can select which variables to plot on the x and y axes. 

6. Finally, let's look at subtypes. Influenza viruses shuffle their genomes through a process called reassortment, which occurs when co-infecting virions co-infect the same cell. Reassortment is how HA and NA segments gets shuffled into new combinations (e.g., h3n1, h3n5, h3n8, etc...). Using the scatter plot view and the tree view, do particular hosts harbor more subtype diversity than others? If so, what does that tell us about infection frequency?


Some questions with the internal gene segments: Do the internal gene segments show similar rates of cross-species transmission, or are they distinct? How similar or different are the tree topologies and host reconstructions? Hint: you can look at 2 trees simultaneously by selecting `2nd tree` in the auspice drop-down menu. 

### Helpful links: 
Nextstrain documentation page: https://docs.nextstrain.org/en/latest/index.html
Nextstrain augur sub-commands documentation: https://docs.nextstrain.org/projects/augur/en/stable/usage/usage.html
Github repository for Nextstrain: https://github.com/nextstrain
Treetime documetation: https://treetime.readthedocs.io/en/latest/index.html



