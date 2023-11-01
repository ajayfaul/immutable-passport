# Immutable Passport Integration

Here are the complete guide for integrating Immutable Passport into an application, including the necessary code examples.

---

**Prerequisites:**

- Node.js and npm installed on your system
- Basic knowledge of HTML and JS
- Git and Text Editor
- Immutable Passport account / Developer Hub Account

To create a simple app that integrates Immutable Passport, you can either create a new project from scratch or clone an existing repository.

### Step into Immutable Passport Account

Once you have created or cloned the simple application, you need to register it on the Immutable Developer Hub. This will give you access to the Immutable Passport API and allow you to create and manage Immutable Passport users.

To register your application, follow these steps:

1. Go to the Immutable Developer Hub and click on the "Sign Up" button.
2. Create an account and verify your email address.
3. Once you have verified your email address, click on the "Create Project" button.
4. Enter a name and description for your application and select your immutable env.
5. After that, Select the "Immutable Passport" permission scope.
6. Create passport on passport configuration.
7. Once your project has been created, you will be given an immutable passport Client ID.

---

### **Installing and Initializing Passport Client Integration**

1. Install the Immutable Passport client library using npm:

   > npm install -D @imtbl/sdk

2. In your app.js file, import and initialize the Passport client using the credentials obtained from the Immutable Developer Hub:

```other
const client = new ImmutablePassport({
   baseConfig: ImmutableConfiguration;
  clientId: string;
  logoutRedirectUri: string;
  logoutMode?: 'redirect' | 'silent'; // defaults to 'redirect'
  redirectUri: string;
  scope?: string;
  audience?: string;
   });
```

### **Logging in a User with Passport**

1. Add an event listener to the login button in your HTML file:

   `<button id="login-button">Log In</button>`

2. In app.js, add code to handle the login button click event:

```other
try {
    const { idToken, accessToken, nickname } = await client.login();
    // Display the obtained user information on your application.
    console.log('ID Token:', idToken);
    console.log('Access Token:', accessToken);
    console.log('Nickname:', nickname);
    } catch (error) {
   console.error('Login error:', error);
   }
  });
```

### **Logging Out a User**

1. Add a logout button in your HTML:

   `<button id="logout-button">Log Out</button>`

2. Handle the logout button click event in app.js:

```other
client.logout();
    // Optionally, clear user information from your application interface.
   });
```

### **Initiating a Transaction from Passport**

To initiate a transaction using Passport, you need to interact with the Immutable blockchain. This typically involves sending assets or invoking a smart contract function. Implement this functionality according to your specific use case, using the access token obtained during the login step to authorize the transaction.

For example, if you want to send a placeholder string and obtain the transaction hash:

```other
// Define your transaction data
const transactionData = {
  to: 'RECIPIENT_ADDRESS',
  value: '0.001 ETH', // Specify the amount and currency you want to send.
  data: '0x' + Buffer.from('Hello, Immutable!', 'utf-8').toString('hex'), // Convert your string data to hexadecimal.
};

// Initiate the transaction
try {
  const transactionHash = await client.sendTransaction(transactionData);
  console.log('Transaction Hash:', transactionHash);
} catch (error) {
  console.error('Transaction error:', error);
}
```

Replace **'RECIPIENT_ADDRESS'** with the recipient's Ethereum address.

That's it! You've successfully integrated Immutable Passport into your application, allowing users to log in, log out, and initiate transactions on the Immutable blockchain.

---

### Reference:

[Install and initialise | Immutable Documentation](https://docs.immutable.com/docs/zkevm/products/passport/install/)

[](https://hub.immutable.com/)
