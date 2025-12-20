# Classical Music Generation Model

Original Repo: https://github.com/calvinlchen/classical-music-generation-model.git

## Project Purpose and Motivation
This project explores whether accessible machine learning methods can generate coherent classical-style music. We focus on classical-era composers (roughly 1725–1800 A.D.), training on Haydn, Mozart, and Beethoven to keep a consistent tonal style. The browser app lets musicians, students, and hobbyists experiment with these models to generate MIDIs without deep technical or music-theory expertise. By showcasing a variety of machine learning models for music generation, we conduct an exploratory approach to small-scale AI music generation and highlight the differences in each model's musical capabilities for achieving the unified goal.

## What It Does
Two complementary generators power the app: a transformer that produces musical token sequences, and a diffusion model that synthesizes piano-roll images. Both outputs are converted to MIDI for playback. Users can generate pieces, preview them in-browser, view the piano-roll image, download the MIDI, and optionally draft prompts with an OpenAI-assisted helper.

Within each model type exist two implementations: for transformers, an in-house model and a tuned version of OpenAI GPT-2; for diffusion, an unconditional model and a conditional model trained with classifier-free guidance. Each of these have their strengths and weaknesses, allowing the user to choose a model which best suits their music generation goals. For instance, GPT-2 achieves the best musical results of all the models but is limited in its context window to 1,024 tokens, while our custom in-house model can produce an endless context window but yields more inconsistent results.

Ultimately, though, all models were trained on the same dataset and with the same end-goal:
- MIDI dataset → preprocessing → (A) token stream → transformer
- MIDI dataset → preprocessing → (B) piano-roll images → diffusion
- Both → MIDI reconstruction → playback + download + evaluation

## Video Links
- Demo Video: https://youtu.be/xT_28FBgdWQ
- Technical Walkthrough Video: https://youtu.be/T3jJrlgVNk8

## Individual Contributions

### Calvin Chen

- Collected the dataset from Hugging Face and was able to performed data cleaning, preprocessing, and spliting the data for model training.
- Built custom tokenizer and conversion methods for MIDI files to/from text and image.
- Desgined and trained the Transformer model for music generation.
- Designed and trained the Diffusion models to generate piano roll images.
- Implemented tuning of GPT-2 for music generation.
- Implemented the backend API for running the models and generating the MIDI files.
- Helped build and deployed the React web application, and helped build and test features such as the audio playback, MIDI downloading, and the OpenAI integration feature.

### Johan Nino Espino
- Led cross-platform testing and debugging of the full project across different environments, including macOS, to ensure stability and compatibility.
- Tested and debugged the complete web application stack, including the React frontend and FastAPI backend, resolving issues in model inference, API routing, and file handling.
- Verified and debugged the OpenAI API integration in the web app, ensuring that user text prompts correctly influence transformer-based music generation.
- Tested and debugged the GPT-2 transformer model within the web application to confirm proper loading, inference behavior, and output quality.
- Contributed extensively to project documentation and deliverables, including the README.md, SETUP.md, technical walkthrough materials, and evaluation summaries.
- Validated that both the transformer and diffusion pipelines run correctly end to end, from data preprocessing and model execution to MIDI generation and playback.
