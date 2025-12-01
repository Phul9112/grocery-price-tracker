Grocery Pricing Tracker – Starter Files

This zip contains:
- index.html  → the full web app UI + logic
- README.txt  → this file

You only need to do 3 things:

1) Create a Firebase project
2) Copy/paste a few lines from Firebase into index.html
3) Run index.html on your computer

-----------------------------------
1. Create a Firebase project
-----------------------------------
1. Go to: https://console.firebase.google.com
2. Click “Add project”.
3. Name it something like: grocery-pricing
4. Finish the steps (you can skip Google Analytics).

-----------------------------------
2. Add a Web App in Firebase
-----------------------------------
1. In your Firebase project, click the Web </> icon (“Add app”).
2. Give it a name like: grocery-web.
3. Firebase will show you some code.

You need TWO pieces from that page:

A) The script tags (look like this, versions may differ):

   <script src="https://www.gstatic.com/firebasejs/10.x.x/firebase-app-compat.js"></script>
   <script src="https://www.gstatic.com/firebasejs/10.x.x/firebase-firestore-compat.js"></script>
   <script src="https://www.gstatic.com/firebasejs/10.x.x/firebase-storage-compat.js"></script>

B) The firebaseConfig object (looks like):

   const firebaseConfig = {
     apiKey: "ABC...",
     authDomain: "grocery-pricing.firebaseapp.com",
     projectId: "grocery-pricing",
     storageBucket: "grocery-pricing.appspot.com",
     messagingSenderId: "1234567890",
     appId: "1:1234567890:web:abcdef..."
   };

Keep that browser tab open.

-----------------------------------
3. Enable Firestore and Storage
-----------------------------------
In the left menu in Firebase console:

1. Click “Firestore Database” → “Create database” → Start in production mode → Continue.
2. Click “Storage” → “Get started” → Continue with defaults.

-----------------------------------
4. Edit index.html (one-time wiring)
-----------------------------------
Open index.html in a text editor (VS Code, Notepad, etc).

A) Paste the script tags

Near the bottom you’ll see this comment:

  <!-- PASTE YOUR FIREBASE SCRIPT TAGS FROM CONSOLE BELOW THIS LINE -->

Paste the 3 <script> lines from Firebase right under that comment.

B) Paste your firebaseConfig

In index.html, find this section:

  const firebaseConfig = {
    apiKey: "REPLACE_ME",
    authDomain: "REPLACE_ME",
    projectId: "REPLACE_ME",
    storageBucket: "REPLACE_ME",
    messagingSenderId: "REPLACE_ME",
    appId: "REPLACE_ME"
  };

Replace that whole object with the one Firebase gave you.

Save the file.

-----------------------------------
5. Run the app on your computer
-----------------------------------
Simplest way: tiny local web server using Python.

1. Put index.html and README.txt in a folder, for example:
   - Windows:  C:\grocery-app
   - Mac:      /Users/yourname/grocery-app

2. Open a terminal / command prompt in that folder:
   - Windows: open the folder in File Explorer, click the address bar, type “cmd” and hit Enter.
   - Mac: open Terminal and run:
       cd /Users/yourname/grocery-app

3. Run this command:

   python -m http.server 8000

4. In your browser, go to:

   http://localhost:8000/index.html

If your Firebase config is correct, you’ll see:
- “Grocery Pricing” at the top
- The UI with Stores / Items, etc.

-----------------------------------
6. How to use the app
-----------------------------------
• Add stores (right panel)
  - Type store name (Costco, Walmart, etc).
  - Click “Add”.
  - Remove with the small “✕”.

• Add items (left panel)
  - Enter item name, optional category, optional photo.
  - Click “Add item”.

• Set prices
  - In each item card, you’ll see a row per store.
  - Type the price and click “Save”.
  - This updates current price AND logs it in price history with date/time.

• Bulk edit
  - Click “Bulk Edit” to turn it on.
  - Check the items you want.
  - Enter:
    - A category and click “Apply category”, and/or
    - A store + price and click “Apply price”.
  - Turn bulk mode off when done.

• Price history
  - Click “📈 History” on an item.
  - Choose a store in the dropdown.
  - You’ll see a line chart of that store’s price for this item over time.

• Photos
  - Click “📷 Photo” on an item.
  - Choose an image; it uploads to Firebase Storage and updates the item.

• Export / Import
  - “Export” downloads a JSON file that contains everything (stores, items, prices, history).
  - “Import” lets you pick a JSON backup and write it back into Firestore.

• Sync across devices
  - Open the same index.html (or later, a hosted version) on laptop, phone, etc.
  - As long as they point to the same Firebase project, changes sync in near-real-time.
  - “Sync” button triggers a manual refresh if you want it.

-----------------------------------
7. If you get stuck
-----------------------------------
If something doesn’t work:
- Take a screenshot or copy the exact error message.
- Come back to ChatGPT and paste it.
- Say what step you were on (example: “after I pasted firebaseConfig”).

We can then fix it line-by-line.
