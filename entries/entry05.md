# Entry 5
##### 4/26/22

### Context

After making it so you can add and delete a card, It was time for our final part which is to make it so you can edit / update a card. In order to update a card we need to import another tool from firebase which is `updateDoc`. These are all of our final imported tools.

```
import{ initializeApp }from 'firebase/app'
import{
  getFirestore, collection, getDocs,
  addDoc, deleteDoc, getDoc, doc,
  onSnapshot, updateDoc
} from 'firebase/firestore'
```
Here is the code for updating a card :

```
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

Before I explain the code, How this app works right now is that when you there is a card that displays some of the information from the card. When you click the card, a pop-up appears with all the information written down by the user. The way you edit these cards is by clicking on a section which allows the user to delete and write new information. The first line of code makes it so the save button listens for a click, which will update and save all of the information inside the card. The next line grabs the element that contains the ID of the card. Every card has a unique ID and we only want to work with one card at a time, not all. Line 3 creates a constant that stores the actual ID of the card. From lines 4 to 6, We use `updateDoc` and pass `docRef` so it updates only the card with the same ID. We use `querySelector` to select the elements that contain information, and after that, line 7 closes the pop-up.

After changing the firebase information, we have to change the display information of the card before we click on it. This is the code for that:

```
document.querySelector('#save').addEventListener('click',function(){
    names.innerHTML = document.querySelector('#title').innerHTML
    description.innerHTML = document.querySelector('#shortdescription').innerHTML
          
 })
```

It listens for the same click on the save button, But this time it changes the contents of the card outside of the pop-up.

[Previous](entry04.md) | [Next](entry06.md)

[Home](../README.md)
