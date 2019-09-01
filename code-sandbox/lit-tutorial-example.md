# Lit Example

This covers almost all basic examples of LitHtml

- Basic Templating
- Creating Properties
- Conditional Templating
- Repeating Template

## Lit - Basic Example

```javascript
//Imports
import { LitElement, html, css } from 'lit-element';

//Creating My Element Weeb Component
class MyElement extends LitElement {
  constructor() {
    super();
    this.message = "I am dynamic message";
    this.decision = false;
    this.items = ['Groceries', 'Monthly Rent', 'Credit Card'];
  }

//Setting up the styles
  static get styles() {
    return css`p {
      font-size: 20px;
    }
    .red {
      color: red;
    }
    .blue {
      color: blue;
    }
    `;
    
  }
  
 //Setting up the properties 
  static get properties() {
    return {
      message: {type: String},
      decision: {type: Boolean},
      items: {type: Array}
    };
  }

//Event Handler
  clickHandler(event) {
    console.log('Clicked Happened');
    this.decision = !this.decision;
  }

//Render Funcction
  render() {
    return html`
      <!-- TODO: Replace text content with your property -->
      <p>Hello world! From my-element</p>
      <p class="${this.decision ? 'blue' : 'red'}">I have message: ${this.message}</p> 
      <ul class="${this.decision ? 'blue' : 'red'}">
        ${this.items.map(item => html`<li>I have to for: ${item}</li>`)}
      </ul>

      ${(this.decision) ? html`<p>We are with the dicision</p>` : html`<p>We are against the decision</p>`}
      <button @click=${this.clickHandler}>Click Me</button>
    `;
  }
}
customElements.define('my-element', MyElement);
```