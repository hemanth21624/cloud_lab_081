# Experiment 9: Use Google App Engine Launcher to Launch Web Applications

**Name:** K.Hemanth kumar  
**USN:** 4SF23CS081  

## Aim
To use Google App Engine Launcher to launch web applications.

## Prerequisites
- Google App Engine SDK with Google App Engine Launcher installed
- Python runtime installed
- Text editor (e.g., jEdit, VS Code, or Notepad)
- Web browser

## Procedure

### Step 1: Create the Application Directory
1. Create a working directory, for example:
   ```
   C:\Documents and Settings\<user>\Desktop\apps
   ```
2. Inside the `apps` directory, create a sub-folder named `ae-01-trivial`:
   ```
   C:\Documents and Settings\<user>\Desktop\apps\ae-01-trivial
   ```

### Step 2: Create Configuration File (`app.yaml`)
Using a text editor, create a file named `app.yaml` inside the `ae-01-trivial` directory with the following contents:

```yaml
application: ae-01-trivial
version: 1
runtime: python
api_version: 1

handlers:
- url: /.*
  script: index.py
```

### Step 3: Create Application Script (`index.py`)
In the `ae-01-trivial` directory, create a file called `index.py` with three lines:

```python
print 'Content-Type: text/plain'
print ''
print 'Hello there Chuck'
```

### Step 4: Add Existing Application in Launcher
1. Open the **GoogleAppEngineLauncher** application from Applications / Start Menu.
2. In the menu bar, navigate to **File** > **Add Existing Application**.
3. Browse to the `apps` directory and select the `ae-01-trivial` folder.
4. Once the application is added, select it from the list so you can control it using the launcher.

### Step 5: Run the Application
1. Select the application (`ae-01-trivial`) and click the **Run** button.
2. After a few moments, the application will start, and the launcher will show a green icon next to your application indicating it is active.

### Step 6: Browse the Web Application
1. Click the **Browse** button or open a web browser and navigate to:
   ```
   http://localhost:8080/
   ```
2. The browser displays:
   ```
   Hello there Chuck
   ```

### Step 7: Modify the Application Output
1. Edit the `index.py` file to replace `"Chuck"` with your own name:
   ```python
   print 'Content-Type: text/plain'
   print ''
   print 'Hello there Hemanth'
   ```
2. Save the file.
3. Refresh the browser at `http://localhost:8080/` to verify your updates.

### Step 8: View Server Logs
1. Select the application in the Google App Engine Launcher and click the **Logs** button to open the Log Console window.
2. You can view the internal log of server operations:
   - Each time you refresh the browser, the log console records the incoming request, such as `"GET / HTTP/1.1" 200`.

---

### Dealing with Errors
With two files to edit, there are two general categories of errors that may occur:
- **`app.yaml` Errors:** If there is a mistake in `app.yaml`, the App Engine server will fail to start, and the launcher will display a yellow warning icon next to the application. Check the log console for syntax or configuration issues.
- **`index.py` Errors:** If there is an error in `index.py`, requests to `http://localhost:8080/` may produce an HTTP 500 error or crash the worker. The Log Console will provide detailed traceback information to help debug.

## Output
- The web application runs successfully locally on `http://localhost:8080/` through the Google App Engine Launcher.
- The web browser renders the plain-text output from `index.py`.
- Refreshing the web browser displays updated content, and the Log Console tracks every incoming HTTP GET request with status code 200.

## Result
Successfully configured and launched a Python web application using Google App Engine Launcher, verified the local deployment via a web browser, modified the application output, and monitored server logs using the Log Console.
