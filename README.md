
# Timetable Generator API 🗓️

This FastAPI-based application allows users to upload a PDF containing course registration details, extract course codes, and generate a personalized class timetable in Excel format. It also provides functionality to create and download a timetable based on the extracted course codes.



---

## Features

- **PDF Course Code Extraction**: Extract course codes from a PDF file.
- **Timetable Generation**: Generate a personalized timetable based on the extracted course codes.
- **Excel Export**: Export the generated timetable as an Excel file.
- **FastAPI Backend**: A fast and scalable backend built with FastAPI.
- **Pydantic Models**: Ensures type safety and validation for API requests and responses.

---

## Installation

To run the Timetable Generator API locally, follow these steps:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/timetable-generator.git
   cd timetable-generator
   ```

2. **Set up a virtual environment** (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the FastAPI application**:
   ```bash
   uvicorn app:app --reload
   ```

5. **Access the API**:
   Open your browser and navigate to `http://127.0.0.1:8000/docs` to access the Swagger UI for API documentation.

---

## API Endpoints

### 1. **Upload Course Registration PDF**
   - **Endpoint**: `POST /upload_course_reg/`
   - **Description**: Upload a PDF file containing course registration details to extract course codes.
   - **Request Body**:
     ```json
     {
       "file": "<PDF_FILE>"
     }
     ```
   - **Response**:
     ```json
     {
       "course_codes": ["CSC101", "MAT201", ...]
     }
     ```

### 2. **Create Class Timetable**
   - **Endpoint**: `POST /create_class_timetable/`
   - **Description**: Generate a timetable based on a list of offered courses.
   - **Request Body**:
     ```json
     ["CSC101", "MAT201", ...]
     ```
   - **Response**:
     ```json
     {
       "CSC101": [
         {
           "course": "CSC101",
           "Building": "Building A",
           "Room": "Room 101",
           "Time": "8am-9am",
           "Day": "Monday"
         },
         ...
       ],
       ...
     }
     ```

### 3. **Generate Timetable Excel**
   - **Endpoint**: `POST /generate_timetable/`
   - **Description**: Generate and download an Excel file containing the timetable.
   - **Request Body**:
     ```json
     {
       "CSC101": [
         {
           "course": "CSC101",
           "Building": "Building A",
           "Room": "Room 101",
           "Time": "8am-9am",
           "Day": "Monday"
         },
         ...
       ],
       ...
     }
     ```
   - **Response**: An Excel file (`timetable.xlsx`) containing the timetable.

---

## File Structure

```
timetable-generator/
├── app.py                # Main FastAPI application
├── timetable/            # Directory containing timetable CSV files
│   ├── monday.csv
│   ├── tuesday.csv
│   ├── wednesday.csv
│   ├── thursday.csv
│   └── friday.csv
├── requirements.txt      # List of dependencies
└── README.md             # Project documentation
```

---

## Dependencies

- Python 3.8+
- FastAPI
- PyMuPDF (`fitz`) for PDF processing
- Pandas for data manipulation
- OpenPyXL for Excel file generation
- Pydantic for data validation

---

## Contributing

Contributions are welcome! If you'd like to contribute to the Timetable Generator API, please follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bugfix.
3. Commit your changes.
4. Submit a pull request.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- [FastAPI](https://fastapi.tiangolo.com/) for providing the web framework.
- [PyMuPDF](https://pymupdf.readthedocs.io/) for PDF processing.
- [Pandas](https://pandas.pydata.org/) for data manipulation.
- [OpenPyXL](https://openpyxl.readthedocs.io/) for Excel file generation.

---


Generate your timetable with ease! 🚀📅

