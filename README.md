# VolumeExpoLerper - Unity Scene Global Volume Adjuster

VolumeExpoLerper is a Unity script designed to simplify the manipulation of the `PostExposure` in URP Global Volume for quick **fade-in**, **fade-out**, or **flashbang** **whiteouts**.

Developed in `2022.03.11f1 LTS`

## Usage

1. **Attach to GameObject**:
   - Attach the `VolumeExpoLerper.cs` script to GameObject and reference the `Global Volume` component to it.
   - Preferably, you can attach it to your `Global Volume` GameObject, which is usually at the top of your scene.

2. **Reference the GameObject containing the script**:

3. **Fade-In, Fade-Out, Flashbang!**:
   - Use `ChangeFromTo(startValue, endValue, duration, callback?)` to adjust the exposure.
   - Parameters:
     - `startValue`: The initial exposure value to be set.
     - `endValue`: The target exposure value after the duration.
     - `duration`: Duration of the transition in seconds.
     - `callback`: Optional callback function when the transition completes.


## Important!

- **Make sure you have a Global Volume**:
  - Ensure that your scene contains a GameObject with the Universal Render Pipeline (URP) Global Volume component.
  - Add `Color Adjustments` from Overrides and Enable/Tick the `PostExposure` field!

4. **Example Usage**:
   ```csharp
    public VolumeExpoLerper volume; // Attach the game object with the script


    void Start(){
        // Fade in to scene 1s
        volume.ChangeFromTo(-10f, 0f, 1f);
    }


    void Flashbang(){    
        // Flashbang 3s
        volume.ChangeFromTo(5f, 0f, 3f, ()=>{
            Debug.Log("You were blinded!");
        });
    }


    void Die(){
        // Fade out 4s
        volume.ChangeFromTo(0f, -5f, 4f, Respawn);
    }
    void Respawn(){
        // ...
    }

    ```


## License

This project is licensed under the [MIT License](LICENSE).
