# React

## React Testing

## React Styled Components

## React Global State

- alternative to very long prop drilling
- global state can be achieved by state management libraries like "zustand"
- states can be used directly in the components, wherer they are needed

```
import { create } from "zustand";

const useUserStore = create((set) => ({
  isLoggedIn: false,
  logIn: () => set(() => ({ isLoggedIn: true })),
  logOut: () => set(() => ({ isLoggedIn: false })),
}));

function App() {
  return <ProductsPage />;
}

function ProductsPage() {
  return <ProductsList />;
}

function ProductsList() {
  return products.map((product) => <ProductCard {...product} />);
}

function ProductCard() {
  return <ProductActions />;
}

function ProductActions() {
  const userIsLoggedIn = useUserStore((state) => state.isLoggedIn);

  return userIsLoggedIn ? (
    <button>One-click Buy</button>
  ) : (
    <button>Add to Basket</button>
  );
}
```

- do not overuse it, just for very nested components!

## React Immutable State

- never mutate the data stored with useState directly, use the setter function instead and if needed to get the former data, use spread before alternating any values, like

```
setUser({
  ...user,
  email: "john_doe@example.com",
});
```

- "immer" library helps to update values in deeply nested data structures
- use the useImmer hook:

```
// useState → useImmer
// setUser → updateUser
const [user, updateUser] = useImmer({
  name: "John Doe",
  contact: {
    email: "john@doe.com",
    phone: {
      mobile: "+001111111111",
      work: "+001234567890",
    },
  },
});
```

- update function receives a callback function and a draft as parameter:

```
updateUser((draft) => {
  // Mutate the draft directly
  draft.contact.phone.mobile = "+009999999999";
});
```

Whether to use immer or not depends on personal preference and on the complexity of the data structure. With deeper nested structures using immer might allow you to create simpler code.

## React Data Fetching

- data fetching library has advantages over useEffect and fetch
- SWR used, see details in the sessions
