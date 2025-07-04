# Sound Clustering with HMMs

This project demonstrates unsupervised clustering of unlabeled sound data using feature extraction, dimensionality reduction, and clustering algorithms. The workflow includes extracting Mel spectrogram features from audio files, reducing dimensionality with PCA and t-SNE, and applying clustering methods such as K-Means and DBSCAN. The results are evaluated and visualized to understand the structure and separability of the sound data.

## Dataset

The dataset consists of `.wav` audio files, which were extracted to a local directory (`unlabelled_sounds`) for processing. This allowed direct access to the files for feature extraction and analysis.

## Workflow

1. **Feature Extraction:**  
   - Mel spectrogram features are extracted from each audio file using `librosa`.
   - The mean of each Mel frequency band is used as the feature vector for each file.

2. **Dimensionality Reduction:**  
   - High-dimensional feature vectors (128 dimensions) are reduced using:
     - **PCA (Principal Component Analysis):** Captures directions of maximum variance.
     - **t-SNE (t-distributed Stochastic Neighbor Embedding):** Preserves local structure and reveals nonlinear clusters.
   - Standardization is applied before reduction.

3. **Clustering:**  
   - **K-Means:** Finds clusters assuming convex, similarly sized groups.
   - **DBSCAN:** Detects clusters of arbitrary shape and identifies noise/outliers.

4. **Evaluation & Visualization:**  
   - Clustering quality is assessed using silhouette and Davies-Bouldin scores.
   - Results are visualized in 2D/3D scatter plots.

## Key Findings

- **Dimensionality reduction** is essential for visualizing and clustering high-dimensional audio features. It highlights the most important structure and removes noise.
- **t-SNE** provided better cluster separability in visualizations compared to PCA, especially for complex, nonlinear groupings.
- **K-Means** performed better than DBSCAN on the PCA-reduced data, producing clear, well-separated clusters.
- **DBSCAN** was able to identify noise and clusters of varying density but was more sensitive to parameter choices and less robust when clusters were not well-separated.
- Real-world audio clustering is challenging due to high dimensionality and noise; proper preprocessing and algorithm selection are critical.

## Requirements

- Python 3.x
- `librosa`
- `numpy`
- `pandas`
- `matplotlib`
- `seaborn`
- `scikit-learn`
- `tqdm`

Install requirements with:
```bash
pip install librosa numpy pandas matplotlib seaborn scikit-learn tqdm
```

## Usage

1. Place your `.wav` files in the `unlabelled_sounds` directory.
2. Run the Jupyter notebook `clustering_notebook.ipynb` step by step.
3. Visualizations and evaluation metrics will be displayed for each stage.

---

**Note:** The dataset was extracted locally to enable direct access to the audio files for feature extraction and