# Effector persist
Micro package for create persists [effector](http://effector.now.sh) store. Like [redux-persist](https://github.com/rt2zz/redux-persist).

### Example:
```typescript
import {withPersist} from "effector-persist";
import { createStore, createEvent } from 'effector'

const store = withPersist(createStore([], {name: 'shops'}));
const addStore = createEvent<{name: string}>();

store.on(addStore, (state, store) => [...state, store]);
``` 

### How it works:
Every store update, `withPersist` cache result of update in LocalStorage with key `persist:<store_name>`.

When store is created `withPersist` restore previous state from snapshot in LocalStorage. 