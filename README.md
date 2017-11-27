# FontPlayWithXamForms
Hi,

I will be showing you a simple way to get Different Fonts working with Xamarin Forms app.
So, we have to go from screenshot 1 to screenshot 2 : 

<img src="https://github.com/SurajB-2601/FontPlayWithXamForms/blob/master/screenshots/FontPlay20.png" height="300" /> 

There are three simple steps, you just have to read carefully.

## For iOS
### 1. Adding the font files properly to your iOS project

  a. In iOS Fonts go under the Resources folder. Create a seperate folder for fonts under resources folder.
  
	b. Paste the needed fonts in this Resources -> Fonts Folder. Alternatively, you can also place it 
      directly under Resources Folder.
	   In the sample i have 2 Font types : 
	   One is Ageng Sans which is regular (Has single file agengsans.ttf)
	   Other is Raleway which when I downloaded, has different files for different font attributes like Bold, Light, Italic.
	   (Eg, Raleway-Bold.ttf, Raleway-Italic.ttf and RalewayLight.ttf)
     
<img src="https://github.com/SurajB-2601/FontPlayWithXamForms/blob/master/screenshots/FontPlay1.png" height="400" />  
     

### 2.Set the proper build action for the Font Files: 

  a. Now we have copied the files but we also have to set the build action to each of the font files as **BundleResource**. You can do that by      selecting all the fonts and set the build action to BundleResource in the properties window.
     We also have to set the **“Copy to Output Directory” flag to “Always Copy”**.
    These steps ensure that the font files go along with your app bundle and the app can access it.
    
    <img src="https://github.com/SurajB-2601/FontPlayWithXamForms/blob/master/screenshots/FontPlay5.png" height="400" />  
    
### 3.Make the font’s entry in Info.plist file: 

  a. You can do this by Right Click the info.Plist file. Select Open With --> Generic Plist Editor. Now, You have to add a new Custom          Property “Fonts Provided by Application”. Add the .ttf file name paths with respect to the Resources directory. Since we have put the       files in Fonts folder under Resources, we will set the file paths in the following way.
  
   <img src="https://github.com/SurajB-2601/FontPlayWithXamForms/blob/master/screenshots/FontPlay3.png" height="200" />  
   
  Try to directly copy paste the file names to avoid name conflict/mismatch.
  
  ### 4.The Most Important Part : Using the proper font name in the application.
  
  Now, If I double click Raleway-Italic.ttf file on windows, it will show the Font Name as “Raleway”. The Font Font window will have title as Raleway Italic(OpenType) and the File Name is “Raleway-Italic.ttf”. So the question is how should I properly refer the font.
The answer is for iOS you should use the Postscript Name of the font. To find the Postscript Name I downloaded a freeware by the name __“dp4fontviewer” (http://us.fontviewer.de/)__. So, after installing the font, I was able to get the font’s postscript name. 
Most of the times, you will see that the file name is the same as postscript name. So, the file name might work in some cases. So, For demo purpose, I changed the font file name from “Raleway-Italic.ttf” to “Raleway-It.ttf”. (In the project as well as in the info.plist)
If you will test it out, you will see that the correct font is displayed only when we choose the postscript name and not the file name.
  
  
## For Android

Now, we will try to use the fonts for android. In Android the steps are simple :

### 1. Add Font Files to Assets Folder :
We will make a seperate Fonts folder to add our font files.

### 2. Verify build action is Android Asset

 <img src="https://github.com/SurajB-2601/FontPlayWithXamForms/blob/master/screenshots/FontPlay4.png" height="400" />  
 
 ### 3. Refer the Font properly in XAML
 
 Refer the Font in your xaml as “Font Path Relative to Assets folder” + “#” + “Font name”. Here also, using the Postscript Name will work.
 Even if you want to use system fonts, the same fonts might not be available on different platforms. In that case you can download the fonts, and use the fonts in your required platforms by referring to their Postscript Name.


__Code for Xaml :__

```
<OnPlatform x:Key="AgengSansFont" 
                        x:TypeArguments="x:String" 
                        iOS="agengsans" 
                        Android="Fonts/agengsans.ttf#agengsans"
                        />
            <OnPlatform x:Key="RalewayBoldFont" 
                        x:TypeArguments="x:String" 
                        iOS="Raleway-Bold" 
                        Android="Fonts/Raleway-Bold.ttf#Raleway-Bold"
                        />
            <OnPlatform x:Key="RalewayItalicFont" 
                        x:TypeArguments="x:String" 
                        iOS="Raleway-Italic" 
                        Android="Fonts/Raleway-It.ttf#Raleway-Italic"
                        /> 
  ```
  
  Thanks,
  Suraj.
