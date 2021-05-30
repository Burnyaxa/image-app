
# ***Saving(with code examples)

## Saving in File
You can save image as a file which needs to provide a file path with callback method when an edited image is saved
   
   ```
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

## Saving as Bitmap
You can also save image as a bitmap using saveAsBitmap provides a callback with saved bitmap

  ```
    mPhotoEditor.saveAsBitmap(new PhotoEditor.OnSaveBitmap() {
                    @Override
                    public void onBitmapReady(@NonNull Bitmap saveBitmap) {
                       Log.e("PhotoEditor","Image Saved Successfully");
                    }

                    @Override
                    public void onFailure(@NonNull Exception exception) {
                        Log.e("PhotoEditor","Failed to save Image");
                    }
                });
```

## Saving with Options
You can also provide your custom options while saving the edited image. 
  ```
   SaveSettings saveSettings = new SaveSettings.Builder()
                        .setClearViewsEnabled(true)
                        .setTransparencyEnabled(true)
                        .setCompressFormat(compressFormat)
                        .setCompressQuality(compressQuality)
                        .build();

    mPhotoEditor.saveAsFile(filePath,saveSettings,new PhotoEditor.OnSaveListener() {
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


Button saving:

[button]!(./img/button_saving.png)


Successful saving:

[sucsaving]!(./img/edit_screen.png)
