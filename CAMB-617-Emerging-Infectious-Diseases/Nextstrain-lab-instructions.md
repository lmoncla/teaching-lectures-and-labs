# Nextstrain lab

## Introduction and background
In human populations, H3N2 and H1N1 influenza viruses circulate via seasonal epidemics, and were originally introduced into humans via cross-species transmission from animals. The 1968, H3N2 influenza pandemic was caused by a reassortment event in which HA and PB1 genes from an avian influenza virus reassorted with the H2N2 seasonal virus that was circulating in humans at the time. The introduction of a novel H3 HA gene, against which humans did not have pre-existing immunity, caused widespread transmission and a pandemic. Following initial transmission in humans, H3N2 continued to circulate seasonally, evolving yearly in a process of continual immune selection. 

Like all influenza viruses, H3 viruses naturally circulate in wild birds. It is thought that frequent reassortment in wild birds continually shuffles viral diversity and generates new subtypes. In addition to humans, avian origin H3 viruses have repeatedly spilled over into other host species, resulting in long-term transmission in pigs, horses, and dogs. However, surprisingly little is understood about how these viruses evolve in these other host species. Additionally, avian H3N8 viruses recently caused 3 infections in humans in China, some of which harbored mutations that are thought to improve viral replication in mammals. In this activity, we will explore how H3Nx viruses (meaning viruses with H3 HAs, packaged with any NA) evolve and trace their history of cross-species transmission. We will do this using Nextstrain, a set of bioinformatic tools that can be used to build interactive phylogenetic trees and for phylodynamic analysis. Other examples of Nextstrain, and how it has been used for outbreak investigation are linked below. Feel free to explore! 


1. How many times have H3 viruses been introduced into new species? 
2. When did these events occur? 
3. Does reassortment contribute to patterns of circulation in different hosts? 
4. How have these viruses spread geographically? 
5. What roles do different hosts play in H3 transmission and evolution? 


## Introduction to Nextstrain

