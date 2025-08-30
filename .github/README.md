# Swift Devcontainter Template

Template to build a swift devcontainer based on the Microsoft Devcontainer Ubuntu Base image.
Installs latest stable Swift version via swiftly.
Adds bash completions for swift and swiftly.

Static Linux SDK installation can be added by uncommenting respective parts in the Dockerfile.
At the moment this needs to be checked on [Install Swift](https://www.swift.org/install/linux/),
to get the most recent install command that matches the installed Swift version.

## License

Tread this template as MIT licensed. The license file itself is placed at `.github/LICENSE` to prevent copying when cloning the template. Github will not automatically identify this license.

Any project based on this template can select its own license.

## Credits

Some code in this project was adapted from [swift-server/swift-devcontainer-template](https://github.com/swift-server/swift-devcontainer-template) from the Swift on Server team.  
Licensed under MIT.