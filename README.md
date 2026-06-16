# Women Safety Analytics

An interactive, Flask-powered web application designed to enhance personal safety for women. This platform integrates real-time geolocation tracking, video capturing with automated person detection, SOS alert dispatching (with audio recording attachments), local safety heuristics, and an interactive chatbot for instant Q&A.

Developed by **Kaushik Ghosh** (Kaushik3389@gmail.com).

---

## 🚀 Key Features

- **SOS Emergency Trigger**: 
  - One-click SOS emergency button that retrieves the user's high-precision GPS coordinates using the HTML5 Geolocation API.
  - Automatically records 5 seconds of audio from the user's microphone.
  - Emails the location link (via Google Maps) and the recorded audio file to the pre-configured emergency contacts using Flask-Mail.
- **Webcam Capture & Person Detection**:
  - Captures 10 seconds of live video directly from the user's webcam.
  - Employs **OpenCV Haar Cascade Classifiers** (`haarcascade_fullbody.xml`) to detect and draw bounding boxes around people in real-time.
  - Saves the recorded file locally (`static/video.webm` / `.avi`) and automatically emails it to emergency contacts.
- **Interactive Help Map**:
  - Integrates **Leaflet.js** and **OpenStreetMap** to show the user's current location.
  - Utilizes **Google Places API** to dynamically query and plot nearby emergency resources (Hospitals, Police Stations, and Railway Stations) within a 5km radius.
- **Safety Assessment Incident Form**:
  - Form to document incidents with date, time, location, description, and people involved.
  - Quick-check safety calculator applying heuristic rules to flag immediate safety threats (e.g., alerting when a lone female is surrounded by men).
- **Intelligent Assistant (Chatbot)**:
  - Responsive, floating chatbot built using Alpine.js.
  - Provides instant Q&A answers on safety measures, app usage instructions, and registration guides.

---

## 🛠️ Technology Stack

- **Backend**: Python 3.x, Flask, Flask-Mail (SMTP), OpenCV (`cv2`)
- **Frontend**: HTML5, Vanilla CSS, Tailwind CSS (via CDN), Alpine.js, FontAwesome (icons)
- **APIs & Libraries**: Leaflet.js, Google Places API, Web Geolocation API, Web MediaRecorder API

---

## 📂 Project Structure

```text
Women_Saftey-main/
├── README.md                    # Root Documentation
└── Women_Saftey-main/
    ├── README.md                # Inner Project README
    └── Women_Web/
        ├── app.py               # Main Flask Server (SOS, Video/Person Detection, Mailer)
        ├── send.py              # CLI/Alternative Script for Webcam Capture & SMTP Sending
        ├── static/              # Directory for Static Assets & Uploaded Videos
        │   └── video.webm       # Sample/Recorded WebM video
        └── templates/           # HTML Templates
            ├── index.html       # Landing Dashboard, SOS Trigger & Floating Chatbot
            ├── Kaushik.html     # Incident Reporting & Safety Heuristic Form
            ├── location.html    # Leaflet Map with Google Places API Integration
            ├── login.html       # Login Screen
            └── signup.html      # Signup Screen
```

---

## ⚙️ Prerequisites & Installation

### 1. Clone the Repository
```bash
git clone https://github.com/KaushikGhosh-code/Women_Saftey.git
cd Women_Saftey-main/Women_Saftey-main/Women_Web
```

### 2. Install Required Python Packages
Make sure you have Python installed, then run:
```bash
pip install flask flask-mail opencv-python
```

### 3. Setup API Keys & Email Configuration

#### **Google Places API Setup**
To display nearby police stations and hospitals on the map, you need a Google Places API key:
1. Open [Women_Web/templates/location.html](file:///c:/Users/kastu/Downloads/Women_Saftey-main/Women_Saftey-main/Women_Web/templates/location.html#L24)
2. Locate the Google script tag and replace `YOUR_GOOGLE_PLACES_API_KEY` with your actual API key:
   ```html
   <script src="https://maps.googleapis.com/maps/api/js?key=YOUR_GOOGLE_PLACES_API_KEY&libraries=places"></script>
   ```

#### **Flask-Mail (SMTP) Setup**
For the SOS email dispatching to function correctly:
1. Open [Women_Web/app.py](file:///c:/Users/kastu/Downloads/Women_Saftey-main/Women_Saftey-main/Women_Web/app.py#L14-L20) and [Women_Web/send.py](file:///c:/Users/kastu/Downloads/Women_Saftey-main/Women_Saftey-main/Women_Web/send.py#L13-L18).
2. Configure your SMTP credentials:
   ```python
   # Configure Flask-Mail
   app.config['MAIL_SERVER'] = 'smtp.gmail.com'
   app.config['MAIL_PORT'] = 465
   app.config['MAIL_USERNAME'] = 'your_email@gmail.com'   # Your email address
   app.config['MAIL_PASSWORD'] = 'your_app_password'      # Your App-Specific password
   app.config['MAIL_USE_TLS'] = False
   app.config['MAIL_USE_SSL'] = True
   ```
   *Note: For Gmail accounts, it is highly recommended to set up and use a Google **App Password** rather than your primary password due to Gmail SMTP security protocols.*

---

## 🏃 Running the Application

1. Navigate to the `Women_Web` directory:
   ```bash
   cd Women_Saftey-main/Women_Web
   ```
2. Start the Flask server:
   ```bash
   python app.py
   ```
3. Open your browser and navigate to:
   [http://127.0.0.1:5000](http://127.0.0.1:5000)

---

## 🔒 Safety and Privacy Disclaimer
This application requests access to user location and camera/microphone. All recordings and location metrics are processed locally or sent directly to your designated emergency contact emails via secure SMTP mail server configurations. They are not stored on any external third-party cloud database.

---

## 👨‍💻 Developer Credits
- **Developer**: Kaushik Ghosh
- **Email**: [Kaushik3389@gmail.com](mailto:Kaushik3389@gmail.com) / [Kaushikghoshkg04@gmail.com](mailto:Kaushikghoshkg04@gmail.com)
