## How to install docker on windows home 
This is derived from this life saver https://itnext.io/install-docker-on-windows-10-home-d8e621997c1d

### Steps
- *install hypver*
    - create a bat file, good name is `InstallHyperV.bat`
    - add this snippet to it 
        ```
        pushd "%~dp0"
        dir /b %SystemRoot%\servicing\Packages\*Hyper-V*.mum >hyper-v.txt
        for /f %%i in ('findstr /i . hyper-v.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"
        del hyper-v.txt
        dism /online /enable-feature /featurename:Microsoft-Hyper-V -All /LimitAccess /ALL
        pause
        ```
    - run the bat file `InstallHyperV.bat`
    - do not restart PC

-  *install containers*
    - create a bat file, good name is `InstallContainers.bat`
    - add this snippet to it
        ```
        pushd "%~dp0"
        dir /b %SystemRoot%\servicing\Packages\*containers*.mum >containers.txt
        for /f %%i in ('findstr /i . containers.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"
        del containers.txt
        dism /online /enable-feature /featurename:Containers -All /LimitAccess /ALL
        pause
        ```
    - run the bat file `InstallContainers.bat`

- Restart your PC
- *Update windows version to Professional*
    - Press `Windows key + R`
    - enter `regedit`
    - navigate `\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT`
    - click on `CurrentVersion`
    - look for `EditionID`, click and select `modify`
    - update the value to `Professional`
    - press ok
- install docker 
- restart your pc, ensure that the `EditionID` is now back to `core`, if not repeat step `Update windows version to Professional` but set value to `core`
