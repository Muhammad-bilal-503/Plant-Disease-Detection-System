# Plant Disease Identification App

An Android application that helps users identify plant diseases using machine learning, camera functionality, and weather-based farming advice.

## 📱 Project Overview

This is an Android application developed for the Smart India Hackathon (SIH) 2023 that enables users to:
- Capture or upload images of plants
- Identify plant diseases using TensorFlow Lite machine learning models
- Get location-based weather information for better farming decisions
- Manage their plant collection
- Access expert advice and recommendations

## ✨ Features

### 1. **User Authentication**
- Login and Sign-up functionality
- Support for both regular users and expert users
- Secure authentication flow with splash screen

### 2. **Camera Integration**
- High-quality camera interface using CameraX API
- Advanced camera features:
  - Tap-to-focus functionality
  - Pinch-to-zoom gesture support
  - Flash/torch control
  - Image preview and retake option
  - Automatic image orientation correction

### 3. **Plant Disease Detection**
- Machine learning-powered disease identification using TensorFlow Lite
- Support for multiple plant types (fruits, vegetables, etc.)
- Real-time image processing and analysis
- Disease diagnosis results display

### 4. **Weather Integration**
- Location-based weather information using OpenWeatherMap API
- Real-time weather data including:
  - Temperature
  - Humidity
  - Sky conditions
  - Sunrise/sunset times
- Farming advice based on weather conditions

### 5. **Location Services**
- Automatic location detection using Google Play Services
- GPS-based coordinate tracking
- Location-based weather updates

### 6. **User Interface**
- Modern Material Design UI
- Bottom navigation for easy access to main features
- Fragment-based architecture for modular UI
- Responsive layouts for different screen sizes
- Lottie animations for enhanced user experience

## 🏗️ Architecture

The app follows a **Fragment-based architecture** with the following structure:

```
MainActivity (Splash) → LoginActivity → PlantActivity (Main Container)
                                              ↓
                    ┌─────────────────────────┼─────────────────────────┐
                    ↓                         ↓                         ↓
            HomeFragment              DiagnoseFragment          MyPlantFragment
                    ↓                         ↓                         ↓
            AccountFragment
```

### Key Activities:
- **MainActivity**: Entry point with splash screen, redirects to LoginActivity
- **LoginActivity**: User authentication interface
- **SignUpActivity**: User registration (supports both regular and expert users)
- **PlantActivity**: Main activity container with bottom navigation
- **CameraActivity**: Camera interface for capturing plant images

### Key Fragments:
- **HomeFragment**: Displays weather information and quick access to camera
- **DiagnoseFragment**: Plant disease diagnosis interface
- **MyPlantFragment**: User's plant collection and disease analysis
- **AccountFragment**: User account management

## 🛠️ Technologies & Libraries

### Core Technologies:
- **Language**: Java
- **Platform**: Android (API 23 - 34)
- **Build System**: Gradle (Kotlin DSL)
- **Minimum SDK**: 23 (Android 6.0)
- **Target SDK**: 34 (Android 14)

### Key Dependencies:

#### UI & Design:
- `androidx.appcompat:appcompat:1.6.1` - App compatibility
- `com.google.android.material:material:1.11.0` - Material Design components
- `androidx.constraintlayout:constraintlayout:2.1.4` - Constraint layouts
- `com.airbnb.android:lottie:6.1.0` - Lottie animations
- `androidx.core:core-splashscreen:1.0.1` - Splash screen support

#### Camera:
- `androidx.camera:camera-core:1.3.1` - CameraX core
- `androidx.camera:camera-camera2:1.3.1` - Camera2 integration
- `androidx.camera:camera-lifecycle:1.3.1` - Camera lifecycle management
- `androidx.camera:camera-view:1.3.1` - Camera view components

#### Machine Learning:
- `org.tensorflow:tensorflow-lite-support:0.1.0` - TensorFlow Lite support
- `org.tensorflow:tensorflow-lite-metadata:0.1.0` - Model metadata
- `org.tensorflow:tensorflow-lite-gpu:2.3.0` - GPU acceleration support

