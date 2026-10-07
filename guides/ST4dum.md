# Using the SillyTavern Extension for Dummies

This is a very informal guide on how to use the SillyTavern extension for Alethia. These are the steps I personally took and tested. **Your mileage may vary (YMMV).**

## Installation

### 1\. Download and extract the extension

Download the ZIP file and extract it.

The extracted folder should be named:

```
v01.0a_ST_EXTENSION
```

### 2\. Install the SillyTavern extension

Move the `aletheia-bridge` folder into:

```
SillyTavern-Launcher/SillyTavern/public/scripts/extensions/third-party/
```

### 3\. Choose a location for the Alethia application

Keep the general extension folder somewhere convenient. This is where you will run the Python application from and where the RAG database will be stored.

For example, I moved mine to my `Documents` directory.

### 4\. Install the Python requirements

Inside the `ST_EXTENSION` directory, install the required Python packages from `requirements.txt`:

```
python3 -m pip install -r requirements.txt
```

### 5\. Run the application

Start the Alethia application with:

```
python3 app.py
```

**Keep this Python program open and running while you use the extension.**

### 6\. Launch SillyTavern

Launch SillyTavern as you normally would.

The exact instructions for doing this will depend on how you initially installed SillyTavern and your particular setup.

> **Important:** Keep the Python program from the previous step running while using SillyTavern.

## Setting Up the Personas

### 7\. Create the personas

Once SillyTavern has launched, create the following two personas:

- **The Librarian**
- **The Archivist**

### 8\. Archive messages

You should now be able to use the **Archive Last Message** button, which is located in the **Extensions** tab.

Use this to archive messages from **The Archivist**.

### 9\. Add files to the Data Bank

Before speaking with **The Librarian**, make sure you add your files using the **Data Bank** option.

You can find **Data Bank** by clicking the **wand** icon in SillyTavern.

> **Note:** As mentioned on the main page, you may occasionally need to re-vectorize files in the Data Bank. See the [SillyTavern Data Bank documentation](<https://docs.sillytavern.app/usage/core-concepts/data-bank/>) for more information.


## Quick Summary

If you just want the short version:

1. Extract `v01.0a_ST_EXTENSION`.
2. Move `aletheia-bridge` into SillyTavern's `third-party` extensions directory.
3. Put the main extension/application folder somewhere convenient.
4. Install the Python requirements:

```
   python3 -m pip install -r requirements.txt
```

5. Start the application:

```
   python3 app.py
```

6. Keep the Python application running.
7. Launch SillyTavern.
8. Create **The Librarian** and **The Archivist** personas.
9. Use **Archive Last Message** to archive messages from **The Archivist**.
10. Add your files through **Data Bank** before talking to **The Librarian**.
11. Re-vectorize your Data Bank files when necessary.
