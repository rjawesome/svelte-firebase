# svlete-firebase
- put this in a folder where ur source code is called svelte-firebase. this library currently supports firebase auth and firestore. also do ``npm i firebase-tools``

```javascript
import firebase from "firebase/app"
import "firebase/auth" //if you are using auth
import "firebase/firestore" //if you are using firestore
import { User, Doc, Collection } from "./svelte-firebase"
```

ok so now how to use the components. so first step is to inintialize ur firebase app alright. so do

```javascript
if (firebase.apps.length !== 0) {
  firebase.initializeApp({ /* config details*/ })
}
```

ok so now ur done with that. u can move on to the next step which is to use the user component. so here the user will be stored in a variable called user.
the slots will show if it is loading or user is not signed in. if it is in a slot it will not show the code which is not inside a slot

```javascript
<User let:user>
<div slot="loading">Loading...</div>
<div slot="signed-out">Please Sign In!!!</div>
Hi {user.displayName}!
</User>
```

