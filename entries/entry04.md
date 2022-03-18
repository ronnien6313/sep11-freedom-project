# Entry 4
##### 3/18/22

### Context

During SEP in the past few months, Me and my partner chose to learn about firebase in order to create an app that we though of. But after learning bits and pieces of firebase, it was time for me and my partner to start creating our MVP (Minimal Viable Product) for the Freedom Project. Our idea for the Freedom Project was to create an app where you can add cards that stored information. We broke this project down into little sections to be done over the next few weeks. My partner has already initialized the project and done `adding` cards to the DB, so it was time for me to write the code for visualizing and deleting the card.

When wanting to delete a doc, we had to import some tools from firebase. The tools that we needed in order to delete cards from firebase were deleteDoc, doc, and onSnapshot.

```js
import{
  getFirestore, collection, getDocs,
  addDoc, deleteDoc, getDoc, doc,
  onSnapshot
} from 'firebase/firestore'
```

After importing the tools, I thought about how can go about deleting. My thought process is as listed.

* I need to get the id of a document
* I need have a button that listens for a click
* I need to use querySelector
* I need to use innerHTML to show the contents of the card
*


```js
place.addEventListener('click',function(thing){
          document.querySelector('.box').style.display ='block'. // line 1
          let currentDoc = thing.target.nextElementSibling.children[2].innerHTML // line 2
          let docRef = doc(db, 'cards', currentDoc) // line 3
          
          // information variable
          var cardName = document.querySelector("#title")
          var cardDesc = document.querySelector("#shortdescription")
          var cardNote = document.querySelector("#notes")
          var cardImg = document.querySelector("#image")
          var cardid = document.querySelector('#gone')
          
          // shows the information
          onSnapshot(docRef, (doc) => {
            cardImg.src = doc.data().imgurl
            cardName.innerHTML = doc.data().name
            cardDesc.innerHTML = doc.data().shortdescription
            cardNote.innerHTML = doc.data().notes
            cardid.innerHTML =  currentDoc
          })
})
```

The code above is used to display the card information when you click. The first function gives every card an `eventListener` that waits for a click. Once clicked, It will create a popup that has all the contents of the card. The popup is done by using line 1, which basically activates the CSS that creates the popup. The next part is using `querySelector` in order to get the element that will contain the information of the card. The next part is creating a variable that contains the card's id. I don't really understand how line 2 works much, But my partnet helped me a little with that. After getting the doc id it was time to create another variable that will store where the doc id came from. Line 3 basically gets all of the information of the card clicked from our firbase database. We can then use `docRef` with `onSnapshot` to finally display the data. `onSnapshot` is a realtime listener which basically makes it so whenever a card is altered, the information displayed wil change immediately. We then pass the argument `docRef`, which fires an event where it will asign the `innerHTML` of the data to their respective places.

After visualizing information comes deleting.


```js
document.querySelector('#delete').addEventListener('click', function(event){
      deleteDoc(doc(db,'cards', document.querySelector('#gone').innerHTML))
      then(() => {
        document.querySelector('.box').style.display ='none'
        document.querySelector('.'+document.querySelector('#gone').innerHTML).remove()
      })
})
```

The 











[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)
