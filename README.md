// Import ethers.js library
const ethers = require('ethers');

// Function to connect to the Ethereum network using Metamask provider
async function connectToMetamask() {
  if (window.ethereum) {
    try {
      await window.ethereum.request({ method: 'eth_requestAccounts' });
      return new ethers.providers.Web3Provider(window.ethereum);
    } catch (error) {
      throw new Error('Connect to Metamask and try again.');
    }
  } else {
    throw new Error('Metamask not detected. Please install Metamask extension.');
  }
}

// Replace contractAddress and contractABI with your deployed contract's address and ABI
const contractAddress = '0x...'; // Replace with your contract address
const contractABI = [...]; // Replace with your contract ABI

// Function to get the greeting message from the contract
async function getGreeting() {
  try {
    const provider = await connectToMetamask();
    const signer = provider.getSigner();
    const contract = new ethers.Contract(contractAddress, contractABI, signer);
    const greeting = await contract.getGreeting();
    console.log('Greeting:', greeting);
  } catch (error) {
    console.error('Error:', error.message);
  }
}

// Function to set a new greeting message in the contract
async function setGreeting(newGreeting) {
  try {
    const provider = await connectToMetamask();
    const signer = provider.getSigner();
    const contract = new ethers.Contract(contractAddress, contractABI, signer);
    const tx = await contract.setGreeting(newGreeting);
    await tx.wait();
    console.log('New greeting set successfully');
  } catch (error) {
    console.error('Error:', error.message);
  }
}

// Call the functions to interact with the contract
getGreeting();
// Uncomment the line below and replace 'New Greeting Message' with the desired message to set a new greeting
// setGreeting('New Greeting Message');

// Import ethers.js library
const ethers = require('ethers');

// Function to connect to the Ethereum network using Metamask provider
async function connectToMetamask() {
  if (window.ethereum) {
    try {
      await window.ethereum.request({ method: 'eth_requestAccounts' });
      return new ethers.providers.Web3Provider(window.ethereum);
    } catch (error) {
      throw new Error('Connect to Metamask and try again.');
    }
  } else {
    throw new Error('Metamask not detected. Please install Metamask extension.');
  }
}

// Replace contractAddress and contractABI with your deployed contract's address and ABI
const contractAddress = '0x...'; // Replace with your contract address
const contractABI = [...]; // Replace with your contract ABI

// Function to get the greeting message from the contract
async function getGreeting() {
  try {
    const provider = await connectToMetamask();
    const signer = provider.getSigner();
    const contract = new ethers.Contract(contractAddress, contractABI, signer);
    const greeting = await contract.getGreeting();
    console.log('Greeting:', greeting);
  } catch (error) {
    console.error('Error:', error.message);
  }
}

// Function to set a new greeting message in the contract
async function setGreeting(newGreeting) {
  try {
    const provider = await connectToMetamask();
    const signer = provider.getSigner();
    const contract = new ethers.Contract(contractAddress, contractABI, signer);
    const tx = await contract.setGreeting(newGreeting);
    await tx.wait();
    console.log('New greeting set successfully');
  } catch (error) {
    console.error('Error:', error.message);
  }
}

// Call the functions to interact with the contract
getGreeting();
// Uncomment the line below and replace 'New Greeting Message' with the desired message to set a new greeting
// setGreeting('New Greeting Message');


<!DOCTYPE html>
<html>
<head>
  <title>Smart Contract Interaction</title>
</head>
<body>
  <h1>Smart Contract Interaction</h1>
  <div>
    <label for="newGreeting">New Greeting:</label>
    <input type="text" id="newGreeting" />
    <button onclick="setNewGreeting()">Set Greeting</button>
  </div>
  <div>
    <button onclick="getGreeting()">Get Greeting</button>
    <div id="greetingResult"></div>
  </div>

  <!-- ethers.js library -->
  <script src="https://cdn.ethers.io/lib/ethers-5.5.0.min.js"></script>
  <!-- your JavaScript file to interact with the smart contract -->
  <script src="app.js"></script>
</body>
</html>


// Function to get the greeting message from the contract
async function getGreeting() {
  try {
    const provider = await connectToMetamask();
    const signer = provider.getSigner();
    const contract = new ethers.Contract(contractAddress, contractABI, signer);
    const greeting = await contract.getGreeting();
    document.getElementById('greetingResult').innerText = `Greeting: ${greeting}`;
  } catch (error) {
    console.error('Error:', error.message);
    document.getElementById('greetingResult').innerText = `Error: ${error.message}`;
  }
}

// Function to set a new greeting message in the contract
async function setNewGreeting() {
  const newGreeting = document.getElementById('newGreeting').value;
  if (!newGreeting) return; // Do not proceed if the input is empty

  try {
    const provider = await connectToMetamask();
    const signer = provider.getSigner();
    const contract = new ethers.Contract(contractAddress, contractABI, signer);
    const tx = await contract.setGreeting(newGreeting);
    await tx.wait();
    console.log('New greeting set successfully');
    document.getElementById('greetingResult').innerText = 'New greeting set successfully';
  } catch (error) {
    console.error('Error:', error.message);
    document.getElementById('greetingResult').innerText = `Error: ${error.message}`;
  }
}

// Uncomment the line below and replace 'New Greeting Message' with the desired message to set a new greeting
// setGreeting('New Greeting Message');
