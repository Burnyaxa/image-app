# **Bussiness logic(code and screenshots)


## Features

- [**Drawing**](#drawing) on image with option to change its Brush's Color, Size, Opacity and Erasing.
- Apply [**Filter Effect**](#filter-effect) on image using MediaEffect
- Adding/Editing [**Text**](#text) with option to change its Color with Custom Fonts.
- Adding [**Emoji**](#emoji) with Custom Emoji Fonts.
- Adding [**Images/Stickers**](#adding-imagesstickers)
- Pinch to Scale and Rotate views.
- [**Undo and Redo**](#undo-and-redo) for Brush and Views.
- [**Deleting**](#deleting) Views
- [**Saving**](#saving) Photo after editing.


## Drawing
We can customize our brush and paint with different set of property. To start drawing on image we need to enable the drawing mode

![](https://i.imgur.com/INi5LIy.gif)

| Type  | Method |
| ------------- | ------------- |
| Enable/Disable  | `mPhotoEditor.setBrushDrawingMode(true);` |
| Brush Size (px)  | `mPhotoEditor.setBrushSize(brushSize)` |
| Color Opacity (In %)  |   `mPhotoEditor.setOpacity(opacity)`  |
| Brush Color | `mPhotoEditor.setBrushColor(colorCode)`  |
| Brush Eraser  | `mPhotoEditor.brushEraser()` |

**Note**: Whenever we set any property of a brush for drawing it will automatically enable the drawing mode



## Filter Effect
We can apply inbuild filter to the source images using 

 `mPhotoEditor.setFilterEffect(PhotoFilter.BRIGHTNESS);`

![](https://i.imgur.com/xXTGcVC.gif)

We can also apply custom effect using `Custom.Builder`

For more details check [Custom Filters](https://github.com/burhanrashid52/PhotoEditor/wiki/Filter-Effect)



## Text

![](https://i.imgur.com/491BmE8.gif)

We can add the text with inputText and colorCode like this

`mPhotoEditor.addText(inputText, colorCode);` 

It will take default fonts provided in the builder. If we want different fonts for different text we can set typeface with each text like this

`mPhotoEditor.addText(mTypeface,inputText, colorCode);`

In order to edit the text we need the view, which we will receive in our PhotoEditor callback. This callback will trigger when we **Long Press** the added text

 ```java
 mPhotoEditor.setOnPhotoEditorListener(new OnPhotoEditorListener() {
            @Override
            public void onEditTextChangeListener(View rootView, String text, int colorCode) {
                
            }
        });
  ```
Now we can edit the text with a view like this

`mPhotoEditor.editText(rootView, inputText, colorCode);`

If you want more customization on text. Please refer the wiki page for more details.


## Emoji

![](https://i.imgur.com/RP8kqz6.gif)

We can add the Emoji by `PhotoEditor.getEmojis(getActivity());` which will return a list of emojis unicode.

`mPhotoEditor.addEmoji(emojiUnicode);`

It will take default fonts provided in the builder. If we want different Emoji fonts for different emoji we can set typeface with each Emoji like this

`mPhotoEditor.addEmoji(mEmojiTypeface,emojiUnicode);`




## Adding Images/Stickers
 We need to provide a Bitmap to add our Images  `mPhotoEditor.addImage(bitmap);`
 
 
 

## Undo and Redo

![](https://i.imgur.com/1Y9WcCB.gif)

 ```java
   mPhotoEditor.undo();
   mPhotoEditor.redo();
 ```
 


## Deleting
  For deleting a Text/Emoji/Image we can click on the view to toggle the view highlighter box which will have a close icon. So, by clicking on the icon we can delete the view.
  
  
  

## Saving
   
   We need to provide a file with callback method when edited image is saved
   
   ```java
    mPhotoEditor.saveAsFile(filePath, new PhotoEditor.OnSaveListener() {
                    @Override
                    public void onSuccess(@NonNull String imagePath) {
                       Log.e("PhotoEditor","Image Saved Successfully");
                    }

                    @Override
                    public void onFailure(@NonNull Exception exception) {
                        Log.e("PhotoEditor","Failed to save Image");
                    }
                });
```
