# Smart Agriculture - Plant Disease Detection

An AI-powered web application for detecting plant diseases from images using machine learning and providing detailed analysis with treatment recommendations.

## Features

- 🌱 **Image Upload**: Drag & drop or click to upload plant images
- 🤖 **AI Detection**: Advanced machine learning model for disease identification
- 📊 **Detailed Analysis**: Comprehensive disease analysis with confidence scores
- 💊 **Treatment Recommendations**: Expert treatment and prevention advice
- 🧠 **LLM Integration**: Powered by OpenAI for detailed explanations
- 📱 **Responsive Design**: Works on desktop, tablet, and mobile devices

## Detectable Diseases

- Healthy Plants
- Bacterial Blight
- Brown Spot
- Leaf Smut
- Powdery Mildew
- Rust Disease
- Septoria Leaf Spot
- Yellow Leaf Disease
- Mosaic Virus
- Root Rot

## Technology Stack

### Backend
- **Flask**: Web framework
- **TensorFlow/Keras**: Machine learning model
- **OpenAI API**: LLM integration for detailed analysis
- **Pillow**: Image processing
- **OpenCV**: Computer vision

### Frontend
- **HTML5/CSS3**: Modern responsive design
- **Bootstrap 5**: UI framework
- **JavaScript**: Interactive functionality
- **Font Awesome**: Icons

## Installation

### Prerequisites
- Python 3.8 or higher
- pip (Python package installer)

### Setup Instructions

1. **Clone or download the project**
   ```bash
   cd "smart aggri"
   ```

2. **Create a virtual environment (recommended)**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables**
   - Copy `.env` file and update with your settings
   - Add your OpenAI API key for LLM integration:
     ```
     OPENAI_API_KEY=your_openai_api_key_here
     ```

5. **Create dummy model (for demonstration)**
   ```bash
   python3 create_dummy_model.py
   ```

6. **Run the application**
   ```bash
   python3 app.py
   ```

7. **Open your browser**
   - Navigate to `http://localhost:5000`
   - Upload a plant image and get instant disease detection!

## Project Structure

```
smart aggri/
├── app.py                 # Main Flask application
├── requirements.txt       # Python dependencies
├── .env                  # Environment configuration
├── README.md             # Project documentation
├── create_dummy_model.py  # Dummy model generator
├── model_trainer.py      # ML model training script
├── static/               # Static files
│   ├── css/
│   │   └── style.css     # Custom styles
│   ├── js/
│   │   └── main.js       # JavaScript functionality
│   └── images/           # Static images
├── templates/            # HTML templates
│   ├── base.html         # Base template
│   ├── index.html        # Homepage
│   └── about.html        # About page
├── models/               # ML models and info
│   ├── dummy_model.pkl   # Dummy model for demo
│   └── model_info.json   # Model metadata
└── uploads/              # Uploaded images
```

## Usage

### Basic Usage
1. Open the application in your browser
2. Upload an image of a plant, leaf, fruit, or vegetable
3. Click "Analyze Image" to get disease detection results
4. View detailed analysis, treatment, and prevention recommendations

### API Endpoints
- `GET /` - Homepage
- `POST /upload` - Upload and analyze image
- `GET /about` - About page

## Model Training

To train your own model with real data:

1. **Prepare your dataset**
   ```bash
   python3 model_trainer.py  # This creates the dataset structure
   ```

2. **Add your images**
   - Place images in `dataset/train/[disease_name]/`
   - Place validation images in `dataset/val/[disease_name]/`
   - Place test images in `dataset/test/[disease_name]/`

3. **Train the model**
   - Uncomment the training code in `model_trainer.py`
   - Run: `python3 model_trainer.py`

4. **The trained model will be saved as `models/plant_disease_model.h5`**

## LLM Fine-Tuning (Optional)

You can fine-tune the LLM to produce highly tailored, structured responses for plant disease analysis.

1. Generate the training dataset (chat JSONL):
   ```bash
   python3 llm_finetune.py
   ```
   - Outputs `models/llm_training.jsonl` and `models/llm_training_info.json`.

2. Submit the JSONL file to your preferred fine-tuning provider (e.g., an OpenAI fine-tuning job that accepts chat-format datasets).

3. Set the environment variable with the resulting model ID:
   ```bash
   export LLM_MODEL_ID="your_fine_tuned_model_id"
   ```

4. Restart the app. `llm_analyzer.py` will use `LLM_MODEL_ID` instead of the default model.

