# # Lab assignment #2 Database Design and Implementation

# if no module found, install using this command: !pip install network
import networkx as nx

# if no module found, install using this command: !pip install matplotlib
import matplotlib.pyplot as plt

# create graph to represent the social network of students and their connections
G = nx.Graph()

# student list
students = ["Alice", "Bob", "Charlie", "David", "Eve", "Frank", "Grace"]

# add students as nodes to the graph
G.add_nodes_from(students)

print(students)

# list of connections between students, represents a connection between two students
connections = [
    ("Alice", "Bob"),
    ("Alice", "Charlie"),
    ("Bob", "Charlie"),
    ("Bob", "David"),
    ("Charlie", "David"),
    ("Charlie", "Eve"),
    ("David", "Eve"),
    ("Eve", "Frank"),
    ("Frank", "Grace"),
    ("Grace", "Eve")
]

# add connections as edges to the graph
G.add_edges_from(connections)

print(connections)

# print basic information about the graph
print("Nodes of the graph:", G.nodes())
print("Edges of the graph:", G.edges())
print("Number of Nodes:", G.number_of_nodes())
print("Number of edges:", G.number_of_edges())

# visualize network
nx.draw(G, with_labels=True, font_weight='bold', node_color='skyblue', node_size=1000, edge_color='gray')
plt.title("Social Network Graph Model")
plt.show()

# centrality means a network is directly connected to many others ( degree centrality)
degree_centrality = nx.degree_centrality(G)
print("/nDegree Centrality:")
for students, centrality in degree_centrality.items():
    print(f"{students}: {centrality:.2f}")

# serve as a key broker between many other nodes (betweenness centrality)
betweeness_centrality = nx.betweenness_centrality(G)
print("/nBetweeness Centrality:")
for student, centrality in degree_centrality.items():
   print(f"{student}: {centrality:.2f}")

# close to many others indirectly (closeness centrality)
closeness_centrality = nx.closeness_centrality(G)
print("/nCloseness Centrality:")
for student, centrality in closeness_centrality.items():
   print(f"{student}: {centrality:.2f}")
