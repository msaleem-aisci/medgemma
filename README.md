Overview:
Google has released open-weight models specifically designed to help developers more efficiently create novel healthcare and life sciences applications. MedGemma and the rest of HAI-DEF collection give developers a starting point for building powerful tools while allowing them full control over the models and associated infrastructure.

In this competition, you’ll use these models to build full fledged demonstration applications. Whether you’re building apps to streamline workflows, support patient communication, or facilitate diagnostics, your solution should demonstrate how these tools can enhance healthcare

The Problem (The "Why")
Doctors need to know if a tumor has specific genetic mutations (like MSI-High) to prescribe the right drug.
Currently, finding this out requires expensive genetic testing ($3,000+ and weeks of waiting).
Standard microscopes (H&E slides) are cheap and available everywhere, but humans can't "see" mutations in them.
The Solution (The "What")
Onco-Gemma is an AI Agent that predicts these invisible genetic markers directly from standard pathology images.
It turns a cheap microscope slide into a "Genomic Screener."
The Tech Stack (The "How")
Vision Engine: Google Path Foundation Model. (We use this to extract "embeddings" from tissue patches).
Classifier: A simple lightweight model (Logistic Regression or MLP) trained to classify MSI vs. MSS based on those embeddings.
Reasoning Engine: MedGemma (LLM). It takes the classification result and drafts a clinical recommendation (e.g., "High probability of MSI-H. Recommend Immunotherapy.").
The Dataset
We are targeting Colorectal Cancer (CRC) histology tiles (likely the Kather 2019 dataset or similar on Kaggle) which are labeled as MSI (Mutated) or MSS (Stable).
1. Colorectal Cancer (CRC) & The "Brain vs. Colon" Correction
What it is: Cancer of the Colon or Rectum (the large intestine).
Why we are using it (Important):
You mentioned "Brain" in your message, but the specific "MSI" project we designed is actually for Colon Cancer.
Reason: MSI (the mutation we are hunting) is a huge deal in Colon Cancer. It determines if a patient lives or dies based on the drug choice. In Brain cancer, we usually look for other things (like IDH mutations).
Recommendation: To win the hackathon, stick to Colon Cancer. The data (Kather 2019) is famous, clean, and ready to use. If we try to find "MSI in Brain," we will struggle to find data.
2. MSI vs. MSS (The "Hidden Label")
Think of the tumor as a locked door.
MSI (Microsatellite Instability): This is a "Mutated" tumor. The DNA is unstable.
Good News: This tumor has a specific "keyhole." If the doctor knows it is MSI, they can use a special "Key" (Immunotherapy drugs like Pembrolizumab) that melts the tumor away.
MSS (Microsatellite Stable): This is a "Stable" tumor.
Bad News: The special key doesn't work. The doctor must use standard Chemo.
The Problem: You can't tell them apart just by looking. You usually need a $3,000 DNA test.
Your AI: Looks at the image and says "Hey, this looks like MSI! Give them the special drug!"
3. Google Path Foundation Model (The "Super Eye")
Analogy: Imagine a medical student who has spent 10 years looking at millions of pathology slides. They haven't specialized in "Colon Cancer" yet, but they know exactly what a "cell" looks like, what "tissue" looks like, and what "cancer" looks like.
Technical: It is a pre-trained Vision Transformer (ViT) from Google.
Your Job: You don't need to teach it to see. You just show it a few Colon Cancer images, and it learns the specific task instantly.
4. Embeddings (The "Translator")
Analogy: A computer cannot understand an image (pixels). It only understands numbers.
How it works: When you feed an image into the Path Foundation Model, it doesn't just say "Cancer." It converts the image into a list of numbers (e.g., [0.1, 0.5, -0.9, ...]).
The Result: This list of numbers is the "Embedding." It represents the "DNA" of the image. We train your simple classifier on these numbers, not the image itself.
Progress
Google Path Foundation model 
Classifier
Faiss


