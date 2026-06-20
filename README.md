Whitelist-Based Face Recognition Web App

A real-time face recognition web application built with Python, OpenCV, and Flask. The app implements a whitelist detection system — known faces are silently masked while unknown faces are flagged with an alert label, demonstrating a practical privacy-aware security use case.


How It Works

The system encodes a reference image of a known (whitelisted) person at startup. When the live webcam feed is processed:


Known face detected → bounding box drawn, labelled "No person detected" — the person is effectively hidden from the system
Unknown face detected → bounding box drawn, labelled "Hello there" — flagged as an unrecognised individual


This whitelist approach inverts the typical face recognition pattern, making it useful for scenarios where you want to ignore authorised individuals and alert on strangers — a real security and privacy engineering concept.


Pipeline

Browser webcam → Base64 encoding → POST /recognize → Flask backend
→ face_recognition (dlib) → compare against whitelist encoding
→ JSON response (bounding box + label) → rendered on live video


Features


Live webcam stream captured directly in the browser via MediaDevices API
Base64 frame encoding sent to a Flask REST API for server-side processing
Face detection and recognition using the face_recognition library (dlib-based)
Whitelist logic — known faces masked, unknown faces flagged
Bounding box coordinates and labels returned as JSON and rendered on frontend
Supports multiple simultaneous faces in a single frame



Tech Stack

LayerTechnologyBackendPython, FlaskComputer VisionOpenCV, face_recognition (dlib)FrontendHTML, JavaScriptCommunicationREST API, JSON, Base64


Project Structure

face-recognition-webapp/
├── app.py        # Flask backend — whitelist logic, detection and recognition
├── index.html    # Frontend — webcam capture and bounding box rendering
└── known.jpeg    # Reference image for whitelisted face encoding (add your own)


Setup & Run

bash# Clone the repo
git clone https://github.com/AkheelGogeri/face-recognition-webapp.git
cd face-recognition-webapp

# Install dependencies
pip install flask opencv-python face_recognition numpy

# Add your reference image
# Replace known.jpeg with a clear front-facing photo of the person to whitelist
# Update the filename reference in app.py if needed

# Run the app
python app.py

Then open http://localhost:5000 in your browser and allow webcam access.


Dependencies


Python 3.8+
Flask
OpenCV (opencv-python)
face_recognition
NumPy



Use Case

This pattern is applicable to:


Privacy-preserving surveillance (ignore authorised staff, flag visitors)
Access control systems
Household security (ignore family members, alert on strangers)



Author

Akheel R Gogeri
MSc Artificial Intelligence with Data Science — University of Liverpool
