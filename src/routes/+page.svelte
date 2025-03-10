<script>
    let encryptInput = '';
    let decryptInput = '';
    
    // Function for simple Caesar cipher encryption (shift by 3)
    function encryptText(text) {
      return text.split('').map(char => {
        let code = char.charCodeAt(0);
        if (code >= 65 && code <= 90) {  // Uppercase letters (A-Z)
          return String.fromCharCode((code - 65 + 3) % 26 + 65);
        } else if (code >= 97 && code <= 122) {  // Lowercase letters (a-z)
          return String.fromCharCode((code - 97 + 3) % 26 + 97);
        }
        return char;  // Return non-alphabetic characters unchanged
      }).join('');
    }
  
    // Function for simple Caesar cipher decryption (shift by 3)
    function decryptText(text) {
      return text.split('').map(char => {
        let code = char.charCodeAt(0);
        if (code >= 65 && code <= 90) {  // Uppercase letters (A-Z)
          return String.fromCharCode((code - 65 - 3 + 26) % 26 + 65);
        } else if (code >= 97 && code <= 122) {  // Lowercase letters (a-z)
          return String.fromCharCode((code - 97 - 3 + 26) % 26 + 97);
        }
        return char;  // Return non-alphabetic characters unchanged
      }).join('');
    }
  
    // Function to handle encryption and update the encrypted input
    function saveEncryptValue() {
      encryptInput = encryptText(encryptInput);  // Encrypt the input text
      console.log('Encrypted value: ', encryptInput);  // Log the encrypted value
    }
  
    // Function to handle decryption and update the decrypted input
    function saveDecryptValue() {
      decryptInput = decryptText(decryptInput);  // Decrypt the input text
      console.log('Decrypted value: ', decryptInput);  // Log the decrypted value
    }
  </script>
  
  <style>
    :global(body) {
      background-color: gray;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }
  
    .boxMiddle {
      background-color: white;
      width: 500px;
      height: 650px;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  
      display: flex;
      flex-direction: column;  /* Stack the content vertically */
      justify-content: center;
      align-items: center;
      text-align: center;
    }
  
    form {
      display: flex;
      flex-direction: column;
      gap: 15px;  /* Space between input fields and buttons */
    }
  
    input, button {
      padding: 10px;
      font-size: 16px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
  
    input[type="button"] {
      background-color: #4CAF50;
      color: white;
      border: none;
      cursor: pointer;
    }
  
    input[type="button"]:hover {
      background-color: #45a049;
    }
  </style>
  
  <div class="boxMiddle">
    <h1>Enter the text to Encryt or Decrypt here</h1>
    <form>
      <input type="text" placeholder="Enter to encrypt" bind:value={encryptInput}>
      <input type="text" placeholder="Enter to decrypt" bind:value={decryptInput}>
      <input type="button" value="Submit Encrypt" on:click={saveEncryptValue}>
      <input type="button" value="Submit Decrypt" on:click={saveDecryptValue}>
    </form>
  </div>
  