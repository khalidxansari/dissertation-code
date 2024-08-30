AI-Driven Metadata Tagging for Image Collections
This project evaluates the performance of Google Cloud Vision, Microsoft Azure Computer Vision, and Amazon Rekognition in generating metadata tags for diverse image categories.
1. Libraries Used
NumPy

Purpose: Numerical operations and array manipulations
Usage: Calculating mean scores, handling multi-dimensional data structures

scikit-learn

Purpose: Machine learning tools, including metric calculations
Usage: Computing precision, recall, F1 score, and accuracy metrics

Matplotlib and Seaborn

Purpose: Data visualization
Usage: Creating bar plots, heatmaps, and other visualizations to represent performance metrics

NetworkX

Purpose: Creating and manipulating complex networks
Usage: Visualizing relationships between AI-generated tags and controlled vocabulary terms

Pandas

Purpose: Data manipulation and analysis
Usage: Organizing and structuring performance data for analysis and visualization

2. Code Examples
Calculating Performance Metrics
pythonCopyfrom sklearn.metrics import precision_score, recall_score, f1_score, accuracy_score

def calculate_metrics(y_true, y_pred):
    precision = precision_score(y_true, y_pred, average='weighted', zero_division=0)
    recall = recall_score(y_true, y_pred, average='weighted', zero_division=0)
    f1 = f1_score(y_true, y_pred, average='weighted', zero_division=0)
    accuracy = accuracy_score(y_true, y_pred)
    return precision, recall, f1, accuracy

# Usage
precision, recall, f1, accuracy = calculate_metrics(ground_truth_tags, ai_generated_tags)
Visualizing Performance Across Categories
pythonCopyimport matplotlib.pyplot as plt
import seaborn as sns

def plot_performance_heatmap(performance_data, categories, metrics):
    plt.figure(figsize=(12, 8))
    sns.heatmap(performance_data, annot=True, cmap='YlGnBu', 
                xticklabels=categories, yticklabels=metrics)
    plt.title('AI Service Performance Across Image Categories')
    plt.tight_layout()
    plt.show()

# Usage
performance_data = np.array([precision_scores, recall_scores, f1_scores, accuracy_scores])
categories = ['People', 'Art', 'Nature', 'Objects', 'Text', 'Urban/Rural']
metrics = ['Precision', 'Recall', 'F1 Score', 'Accuracy']
plot_performance_heatmap(performance_data, categories, metrics)
Network Graph of Tag Relationships
pythonCopyimport networkx as nx

def create_tag_network(ai_tags, controlled_vocab):
    G = nx.Graph()
    for ai_tag in ai_tags:
        for cv_tag in controlled_vocab:
            if ai_tag.lower() in cv_tag.lower():
                G.add_edge(ai_tag, cv_tag)
    return G

def plot_tag_network(G):
    plt.figure(figsize=(12, 8))
    pos = nx.spring_layout(G)
    nx.draw(G, pos, with_labels=True, node_color='lightblue', 
            node_size=3000, font_size=8, font_weight='bold')
    plt.title('AI-Generated Tags vs. Controlled Vocabulary')
    plt.axis('off')
    plt.tight_layout()
    plt.show()

# Usage
G = create_tag_network(ai_generated_tags, controlled_vocabulary)
plot_tag_network(G)
3. Adapting Code for Different Categories
The code was designed to be flexible and adaptable for different image categories. Here's how it was adjusted:
Category-Specific Controlled Vocabularies
pythonCopycontrolled_vocab = {
    'People': ['Group photo', 'Portrait', 'Facial expression', 'Age', 'Gender', 'Ethnicity'],
    'Art': ['Painting', 'Sculpture', 'Style', 'Medium', 'Artist', 'Period'],
    'Nature': ['Landscape', 'Flora', 'Fauna', 'Weather', 'Geographical features'],
    'Objects': ['Household items', 'Tools', 'Technology', 'Vehicles', 'Artifacts'],
    'Text': ['Document type', 'Language', 'Script', 'Content type'],
    'Urban/Rural': ['Architecture', 'Infrastructure', 'Settlement type', 'Land use']
}

def evaluate_category(category, ai_tags):
    category_vocab = controlled_vocab[category]
    y_true = [1 if tag in category_vocab else 0 for tag in category_vocab]
    y_pred = [1 if tag in ai_tags else 0 for tag in category_vocab]
    return calculate_metrics(y_true, y_pred)

# Usage
for category in categories:
    precision, recall, f1, accuracy = evaluate_category(category, ai_generated_tags)
    # Store or process results
Customizing Visualization for Each Category
pythonCopydef plot_category_performance(category, metrics):
    plt.figure(figsize=(10, 6))
    plt.bar(metrics.keys(), metrics.values())
    plt.title(f'Performance Metrics for {category}')
    plt.ylabel('Score')
    plt.ylim(0, 1)
    plt.tight_layout()
    plt.show()

# Usage
for category in categories:
    metrics = {
        'Precision': precision_scores[category],
        'Recall': recall_scores[category],
        'F1 Score': f1_scores[category],
        'Accuracy': accuracy_scores[category]
    }
    plot_category_performance(category, metrics)
This structure allows for easy adaptation to different image categories by modifying the controlled vocabularies and adjusting the evaluation and visualization functions as needed for each specific category.


