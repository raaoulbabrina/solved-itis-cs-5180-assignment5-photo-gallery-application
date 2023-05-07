Download Link: https://assignmentchef.com/product/solved-itis-cs-5180-assignment5-photo-gallery-application
<br>
In this assignment we are going to make a Photo Gallery application, which will use a URL that retrieves a text file containing a dictionary of keywords and image URLs related to the associated keyword. The application consists of a single activity that enables the user to download and view online photos.

APIs:

<ul>

 <li>(Get Keywords API) To get the list of possible keywords:</li>

 <li>URL : <a href="http://dev.theappsdr.com/apis/photos/keywords.php">http://dev.theappsdr.com/apis/photos/keywords.php</a> Method : GET</li>

 <li>Output : returns the possible keywords separated by “;”. For example: android;aurora;uncc;winter;wonders</li>

 <li>(Get Urls API) To get photos for a given keyword:</li>

 <li>URL : <a href="http://dev.theappsdr.com/apis/photos/index.php">http://dev.theappsdr.com/apis/photos/index.php</a>          Method : GET</li>

 <li>Parameter:</li>

 <li>keyword : is the keyword selected by the user.</li>

 <li>Output: returns the photo urls for images related to this keyword with each url on a separate line. For example for a keyword parameter set to winter the following output is returned</li>

</ul>

https://c2.staticflickr.com/6/5538/11966402046_fbd73d52e9_c_d.jpg              https://c1.staticflickr.com/5/4010/4255115508_e21a09138c_z_d.jpg               https://c2.staticflickr.com/4/3746/11948232454_bd5cfd5b8f_c_d.jpg              https://c1.staticflickr.com/9/8474/8413293701_4c63cb5ff8_c_d.jpg

<ul>

 <li>Note: The retrieved text contains a url in each separate line. The “keyword” is the search keyword. For example, “weather” returns 4 URLs associated with it. Other keywords may have more or less.</li>

</ul>

<strong>Figure 1, Application Wireframe</strong>

<strong>Figure 2, App Wireframe</strong>

<strong>Figure 3, App Wireframe</strong>

<strong>Loading Images based on Keywords </strong>

The interface should be created to match the user interface (UI) presented in Figure 1. You will be using layout files, and strings.xml to create the user interface. Perform the following tasks:

<ol>

 <li>When the activity starts, the keyword api should be called to get the list of possible keywords. The keyword api should be called using an AsyncTask.</li>

 <li>Clicking on the “Go” Button should display a list of keywords as shown in Figure 2(a). You can either Alert Dialog or Spinner to implement it.</li>

 <li>Clicking on a Keyword should do the following:

  <ol>

   <li>The TextView will hold the search keyword clicked by the user.</li>

   <li>Use AsyncTask/Thread to connect to the Get URLs API and retrieve the list of image urls related to the selected keyword.</li>

  </ol></li>

 <li>When the api data is retrieved:

  <ol>

   <li>Use another AsyncTask/Thread to retrieve the first image associated with the keyword and display it in the ImageView.</li>

   <li>The AsyncTask/Thread class should be in a separate file/class not inner to the main thread. i.e. You should manage passing parameters to the class and then pass back the result image downloaded to the UI.</li>

   <li>While the image is being retrieved, you should display a Progress Dialog as indicated in Figure 3(b).</li>

  </ol></li>

 <li>The Next and Previous photo icons should be disabled when the application is launched, and enabled after the first photo is displayed. The buttons will also remain disabled in the case there is only 1 image or there are no images corresponding to a keyword. Use icons provided in Support Files for setting the image icons (<strong>png, prev.png</strong>)</li>

 <li><strong>Do not</strong> store the photos, simply download and display the retrieved photos. Also do not attempt to download all the URLs receive, and your app should only download and display a single photo at any given time.</li>

 <li>Upon clicking the “Next Photo” icon, you should download the next photo in list of URLs retrieved (following the of order of appearance in the URL list retrieved). You should call the AsyncTask/ Thread used to download the next photo.

  <ol>

   <li>If the currently displayed photo happens to be the last photo, you should download and retrieve the photo at index 0 (the first photo) when the Next icon is pressed.</li>

  </ol></li>

 <li>Clicking the “Previous Photo” icon, you should download the previous photo. If the currently displayed photo happens to be the first photo, you should download and retrieve the photo at the last index position (last photo).</li>

 <li>If the api returns an empty list of urls, then clear the currently displayed ImageView and display an error Toast message “No Images Found”.</li>

 <li>Your application should download the requested photo only if there is an established internet connection. If there is no internet connection you should display a Toast message indicting that there is no internet connection and do not attempt to send the HTTP request.</li>

</ol>