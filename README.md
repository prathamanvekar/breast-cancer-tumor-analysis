# BreastCancer Tumor Analysis System

Hybrid deep learning model for segmentation and size estimation of breast cancer tumors in histopathology images using HoVerNet and Graph Neural Networks.

## Features

- **Nucleus Segmentation**: HoVerNet-based identification and segmentation of individual cell nuclei
- **Spatial Analysis**: Graph Neural Network (GNN) analysis of cell density patterns and structural relationships
- **Tumor Size Estimation**: Automated measurement and estimation of tumor area
- **Web Interface**: User-friendly Flask web application for uploading and analyzing histopathology images
- **Explainability**: XAI heatmaps highlighting critical decision regions
- **Model Comparison**: Performance comparison with CNN, RNN, and ResNet algorithms

## Tech Stack

- **Frontend**: HTML, CSS, JavaScript
- **Backend**: Flask (Python)
- **Deep Learning**: PyTorch, TorchVision
- **Image Processing**: OpenCV, Pillow, SciPy
- **Hardware**: GPU-optimized (CUDA support)

## Prerequisites

- Python 3.8+
- CUDA 11.8+ (optional, for GPU acceleration)
- pip or conda

## Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/yourusername/breast-cancer-tumor-analysis.git
   cd breast-cancer-tumor-analysis
   ```

2. **Create a virtual environment** (recommended)

   ```bash
   # Using venv
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate

   # Or using conda
   conda create -n tumor-analysis python=3.10
   conda activate tumor-analysis
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Download the pre-trained model**
   - Download `hovernet_gnn_model_FIXED.pth` and place it in the `models/` directory
   - [Model Download Link](https://your-link-here)

## Project Structure

```
├── app.py                          # Flask application entry point
├── breast-tumor-full-code-new.ipynb  # Training and analysis notebook
├── requirements.txt                # Python dependencies
├── models/
│   └── hovernet_gnn_model_FIXED.pth  # Pre-trained model weights
├── static/
│   ├── css/
│   │   └── style.css              # Web interface styling
│   ├── js/
│   │   └── main.js                # Frontend logic
│   ├── plots/                     # Generated visualization plots
│   └── uploads/                   # Uploaded histopathology images
├── templates/
│   └── index.html                 # Web interface HTML
└── results/
    ├── hovernet_gnn_results.json  # Analysis results
    ├── model_comparison.csv       # Model performance comparison
    └── test_results.json          # Test set results
```

## Usage

### Running the Web Application

1. **Start the Flask server**

   ```bash
   python app.py
   ```

2. **Access the application**
   - Open your browser and navigate to `http://localhost:5000`
   - Upload a histopathology image (PNG, JPG, JPEG)
   - The model will analyze and display:
     - Nucleus segmentation masks
     - Cell density classification (Low/Medium/High)
     - Tumor size estimation
     - Explainability heatmaps
     - Performance metrics and model comparisons

### Image Requirements

- **Format**: PNG, JPG, JPEG
- **Maximum Size**: 16 MB
- **Recommended Resolution**: 512x512 pixels or higher
- **Type**: Histopathology images (H&E stained recommended)

## Model Details

### HoVerNet Architecture

- ResNet34-based encoder-decoder architecture
- Nucleus boundary (Hover) map prediction
- Cell-type classification (Low/Medium/High density)

### Graph Neural Network

- Cell nodes connected by spatial relationships
- Analyzes tumor microenvironment structure
- Identifies irregular cell distribution patterns

## Results

The application generates and displays:

- **Segmentation Masks**: Visual overlay of detected nuclei
- **Density Maps**: Spatial distribution of cell density
- **Performance Metrics**: Confusion matrix, accuracy, ROC curves
- **Model Comparison**: Benchmarking against traditional deep learning models

## API Endpoints

- `GET /` - Web interface
- `POST /analyze` - Submit image for analysis
  - Returns: Segmentation results, density classification, tumor size estimate, heatmaps
- `GET /static/<path:filename>` - Serve static assets

## Performance

- **Speed**: ~500ms-2s per image (GPU-accelerated)
- **Accuracy**: Achieves superior performance vs. CNN/RNN/ResNet baselines
- **GPU Memory**: ~4GB recommended for batch processing

## Results & Metrics

View performance comparisons in:

- `results/model_comparison.csv` - Comparative analysis
- `results/hovernet_gnn_results.json` - Detailed metrics
- `results/test_results.json` - Test set evaluation

## Future Enhancements

- Batch image processing
- REST API for integration
- Real-time model inference optimization
- Multi-GPU support
- Docker containerization
- Explainability dashboard improvements

## Troubleshooting

**Issue**: CUDA out of memory

- **Solution**: Reduce batch size or use CPU mode

**Issue**: Model weights not found

- **Solution**: Ensure `models/hovernet_gnn_model_FIXED.pth` exists in the models directory

**Issue**: Port 5000 already in use

- **Solution**: `python app.py --port 5001` or stop the conflicting process

## References

- HoVerNet: [Deep Instance Segmentation of Tissues via Boundary-assisted Domain Shift and Self-supervised Learning](https://arxiv.org/abs/2004.00314)
- Graph Neural Networks: [A Comprehensive Survey on Graph Neural Networks](https://arxiv.org/abs/1901.00596)

## License

This project is licensed under the MIT License - see LICENSE file for details.

## Contact & Support

For questions or issues, please open a GitHub issue or contact the development team.

---

**Note**: This system is designed for research and educational purposes. Always consult with medical professionals for clinical applications.
