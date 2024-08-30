AI-Driven Metadata Tagging Comparison
This project compares the performance of Google Cloud Vision, Microsoft Azure Computer Vision, and Amazon Rekognition in generating metadata tags for diverse image categories. The code utilizes various Python libraries for data processing, statistical analysis, and visualization.
Key Libraries and Their Usage
Data Processing and Analysis

NumPy: Used for numerical operations and array manipulations.
pythonCopyimport numpy as np

# Example: Calculate mean precision across categories
mean_precision = np.mean(precision_scores)

pandas: Employed for data manipulation and analysis.
pythonCopyimport pandas as pd

# Example: Create a DataFrame of results
results_df = pd.DataFrame({
    'Category': categories,
    'Precision': precision_scores,
    'Recall': recall_scores,
    'F1 Score': f1_scores
})

scikit-learn: Utilized for calculating performance metrics.
pythonCopyfrom sklearn.metrics import precision_score, recall_score, f1_score, accuracy_score

# Example: Calculate metrics for each AI service
precision = precision_score(y_true, y_pred, average='weighted')
recall = recall_score(y_true, y_pred, average='weighted')
f1 = f1_score(y_true, y_pred, average='weighted')


Visualization

matplotlib: Used for creating various plots and charts.
pythonCopyimport matplotlib.pyplot as plt

# Example: Create a bar plot
plt.figure(figsize=(10, 6))
plt.bar(categories, precision_scores)
plt.title('Precision Scores by Category')
plt.xlabel('Category')
plt.ylabel('Precision')
plt.show()

seaborn: Employed for statistical data visualization.
pythonCopyimport seaborn as sns

# Example: Create a heatmap
plt.figure(figsize=(12, 8))
sns.heatmap(performance_matrix, annot=True, cmap='YlGnBu')
plt.title('Performance Heatmap')
plt.show()

NetworkX: Used for creating network graphs.
pythonCopyimport networkx as nx

# Example: Create a network graph
G = nx.Graph()
G.add_edges_from(tag_relationships)
pos = nx.spring_layout(G)
nx.draw(G, pos, with_labels=True)
plt.title('Tag Relationship Network')
plt.show()


API Interaction

requests: Used for making HTTP requests to AI service APIs.
pythonCopyimport requests

# Example: Send request to API
response = requests.post(api_url, headers=headers, json=payload)


Additional Utilities

json: Used for parsing JSON responses from APIs.
pythonCopyimport json

# Example: Parse JSON response
result = json.loads(response.text)

os: Utilized for file and directory operations.
pythonCopyimport os

# Example: Iterate through image files
for filename in os.listdir(image_directory):
    if filename.endswith(('.jpg', '.png', '.jpeg')):
        process_image(os.path.join(image_directory, filename))


Installation

Clone this repository:
Copygit clone https://github.com/yourusername/ai-metadata-tagging-comparison.git

Install the required packages:
Copypip install -r requirements.txt


Usage

Set up your API credentials in a config.py file.
Run the main script:
Copypython main.py


This will process the images, generate tags using each AI service, calculate performance metrics, and create visualizations.
Contributing
Contributions are welcome! Please feel free to submit a Pull Request.
License
This project is licensed under the MIT License - see the LICENSE file for details.
