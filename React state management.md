
![[Pasted image 20230902183135.png]]
![[Pasted image 20230902183149.png]]
## State
1. app data that may change over time
prefix enviornment variables with REACT_APP 
![[Pasted image 20230902185041.png]]
![[Pasted image 20230902185216.png]]
![[Pasted image 20230902185322.png]]
![[Pasted image 20230902185407.png]]
![[Pasted image 20230902185614.png]]
![[Pasted image 20230902185724.png]]
![[Pasted image 20230902185857.png]]
![[Pasted image 20230902185947.png]]
![[Pasted image 20230902190031.png]]
![[Pasted image 20230902190053.png]]
![[Pasted image 20230902190253.png]]
![[Pasted image 20230902203914.png]]
![[Pasted image 20230904084402.png]]

## Local storage
pass a function as the default parameter to useState
```jsx
export default function App() {
  const [cart, setCart] = useState(() =>
    JSON.parse(localStorage.getItem('cart'))
  );
```
## React persists event 
```jsx
  const [address, setAddress] = useState(emptyAddress);
  function handleChange(e) {
    e.perist();
    setAddress((curAddress) => {
      return { ...curAddress, [e.target.id]: e.target.value };
    });
  }
```
![[Pasted image 20230905045257.png]]
## fetch
```jsx
import { useState, useEffect, useRef } from 'react';
const baseUrl = process.env.REACT_APP_API_BASE_URL;

function useFetch(url) {
  const isMounted = useRef(false);
  const [data, setData] = useState(null);
  const [error, setError] = useState(null);
  const [loading, setLoading] = useState(true);
  useEffect(() => {
    isMounted.current = true;
    async function init() {
      try {
        const response = await fetch(baseUrl + url);
        if (response.ok) {
          console.log(response);
          const json = await response.json();
          if (isMounted.current) setData(json);
        } else {
          console.log('OOPS');
          throw response;
        }
      } catch (e) {
        if (isMounted.current) setError(e)
      } finally {
        if (isMounted.current) setLoading(false);
      }
    }
    init();
    return () => {
      isMounted.current = false;
    };
  }, [url]);
  return { data, error, loading };
}

export default useFetch;
```
![[Pasted image 20230906045625.png]]
## Context
![[Pasted image 20230906052249.png]]
```jsx
import React, { useEffect, useReducer } from 'react';
import cartReducer from './cartReducer';
export const CartContext = React.createContext(null);
let initialCart;
try {
  initialCart = JSON.parse(localStorage.getItem('cart')) ?? [];
} catch {
  console.error('The cart could not be parsed into JSON');
  initialCart = [];
}
export function CartProvider(props) {
  const [cart, dispatch] = useReducer(cartReducer, initialCart);
  useEffect(() => localStorage.setItem('cart', JSON.stringify(cart)), [cart]);
  return (
    <CartContext.Provider value={{ cart, dispatch }}>
      {props.children}
    </CartContext.Provider>
  );
}
```
```jsx
import React, { useEffect, useReducer, useContext } from 'react';
import cartReducer from './cartReducer';
const CartContext = React.createContext(null);
let initialCart;
try {
  initialCart = JSON.parse(localStorage.getItem('cart')) ?? [];
} catch {
  console.error('The cart could not be parsed into JSON');
  initialCart = [];
}
export function CartProvider(props) {
  const [cart, dispatch] = useReducer(cartReducer, initialCart);
  useEffect(() => localStorage.setItem('cart', JSON.stringify(cart)), [cart]);
  return (
    <CartContext.Provider value={{ cart, dispatch }}>
      {props.children}
    </CartContext.Provider>
  );
}
export function useCart() {
  const context = useContext(CartContext);
  return context;
}
```
