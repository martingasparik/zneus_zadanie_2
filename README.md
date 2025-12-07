# Documentation
## EDA
In the first phase, the "Animals-10" dataset, which contains images of 10 different animal species, was analyzed.
Firstly, Loading and translation - (and correcting it)
Vlastnosti obrázkov:
- Dataset obsahuje celkovo 26 179 obrázkov.
- Dominantný formát súborov je .jpeg (~24 000+), nasleduje .jpg a malé množstvo .png.
- Väčšina obrázkov (26 128) používa farebný model RGB.
- Rozmery obrázkov nie sú jednotné, s priemernou šírkou cca 320 px a výškou 252 px.
Distribúcia tried: Pôvodný dataset bol značne nevyvážený. Najpočetnejšie triedy (pes a pavúk) mali takmer 5000 obrázkov, zatiaľ čo najmenej početné (slon) len okolo 1400.
___
## Preprocessing
- Filtering: Only images with RGB color mode were retained.
- Dataset balancing: To eliminate class imbalance, the number of images for each class was adjusted to 2000. For classes with a higher number, the undersample method (random selection without repetition) was used.
- Split: 0.7/0.15/0.15
___
## Augmentation and Data Generators
- ImageDataGenerator is used to load and modify images during training. 
- Image parameters: All images are reduced to a size of 224 x 224 pixels or smaller during loading and processed in batches of 32.
- Training generator: Applies normalization (pixel values 0-1) and various augmentation techniques to increase model robustness:
  - Rotation (up to 20°)
  - Horizontal and vertical shift (0.2)
  - Horizontal flip
  - Zoom and shear (shear)

Validation and testing generator: Applies only normalization (rescale=1./255) without further image deformation to maintain objectivity in evaluation.
