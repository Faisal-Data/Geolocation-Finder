# Geolocation Finder with Music Generation

This program asks for an image of any place. Using Zero-Shot Image Classification, it guesses the country where the photo was taken. Additionally, it uses another pipeline to generate a short piece of music based on this country.

Bilinguality in this pipeline is not needed since the only input is an image, but we can manipulate the output (country names) to be in two languages. Unfortunately, I did not have time to do this, but it will be added in a future update.

I wanted to use two different pipelines in this project to demonstrate an understanding of different kinds of pipelines and make the space more creative.


### StreetCLIP
StreetCLIP is a model pretrained by deriving image captions synthetically from image class labels using a domain-specific caption template. This allows StreetCLIP to transfer its generalized zero-shot learning capabilities to a specific domain (i.e. the domain of image geolocalization). StreetCLIP builds on the OpenAI's pretrained large version of CLIP ViT, using 14x14 pixel patches and images with a 336 pixel side length.

StreetCLIP was made by Lukas Haas and Silas Alberti and Michal Skreta
### MusicGen
MusicGen is a text-to-music model capable of genreating high-quality music samples conditioned on text descriptions or audio prompts. It is a single stage auto-regressive Transformer model trained over a 32kHz EnCodec tokenizer with 4 codebooks sampled at 50 Hz. Unlike existing methods, like MusicLM, MusicGen doesn't require a self-supervised semantic representation, and it generates all 4 codebooks in one pass. By introducing a small delay between the codebooks, we show we can predict them in parallel, thus having only 50 auto-regressive steps per second of audio.

MusicGen was published in Simple and Controllable Music Generation by Jade Copet, Felix Kreuk, Itai Gat, Tal Remez, David Kant, Gabriel Synnaeve, Yossi Adi, Alexandre Défossez.

## Expected Outputs
The program should receive an image of any real-life place and, based on that image, guess the country. After that, it takes the country name and puts it into another pipeline that generates music. This means there should be two outputs: one is the name of the country, and the second one is the music piece.

# UPDATE
I have changed the way I implemented the MusicGen model. Now, it works perfectly fine as a Hugging Face space, and I have shortened the length of the generated music for faster output. And I have added Arabic country names.

# HuggingFace Space
https://huggingface.co/spaces/Faisal-Data/GeolocationFinder_MusicGenerator
