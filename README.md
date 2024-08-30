AI-Driven Metadata Tagging for Large Image Collections
This project compares the effectiveness of Google Cloud Vision, Microsoft Azure Computer Vision, and Amazon Rekognition in generating metadata tags for diverse image categories. It aims to inform the integration of AI technologies in digital asset management practices for organizations dealing with large image collections.
Background
Initially intended to use datasets from the Special Collection Unit at the Institute of Ismaili Studies, London, and the British Cultural Archives, London, the study pivoted to a carefully curated public dataset due to institutional challenges. This shift highlights broader issues in the cultural heritage sector regarding data privacy, ethical considerations, and digital infrastructure.
Features

Evaluates AI performance across multiple image categories: People, Art and Creative Craft, Scenes of Daily Life, Nature, Objects, Text and Documents, and Urban and Rural Settings
Calculates quantitative metrics: precision, recall, F1 score, and accuracy
Provides qualitative analysis of tag relevance and contextual appropriateness
Compares AI-generated tags against custom controlled vocabularies

Requirements

Python 3.8+
NumPy
pandas
matplotlib
seaborn
scikit-learn
NetworkX

Installation

Clone this repository:
Copygit clone https://github.com/khalidxansari/dissertation-code.git

Install the required packages:
Copypip install -r requirements.txt


Usage

Prepare your image dataset and controlled vocabularies.
Update the config.py file with your API keys for Google Cloud Vision, Microsoft Azure Computer Vision, and Amazon Rekognition.
Run the main script:
Copypython main.py

The script will process the images, generate tags using each AI service, and produce performance metrics and visualizations.

Key Findings

Performance varied significantly across image categories and AI services.
Microsoft Azure generally performed best for 'People' and 'Daily Life Scenes'.
Amazon Rekognition excelled in 'Urban and Rural Settings'.
All services struggled with 'Text and Documents'.
AI services showed high precision but low recall, indicating accurate but incomplete tagging.

Visualizations
The project generates several types of visualizations:

Bar plots comparing metrics across AI services
Network graphs showing relationships between AI-generated tags and controlled vocabulary terms
Heatmaps illustrating performance across different image categories

Limitations and Future Work

The public dataset may not fully capture the nuances of institutional collections.
Further research is needed on custom AI models, federated learning approaches, and user interfaces for human-AI collaboration.
Long-term impacts of AI-generated metadata on cultural heritage preservation and access require investigation.

Contributing
Contributions are welcome! Please feel free to submit a Pull Request.
License
This project is licensed under the MIT License - see the LICENSE file for details.
Acknowledgments
Special thanks to Dr. Hannah Ishmael, Dr. Laura Gibson, Dr. Daniel Chávez Heras, Dr. David Young, and Dr. Erik Ketzan for their guidance and support throughout this research.
