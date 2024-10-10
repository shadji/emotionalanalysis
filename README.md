
# Emotion Prediction with BlazeFace and TFLite Models

This project demonstrates real-time emotion prediction by detecting faces using the BlazeFace model and predicting emotions using a TFLite model. The emotions are visualized by overlaying corresponding emoji icons on top of the video stream, and a dynamic bar graph is displayed below the video to show the relative probabilities of each emotion.
## Overview
```mermaid
graph TB
    %% Define Subgraphs (User I/O, APP Logic, and AI Processing)
    subgraph AI_System [AI Processing]
        direction TB
        C["<i class='fa fa-cogs'></i> Face Extraction & Preprocessing"]
        D["<i class='fa fa-smile'></i> Emotion Detection - Emotional AI"]
    end
    subgraph APP_Logic [APP Logic]
        direction TB
        B["<i class='fa fa-search'></i> Capture Frame"]
        E["<i class='fa fa-bar-chart'></i> Real-Time Emotion Feedback"]
    end   
    subgraph User_IO [User Input/Output]
        direction TB
        A["<i class='fa fa-camera'></i> User's Camera"]
        F["<i class='fa fa-desktop'></i> User Interface"]
    end



   

    %% Define Flow between Subgraphs
    A -->|Video Feed| B -->|Detect Face| C -->|Processed Face Data| D -->|Classified Emotion| E -->|Show Results| F

    %% Style and Node Coloring
    style A fill:#f96,stroke:#333,stroke-width:2px
    style F fill:#ffc107,stroke:#333,stroke-width:2px
    style B fill:#6f9,stroke:#333,stroke-width:2px
    style E fill:#69f,stroke:#333,stroke-width:2px
    style C fill:#ffeb3b,stroke:#333,stroke-width:2px
    style D fill:#f36,stroke:#fff,stroke-width:2px

    %% Arrow styling for consistency
    linkStyle default stroke:#333,stroke-width:2px,fill:none
```
## Features
- **Face Detection**: Uses the BlazeFace model to detect faces in the video stream.
- **Emotion Prediction**: Uses a TFLite model to classify emotions into four categories: Happy, Neutral, Sad, and Surprise.
- **Emoji Overlay**: Displays an emoji corresponding to the predicted emotion over the detected face.
- **Bar Graph Visualization**: A four-column bar graph shows the relative percentage of the predicted emotion classes in real-time.
- **Dynamic Updates**: Both the emoji and the bar graph update dynamically as predictions are made.

## Project Structure

- **index.html**: The main HTML file that includes the video stream, bar graph, and JavaScript logic for emotion prediction.
- **CSS Styling**: Basic CSS is used to style the layout, video stream, bar graph, and emoji overlays.
- **JavaScript Logic**: Includes the TensorFlow.js and TFLite libraries to handle the BlazeFace model and the custom TFLite model for emotion prediction.

## How to Run the Project

### Prerequisites

- A web browser that supports modern JavaScript features.
- An active internet connection to load TensorFlow.js and BlazeFace from the CDN.
- A webcam to capture live video for face detection and emotion prediction.

### Steps

1. **Download the Project Files**: Make sure to have the `index.html` file in your local environment.
2. **Open the HTML File**: Simply open `index.html` in your web browser. Ensure the browser has permissions to access your webcam.
3. **Watch in Action**: The webcam feed will be displayed on the page. Once the models are loaded, the face detection and emotion prediction will begin. An emoji will appear over your face, and a bar graph will update dynamically to show the relative confidence levels of the four emotion classes:
   - **Happy** (Green)
   - **Neutral** (Gray)
   - **Sad** (Red)
   - **Surprise** (Yellow)

### Project Files

- **index.html**: Contains the main HTML structure, styles, and scripts for the emotion detection and visualization.
- **TFLite Model**: A custom `.tflite` model named `emoji_4.tflite` is loaded via TensorFlow.js to predict the emotion. This model needs to be hosted and referenced in the `index.html` file.

### Example Code Snippets

#### BlazeFace Model Loading
```javascript
blazefaceModel = await blazeface.load(); // Load BlazeFace model
emojiModel = await tflite.loadTFLiteModel('emoji_4.tflite'); // Load your emoji TFLite model
```

#### Prediction and Bar Graph Update
```javascript
function updateBarGraph(predictionData) {
  for (let i = 0; i < 4; i++) {
    const bar = document.getElementById(`bar-${i}`);
    const percentage = predictionData[i] * 100; // Convert to percentage
    bar.style.height = `${percentage}%`;
  }
}
```

## Customization

- **Emotion Labels**: The four emotion classes are labeled as "Happy", "Neutral", "Sad", and "Surprise". You can customize these labels by modifying the labels in the `index.html` file.
- **Bar Graph Colors**: The colors for each emotion are green (Happy), gray (Neutral), red (Sad), and yellow (Surprise). These can be changed in the CSS section.
- **Prediction Model**: The TFLite model (`emoji_4.tflite`) can be replaced with a custom model if you'd like to predict different emotions.

## Future Enhancements
- **Add More Classes**: Extend the model to predict additional emotions and update the UI accordingly.
- **Optimize Performance**: Reduce computational load by predicting every few frames instead of every frame.
- **Improve Visualization**: Add animations or transitions to the bar graph for a more polished user experience.

## License
This project is for educational purposes. Feel free to customize and adapt it for your needs.
