# Find_the_Chemical_Reaction
This is ML project done in collaboration with my friends, help in finding the reaction from internet taking reactants images as input. 

## **Content**
---
1. model.ipynb
2. find_reaction.ipynb
3. reactants.zip

## model.ipynb
---
# <#Srikar OP>

*Find Training Image Dataset from* [here](https://drive.google.com/file/d/1VtH9o5Vg34pHhDRlCqxi53BZIi6AYzDP/view?usp=sharing)
### Model Structure

<img width="432" alt="model" src="https://user-images.githubusercontent.com/76400354/128726402-e140d20f-bcbe-492b-8d17-d0bba89a26ca.png">




## find_reaction.ipynb

---


This file does three things 
* **Detection**: Locate the text in the image
* **Recognition**: Predict the text in the image
* **Searching Products**: Search the reaction from Internet 

Short explaination of functions defined:
1. #### Recognition
  *  **add_border**: Adds a white border around the image given as input i.e *img* to the funtion. The border is of width *bordersize*.
  *  **predict_char**: It takes *x1,x2,y1,y2* as input to get location of concerned character from *img*. Using pretrained model its predict the charcter class the image belongs to.
  *  **find_edges**: It locates the space around characters using a logic of logical_xor between pixcels.
  *  **find_character**: Using above three it returns the word in *imag*, i.e. taken as input.
2. #### Searching products
  *  **find_result**: It search the *reaction* from a website named *chemequations.com* using *AutoScraper* liabrary. 
3. #### Detection
  *  **find_reaction**: Using OpenCV it read image from the *path*. Then detect the location of text and makes bounding box around the same, pass those to *find_character* through loop. Through loop it collects the texts recognised.
    
## reactants.zip
---
Find the test images from this zip file. You may find more from [here](https://drive.google.com/drive/folders/1VwN8h57rbff5GzMFPsxPipc59JmhrI0b?usp=sharing)