1. Navigate to the [H3Nx Nextstrain build](https://nextstrain.org/groups/moncla-lab/non-human-h3?c=host). This is a phylogenetic tree built from HA genes from a variety of host species. This is a time-resolved phylogeny, so the x-axis represents time in years. Each dot (or tip) represents a unique sampled HA sequence, and each internal node represents an inferred ancestor on the tree. In this view, we have used a model to infer the most likely ancestor at each internal node. For example, you can see that most of the deep branches in the tree are colored red, to indicate that that they are avian. This is because birds are the natural reservoir for influenza, so all circulating viruses in this tree that were sampled from other species were originally transmitted from birds. 

2. We can change how we view the tree by interacting with the panel on the left. For example, if we wanted to change the view so that the tree was colored by geographic region instead of host, navigate to the `Color By` panel on the left, and click on the drop down menu. Select `Region`.   

3. Sometimes, we might want to view the tree scaled by mutations instead of time. To do so, go back to the left panel under `Tree`, and look under `Branch Length`, and click on `DIVERGENCE`. You will notice that the overall tree shape doesn't really look all that different, but that the x-axis is now scaled by the number of substitutions per site per year (usually called divergence). The reason that the overall topology doesn't change is that most viruses evolve by a "molecular clock". This means that the rate at which mutations accumulate in viral genomes is approximately constant over time. Because of this, we can use the number of mutations to estimate how far back in time two sampled infections share a common ancestor. To view the rate of mutation accumulation, or "clock rate", look under `Tree`, `Layout`, and click on `Clock`. To get back to the tree view, click on `Rectangular` again. 

4. One interesting question is whether these viruses might evolve at different rates in different host species. One way we can take a look at that question is by comparing the clock rates by host. We can look at this visually, but it is a little challenging to see. Try that first. Based on what you can see by looking at the clock view, colored by host, do some hosts seem to have higher rates of evolution than others? 

Now let's try filtering the data by host. In the lefthand panel, under "Filter Data", click in the box. You should see some options auto-fill. Select `Host -> Equine` and `Host -> Swine`. When you filter by a particular host, it will recalculate the clock rate for only those tips. If you select multiple hosts at the same time, it will use all of those hosts to calculate a rate, but you can see whether particular species fall above or below the mean line. Is there any noticeable difference in clock rates among these hosts? Now try filtering on `Host -> Canine`. What is different about canine evolution?  

5. Now, look at the tree in rectangular view again, colored by host. You'll notice that we have inferred "host" traits onto internal nodes on the phylogeny. We can infer host switches on the tree by looking at the internal nodes at the which a host switch occurred. How many host switch events have there been over the history of this tree? Which host groups are major donors and which hosts are recipients? Which host switches have been the most successful, i.e., circulated for the longest or with the most diversity? Do different avian orders play different roles in H3 evolution and transmission? Which host order (anseriformes, galliformes, or neoaves) act more frequently as sources? 

6. As part of our reconstruction, we also inferred nucleotide and amino acid mutations on the internal nodes of the phylogeny. Zoom in on different branches of the tree by clicking on them. Take a look at some of the branches leading to host switches. We see that many of these host switch branches have amino acid changing mutations. If we want to filter the tree to color by mutations, under "Color By", select "Genotype" -> "HA", then the amino acid. Take for example site 179. Look at this site in the tree view and the scatterplot view. We can see that it is highly polymorphic in different host species. Without further data on phenotype, it is impossible to know whether this illicits an important change evolutionarily, but it is an interesting hypothesis that could be tested. 

7. Now let's look at geographic regions. Change the colorby view to "region" and take a look at the tree. How geographically structured are these populations? Are particular host groups restricted to particular geographic regions? Are viruses from some hosts more geographically widespread than others? Why might this be? As another fun way to visualize this, play around with the scatterplot view of the tree. To do this, look under `Tree`, `Scatter`, and select which variables you want on the x and y axes. 

8. Now, let's look at subtypes. Influenza viruses shuffle their genomes through a process called reassortment, which occurs when co-infecting virions co-infect the same cell. Reassortment is how HA and NA segments gets shuffled into new combinations (e.g., h3n1, h3n5, h3n8, etc...). Using the scatter plot view and the tree view, do particular hosts harbor more subtype diversity than others? If so, what does that tell us about infection frequency?

9. Although there is a lot we can learn by looking at just HA, we have sequences for the other 7 gene segments as well. Navigate to our lab [Nextstrain page](https://nextstrain.org/groups/moncla-lab/), and scroll down to the other gene segments. Start with PB2. Take a look at this phylogeny. It should look pretty different! That is because of reassortment. 

10. PB2 is a protein that plays an important role in host switching. PB2 interacts with host transcription machinery, and is responsible for flu's cap snatching behavior. It also mediates interactions with host restriction factors which often vary between avian and mammal species. One well-known mutation that mediates species specificity is PB2 E627K. An E is very common in birds, while a K is often selected in mammals. D701N is another mutation that provides a fitness advantage in mammals. Using the scatterplot view, select `Color By` and `Genotype`, and specify `PB2` and site `627`. Set the x-axis as `Host`, the y-axis as `Genotype PB2:627`, and turn off `show branches`. Now toggle back to the tree view. Is there evidence that these mutations have arisen multiple times in mammals? 

11. Let's take a look at the sequence form a recent human infection with an avian H3N8 virus. Under `Filter Data`type in the strain name `A/Guangdong/ZS-23SF005/2023`. Does this human harbor either of these known adaptive mutations? What about mutations in HA? 



### Other interesting uses of Nextstrain for outbreak analysis: 

The links below include "narratives". These interactive, online slide shows that walk through genomic analyses and discuss how genomes sampled from outbreaks have been used to reconstruct viral transmission. Anyone can make a narrative and share it online, and you can exit the narrative and explore the tree yourself by clicking on the right side of the screen on `EXPLORE THE DATA YOURSELF`. 

1. [Analysis of SARS-CoV-2 genomes from January 2020](https://nextstrain.org/ncov/2019#sit-reps). There are now millions of SARS-CoV-2 genomes that are publicly available. However, one remarkable feature of the pandemic was how rapidly people generated and shared viral genomes early on. Even back in January of 2020, there were already 24 SARS-CoV-2 genomes publicly available. This situation report was written by members of the Nextstrain team to provide an overview of the outbreak at that time, and analysis that showed human to human transmission was occurring. There are reports from the entire first 6 months of the outbreak, that are interesting to see. 

2. [Tracing the expansion of West Nile Virus into North America](https://nextstrain.org/narratives/twenty-years-of-WNV). This analysis traces the transmission of West Nile Virus into the US, and its dispersion across geographic space. 

3. [Ebola in the Democratic Republic of Congo](https://nextstrain.org/narratives/inrb-ebola-example-sit-rep). This narrative was put together by investigators in the DRC who sequenced local Ebola genomes from an outbreak, and build this narrative to disseminate their results. 


### Helpful links: 
Nextstrain documentation page: https://docs.nextstrain.org/en/latest/index.html
Github repository for Nextstrain: https://github.com/nextstrain



