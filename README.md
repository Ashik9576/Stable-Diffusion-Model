# Stable-Diffusion-Model
Text to image generator

# How do we go from Diffusion to Text-to-Image Generation ?
This is also done in a clever way. Together with image that needs to be diffused, we put together the text associated with the image (after converting it to embeddings) into a model and guide the diffusion model towards some target class. This gives us an denoised image which is closely related to the caption as well. However complicated it sounds, it is done through a rather simple and VERY clever technique called Classifier Guidance.

# Classifier Guidance :
In Stable Diffusion, we make use of something called CLIP embeddings to guide the diffusion towards the target class during the training. CLIP stands for Contrastive Loss Image Pair. The ideas behind this is to make the image and word embeddings similar in their semantics. Similar CLIP embeddings are used in DALL-E as well.

# Generation of never seen images - Classifier Free Guidance :
One question that is often asked when people see Text-To-Image generation is - How can it come up with images it has never seen before ? As with everything in this notebook - this was also done using a clever technique called Classifier Free Guidance.

In Classifier free guidance - instead of one noisy image, two same images are fed to model - one without the text embeddings and one with it. The diffusion model therefore comes up with two image - one without text embeddings and one without it. Together, these two noise images* can be used to amplifiy the signal and generate images which are previously not generated.

# *Rememer that the model generates noise, not the actual image
