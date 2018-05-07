# Symbols, Patterns and Signals

## Introduction

This unit is about using data: generating and interpreting data, and making decisions based on it. What is data? Text, images, video, DNA sequences, emails, web pages, speech, audio, GPS signals, etc.

When comparing different methods, it's important to consider **what** we need to do (methods), **when** it works (applicability), and **how well** it works (performance). It's also important to remember to consider why we use it.

### Why is this important? Why do we learn it?

These techniques are fundamental to many different areas of computer science:

- AI, machine learning
- image processing, pattern recognition
- wearable and mobile computing
- graphics, animation, VR
- computer vision and robotics.
- speech and audio processing

And lots of money in data science 😜

### Example: Pattern Classification

**Data**: images of fish

**Aim**: Distinguish between sea bass and salmon

          image
            |
            V
      pre-processing
            |
            V
    feature extraction
            |
            V
      classification
           /   \
          /     \
        └─       ─┘
    sea bass    salmon

#### Possible solution

1. Obtain many example images of salmon, sea bass
2. Determine avg. width and lightness of each image, compute histograms
3. Find the best division point of each, such that the majority of example fish are correctly classified. 1-D linear classification.
4. Plot these metrics in 2-D, and find the best line between the two different regions. Straight line => 2-D linear decision model. Could also use a parabola, hyperbola etc. However, be careful of overfitting with a very wiggly line, as this is likely more down to chance of the data picked than the actual distribution.

### Image segmentation

**Data**: array of pixel values (either colour or greyscale)

**Aim**: identify the regions of different objects in the image

Simplest approach: assume each object is a region of pixels with a similar colour. 