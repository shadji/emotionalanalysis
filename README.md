
# Emotion Prediction with BlazeFace and TFLite Models

This project demonstrates real-time emotion prediction by detecting faces using the BlazeFace model and predicting emotions using a TFLite model. The emotions are visualized by overlaying corresponding emoji icons on top of the video stream, and a dynamic bar graph is displayed below the video to show the relative probabilities of each emotion.

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