#### Networking:
- `com.squareup.retrofit2:retrofit:2.9.0` - REST API client
- `com.squareup.retrofit2:converter-gson:2.9.0` - JSON conversion

#### Location Services:
- `com.google.android.gms:play-services-location:21.0.1` - Google Location Services

#### Utilities:
- `androidx.lifecycle:lifecycle-extensions:2.2.0` - Lifecycle management
- `androidx.exifinterface:exifinterface:1.3.7` - Image EXIF data handling

## 📁 Project Structure

```
app/
├── src/
│   ├── main/
│   │   ├── java/com/sih23/plantdiseaseidentifiers/
│   │   │   ├── MainActivity.java              # Entry point with splash
│   │   │   ├── LoginActivity.java             # User login
│   │   │   ├── SignUpActivity.java            # User registration
│   │   │   ├── PlantActivity.java              # Main container activity
│   │   │   ├── CameraActivity.java             # Camera interface
│   │   │   │
│   │   │   ├── fragments/
│   │   │   │   ├── HomeFragment.java           # Home screen with weather
│   │   │   │   ├── DiagnoseFragment.java       # Disease diagnosis
│   │   │   │   ├── MyPlantFragment.java        # User's plants
│   │   │   │   ├── AccountFragment.java        # Account management
│   │   │   │   ├── UserSignUpFragment.java     # User sign-up form
│   │   │   │   └── ExpertSignUpFragment.java   # Expert sign-up form
│   │   │   │
│   │   │   ├── adapters/
│   │   │   │   └── FruitAdapter.java           # RecyclerView adapter
│   │   │   │
│   │   │   ├── utils/
│   │   │   │   ├── ImageUtils.java             # Image processing utilities
│   │   │   │   └── AppExecutors.java           # Thread management
│   │   │   │
│   │   │   ├── WeatherService.java             # Weather API interface
│   │   │   ├── WeatherResponse.java            # Weather data model
│   │   │   ├── WeatherEntry.java               # Weather entry model
│   │   │   ├── LocationViewModel.java          # Location ViewModel
│   │   │   ├── DefaultLocationTracker.java     # Location tracking
│   │   │   ├── FruitEntry.java                 # Fruit/plant data model
│   │   │   └── ml/
│   │   │       └── Model.java                  # TensorFlow Lite model
│   │   │
│   │   ├── res/
│   │   │   ├── layout/                         # XML layouts
│   │   │   ├── drawable/                       # Drawable resources
│   │   │   ├── values/                         # Strings, colors, themes
│   │   │   └── menu/                           # Menu definitions
│   │   │
│   │   └── AndroidManifest.xml                 # App manifest
│   │
│   ├── test/                                   # Unit tests
│   └── androidTest/                            # Instrumented tests
│
└── build.gradle.kts                            # App-level build config
```

## 🔑 Key Components

### 1. **CameraActivity**
- Implements CameraX for modern camera functionality
- Features:
  - Real-time preview
  - Image capture with proper orientation
  - Tap-to-focus with visual feedback
  - Pinch-to-zoom gestures
  - Flash control
  - Image review and retake option

### 2. **MyPlantFragment**
- Loads captured images from internal storage
- Processes images through TensorFlow Lite model
- Displays disease identification results
- Supports image upload from gallery

### 3. **HomeFragment**
- Fetches weather data using Retrofit and OpenWeatherMap API
- Displays:
  - Current temperature
  - Humidity levels
  - Sky conditions
  - Sunrise/sunset times
  - Farming advice based on weather
- Shows horizontal scrollable list of plant categories

### 4. **LocationViewModel & DefaultLocationTracker**
- Manages location tracking using Google Play Services
- Provides coordinates to weather service
- Handles location permissions

### 5. **WeatherService**
- Retrofit interface for OpenWeatherMap API
- Fetches current weather based on GPS coordinates
- Returns structured weather data

## 🔐 Permissions

