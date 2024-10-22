# Artist2Art
AI that turns faces into original artworks

# Why?
* This project explores the relationship between artist and art.
* If art is generated by an AI, then who is the artist?
  * Is the computer the artist?
  * Is the original programmer of the AI the artist?
  * Am I, the person who pressed the 'enter' key, the artist?
  * Are the people whose faces I used the artists?
  * Or are the artists from the dataset the artists?


# How?

Using the [Pix2Pix Tensorflow port](https://github.com/affinelayer/pix2pix-tensorflow) on a CUDA-enabled NVidia GPU, trained on a dataset of ~65 artists faces mapped to their artworks, this program can generate new artworks from the faces it's fed.

In order to complete this project I had to:

1. Install CUDA on my desktop PC
  * First attempt, it didn't detect the GPU driver
  * I reinstalled the GPU driver, it still didn't detect it
  * I let CUDA install its own version of the driver, but it still didn't detect it
  * I then clean-installed Ubuntu 17.10, which was recommended by NVidia
  * Finally got CUDA to work after that
2. Install CudNN, the Neural-network CUDA library
  * This is pretty easy, just drag and drop a few files into the CUDA folder
3. Create an Anaconda environment with Tensorflow and run Pix2Pix
  * Tensorflow did not detect my GPU at first
  * I later found out that my GPU is only CUDA-compute 3.0 enabled, and my version of tensorflow required 3.5. 
  * In order to fix this, I had to compile Tensorflow from source which took me all day to do.
  * After compiling it from source, I got a custom build of tensorflow for my exact setup, which I installed into anaconda using Pip. 
4. Get data
  * I manually scraped a bunch of pictures of artists and their art from Wikipedia. 
  * I attempted to automate this process with a Python script, but it proved to be pretty difficult, as each artist's wikipedia page had to be checked for a picture of them, and a picture of their art. 
  * I gave up and got help from a friend. We sat down and manually downloaded all of the images.
  * Next, I used pix2pix tools/process.py to normalize all of the images

# Next Steps
## Web Interface
* I started making a web interface using Flask for this, which would allow you to upload a picture and turn it into art.
* Once it's finished, it will work by using Python's *os* module, and the `os.system` function, and the linux commands to operate pix2pix.
## Automatic Scraper
* While making a truely automatic scraper would be pretty much impossible, a "helper" program to help scrape could be made using Processing.
* Using the Wikipedia API and the [List of Painters by name](https://en.wikipedia.org/wiki/List_of_painters_by_name) article, a processing sketch could be made which displays all of the images from pages in the list. You could then manually select the picture of the artist, and the picture of their art for the dataset, and skip the ones which don't have the images you need.

