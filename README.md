# pjcat

`pjcat` (Project Cat) is a command-line tool that displays the contents of text files in a project. It's designed to help developers quickly inspect and analyze the contents of their project files while providing options to customize the output.

## Features

- Display contents of text files in a project
- Exclude binary files, common directories (e.g., node_modules, .git), and specific patterns
- Include files or directories that are excluded by default
- Option to include binary files in the output
- Customizable file search patterns

## Installation

1. Clone this repository or download the `pjcat` script.
2. Make the script executable:
   ```
   chmod +x pjcat
   ```
3. Move the script to a directory in your PATH, for example:
   ```
   sudo mv pjcat /usr/local/bin/
   ```

## Usage

```
pjcat [OPTIONS] [SEARCH_PATTERN]
```

### Options

- `-h, --help`: Show the help message and exit
- `-e, --exclude PATTERN`: Exclude files/directories matching the specified pattern (additional)
- `-i, --include PATTERN`: Include files/directories that are excluded by default
- `-b, --include-binary`: Include binary files in the output

### Arguments

- `SEARCH_PATTERN`: Regular expression pattern to match filenames (default: ".*")

### Examples

1. Display contents of all text files in the project:
   ```
   pjcat
   ```

2. Display contents of all JavaScript files:
   ```
   pjcat ".*\.js$"
   ```

3. Display contents of all JavaScript and TypeScript files, excluding the "dist" directory and temporary files:
   ```
   pjcat -e "dist" -e "*.tmp" ".*\.(js|ts)$"
   ```

4. Include the "node_modules" directory (which is excluded by default) but exclude the "build" directory:
   ```
   pjcat -i "node_modules" -e "build" ".*"
   ```

5. Include binary files in the output:
   ```
   pjcat -b ".*"
   ```

## Customization

You can customize the default excluded directories and file extensions by modifying the `binary_extensions` and `text_extensions` variables in the script.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is open source and available under the [MIT License](LICENSE).

## Support

If you encounter any problems or have any questions, please open an issue in this repository.