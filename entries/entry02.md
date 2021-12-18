# Entry 2
##### 11/13/21

### Content

During the past few weeks I have been learning more and more about firebase. To be more specific, I've been learning how to get documentations, add documentations, and delete documentations. The first thing I did was initialize my firebase project, when creating a project on firebase firestore, it usually already gives you the code you need to initialize, so I just copy and pasted it into my script.js. The next thing I did was search up some type of tutorial that can teach me how to get, add, and delete docs and the one I found was [this](https://www.youtube.com/watch?v=s1frrNxq4js&list=PL4cUxeGkcC9jERUGvbudErNCeSZHWUVlb&index=5) tutorial. The first thing I learned is that if you want to use a tool in firestore, you have to type what tool you want under `import {}`. The tools I needed are `getFirestore, collection, getDocs, addDocs, deleteDocs, doc`. This is how I imported these tools - 

```js
import {
    getFirestore, collection, getDocs,
    addDoc, deleteDoc, doc
} from 'firebase/firestore'
```
The next the I did from the tutorial was add some data to my firestore collection. I made a collection called games, added a few game names, and wrote the developer of each one. After that, I created two constants

```js
const db = getFirestore()

const colRef = collection(db, 'games')
```
The first const called db and assigned it to getFirestore() which basically gives me access to Firestore. The second const is called colRef which basically goes into my firestore collection and grabs `games`. `games` stores the data of the game names and their developers.

Next thing I learned was how to get documents and see them in the console.

```js
getDocs(colRef)
  .then(snapshot => {
    console.log(snapshot.docs)
    let books = []
    snapshot.docs.forEach(doc => {
      books.push({ ...doc.data(), id: doc.id })
    })
    console.log(books)
  })
  .catch(err => {
    console.log(err.message)
  })
```
This code basically gets the documents from my games collection, colRef. It takes a snapshot of the document which allows us to read the data. It creates a variable using `let`, assigning it the array it will push. Next thing it does it push the documents into the array and logs it into the console. The last part is for errors.

The next thing I did was learn how to add and delete documents.

```js
const addGameForm = document.querySelector('.add')
addGameForm.addEventListener('submit', (e) => {
    e.preventDefault()

    addDoc(colRef, {
        name: addGameForm.name.value,
        developer: addGameForm.developer.value,
    })
    .then(() => {
        addGameForm.reset()
    })
})
```

Let's start with adding documents. The first thing the code does is create a constant called addGameForm which creates a document that will be added to the output. The next thing it does is create a working button that allows it to actually go through with the code. Next thing it does it use `addDoc` to basically add the name and developer of the game to colRef. Finally, after you press submit on the button, the bar resets it's word.

```js
const deleteGameForm = document.querySelector('.delete')
deleteGameForm.addEventListener('submit', (e) => {
    e.preventDefault()

    const docRef = doc(db, 'games', deleteBookForm.id.value)
    deleteDoc(docRef)
    .then(() => {
      deleteBookForm.reset()
    })
})
```

Finally we have deleting documents.  Just like adding documents the code creates a constant that will remove a document from the database. It then creates a constant called docRef which goes into the database, into games, and then takes the id of the document that you want to delete. `deleteDoc(docRef)` then deletes the doc that the id represents.


### EDP



### Skills



[Previous](entry01.md) | [Next](entry03.md)


[Home](../README.md)
