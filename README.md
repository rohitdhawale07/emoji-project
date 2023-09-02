# emoji-project

## Hosted Link :- https://rohitdhawale07.github.io/emoji-project/

This is the project of crating a web page whill will search the emojis.
when we type syambol name in search box the respective emoji will appear in front.
Firstly we created a simple HTML for search box and search button.
And searched emojis will appear in the below in result container.
HTML code for emojis project is as below:
## HTML code
```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Emoji project</title>
    <link rel="stylesheet" href="./style.css" />
  </head>
  <body>
    <div class="main">
      <h1>Emoji Searching App</h1>
      <br />
      <br />
      <div>
        <input value="" type="search" name="" id="searchBar" />

        <button id="submitButton">Search</button>
      </div>
      <div id="searchResultContainer"></div>
    </div>
    <script src="./index.js"></script>
    <script src="./emojiList.js"></script>
  </body>
</html>
```
After html we gave proper CSS Styling to the web page as below
## CSS 
```
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  body{
    background-color: black;
    color: white;
  }
  
  .main {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
  }
  
  h1 {
    border-bottom: 2px solid black;
    width: 100%;
    display: flex;
    justify-content: center;
    padding: 1rem;
    font-size: 3rem;
   
}
#searchBar{
    width: 400px;
    height: 30px;
    font-size: 1.2rem;

}
#submitButton{
    width: 80px;
    height: 30px;
    font-size: 1.2rem;
}
#submitButton:hover{
    background-color: black;
    color: white;
    cursor: pointer;
}
```
Searching for emojis we made one array of emojis consisting of objects of emoji data.
We get id's of input box and add button by getElementById() method.
Created elements h1 h2 h2 for displaying result format.
Created one function which will return the emoji as per search value.
and appened that search result in the below resultContainer.

## Javascript Code
```
const searchField = document.getElementById("searchBar");
const submitButton = document.getElementById("submitButton");
console.log(searchField, submitButton);

const searchEmoji = () => {

if(searchField.value !== ""){
submitButton.style.display = ""
}else{
submitButton.style.display = ""

}
console.log(submitButton)


  console.log("function called");
  const searchFieldValue = searchField.value;

  console.log(emojiList);
  const filteredList = emojiList.filter((e) => {
    if (e.aliases.some((ele) => ele.startsWith(searchFieldValue))) {
      return true;
    }
    if (e.tags.some((ele) => ele.startsWith(searchFieldValue))) {
      return true;
    }
  });
  const searchResultContainer = document.getElementById(
    "searchResultContainer"
  );
  searchResultContainer.innerText = "";
  filteredList.map((ele) => {
    console.log(ele);

    const emoji = document.createElement("h1");
    const description = document.createElement("p");
    const category = document.createElement("h3");

    emoji.innerText = ele.emoji;
    description.innerText = ele.description;
    category.innerText = ele.category;

    searchResultContainer.appendChild(emoji);
    searchResultContainer.appendChild(category);
    searchResultContainer.appendChild(description);
  });
};


if(searchField.value == ""){

	submitButton.style.display = "none"
}

submitButton.addEventListener("click", searchEmoji);
searchField.addEventListener("keyup", searchEmoji);

window.onload = () => searchEmoji()
```
