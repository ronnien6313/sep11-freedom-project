# Entry 5
##### 4/26/22

### Context

After making it so you can add and delete a card, It was time for our final part which is to make it so you can edit / update a card. In order to update a card, we need to import another tool from firebase which is `updateDoc`. These are all of our final imported tools.

```js
import{ initializeApp }from 'firebase/app'
import{
  getFirestore, collection, getDocs,
  addDoc, deleteDoc, getDoc, doc,
  onSnapshot, updateDoc
} from 'firebase/firestore'
```
Here is the code for updating a card :

```js
document.querySelector('#save').addEventListener('click', function(){ // line 1
  const docId = document.querySelector('#gone') // line 2
  const docRef = doc(db, 'cards', docId.innerHTML) // line 3
  updateDoc(docRef, {
    name: document.querySelector('#title').innerHTML // line 4
  })
  updateDoc(docRef, {
    notes: document.querySelector('#notes').innerHTML // line 5
  })
    updateDoc(docRef, {
    shortdescription: document.querySelector('#shortdescription').innerHTML // line 6
  })
  document.querySelector('.box').style.display = 'none' // line 7
})

```

Before I explain the code, How this app works right now is that there is a card that displays some of the information. When you click the card, a pop-up appears with all the information written down by the user. The way you edit these cards is by clicking on a section that allows the user to delete and write new information. The first line of code makes it so the save button listens for a click, which will update and save all of the information inside the card. Line 2  grabs the element that contains the ID of the card. Every card has a unique ID and we only want to work with one card at a time. Line 3 creates a constant that stores the actual ID of the card. By using this ID, we can call the information contained in the card, in this case, it is the title of the card, the notes, and the description. From lines 4 to 6, We use `updateDoc`, and by passing `docRef` we basically say that we want to access the information of the card we clicked and update it. We use `querySelector` to select the elements that contain information, and after that, line 7 closes the pop-up.

After changing the firebase information, we have to change the display information of the card prior to clicking on it. This is the code for that:

```
document.querySelector('#save').addEventListener('click',function(){
    names.innerHTML = document.querySelector('#title').innerHTML
    description.innerHTML = document.querySelector('#shortdescription').innerHTML
          
 })
```

It listens for the same click on the save button, But this time it changes the contents of the card outside of the pop-up. The way the card looks prior to clicking on it has the image, title, and description of the card, not the notes.

### EDP

I think that I and my partner are currently on Stage 6 or 7 of the EDP. We finished our MVP already and what's next is to make sure that it works well and possibly goes beyond our MVP. Right now, everything mostly works as intended, and going beyond MVP would be like adding Authentication. We can also do stuff like make the app look better and add more features like a search bar or sort the cards in alphabetical order, date added, etc.

### Skills

Some skills that I have learned from working towards the MVP are debugging and embracing failure. These two skills kind of go hand in hand because they both have to do with errors. Especially towards the end of our work, Me and my partner have been experiencing more errors than before. It seemed like updating and deleting docs were kind of confusing at times. Instead of just quitting after encountering errors, I and my partner worked together to figure out the problem. My partner especially helped me at times because we talked through whether or not code should go inside a certain loop or outside.

[Previous](entry04.md) | [Next](entry06.md)

[Home](../README.md)


