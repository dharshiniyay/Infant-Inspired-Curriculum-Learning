<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Infant-Inspired-Curriculum-Learning</title>
</head>
<body style="font-family: Arial, sans-serif; line-height: 1.6; max-width: 800px; margin: auto; padding: 20px;">

<h1>Infant-Inspired-Curriculum-Learning</h1>

<p>This repository contains code and training notebooks for the research project <strong>"Infant Inspired Curriculum Training for Self-Supervised Visual Representation Learning"</strong>. The project investigates whether curriculum-based self-supervised learning (SSL), inspired by the visual development stages of human infants (e.g., blurry to clear vision and low to high colour saturation), can improve the robustness and quality of learned visual representations.</p>

<h2>📖 Project Overview</h2>

<p>Inspired by developmental psychology, this work explores how training a Vision Transformer-based Masked Autoencoder (MAE-ViT) on progressively challenging visual inputs can impact representation learning. The study focuses on two curriculum strategies:</p>
<ul>
    <li><strong>Blur Curriculum</strong>: Gradually decreasing Gaussian blur intensity.</li>
    <li><strong>Colour Saturation Curriculum</strong>: Gradually increasing colour saturation from grayscale to full-colour.</li>
</ul>
<p>Results are compared against a standard non-curriculum baseline using classification accuracy on challenging test sets, such as noisy and silhouette-transformed images.</p>

<h2>📁 Repository Structure</h2>
<table border="1" cellspacing="0" cellpadding="5">
    <tr><th>File</th><th>Description</th></tr>
    <tr><td><code>Normal.ipynb</code></td><td>Baseline MAE-ViT training on unaugmented data.</td></tr>
    <tr><td><code>Blur.ipynb</code></td><td>Trains on heavily blurred images only.</td></tr>
    <tr><td><code>Blur_NonBlur.ipynb</code></td><td>Curriculum training: blur to non-blur (progressively decreasing blur).</td></tr>
    <tr><td><code>NonBlur_Blur_500.ipynb</code></td><td>Reverse curriculum: non-blur to blur.</td></tr>
    <tr><td><code>NonColour.ipynb</code></td><td>Trains on grayscale images only.</td></tr>
    <tr><td><code>NonColour_Colour.ipynb</code></td><td>Curriculum training: grayscale to colour saturation.</td></tr>
    <tr><td><code>Colour_NonColour.ipynb</code></td><td>Reverse curriculum: colour to grayscale.</td></tr>
    <tr><td><code>README.md</code></td><td>Project description and usage guide.</td></tr>
</table>

<h2> 📈Model Architecture</h2>
<ul>
    <li><strong>Backbone:</strong> ViT-Tiny</li>
    <li><strong>Self-Supervised Pretraining:</strong> Masked Autoencoder (MAE)</li>
    <li><strong>Linear Probe:</strong> MLP with two linear layers</li>
    <li><strong>Training Epochs:</strong> 500</li>
    <li><strong>Loss:</strong> Mean Squared Error (MSE) on masked patches</li>
    <li><strong>Optimiser:</strong> AdamW with Cosine Annealing scheduler</li>
</ul>

<h2> 🧪Evaluation</h2>
<p>Trained encoders were evaluated using linear probing on:</p>
<ul>
    <li>Normal images</li>
    <li>White noise images</li>
    <li>Black noise images</li>
    <li>Silhouette images</li>
</ul>
<p>Curricula models showed better robustness than the baseline on distorted datasets, though not significantly better on clean datasets.</p>

<h2>📊 Results Summary</h2>
<table border="1" cellspacing="0" cellpadding="5">
    <tr>
        <th>Curriculum Type</th>
        <th>Normal</th>
        <th>White Noise</th>
        <th>Black Noise</th>
        <th>Silhouette</th>
    </tr>
    <tr><td>Normal</td><td>61.62%</td><td>45.70%</td><td>30.26%</td><td>25.88%</td></tr>
    <tr><td>Blur → Non-Blur</td><td>54.97%</td><td>46.36%</td><td>29.29%</td><td>26.39%</td></tr>
    <tr><td>Non-Blur → Blur</td><td>42.18%</td><td>36.73%</td><td>30.46%</td><td>22.21%</td></tr>
    <tr><td>Blur Only</td><td>38.41%</td><td>30.97%</td><td>24.96%</td><td>22.87%</td></tr>
    <tr><td>Non-Colour → Colour</td><td>56.90%</td><td>52.11%</td><td>37.80%</td><td>23.64%</td></tr>
    <tr><td>Colour → Non-Colour</td><td>59.25%</td><td>54.36%</td><td>38.82%</td><td>19.51%</td></tr>
    <tr><td>Grayscale Only</td><td>52.57%</td><td>48.65%</td><td>35.66%</td><td>22.41%</td></tr>
</table>

<h2>📌 Requirements</h2>
<pre><code>Python 3.8+
PyTorch
torchvision
numpy
matplotlib
scikit-learn
PIL
</code></pre>
</body>
</html>
