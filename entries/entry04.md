# Entry 4
##### 3/18/22

### Context

During SEP in the past few months, Me and my partner chose to learn about firebase in order to create an app that we thought of. But after learning bits and pieces of firebase, it was time for me and my partner to start creating our MVP (Minimal Viable Product) for the Freedom Project. Our idea for the Freedom Project was to create an app where you can add cards that stored information. We broke this project down into little sections to be done over the next few weeks. My partner has already initialized the project and done `adding` cards to the DB, so it was time for me to write the code for visualizing and deleting the card.

When wanting to delete a doc, we had to import some tools from firebase. The tools that we needed in order to delete cards from firebase were deleteDoc, doc, and onSnapshot.

```js
import{
  getFirestore, collection, getDocs,
  addDoc, deleteDoc, getDoc, doc,
  onSnapshot
} from 'firebase/firestore'
```

After importing the tools, I thought about how to go about deleting. My thought process is as listed.

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

The code above is used to display the card information when you click. The first function gives every card an `eventListener` that waits for a click. Once clicked, It will create a popup that has all the contents of the card. The popup is done by using line 1, which basically activates the CSS that creates the popup. The next part is using `querySelector` in order to get the element that will contain the information of the card. The next part is creating a variable that contains the card's id. I don't really understand how line 2 works much, But my partner helped me a little with that. After getting the doc id it was time to create another variable that will store where the doc id came from. Line 3 basically gets all of the information of the card clicked from our firebase database. We can then use `docRef` with `onSnapshot` to finally display the data. `onSnapshot` is a real time listener which basically makes it so whenever a card is altered, the information displayed will change immediately. We then pass the argument `docRef`, which fires an event where it will assign the `innerHTML` of the data to their respective places.

After visualizing information comes deleting.


```js
document.querySelector('#delete').addEventListener('click', function(event){
      deleteDoc(doc(db,'cards', document.querySelector('#gone').innerHTML)) // line 1
      then(() => {
        document.querySelector('.box').style.display ='none' // line 2
        document.querySelector('.'+document.querySelector('#gone').innerHTML).remove() // line 3
      })
})
```

What this does is make it so the delete button listens for a click, and when it is triggered it will delete the current card. What line one does is actually delete all of the card info. We use the `deleteDoc()` function, and pass the arguments `db, cards`. These two arguments basically just goes into our firestore database, we then pass the argument `document.querySelector('#gone').innerHTML`. This argument contains the unique ID of the card we want to delete. After deleting the card, we want to close the popup which is what line 2 does. What line 3 does is remove the card from the website, because not only do we have to delete the information, but the literal card itself.


### EDP

I think that I am currently on stage 5 of the EDP. Me and my partner are currently working towards our MVP (Minimal Viable Product). Once me and my partner finish the MVP, we can move on to stage 6 to make sure everything is working right. In order to get there, What we need to focus on next is making our cards editable. Our plan right now is to use the function `updateDoc` for that.

### Skills

The skills I have learned from working towards our MVP are Communication and Collaboration. Communication is important because there have been many times where I have had problems with my code and communicating with my partner was one of the best ways to solve them. Not only that but every Monday in class, we would communicate what our next steps should be and how the work would be split up. This would eventually bridge to Collaboration because everytime we finish our part, we would talk about what we should fix or change about our partner's code.



[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)
