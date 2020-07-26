# svlete-firebase
- put this in a folder where ur source code is called svelte-firebase. this library currently supports firebase auth and firestore. also do ``npm i firebase-tools``

```javascript
import firebase from "firebase/app"
import "firebase/auth" //if you are using auth
import "firebase/firestore" //if you are using firestore
import { User, Doc, Collection } from "./svelte-firebase"
```
