# svelte-firebase
Setup:
- Put this in a folder where your source code is and call this folder ``svelte-firebase``
- Do ``npm i firebase-tools`` to install firebase tools
- Run ``firebase login`` to login to firebase
- Get your firebase app configuration

Imports:
```javascript
import firebase from "firebase/app"
import "firebase/auth" //if you are using auth
import "firebase/firestore" //if you are using firestore
import { User, Doc, Collection } from "./svelte-firebase"
```

App Initialization:
```javascript
if (firebase.apps.length !== 0) {
  firebase.initializeApp({ /* config details*/ })
}
```

User Component:
```javascript
<User firebase={firebase} let:user>
  <div slot="loading">Loading...</div>
  <div slot="signed-out">Please Sign In!!!</div>
  Hi {user.displayName}!
</User>
```


Doc Component (this component will react automatically to changes in the Document) -- In this example I assume this Doc component is inside the User Component:
```javascript
<Doc firebase={firebase} path="/users/{user.uid}" let:id let:doc>
  <div slot="loading">Loading...</div>
  <div slot="fallback">Document doesnt exist :(</div>
  The doc id {id}. The doc data is {doc}.
</Doc>
```


Collection Component (this component will react automatically to changes in the Collection) -- In this example I assume this Collection component is inside the User Component:
```javascript
<Doc firebase={firebase} path="/users/{user.uid}/posts" let:collection>
  <div slot="loading">Loading...</div>
  <div slot="fallback">Collection doesnt exist :(</div>
  {#each Object.entries(collection) as doc}
    The doc id is {doc[0]}. The data is {doc[1]}
  {/each}
</Doc>
```
