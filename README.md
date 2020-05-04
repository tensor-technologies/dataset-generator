# Voice Up Lib
A python library wrapper for the VoiceUp dataset.

## Usage
(also in main_voiceup.py)
### Random wav data accessing:
```python
from voiceup import VoiceUp
v = VoiceUp('D:\\Documents\\Datasets\\voca-corona-dataset-2020-04-10', limit_rows=100)
v.load_recordings_data('cough')
random_wav = v.df['cough_data'].dropna().iloc[0]
plt.plot(random_wav)
plt.show()
```
### Functional Analysis
```python
v = VoiceUp('D:\\Documents\\Datasets\\voca-corona-dataset-2020-04-10', limit_rows=100)
v.load_functionals('cough')
F0_sma_range = v.df['cough_F0_sma_range']
# ...
```

### Targeted analysis
```python
p = Person('D:\\Documents\\Datasets\\voca-corona-dataset-2020-04-10', id='5e730b5d19fe630007a3e97a')
p.load_recording('cough')
# Not we can access the features as normal attributes
print('p.cough_F0_sma_range:', p.cough_F0_sma_range)
print('p.cough_F0env_sma_min:', p.cough_F0env_sma_min)
print('p.cough_F0env_sma_max:', p.cough_F0env_sma_max)
```

### Targeted analysis LLD (WIP)
```python
p = Person('D:\\Documents\\Datasets\\voca-corona-dataset-2020-04-10', id='5e730b5d19fe630007a3e97a')
lld = p.get_lld('cough')
plt.plot(lld['pcm_fftMag_mfcc_sma[1]'])
plt.show()
```

