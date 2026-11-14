This notebook explores community detection in Zachary's Karate Club network using the spectral modularity method described by Newman (2006).

I start by constructing the modularity matrix, $B = A - kk^T/2m$, and then divide the network into smaller groups using the signs of the leading eigenvector of each group's restricted modularity matrix. The matrix also includes Newman's diagonal correction, which allows the modularity gain from each split to be calculated accurately.

At every step, the group with the highest modularity gain is chosen for splitting. If the leading eigenvector does not produce a meaningful division because all its entries have the same sign, the code checks the second and then the third eigenvector.

According to the assignment instructions, the process should stop when $\lambda_1 \leq 0$, resulting in five communities. However, I continued the process up to seven communities to explore the smaller friendship groups in more detail. The results show that these additional splits do not improve the overall community structure. The modularity score is highest at around 0.393 with four communities and decreases to around 0.352 with seven communities.

### What the notebook produces

- A graph visualisation at each iteration, using the same spring layout throughout so that the positions of the nodes remain unchanged. Friendships within a community and those connecting different communities are shown using different styles, making it easier to distinguish between them.
- Plots showing how the degree, betweenness and closeness centralities, along with the clustering coefficient, change for each member after every split. These values are calculated within each member's community and compared with their values in the original network.

### Findings

The first split correctly identifies the original division of the club for 33 out of 34 members. Members 1, 34, 3, 33 and 32 remain among the most central members throughout the process.

### Use of AI

Claude was used to help write and organise parts of the code, particularly the recursive community-splitting process, NetworkX graph visualisations and multi-panel plots for comparing network metrics.
