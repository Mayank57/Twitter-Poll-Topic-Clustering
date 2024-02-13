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
primarily in English and deduplicate. Furthermore,
we identify columns that are NaN (or any single-
value) throughout, thereby providing us with no
informative meta-data. In an attempt to incorporate the date of posting of the poll, we provide a
provision to append Timestamp to the poll before
generating Embeddings.

Text Extraction

Text was extracted from the Twitter polls data for
analysis. This step involves pulling out the relevant textual information from the polls, which is
essential for further processing and analysis. Since
there might be a lot of spam tweet polls as well, hence we consider only those texts which have
been retweeted. Post this, all the texts have been
cleaned, and then passed to the embeddings func-
tion.

Text Embedding

Applied Sentence Transformers, which internally
use the BERT architecture, to generate embeddings from the resulting texts. This process involves converting text data into numerical form
(embeddings) that capture the semantic meanings of the words and sentences. These embed-
dings were projected onto a 384-dimensional vector space. This high-dimensional space allows for
a detailed representation of the text data.

Clustering

Clustering is a technique used to group similar
items together. In this context, it helps to identify
polls with similar themes or topics.

K-Means Clustering is an unsupervised machine
learning algorithm designed to group data points
into k clusters based on similarity. The algorithm iteratively assigns data points to clusters by
minimizing the Euclidean distance to the centroid
of each cluster, then updates the centroids as the
mean of the assigned points. K-Means is computationally efficient and commonly used in appli-
cations such as customer segmentation and image
compression. However, it has limitations, including sensitivity to initializations and assumptions
about cluster shapes and sizes. The algorithm’s
success relies on determining an appropriate number of clusters (k) and addressing these limitations
for optimal results.

Hierarchical Clustering organizes data points into
a tree-like structure, or hierarchy, based on their
similarities. It does so by iteratively merging or
dividing clusters until a dendrogram is formed, revealing relationships at different levels of granularity. This method provides a visual representation of the data’s inherent structure and doesn’t
require specifying the number of clusters beforehand, offering flexibility in analysis. We use this
to introspect the relations between the clusters. We
use the following algorithms for the same

Agglomerative Clustering is a bottom-up hierarchical clustering algorithm. It starts by considering each data point as a separate cluster and then
iteratively merges the closest clusters until a single cluster encapsulates all the data points. The
process continues until a desired number of clusters is reached. This method is flexible and does
not require specifying the number of clusters in
advance.

Hierarchical Density-Based Spatial Clustering
of Applications with Noise is a density-based clustering algorithm that identifies clusters of varying
shapes and densities in data. It utilizes a hierarchical approach to form clusters while handling
noise and outliers effectively. HDBScan determines cluster sizes dynamically and does not require specifying the number of clusters beforehand. This makes it well-suited for datasets with
irregular structures and varying cluster densities.

Analysis

Our main aim is to find order in the chaos, as in
separating the raw data into meaningful clusters.
Having separated the data into clusters, and we
find ways to find information about the clusters.
5.5.1 Brute-Force Analysis
We look at the clusters, and label the clusters with
whatever the inspector (i.e us) feel the overarching theme is. A cluster is labeled only when it is
apparent that the cluster does, indeed make sense.

Qualitative Analysis

After having labeled the clusters, we provide a
discussion analysing the meaning of the clusters
- what they must have meant in the context of August 2021, and in that of the social media landscape, and how relevant topic clusters help us in
trend identification.

Intruder Tests

We sample 50 samples from each cluster and
manually label each sample as ”Belongs” or ”Intruder”. The ratio of Intruders to the total samples
in the cluster is the Intruder Ratio. This acts as a
proxy stability analysis of the clusters.

Topic Modeling

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

Comparisons between Clustering Algo

We provide the clusters labels for three clustering algorithms - qualitatively compare their quality with each other. We identify Pros and Cons for
each of the three
