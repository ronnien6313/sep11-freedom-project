# Entry 3
##### 2/10/22

### Content

Tutorial : [Auth Tutorial from 11 to 13](https://www.youtube.com/watch?v=n-kUZw97-lA&list=PL4cUxeGkcC9jERUGvbudErNCeSZHWUVlb&index=11)

So far, What I focused on learning about on Firebase was Firestore, their real-time database. But since the last blog, I stated that I wanted to learn how to use Firebase Authentication over winter break, and that's exactly what I did. Although I did not dive too deep into it, it was pretty cool to learn and I hope to implement it into my MVP. 

So just like Firestore, I need to import some tools from Firebase under `import{}`. The tools that I have imported this time are `getAuth`, `createUserWithEmailAndPassword`, `signOut`, and `signUpWithEmailAndPassword`. Just like their names suggest, I need `getAuth` is basically just Authentication, `createUserWithEmailAndPassword` helps register a new user, `signOut` logs them out, and `signUpWithEmailAndPassword` allows them to login. The import code looks like this :

```js
import{
  getAuth,
  createUserWithEmailAndPassword,
  signOut, signInWithEmailAndPassword
} from 'firebase/auth'
```

The next thing I did was create a `const` called "auth" that stores the `getAuth` information.

After that is the first block of code which allows users to sign up.

```js
const signUpForm = document.querySelector('.signup')
signUpForm.addEventListener('submit', (e) => {
  e.preventDefault()

  const email = signUpForm.email.value
  const password = signUpForm.password.value

 createUserWithEmailAndPassword(auth, email, password)
 .then((cred) => {
   console.log('user created:', cred.user)
   signUpForm.reset()
 })
 .catch((err) => {
   console.log(err.message)
 })

   
})
```

What the code first does is use `addEventListener` to basically make it so when the user pressed the button it fires the next block of code. We then write two consts, `email` and `password` to store the users email and password.It then uses `createUserWithEmailAndPassword` to create the users account by taking in their email and password. Finally, it notifies us that the account has been created in the console and then logs any errors.

The next part in Auth is logging in a user.

```js
const logOutButton = document.querySelector('.logout')
logOutButton.addEventListener('click', () => {
  signOut(auth)
  .then(() => {
    console.log('user signed out')
    .catch((err) => {
      console.log(err.message)
    })
  })
  
})
```

Just like the previous code it uses `addEventListener` to make it so on click it will sign out a user. To my knowledge, the difference between `submit` and `click` is that `click` makes the computer wait for a click, nothing more. But when we use `submit` it's kind of like passing through more data to the computer. 

The log out code isn't that complicated to understand as it is pretty straightfoward. It notifies us in the console that the user has signed out, and then proceeds to log into the console any errors we get.

The final thing I did for Auth is logging a user in.

```js
const logInForm = document.querySelector('.login')
logInForm.addEventListener('submit', (e) => {
  e.preventDefault()
  
  const email = logInForm.email.value
  const password = logInForm.password.value
  
   signInWithEmailAndPassword(auth, email, password)
   .then((cred) => {
     console.log('user logged in', cred.user)
   })
  .catch((err) =>{
    console.log(err.message)
  })
})
```

Once again, we use `addEventListener` to make it that when the button is presed the next block of code is fired. It then creates two consts, `email` and `password` which is the users information. It then uses `signInWithEmailAndPassword` to log the user in using the email and password from the `auth` const. The computer notifies us that the user has successfully logged in and then logs any errors into the console. But, If you type in the wrong user credentials, the code will return an error in the console saying that the credentials don't match.

### EDP

I think that I am still hovering around EDP stage 2 or 3 because I'm still learning more about my tool and what I can use to help reach my MVP. To be honest, I think that I will leave Auth out for a bit because I want to learn how I can display my firebase data on the page, not just the console so users can actually visualize what they put.

### Skills

The skills that I have learned while doing firebase so far is communication and time management. I have to convey to my partner what I'm learning and what he's learning so we can kind of be on the same page. We both wanted to learn Authentication and finish the tutorial so we could move on to something else. The next skill I learned so far is time management. I wouldn't say it is a skill I developed but a mistake I have learned from. When I was first learning firebase I had been managing my time well, but after awhile I started slacking a bit and started to slow down on the learning. But the wakeup call was when my blog was coming up and thats when I realised that I should start managing my time better.



[Previous](entry02.md) | [Next](entry04.md)

[Home](../README.md)
