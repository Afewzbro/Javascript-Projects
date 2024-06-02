OOP, or Object Oriented Programming, is one of the major approaches to the software development process. In OOP, developers use objects and classes to structure their code.

In this shopping cart project, you'll learn how to define classes and use them. You'll create class instances and implement methods for data manipulation.

This project will cover concepts like the ternary operator, the spread operator, the this keyword, and more.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### Explanation of the Shopping Cart Code

#### HTML Elements
The code starts by grabbing references to several HTML elements that will be used to display and interact with the shopping cart and products:

```javascript
const cartContainer = document.getElementById("cart-container");
const productsContainer = document.getElementById("products-container");
const dessertCards = document.getElementById("dessert-card-container");
const cartBtn = document.getElementById("cart-btn");
const clearCartBtn = document.getElementById("clear-cart-btn");
const totalNumberOfItems = document.getElementById("total-items");
const cartSubTotal = document.getElementById("subtotal");
const cartTaxes = document.getElementById("taxes");
const cartTotal = document.getElementById("total");
const showHideCartSpan = document.getElementById("show-hide-cart");
let isCartShowing = false;
```

#### Products List
The `products` array holds the list of available products:

```javascript
const products = [
  { id: 1, name: "Vanilla Cupcakes (6 Pack)", price: 12.99, category: "Cupcake" },
  // other products...
];
```

#### Display Products
Products are displayed on the page using `innerHTML`:

```javascript
products.forEach(({ name, id, price, category }) => {
  dessertCards.innerHTML += `
    <div class="dessert-card">
      <h2>${name}</h2>
      <p class="dessert-price">$${price}</p>
      <p class="product-category">Category: ${category}</p>
      <button id="${id}" class="btn add-to-cart-btn">Add to cart</button>
    </div>
  `;
});
```

#### ShoppingCart Class
This class manages the shopping cart's state and operations:

```javascript
class ShoppingCart {
  constructor() {
    this.items = [];
    this.total = 0;
    this.taxRate = 8.25;
  }
```

##### Adding Items to Cart
The `addItem` method adds products to the cart and updates the UI:

```javascript
addItem(id, products) {
  const product = products.find((item) => item.id === id);
  this.items.push(product);

  const totalCountPerProduct = {};
  this.items.forEach((dessert) => {
    totalCountPerProduct[dessert.id] = (totalCountPerProduct[dessert.id] || 0) + 1;
  });

  const currentProductCount = totalCountPerProduct[product.id];
  const currentProductCountSpan = document.getElementById(`product-count-for-id${id}`);

  currentProductCount > 1
    ? currentProductCountSpan.textContent = `${currentProductCount}x`
    : productsContainer.innerHTML += `
      <div id="dessert${id}" class="product">
        <p>
          <span class="product-count" id="product-count-for-id${id}"></span>${name}
        </p>
        <p>${price}</p>
      </div>
    `;
}
```

##### Getting Item Count
The `getCounts` method returns the total number of items in the cart:

```javascript
getCounts() {
  return this.items.length;
}
```

##### Clearing the Cart
The `clearCart` method clears all items from the cart and updates the UI:

```javascript
clearCart() {
  if (!this.items.length) {
    alert("Your shopping cart is already empty");
    return;
  }

  const isCartCleared = confirm("Are you sure you want to clear all items from your shopping cart?");
  if (isCartCleared) {
    this.items = [];
    this.total = 0;
    productsContainer.innerHTML = "";
    totalNumberOfItems.textContent = 0;
    cartSubTotal.textContent = 0;
    cartTaxes.textContent = 0;
    cartTotal.textContent = 0;
  }
}
```

##### Calculating Taxes
The `calculateTaxes` method calculates the tax for a given amount:

```javascript
calculateTaxes(amount) {
  return parseFloat(((this.taxRate / 100) * amount).toFixed(2));
}
```

##### Calculating Total
The `calculateTotal` method calculates the subtotal, tax, and total cost:

```javascript
calculateTotal() {
  const subTotal = this.items.reduce((total, item) => total + item.price, 0);
  const tax = this.calculateTaxes(subTotal);
  this.total = subTotal + tax;
  cartSubTotal.textContent = `$${subTotal.toFixed(2)}`;
  cartTaxes.textContent = `$${tax.toFixed(2)}`;
  cartTotal.textContent = `$${this.total.toFixed(2)}`;
  return this.total;
}
```

#### Event Listeners
Handles adding items to the cart, showing/hiding the cart, and clearing the cart:

```javascript
const cart = new ShoppingCart();
const addToCartBtns = document.getElementsByClassName("add-to-cart-btn");

[...addToCartBtns].forEach((btn) => {
  btn.addEventListener("click", (event) => {
    cart.addItem(Number(event.target.id), products);
    totalNumberOfItems.textContent = cart.getCounts();
    cart.calculateTotal();
  });
});

cartBtn.addEventListener("click", () => {
  isCartShowing = !isCartShowing;
  showHideCartSpan.textContent = isCartShowing ? "Hide" : "Show";
  cartContainer.style.display = isCartShowing ? "block" : "none";
});

clearCartBtn.addEventListener("click", cart.clearCart.bind(cart));
```

### Summary
- **HTML Elements**: References to key elements for displaying the cart and products.
- **Products**: An array of available products.
- **Display Products**: Generates product cards with "Add to cart" buttons.
- **ShoppingCart Class**: Manages the cart's items, including adding items, calculating totals, and clearing the cart.
- **Event Listeners**: Handles user interactions like adding items to the cart, showing/hiding the cart, and clearing the cart.