The app requires the following permissions:

- **CAMERA**: For capturing plant images
- **READ_EXTERNAL_STORAGE / READ_MEDIA_IMAGES**: For accessing gallery images
- **WRITE_EXTERNAL_STORAGE**: For saving captured images (Android 12 and below)
- **INTERNET**: For weather API calls
- **ACCESS_FINE_LOCATION**: For GPS-based weather information
- **ACCESS_COARSE_LOCATION**: For approximate location

## 🌐 API Integration

### OpenWeatherMap API
- **Base URL**: `https://api.openweathermap.org/`
- **Endpoint**: `/data/2.5/weather`
- **Usage**: Fetches current weather data based on latitude and longitude
- **API Key**: Configured in `HomeFragment.java`

## 🤖 Machine Learning Model

The app uses **TensorFlow Lite** for on-device plant disease detection:

- **Model Input**: 150x150 RGB images
- **Model Location**: `app/src/main/ml/`
- **Processing**: 
  - Images are resized to 150x150 pixels
  - Converted to TensorBuffer format
  - Processed through the ML model
  - Results displayed to the user

### Model Integration:
```java
Model model = Model.newInstance(getContext());
TensorBuffer inputFeature0 = TensorBuffer.createFixedSize(
    new int[]{1, 150, 150, 3}, 
    DataType.FLOAT32
);
inputFeature0.loadBuffer(TensorImage.fromBitmap(bitmap).getBuffer());
Model.Outputs outputs = model.process(inputFeature0);
```

## 🚀 Setup Instructions

### Prerequisites:
1. Android Studio (latest version recommended)
2. Android SDK (API 23 - 34)
3. Java JDK 8 or higher
4. Android device or emulator (API 23+)

### Installation Steps:

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd Plant-Disease-Identification-App
   ```

2. **Open in Android Studio**
   - Open Android Studio
   - Select "Open an existing project"
   - Navigate to the project directory

3. **Configure API Keys**
   - Update the OpenWeatherMap API key in `HomeFragment.java`:
     ```java
     public static String AppId = "YOUR_API_KEY_HERE";
     ```

4. **Sync Gradle**
   - Android Studio will automatically sync Gradle dependencies
   - Wait for all dependencies to download

5. **Build the Project**
   - Click "Build" → "Make Project" or press `Ctrl+F9` (Windows/Linux) / `Cmd+F9` (Mac)

6. **Run the App**
   - Connect an Android device or start an emulator
   - Click "Run" → "Run 'app'" or press `Shift+F10`

## 📱 Usage

1. **Launch the App**: The app starts with a splash screen, then navigates to login
2. **Login/Sign Up**: Create an account or login with existing credentials
3. **Home Screen**: View weather information and access camera
4. **Capture Image**: 
   - Tap the camera button on home screen
   - Capture a plant image using the camera
   - Review and confirm the image
5. **Diagnose Disease**: 
   - Navigate to "My Plants" tab
   - View captured image
   - Tap "Find Disease" to analyze
6. **View Results**: Disease identification results are displayed

## 🔮 Future Improvements

Based on the code structure, potential enhancements include:

- [ ] Complete authentication backend integration
- [ ] Cloud storage for plant images
- [ ] Disease history tracking
- [ ] Treatment recommendations
- [ ] Expert consultation feature
- [ ] Push notifications for weather alerts
- [ ] Offline mode support
- [ ] Multiple language support
- [ ] Enhanced ML model with more plant types
- [ ] Social sharing features
- [ ] Plant care reminders

## 🐛 Known Issues / TODOs

- Authentication is currently simulated (no backend)
- Some fragments have placeholder implementations
- ML model labels need to be properly mapped
- Location permission handling needs refinement
- Image storage path management could be improved

## 📄 License

This project was developed for Smart India Hackathon (SIH) 2023.

## 👥 Contributors

Developed by the SIH 2023 team.

---

**Note**: This app requires an active internet connection for weather data and proper camera permissions for image capture functionality.