Notes:
- If no API key or fine-tuned model ID is available, the analyzer falls back to built-in domain guidance.
- The dataset contains examples for the disease classes listed in `app.py` and is aligned with the structured JSON keys the UI expects.

## Configuration

### Environment Variables
- `OPENAI_API_KEY`: Your OpenAI API key for LLM integration
- `FLASK_ENV`: Flask environment (development/production)
- `SECRET_KEY`: Flask secret key for sessions
- `MAX_CONTENT_LENGTH`: Maximum file upload size (default: 16MB)

### Model Configuration
- Input image size: 224x224 pixels
- Supported formats: PNG, JPG, JPEG, GIF, BMP
- Maximum file size: 16MB

## Development

### Adding New Disease Classes
1. Update `DISEASE_CLASSES` in `app.py`
2. Update `class_names` in `model_trainer.py`
3. Retrain the model with new data

### Customizing the UI
- Modify `static/css/style.css` for styling
- Update `templates/` for HTML structure
- Enhance `static/js/main.js` for functionality

## Deployment

### Local Development
```bash
python3 app.py
```

### Production Deployment
```bash
gunicorn -w 4 -b 0.0.0.0:5000 app:app
```

## Troubleshooting

### Common Issues

1. **Module not found errors**
   - Make sure you've activated your virtual environment
   - Install dependencies: `pip install -r requirements.txt`

2. **OpenAI API errors**
   - Check your API key in `.env` file
   - Ensure you have sufficient API credits

3. **Image upload issues**
   - Check file size (max 16MB)
   - Ensure supported format (PNG, JPG, JPEG, GIF, BMP)

4. **Model loading errors**
   - Run `python3 create_dummy_model.py` to create demo model
   - For production, train your own model with real data

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is open source and available under the MIT License.

## Support

For support and questions:
- Check the troubleshooting section
- Review the code documentation
- Create an issue for bugs or feature requests

## Acknowledgments

- TensorFlow team for the ML framework
- OpenAI for LLM capabilities
- Bootstrap team for the UI framework
- Plant pathology experts for disease classification guidance

---

**Happy Farming! 🌱**
## Run in Visual Studio Code

This project includes VS Code configuration to run and debug easily.

### Prerequisites
- VS Code with the Python extension installed
- Python 3.10+ recommended

### Setup
1. Open the workspace folder in VS Code: `smart aggriculture` (root directory).
2. Run the task "Python: Create venv" and then "Python: Install requirements" from the VS Code Command Palette (Tasks: Run Task).
3. Ensure the interpreter is set to `${workspaceFolder}/.venv/bin/python` (VS Code will pick it from `.vscode/settings.json`).
4. Configure environment variables in `smart aggri/.env` if needed.

### Start the App
Use one of the provided debug configurations (Run and Debug panel):
- "Python: Flask (app_simple)" — runs `flask run` on port 5001.
- "Python: Run app_simple.py" — runs the app directly with the integrated terminal.

The app will start on `http://127.0.0.1:5001`.

### Notes
- Marketplace data is stored in `smart aggri/models/marketplace.json`.
- Uploaded images are saved under `smart aggri/uploads/` and served via `/uploads/<filename>`.
 - If you want to change the port, update `FLASK_RUN_PORT` in `.vscode/launch.json` and `.vscode/tasks.json`.

## VS Code Workspace

- A workspace file `smart-aggri.code-workspace` is included. Open via `File -> Open Workspace...`.
- The workspace sets `python.defaultInterpreterPath` to `${workspaceFolder}/.venv/bin/python` and hides `__pycache__`.
- Recommended extensions are declared in `.vscode/extensions.json`.

## Makefile (optional but convenient)

- Common tasks via `make` from the project root:
  - `make venv` — Create a virtual environment in `.venv`.
  - `make install` — Install dependencies from `smart aggri/requirements.txt`.
  - `make run` — Start Flask via `flask run` using `app_simple:app` on port `5001`.
  - `make run-simple` — Run `smart aggri/app_simple.py` directly.
  - `make run-app` — Run `smart aggri/app.py` directly.
  - `make lint` — Run `pylint smart aggri` if installed.
  - `make format` — Run `black smart aggri` if installed.
  - `make clean` — Remove `.venv` and `__pycache__` directories.

Notes:
- Paths with spaces are quoted in the Makefile (e.g., `"smart aggri"`).
- `lint` and `format` will skip if the tools aren’t installed.
