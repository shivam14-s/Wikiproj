Name: Shivam Shrivastava
ID No.: 12041400

The .pynb file will take some time to load because its 60mb in size.
The files new_dataframe , a_bit are temporary files we used during the data extraction
The webscraping codes are also attached in the zip folder.
scraping of the data: 
we used about 1000 nodes of each of the major topics like trigonometry, algebra, etc and did a BFS traversal to generate our dataset.
for each page we extract first 12 p tags and all the valid out links from that page(the ones not with %,user,identifier, etc in their links), page title and page link. We then store all the data in a file called b_bit.csv.

Class Vertex:  #nodes of the graph
for each node it stores label, link, neighbour_list, keyword from the text, NLP features(BOW, TFIDF), degree centrality, tags
and clustering cofficient. The keywords of the node are the top 10 words with the highest TF_IDF score. The top 5 of these words we have considered as tags for the link.


Class Graph:    #stores the Graph
stores the vertices(vert_dict) and links(keys of the dictionary) as a dictionary.
The graph class has functions which are used to structure the vertices and link them. Comments have been added in the jupyter file after each function.

NLP: We used the concepts of feature extraction as taught to us by Anirban Sir in the NLP tutorial and created two feature vectors and stored them as attributes to the nodes of the graph. 
1: bag of words feature vector
2:TF_IDf feature vetor

Labeling of the data:
We used the output.csv file sent to us from Anirban Sir and we extracted their top 10 <p> for creating the feature vector for those LABELLED nodes

Initially our whole graph was unlabelled and none of our nodes matched to the nodes in the output.csv file. So, we extracted the text and created feature vectors for all the links in the output.csv file. We stored a list(label_lst) of these labelled nodes with their feature vectors.

then we compared the dot product of each of our nodes with all the labelled nodes and the most similar node gets the tag of that labeled node.
the graph neural network cannot be applied here as the graph is quite large and the labeled data is quite small dued to which many wrongly labeled nodes will  be assigned.
instead by comparing as above mentioned will give a better labeling to the nodes.

node ordering(Article ordering algorithm):
For article ordering we are using a modified DFS algorithm on a sub graph. The algorithm takes a topic name as input from the user and searches for the corresponding link in our dataset. If found the algorithm returns the link with the lowest(easiest) label value and moves on to the next level in the graph. We do this process for 10 levels and we get 10 links to read after our topic.
We have also implemented a modified BFS to show the top 10 directly attached nodes to our topic instead of 10 levels deep. If there aren't 10 nodes directly attached we go to the next level and start the same process with the node having the least label value.

