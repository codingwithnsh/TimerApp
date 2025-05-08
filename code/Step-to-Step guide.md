# Step-by-Step Guide: Building the Simple Countdown Timer App in MIT App Inventor

This guide provides instructions on how to construct the Simple Countdown Timer application using MIT App Inventor, based on the provided screenshots and inferred component usage.

## Step 1: Project Setup

1.  Navigate to the MIT App Inventor website (appinventor.mit.edu) and log in.
2.  Click **Projects** > **Start new project**.
3.  Enter a project name (e.g., `SimpleCountdownTimer`) and click **OK**.

## Step 2: Designing the User Interface (Designer View)

Switch to the **Designer** view.

1.  **Add Layout for Time Adjustment:**
    * From the **Palette** > **Layout**, drag a **`HorizontalArrangement`** onto the Viewer.
    * Select the `HorizontalArrangement`. In the **Properties** pane, set **`Width`** to `Fill parent` and **`AlignHorizontal`** to `Center`.

2.  **Add Plus and Minus Buttons and Text Box:**
    * From the **Palette** > **User Interface**, drag a **`Button`** into the `HorizontalArrangement`.
    * Select the `Button`. Set **`Text`** to `+`. Adjust size if needed.
    * *Optional but Recommended:* Rename to `PlusButton`.
    * From the **Palette** > **User Interface**, drag a **`TextBox`** into the `HorizontalArrangement` next to the Plus button.
    * Select the `TextBox`. Set **`Width`** to a suitable size (e.g., `80` pixels). Set **`TextAlignment`** to `Center`. Set initial **`Text`** to `0` or a default time. Set **`NumbersOnly`** to `true`.
    * *Optional:* Rename to `TimeTextBox`.
    * From the **Palette** > **User Interface**, drag another **`Button`** into the `HorizontalArrangement` next to the TextBox.
    * Select this `Button`. Set **`Text`** to `-`. Adjust size if needed.
    * *Optional:* Rename to `MinusButton`.

3.  **Add Start and Stop Buttons:**
    * From the **Palette** > **User Interface**, drag a **`Button`** onto the Viewer below the `HorizontalArrangement`.
    * Select the `Button`. Set **`Text`** to `Start`. Set **`Width`** to `Fill parent`.
    * *Optional:* Rename to `StartButton`.
    * From the **Palette** > **User Interface**, drag another **`Button`** onto the Viewer below the Start button.
    * Select this `Button`. Set **`Text`** to `Stop`. Set **`Width`** to `Fill parent`.
    * *Optional:* Rename to `StopButton`.

4.  **Add Non-visible Components:**
    * From the **Palette** > **Sensors**, drag a **`Clock`** component onto the Viewer. It will appear in the "Non-visible components" area.
    * Select the `Clock1`. In Properties, set **`TimerEnabled`** to `false` initially. Set **`TimerInterval`** to `1000` milliseconds (for a countdown in seconds).
    * From the **Palette** > **Media**, drag a **`Sound`** component onto the Viewer.
    * Select the `Sound1`. In Properties, click **`Source`** and upload your desired sound file (e.g., `alarm.mp3`).

Your Designer view should now contain components similar to the screenshot.

## Step 3: Programming the App Logic (Blocks Editor)

Click the **Blocks** button in the top right corner to switch to the Blocks Editor.

1.  **Plus Button Logic:**
    * Click on `PlusButton` (or your renamed button) in the Blocks pane on the left. Drag out the **`when PlusButton.Click do`** block.
    * Inside this block:
        * Click on `TimeTextBox` (or your renamed textbox). Drag out the **`set TimeTextBox.Text to`** block.
        * Click on **Built-in** > **Math**. Drag out the **`+`** addition block.
        * Click on `TimeTextBox`. Drag out the **`TimeTextBox.Text`** block and snap it into the first socket of `+`.
        * Click on **Built-in** > **Math**. Drag out a **`number`** block (with `1`) and snap it into the second socket of `+`.
        * Snap the `+` block into the `set TimeTextBox.Text` socket.

2.  **Minus Button Logic:**
    * Click on `MinusButton`. Drag out the **`when MinusButton.Click do`** block.
    * Inside this block:
        * Click on `TimeTextBox`. Drag out the **`set TimeTextBox.Text to`** block.
        * Click on **Built-in** > **Math**. Drag out the **`-`** subtraction block.
        * Click on `TimeTextBox`. Drag out the **`TimeTextBox.Text`** block and snap it into the first socket of `-`.
        * Click on **Built-in** > **Math**. Drag out a **`number`** block (with `1`) and snap it into the second socket of `-`.
        * Snap the `-` block into the `set TimeTextBox.Text` socket.

3.  **Start Button Logic:**
    * Click on `StartButton`. Drag out the **`when StartButton.Click do`** block.
    * Inside this block:
        * Click on `Clock1`. Drag out the **`set Clock1.TimerEnabled to`** block.
        * Click on **Built-in** > **Logic**. Drag out the **`true`** block and snap it into the socket.

4.  **Stop Button Logic:**
    * Click on `StopButton`. Drag out the **`when StopButton.Click do`** block.
    * Inside this block:
        * Click on `Clock1`. Drag out the **`set Clock1.TimerEnabled to`** block.
        * Click on **Built-in** > **Logic**. Drag out the **`false`** block and snap it into the socket.
        * Click on `Sound1`. Drag out the **`call Sound1.Play`** block.

5.  **Clock Timer Logic (The Countdown):**
    * Click on `Clock1`. Drag out the **`when Clock1.Timer do`** block. This block runs every time the `TimerInterval` (1000ms) passes, as long as `TimerEnabled` is true.
    * Inside this block:
        * Decrement the timer display:
            * Click on `TimeTextBox`. Drag out the **`set TimeTextBox.Text to`** block.
            * Click on **Built-in** > **Math**. Drag out the **`-`** subtraction block.
            * Click on `TimeTextBox`. Drag out the **`TimeTextBox.Text`** block and snap it into the first socket of `-`.
            * Click on **Built-in** > **Math**. Drag out a **`number`** block (with `1`) and snap it into the second socket of `-`.
            * Snap the `-` block into the `set TimeTextBox.Text` socket.
        * Check if the timer reached zero:
            * Click on **Built-in** > **Control**. Drag out an **`if then`** block.
            * Click on **Built-in** > **Logic**. Drag out the **`=`** comparison block.
            * Click on `TimeTextBox`. Drag out the **`TimeTextBox.Text`** block and snap it into the first socket of `=`.
            * Click on **Built-in** > **Math**. Drag out a **`number`** block (with `0`) and snap it into the second socket of `=`.
            * Snap the entire `=` block into the `if` condition socket.
        * If timer is zero:
            * Inside the `then` part of the `if` block:
                * Click on `Clock1`. Drag out the **`set Clock1.TimerEnabled to`** block.
                * Click on **Built-in** > **Logic**. Drag out the **`false`** block and snap it into the socket. (Stop the timer).
                * Click on `Sound1`. Drag out the **`call Sound1.Play`** block. (Play the sound).

Arrange your blocks neatly in the workspace. Your blocks should now look similar to the screenshot provided.

## Step 4: Testing the Application

1.  In the App Inventor web interface, click **Connect** in the top menu.
2.  Choose either "AI Companion" or "Emulator".
3.  Test the application on your device or emulator. Use the "+" and "-" buttons to set a time (e.g., 5). Tap **Start**. Verify that the number counts down every second. Test the **Stop** button and ensure the sound plays. Let the timer count down to zero and verify the sound plays and the timer stops.

You have successfully built the Simple Countdown Timer application!
