![[Pasted image 20230824040934.png]]

Display a list of elements
```js
ReactDOM.render(
  [<Button/>, <Display/>],
  document.getElementById('mountNode'),
);

```
or
```js
ReactDOM.render(
  <div>
    <Button/>
    <Display/>
  </div>,
  document.getElementById('mountNode'),
);
```
![[Pasted image 20230902201353.png]]
![[Pasted image 20230902203632.png]]
![[Pasted image 20230902203825.png]]
## useEffect with axios
```jsx
useEffect(() => {
    async function delayFunc() {
      try {
        const result = await axios.get(restUrl);
        console.log(result);
        // throw 'Had Error';
        setRequestStatus(REQUEST_STATUS.SUCCESS);
        setData(result.data);
      } catch (e) {
        setRequestStatus(REQUEST_STATUS.FAILURE);
        setError(e);
      }
    }
    delayFunc();
  }, []);
```
another example
```jsx
  useEffect(() => {
    async function delayFunc() {
      try {
        const result = await axios.get('http://localhost:3001/products');
        console.log(result); // throw 'Had Error';
        setProducts(result.data);
      } catch (e) {
        console.log('Could not fetch data');
      }
    }
    delayFunc();

  }, []);
```
![[Pasted image 20230902205855.png]]
![[Pasted image 20230902205949.png]]
![[Pasted image 20230902210033.png]]
## useEffect with fetch

using centrealized function
```jsx
const baseUrl = process.env.REACT_APP_API_BASE_URL;
export async function getProducts(category) {
  const response = await fetch(baseUrl + "products?category=" + category);
  if (response.ok) return response.json();
  throw response;
}
```
useEffect call
```jsx
  const [products, setProducts] = useState([]);
  const [size, setSize] = useState('');
  useEffect(() => {
    getProducts('shoes').then((response) => setProducts(response));
  }, []);
```
## ErrrorBoundary

```jsx
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {    // Update state so the next render will show the fallback UI.    return { hasError: true };  }

  render() {
    if (this.state.hasError) {      // You can render any custom fallback UI      return <h1>Something went wrong.</h1>;    }
    return this.props.children; 
  }
}

```
create error state
```jsx
  const [error, setError] = useState(null);
```
add error checking to useEffect
```jsx
  useEffect(() => {

    getProducts('shoes')
      .then((response) => setProducts(response))
      .catch((e) => setError(e))
      .finally(() => setLoading(false));
  }, []);
```
finally is there to set loading to false
throw new error before return statement
```jsx
  if (error) throw error;
  return (
    <>
      <div className='content'>
```
## useEffect refactor promise to async 
```jsx
  useEffect(() => {
    getProducts('shoes')
      .then((response) => setProducts(response))
      .catch((e) => setError(e))
      .finally(() => setLoading(false));
  }, []);
```
you can mark call back function as async you have to create a new function and call it inside the call back function
```jsx
  useEffect(() => {
    async function init() {
      try {
        const response = await getProducts('shoes');
        setProducts(response);
      } catch (e) {
        setError(e);
      } finally {
        setLoading(false);
      }
    }
    init();
  }, []);
```
![[Pasted image 20230903193108.png]]
![[Pasted image 20230903193211.png]]
