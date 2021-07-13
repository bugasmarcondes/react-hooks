## Custom hook

- Is a function that uses other hooks inside of it
- By convention, it should start with the prefix "use<Whatever-name-you-want>"
- Destructuring object and defaulting an empty value

```javascript
options = {
  serialize: JSON.stringify,
  deserialize: JSON.parse
}

==

{serialize = JSON.stringify, deserialize = JSON.parse} = {},
```

## Hook Flow

- (\*) Runs ALL the cleanups, then ALL the effects in the same order

<img src="./src/examples/hook-flow.png">

## State colocation

- State should be as close to where it is relevant as possible
- When specific state change it doesn't re-render the parent component

## State

- Managed State: State that you need to explicitly manage
- Derived State: State that you can calculate based on other state

## useRef

- Used to create a reference do a specific DOM node
- Used when you need to update a reference without triggering a re-render

# HTTP requests

```javascript
// option 1: using .catch
fetchPokemon(pokemonName)
  .then(pokemon => setPokemon(pokemon))
  .catch(error => setError(error))

// option 2: using the second argument to .then
fetchPokemon(pokemonName).then(
  pokemon => setPokemon(pokemon),
  error => setError(error),
)
```

- Using .catch means that you’ll handle an error in the fetchPokemon promise,
  but you’ll also handle an error in the setPokemon(pokemon) call as well. This
  is due to the semantics of how promises work.
- Using the second argument to .then means that you will catch an error that
  happens in fetchPokemon only. In this case, I knew that calling setPokemon
  would not throw an error (React handles errors and we have an API to catch
  those which we’ll use later), so I decided to go with the second argument
  option.
