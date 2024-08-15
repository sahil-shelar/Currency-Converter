# Currency Converter

This is a simple currency converter application built with React and Vite. The app allows users to convert an amount from one currency to another using the latest exchange rates. It also includes features like swapping the "from" and "to" currencies.

## Features

- **Convert Currency:** Enter an amount and convert it between different currencies.
- **Swap Currencies:** Easily swap the "from" and "to" currencies with a single click.
- **Custom Hook (`useCurrencyInfo`):** Fetches the latest currency exchange rates using a custom React hook.

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/currency-converter.git
    cd currency-converter
    ```

2. Install dependencies:
    ```bash
    npm install
    ```

3. Run the development server:
    ```bash
    npm run dev
    ```

4. Open your browser and go to:
    ```
    http://localhost:3000
    ```

## Usage

1. **Enter Amount:** Input the amount you want to convert in the "From" currency input field.
2. **Select Currencies:** Choose the currencies you want to convert from and to, using the dropdowns.
3. **Convert:** Click the "Convert" button to see the converted amount in the "To" field.
4. **Swap Currencies:** Click the "swap" button to swap the "from" and "to" currencies.

## Custom Hook: `useCurrencyInfo`

### Description

The `useCurrencyInfo` hook is a custom React hook designed to fetch and provide the latest currency exchange rates. It takes a currency code (e.g., `"usd"`) as an argument and returns an object containing the exchange rates for that currency against various other currencies.

### Usage

```javascript
import useCurrencyInfo from './hooks/useCurrencyInfo';

function App() {
  const currencyInfo = useCurrencyInfo("usd");
  const exchangeRateToInr = currencyInfo["inr"];
  // Use exchangeRateToInr in your component logic
}
```

### How It Works

- The hook fetches the exchange rates from the API provided by [@fawazahmed0/currency-api](https://github.com/fawazahmed0/currency-api).
- The data is stored in the component's state and is updated whenever the currency code passed to the hook changes.
- The hook ensures that the component using it always has the latest exchange rates.

### Example in App

In the `App` component, the `useCurrencyInfo` hook is used to fetch and display currency exchange rates:

```javascript
const currencyInfo = useCurrencyInfo(from);
const convertedAmount = amount * currencyInfo[to];
```

## Project Structure

```bash
├── public
│   └── index.html
├── src
│   ├── components
│   │   └── InputBox.jsx     # Input component for currency conversion
│   ├── hooks
│   │   └── useCurrencyInfo.js  # Custom hook for fetching currency info
│   ├── App.jsx              # Main application component
│   ├── index.css            # Global styles
│   └── main.jsx             # Entry point for React
├── tailwind.config.js       # Tailwind CSS configuration
├── package.json             # Project dependencies and scripts
└── README.md                # Project documentation
```

## Tailwind CSS Configuration

This project uses Tailwind CSS for styling. Ensure that Tailwind is properly configured by including the following in your `tailwind.config.js`:

```javascript
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

### Styling

- The project uses Tailwind CSS for responsive and utility-first styling.
- Components like buttons, forms, and containers are styled using Tailwind classes to ensure consistency and ease of customization.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
