# Symbols, Patterns and Signals

## A2. Data acquisition

We get data from the real world using an *acquisition process*. Sometimes this is straight-forward data collection (questionaires, surveys, measurements, etc.). At other times, we need more complex application-specific processes, e.g. DNA sequencing. Most of this is out of the remit of this unit, with the exception of acquisition of signals: speech, audio, video.

### Digital representation

We can produce a digital representation of analogue data using sampling and quantisation. This means taking a sample of the data at regular intervals, and *quantising* = rounding the data to the nearest quantisation level. The picture below shows three bits = (2³ = 8) quantisation levels. Sampling rate = frequency = 1/time.

![Quantisation example](https://upload.wikimedia.org/wikipedia/commons/b/b7/3-bit_resolution_analog_comparison.png)

#### Typical levels:
- speech: 8 bits per sample, 8 kHz sampling
- audio: 16 bits per sample, 44 kHz sampling
- colour images: 24 bits per pixel

#### Frequency decomposition

Every signal can be represented as the sum of sine and cosine waves, using Fourier analysis. Can then be represented as a frequency spectrum, using Fourier transform.

#### Sampling Theorem

The **Nyquist-Shannon sampling theorem** states that a signal can be reconstructed from samples if the sampling rate is greater than twice the highest frequency component in the signal. If sampling rate is not greater, there is the risk of *aliasing*, where higher frequencies appear as lower frequencies.

![Two sine waves with the same sample values](https://upload.wikimedia.org/wikipedia/commons/thumb/2/28/AliasingSines.svg/500px-AliasingSines.svg.png)

In 2D images, this appears as a moiré pattern:

![Moiré pattern on a brick wall](https://upload.wikimedia.org/wikipedia/commons/f/fb/Moire_pattern_of_bricks_small.jpg)

### Other ways of representing data

- **Histograms**: plot frequency density against numeric data.
- **Data values**: plot count against symbolic data.
- **Scatter plot**: plot two numeric axes against each other.
- **Scatterplot matrix**: plot each pair of two numeric axes against each other, in a matrix where each row/column is a dimension.
- **Box plot**: for showing uncertainty.
- **Force-directed graph**: for showing links between entities, e.g. a social network.
