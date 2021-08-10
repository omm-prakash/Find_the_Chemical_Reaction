# Find_the_Chemical_Reaction
This is ML project done in collaboration with my friends, help in finding the reaction from internet taking reactants images as input. 

## **Content**
---
1. model.ipynb
2. find_reaction.ipynb
3. reactants.zip

## model.ipynb
---
# CNN Model

*Find Training Image Dataset from* [here](https://drive.google.com/file/d/1VtH9o5Vg34pHhDRlCqxi53BZIi6AYzDP/view?usp=sharing)
### Model Structure

<img width="432" alt="model" src="https://user-images.githubusercontent.com/76400354/128726402-e140d20f-bcbe-492b-8d17-d0bba89a26ca.png">




## find_reaction.ipynb

---


This file does three things 
* **Text detection**: Identifies the location of and crops each character(letters, symbols, numbers) present in the image.
* **Recognition**: Predicts each of the character present in the image(character is obtained from text image), using convolutional network, forming a string in the same order as was present in the image.
* **Searching Products**: Using AutoScraper, the reactants in text string format, is used to search the products of the reaction online, and the solution is presented to the user. 

Short explaination of functions defined:
1. #### Recognition
  *  **add_border**: Adds a white border around the image given as input i.e *img* to the funtion. The border is of width *bordersize*.
  *  **predict_char**: It takes *x1,x2,y1,y2* as input to get location of concerned character from *img*. Using pretrained model its predict the charcter class the image belongs to.
  *  **find_edges**: It creates partitions between adjacent characters present in the image. The logic here is to compress the image to a 1D array, with ith index denoting the sum of the elements(pixel values) of the ith column in the image. For blank regions(all pixel values 0 for the column), this sum is 0, while for regions where the character is present(nonzero pixel values), this sum is nonzero. By taking the xor of adjacent indices of the 1D array(which will be 1 if the adjacent indices hold different values), we can identify the starting and ending points of a character in the image and thus create partitions. 
  *  **find_character**: Using find_edges, it uses the cropped/isolated region of the image and then passes this cropped region of the given *imag*, to predict_char function, which predicts the character present in the cropped region using the cnn model.
2. #### Searching products
  *  **find_result**: It search the *reaction* from a website named *chemequations.com* using *AutoScraper* liabrary. 
3. #### Detection
  *  **find_reaction**:Using OpenCV it reads image from the path. Then it detects the location of the text and makes bounding boxes around each character, passing it further to find_character function and multiple iterations are performed for identifying all characters present in the image. Using a loop the same is extracted and stored in a string which is then used for searching online using Autoscraper.
 
<img width="545" alt="detect" src="https://user-images.githubusercontent.com/76400354/128741317-2b78614f-06ea-43c8-be9c-6dc8251045af.png">

    
## reactants.zip
---
Find the test images from this zip file. You may find more from [here](https://drive.google.com/drive/folders/1VwN8h57rbff5GzMFPsxPipc59JmhrI0b?usp=sharing)

---
## Scope of Further Development
1. With more data the accuracy of model can be improved
2. Major part of data was of computer generated fonts, adding hand written text image the model can be more generalised.
3. The image preprocessing before prediction, have a sound scope of improvment.


