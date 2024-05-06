# AutoImprov
> An LSTM-RNN model trained on sheet music transcriptions that generates jazz solos over chord changes.

This is my first attempt at training an LSTM model that would improvise a jazz solo over a given chord progression. My model converts the notes and chords in the training data into discrete categories and predicts the notes that would be suitable to be played over the chords provided as input (this would include rests and the quarter-note durations of the rests and notes). An empty lead sheet (containing the chords) is passed as an input alongside a seed containing the first few notes of the solo. 

I used transcriptions of Charlie Parker's Omnibook to train my model. The .xml transcriptions were available on: [http://repmus.ircam.fr/dyci2/ressources]

Output:
![Temperature = 0.3 Chord = Yardbird Suite](https://github.com/Junos16/AutoImprov/assets/93246181/447279bb-7085-46c3-ab28-1cbb998055a8)


The main limitation of this naive approach is that only the chords present in the dataset can be used as input. Also the model does not comprehend the relation between the chords and the notes being played over it. 

Libraries Used:
- Music21: I used music21 to parse .musicxml files and work with chords, notes and rests and their respective durations
- Numpy: While sampling with temperature I used numpy to use mathematical functions like logarithm, exponentiation and random choice
- Tensorflow/Keras: I used keras to preprocess data using one-hot encoding, train the LSTM model and generate solos using that model
