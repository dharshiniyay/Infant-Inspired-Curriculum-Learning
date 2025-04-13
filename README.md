# Infant-Inspired-Curriculum-Learning

This repository contains code and training notebooks for the research project "Infant Inspired Curriculum Training for Self-Supervised Visual Representation Learning". The project investigates whether curriculum-based self-supervised learning (SSL), inspired by the visual development stages of human infants (e.g., blurry to clear vision and low to high colour saturation), can improve the robustness and quality of learned visual representations.

## Project Overview 
Inspired by developmental psychology, this work explores how training a Vision Transformer-based Masked Autoencoder (MAE-ViT) on progressively challenging visual inputs can impact representation learning. The study focuses on two curriculum strategies:

<ul>
  <li>Blur Curriculum: Gradually decreasing Gaussian blur intensity.</li>
  <li>Colour Saturation Curriculum: Gradually increasing colour saturation from grayscale to full-colour.</li>
</ul>  
Results are compared against a standard non-curriculum baseline using classification accuracy on challenging test sets, such as noisy and silhouette-transformed images.

## Repository Structure
