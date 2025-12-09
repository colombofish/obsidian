html structure is called - HTML Boilerplate
<!DOCTYPE html> <!-- this shows the latest version of the html is used -->

Hyper links <a "href=https://www.google.co.uk">Google</a> [<tag "attribute=value" "another-Attribute=value">Content</tag>]
Look for mozilla development documentation for more details, and global attributes such as 'draggable="true"'
ex: <a "href=www.googl.com">Draggable Google </a>
<ol start="5"><li>apple</li><li>biscuit</li></ol> [here the start for the ol is set to 5]
<img src="https://picsum.photos/200" alt="A pic from picsum site"/> [size is set as 200 (px)]
url for the image is taken from https://picsum.photos to generate random pics.

File paths: relative vs absolute. Mainly the relative path is used for navigating or displaying images or info on the web page. ../image1.png etc. 

**Publishing your web-page on internet (GitHub)**:
1. GitHub (go and create a new repository. Make sure to keep the README file on, this will ease the uploading process)
2. Next, go to your folder where index.html and other relevant folders and files are there, drag and drop into the repository.
3. Once the contents are uploaded into the repository, click on the Commit button.
4. Next, go to Settings -> Pages, where change the Branch from None to Main or Your-settings (depending on your current naming convention) as /root folder, and Save it.
<input id="patch" type="submit" value="PATCH" formaction="/patch-secret">
Within the PATCH button above /formaction defines the route/path to take as a submit action. 

A sample form below, which is used in the Backend\5.5 Rest APIs

<form id="myForm" method="post">
      <label for="idInput">Id:</label>
      <input type="text" id="idInput" name="id">
      <label for="secretInput">Secret:</label>
      <input type="text" id="secretInput" name="secret">
      <label for="scoreInput">Score:</label>
      <input type="number" id="scoreInput" name="score">
      <label for="submit">Route:</label>
      <input id="get" type="submit" value="GET" formaction="/get-secret">
      <input id="post" type="submit" value="POST" formaction="/post-secret">
      <input id="put" type="submit" value="PUT" formaction="/put-secret">
      <input id="patch" type="submit" value="PATCH" formaction="/patch-secret">
      <input id="delete" type="submit" value="DELETE" formaction="/delete-secret">
    </form>
    
Note that the form method is a POST request for all 5 buttons, and formaction with the defined routes. 