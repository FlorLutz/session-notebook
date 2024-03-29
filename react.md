# React

## React Testing

- unit testing is testing pure functions (without side effects)
- now it is about testing components
- create a `fileName.test.js` in the specific component folder
- import component in the file, write test function, conventional names are "it" or "test"

```
import Movies from ".";
import { render, screen } from "@testing-library/react"

it("renders a movie list", ()=> {
  render(<Movies></Movies>)

  const headline = screen.getByRole("heading", {level: 1}) // looks for elements that are actually displayed on the screen

  expect(headline).toBeInTheDocument();
})
```

- necessary props should be provided in the test:

```
import Movie from ".";
import { render, screen } from "@testing-library/react"

it("renders a movie", ()=> {
  render(<Movie name="The Matrix"></Movie>)

  const matrixTitle = screen.getByRole("heading", {level: 2, name: "The Matrix}) // name in the screen method is referring to content displayed

  expect(matrixTitle).toBeInTheDocument();
})
```

- try to make the test fail in the beginning (for the above example, test for "Matrixi" first)
- functionalitites can also be tested, like buttons:

```
it("renders a movie when the form is submitted with a new movie name", async () => {
  render(<Movies initialMovies={initialMovies}></Movies>)

  const user = userEvent.setup();

  const input = screen.getByLabelText("Name")

  await user.type(input, "The Matrix") // asynchronous action

  const button = screen.getByRole("button", {
    name = "Add"
  })

  await user.click(button)

  const matrixHeading = screen.getByRole("heading", {name: "The Matrix"})

  expect(matricxHeading = screen.getByRole("heading", {name: "The Matrix"}))
})
```

## React Styled Components

- advantage is that we can have all styling in the js
- no classNames necessary
- install styled in package.json and import styled to js-file
- key - value pairs are equal as in regular css
- global styling done in styles.js

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
