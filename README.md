# Twitter-Poll-Topic-Clustering

We prepare an automated algorithm that can
classify Twitter polls based on their topic or
subject matter, and comparing the relevance of
certain topics in public discourse. This could
allow us to determine the level of relevance of
certain topics in public discourse and see how
these patterns change over time for different
topics

Techniques and methods

Data Preprocessing

As mentioned in Data, we keep Tweets that are pri-
marily in English and deduplicate. Furthermore,
we identify columns that are NaN (or any single-
value) throughout, thereby providing us with no
informative meta-data. In an attempt to incorpor-
tate the date of posting of the poll, we provide a
provision to append Timestamp to the poll before
generating Embeddings.

Text Extraction

Text was extracted from the Twitter polls data for
analysis. This step involves pulling out the rel-
evant textual information from the polls, which is
essential for further processing and analysis. Since
there might be a lot of spam tweet polls as well,
hence we consider only those texts which have
been retweeted. Post this, all the texts have been
cleaned, and then passed to the embeddings func-
tion.

5.3 Text Embedding

Applied Sentence Transformers, which internally
use the BERT architecture, to generate embed-
dings from the resulting texts. This process in-
volves converting text data into numerical form
(embeddings) that capture the semantic mean-
ings of the words and sentences. These embed-
dings were projected onto a 384-dimensional vec-
tor space. This high-dimensional space allows for
a detailed representation of the text data.

5.4 Clustering

Clustering is a technique used to group similar
items together. In this context, it helps to identify
polls with similar themes or topics.

K-Means Clustering
K-Means Clustering is an unsupervised machine
learning algorithm designed to group data points
into k clusters based on similarity. The algo-
rithm iteratively assigns data points to clusters by
minimizing the Euclidean distance to the centroid
of each cluster, then updates the centroids as the
mean of the assigned points. K-Means is compu-
tationally efficient and commonly used in appli-
cations such as customer segmentation and image
compression. However, it has limitations, includ-
ing sensitivity to initializations and assumptions
about cluster shapes and sizes. The algorithm’s
success relies on determining an appropriate num-
ber of clusters (k) and addressing these limitations
for optimal results.

Hierarchical Clustering
Hierarchical Clustering organizes data points into
a tree-like structure, or hierarchy, based on their
similarities. It does so by iteratively merging or
dividing clusters until a dendrogram is formed, re-
vealing relationships at different levels of granu-
larity. This method provides a visual representa-
tion of the data’s inherent structure and doesn’t
require specifying the number of clusters before-
hand, offering flexibility in analysis. We use this
to introspect the relations between the clusters. We
use the following algorithms for the same

Agglomerative Clustering
Agglomerative Clustering is a bottom-up hier-
archical clustering algorithm. It starts by consid-
ering each data point as a separate cluster and then
iteratively merges the closest clusters until a sin-
gle cluster encapsulates all the data points. The
process continues until a desired number of clus-
ters is reached. This method is flexible and does
not require specifying the number of clusters in
advance.

HDBScan
Hierarchical Density-Based Spatial Clustering
of Applications with Noise is a density-based clus-
tering algorithm that identifies clusters of varying
shapes and densities in data. It utilizes a hierar-
chical approach to form clusters while handling
noise and outliers effectively. HDBScan deter-
mines cluster sizes dynamically and does not re-
quire specifying the number of clusters before-
hand. This makes it well-suited for datasets with
irregular structures and varying cluster densities.

Analysis

Our main aim is to find order in the chaos, as in
separating the raw data into meaningful clusters.
Having separated the data into clusters, and we
find ways to find information about the clusters.
5.5.1 Brute-Force Analysis
We look at the clusters, and label the clusters with
whatever the inspector (i.e us) feel the overarch-
ing theme is. A cluster is labeled only when it is
apparent that the cluster does, indeed make sense.
5.5.2 Qualitative Analysis
After having labeled the clusters, we provide a
discussion analysing the meaning of the clusters
- what they must have meant in the context of Au-
gust 2021, and in that of the social media land-
scape, and how relevant topic clusters help us in
trend identification.
5.5.3 Intruder Tests
We sample 50 samples from each cluster and
manually label each sample as ”Belongs” or ”In-
truder”. The ratio of Intruders to the total samples
in the cluster is the Intruder Ratio. This acts as a
proxy stability analysis of the clusters.
5.5.4 Topic Modeling
We tried to use several ways to assign labels, as to
what themes or topics are present, to the clusters
formed with unsupervised clustering algorithms.
Smaller models like BERT and RoBERTa do not
provide good results (as is evident by eye). On the
other hand, LLMs provide adequate results. We
present Topics as labeled by LLMs (one of us has
a GPT+ subscription) against the topics that were
labelled manually. As the API key is expensive,
we do not provide it in the implementation, and
hence replicating these might not be possible.
5.5.5 Comparisons between Clustering Algo
We provide the clusters labels for three cluster-
ing algorithms - qualitatively compare their qual-
ity with each other. We identify Pros and Cons for
each of the three
