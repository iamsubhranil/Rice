1. Contributor : [iamsubhranil](github.com/iamsubhranil)

2. Riced Component : lightdm-webkit2-greeter

3. Screenshot : [lightdm-webkit2-greeter_executive_shot_1.jpg](https://github.com/iamsubhranil/Rice/blob/master/Screenshots/lightdm-webkit2-greeter_executive_shot_1.png)

4. Requirements : 
    - [LightDM](https://www.freedesktop.org/wiki/Software/LightDM/)
    - [LightDM-Webkit2-Greeter](https://github.com/antergos/web-greeter)
    - [Aether](https://github.com/NoiSek/Aether)
    - Patience

5. Steps :
    - Install and activate LightDM for your distro. [(ArchWiki)](https://wiki.archlinux.org/index.php/LightDM)
    - Install lightdm-webkit2-greeter. If you use Arch, [this AUR package](https://aur.archlinux.org/packages/lightdm-webkit2-greeter/) will set up everything for you. If you do not, following building options provided at the page. fire up `/etc/lightdm/lightdm.conf` in your favourite text editor with root priviledges and write `lightdm-webkit2-greeter` as the `greeter-session` option under `[Seat:*]`.
    ```
    ...
    [Seat:*]
    ...
    greater-session = lightdm-webkit2-greeter
    ...
    ```
     - Install Aether. Again if you use Arch, [this package](https://aur.archlinux.org/packages/lightdm-webkit2-greeter/) will do it for you. Otherwise, prefer the instructions on the link provided.
     - Here comes the actual styling part. To enable switching wallpaper and showing default user image, open `/etc/lightdm/lightdm-webkit2-greeter.conf` with write priviledges and edit the following :
    ```
    ...
    [branding]
    background_images = /usr/share/lightdm-webkit/themes/lightdm-webkit-theme-aether/src/img/wallpapers/
    logo              = /usr/share/lightdm-webkit/themes/lightdm-webkit-theme-aether/src/img/arch-logo.png
    user_image        = /usr/share/lightdm-webkit/themes/lightdm-webkit-theme-aether/src/img/default-user.png
    ```
     - You can add more wallpapers to `background_images` location to have more wallpapers switching options.
     - To have thinner fonts in username field, do the following steps :
        - Download OpenSans light in WOFF from [here](http://google-webfonts-helper.herokuapp.com/api/fonts/open-sans?download=zip&subsets=latin&variants=300)
        - Extract the zip into `/usr/share/lightdm-webkit/themes/lightdm-webkit-theme-aether/src/font/` and rename the font to `OpenSans-Light-webfont.woff`
        - Open `/usr/share/lightdm-webkit/themes/lightdm-webkit-theme-aether/src/css/style.css` in editor and add the following 
            ```
            font-style: italic; }

            @font-face {
            font-family: 'Open Sans';
            src: url("../font/OpenSans-Light-webfont.woff") format("woff");
            font-weight: 300;
            font-style: normal; }

            ::-webkit-scrollbar {
            ```
        - Modify `.user-panel .login-panel-main .login-form .user-username` to look like the following
            ```
            user-panel .login-panel-main .login-form .user-username {
                text-align: center;
                text-transform: capitalize;
                font-size: 42px;
                font-style: normal;
                font-weight: 300; }
            ```
        - Save `style.css` and close it.
     - Reboot, and the login screen should show now. The next bunch of modifications are to be performed directly from the login screen.
     - Hover the mouse to the bottom left corner, you should see an options button. Click it.
        - Under the `Style` tab, change `Border Radius` to `30px`
        - Under the `Themes` tab, apply `Glass` 
        - Switch back to `Style` tab, then change the colors as following RGBA
            - Command Panel
                - Background : 19 1 1 0.67
                - Icon Color : 133 40 40 1
            - Login Panel
                - Border Enabled : No (Should see a `X` icon)
                - Gradient Top : 10 5 5 0.67
                - Gradient Bottom : 14 7 7 1
                - Button Color : 9 6 6 1
        - Switch to `General` tab, then change the time format to `%l:%M %p` for 12 hour clock
        - Press `save` button. Additionally, save the config as a theme with a name of your choice from the `Themes` tab
        - Close the config window
        - ENJOY


5. Credits :
    - FreeDesktop.org(LightDM)
    - Antergos(lightdm-webkit2-greeter)
    - [NoiSek](github.com/NoiSek)(Aether)
