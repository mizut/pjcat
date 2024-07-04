# pjcat

`pjcat` (Project Cat) is a command-line tool that consolidates and displays the contents of text files in a project. It's designed to streamline the process of project inspection and analysis, making it particularly useful when working with AI language models like ChatGPT or Claude. By providing a comprehensive view of your project's files, `pjcat` enables developers to quickly gather and format project information, making it easy to input into Large Language Models (LLMs) for code review, documentation generation, or problem-solving assistance.

Key features include:
- Efficient aggregation of project file contents
- Customizable file inclusion/exclusion options
- Output formatting optimized for LLM input
- Quick project overview for manual inspection or AI-assisted analysis

Whether you're conducting a code review, seeking AI assistance for refactoring, or generating project documentation, `pjcat` simplifies the process of collecting and presenting your project's contents in a format that's both human-readable and AI-friendly.

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

## Sample Output

Here's an example of what the output might look like when running `pjcat` on a simple project:

```
% cd /path/to/projectdir/
$ pjcat -i ".gitignore"

=== Directory and File List ===
.gitignore
README.md
src/
src/index.js
src/utils/
src/utils/helper.js
tests/
tests/index.test.js

==== .gitignore ====
node_modules/
.DS_Store
*.log


==== README.md ====
# Sample Project

This is a sample project to demonstrate the usage of pjcat.

## Installation

npm install


==== src/index.js ====
const helper = require('./utils/helper');

function main() {
    console.log('Hello, world!');
    helper.doSomething();
}

main();


==== src/utils/helper.js ====
function doSomething() {
    console.log('Doing something useful...');
}

module.exports = {
    doSomething
};


==== tests/index.test.js ====
const assert = require('assert');
const helper = require('../src/utils/helper');

describe('Helper', () => {
    it('should do something', () => {
        // This is just a placeholder test
        assert.strictEqual(typeof helper.doSomething, 'function');
    });
});


```

This sample output shows:
1. A directory and file list of the project
2. The contents of each text file in the project
3. Clear separation between files with headers and blank lines

Using this output, you can quickly get an overview of your project structure and file contents, making it easy to share with AI assistants or review yourself.


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