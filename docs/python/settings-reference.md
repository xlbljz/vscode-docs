---
ContentId: d256dc5c-95e9-4c02-a82f-947bf34a3517
DateApproved: 3/6/2023
MetaDescription: Settings Reference for the Python extension in Visual Studio Code
MetaSocialImage: images/tutorial/python-social.png
---
# Python settings reference

The Python Extension for Visual Studio Code is highly configurable. This page describes the key settings you can work with.

For general information about working with settings in VS Code, refer to [User and workspace settings](/docs/configure/settings.md), as well as the [Variables reference](/docs/reference/variables-reference.md) for information about predefined variable support.

## General Python settings

| Setting<br/>(python.) | Default | Description |
| --- | --- | --- |
| condaPath | `"conda"` | Path to the `conda` executable. |
| defaultInterpreterPath | `"python"` | Path to the default Python interpreter to be used by the Python extension on the first time it loads for a workspace, or the path to a folder containing the Python interpreter. <br> Can use variables like `${workspaceFolder}` and `${workspaceFolder}/.venv`. <br> Using a path to a folder allows anyone working with a project to create an environment in the `.venv` folder as appropriate to their operating system, rather than having to specify an exact platform-dependent path. The `settings.json` file can then be included in a source code repository. <br> **Note**: Changes to this setting made after an interpreter has been selected for a workspace will not be applied or considered by the Python extension. The Python extension doesn't automatically add or change this setting.|
| envFile | `"${workspaceFolder}/`<br/>`.env"` | Absolute path to a file containing environment variable definitions. <br> See [Configuring Python environments - environment variable definitions file](/docs/python/environments.md#environment-variable-definitions-file). |
| experiments.enabled | `true` |  Enables [A/B experiments in the Python extension](https://aka.ms/AAjvt9q). If enabled, you may be provided with proposed enhancements and/or features. |
| globalModuleInstallation | `false` | Specifies whether to install packages for the current user only using the `--user` command-line argument (the default), or to install for all users in the global environment (when set to `true`). Ignored when using a virtual environment. <br> For more information on the `--user` argument, see [pip - User Installs](https://pip.pypa.io/en/stable/user_guide/#user-installs). |
| interpreter.infoVisibility | `"onPythonRelated"` |  Controls when to display the selected interpreter information on the status bar. <br> By default, it only shows when there are Python related files open in the editor. <br> You can set it to `"always"` if you'd like it to always show on the status bar, or `"never"` to hide it entirely. |
| pipenvPath | `"pipenv"` | Path to the pipenv executable to use for activation. |
| poetryPath | `"poetry"` | Specifies the location of the [Poetry dependency manager](https://poetry.eustace.io/) executable, if installed. The default value `"poetry"` assumes the executable is in the current path. <br> The Python extension uses this setting to install packages when Poetry is available and there's a `poetry.lock` file in the workspace folder. |
| REPL.enableREPLSmartSend | `true`| Specifies whether `Shift+Enter` leverage Smart Send. Smart Send looks at the code where the cursor is placed, sends the smallest runnable chunk of code to the Python REPL, and then places your cursor at the next line of code. |
| terminal.activateEnvInCurrentTerminal | `false` | Specifies whether to activate the currently open terminal when the Python extension is activated, using the virtual environment selected. |
| terminal.activateEnvironment | `true` | Indicates whether to automatically activate the environment you select using the **Python: Select Interpreter** command when a new terminal is created.<br> For example, when this setting is `true` and you select a virtual environment, the extension automatically runs the environment's *activate* command when creating a new terminal (`source env/bin/activate` on macOS/Linux; `env\scripts\activate` on Windows). |
| terminal.executeInFileDir | `false` | Indicates whether to run a file in the file's directory instead of the current folder. |
| terminal.focusAfterLaunch | `false` | Whether to switch the cursor focus to the terminal when launching a Python terminal. |
| terminal.launchArgs | `[]` | Launch arguments that are given to the Python interpreter when you run a file using commands such as **Python: Run Python File in Terminal**.<br> In the `launchArgs` list, each item is a top-level command-line element that's separated by a space (quoted values that contain spaces are a single top-level element and are thus one item in the list). <br> For example, for the arguments `--a --b --c {"value1" : 1, "value2" : 2}`, the list items should be `["--a", "--b", "--c", "{\"value1\" : 1, \"value2\" : 2}\""]`. <br> Note that VS Code ignores this setting when debugging because it instead uses arguments from your selected debugging configuration in `launch.json`. |
| venvFolders | `[]` | Paths to folders where virtual environments are created. <br> Depending on the virtualization tool used, it can be the project itself: `${workspaceFolder}`, or separate folders for all virtual environments located side by side: `.\envs`, `~/.virtualenvs`, and so on. |

## Debugger Settings

### General debugging

| Setting<br/>(python.debugpy.) | Default | Description | See also |
| --- | --- | --- | --- |
| debugJustMyCode | `true` | Specifies whether the debugger should only step through user-written code. Disabling allows you to step through library code as well. | [Debugging](/docs/python/debugging.md) |

## Testing settings

### General testing

| Setting<br/>(python.testing.) | Default | Description | See also |
| --- | --- | --- | --- |
| autoTestDiscoverOnSaveEnabled | `true` | Specifies whether to enable or disable auto run test discovery when saving a test file. | [Testing](/docs/python/testing.md) |
| cwd | null | Specifies an optional working directory for tests. | [Testing](/docs/python/testing.md) |
| debugPort | `3000` | Port number used for debugging of unittest tests. | [Testing](/docs/python/testing.md) |
| promptToConfigure | `true` | Specifies whether VS Code prompts to configure a test framework if potential tests are discovered. | [Testing](/docs/python/testing.md)  |

### unittest framework

| Setting<br/>(python.testing.) | Default | Description | See also |
| --- | --- | --- | --- |
| unittestArgs | `["-v", "-s", ".", "-p", "*test*.py"]` | Arguments to pass to unittest, where each top-level element that's separated by a space is a separate item in the list. | [Testing](/docs/python/testing.md) |
| unittestEnabled | `false` | Specifies whether unittest is enabled for testing. | [Testing](/docs/python/testing.md)  |

### pytest framework

| Setting<br/>(python.testing.) | Default | Description | See also |
| --- | --- | --- | --- |
| pytestArgs | `[]` | Arguments to pass to pytest, where each top-level element that's separated by a space is a separate item in the list. When debugging tests with pytest-cov installed, include `--no-cov` in these arguments. | [Testing](/docs/python/testing.md) |
| pytestEnabled | `false` | Specifies whether pytest is enabled for testing. | [Testing](/docs/python/testing.md) |
| pytestPath | `"pytest"` | Path to pytest. Use a full path if pytest is located outside the current environment. | [Testing](/docs/python/testing.md) |

## Code analysis settings

### IntelliSense engine settings

> **Note:** If you have never changed your language server setting, your language server is set to Pylance via the “Default” setting value.

| Setting<br/>(python.) | Default | Description |
| --- | --- | --- |
| languageServer | Default | Defines type of the language server (Default, [Pylance](https://devblogs.microsoft.com/python/announcing-pylance-fast-feature-rich-language-support-for-python-in-visual-studio-code/), Jedi, and None).|

### Python Language Server settings

#### Pylance Language Server

The language server settings apply when `python.languageServer` is `Pylance` or `Default`. If you have difficulties with the language server, see [Troubleshooting](https://github.com/microsoft/pylance-release/blob/main/TROUBLESHOOTING.md) in the language server repository.

| Setting<br/>(python.analysis.) | Default | Description |
| --- | --- | --- |
| aiCodeActions | true | Whether to enable specific AI-assisted code actions. Requires the [GitHub Copilot Chat](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat) extension to be enabled. <br> Accepted value is an object with a code action as key and a boolean as value. <br> Available code actions to use as keys: <ul> <li> `implementAbstractClasses`: enables code action to implement methods of classes inherited from an abstract class, using AI suggestions from GitHub Copilot to populate the method body.  </li> </ul>  Usage example: ```{"implementAbstractClasses": true}``` |
| autoFormatStrings | false | When typing "{" inside a string, whether to automatically prefix it with an "f". |
| autoImportCompletions | false | Controls the offering of auto imports in completions. Available values are `true` and `false`. |
| autoIndent | true | Whether to automatically adjust indentation based on language semantics when typing Python code. <br> Accepted values are `true` or `false`. |
| autoSearchPaths | true | Indicates whether to automatically add search paths based on some predefined names (like `src`). Available values are `true` and `false`. |
| completeFunctionParens | false | Adds parentheses to function completions. Accepted values are `true` and `false`. |
| diagnosticMode | openFilesOnly | Specifies what code files the language server analyzes for problems. <br> Available values are `workspace` and `openFilesOnly`. |
| diagnosticSeverityOverrides | {} | Allows a user to override the severity levels for individual diagnostics. <br> For each rule, the available severity levels are `error` (red squiggle), `warning` (yellow squiggle), `information` (blue squiggle), and `none` (rule disabled). <br> For information about the keys to use for the diagnostic severity rules, see the **Diagnostic severity rules** section below. |
| enableEditableInstalls | `false` | Enables improved IntelliSense support by resolving import paths for packages installed in editable mode (`pip install -e .`) as defined by [PEP 660](https://peps.python.org/pep-0660/). |
| exclude | [] | Paths of directories or files that should not be included in analysis. <br> These override the directories listed under the `python.analysis.include` setting, allowing specific subdirectories to be excluded. <br> Note that files listed in this `exclude` setting may still be included in the analysis if they are referenced/imported by source files that are not in the excluded list. <br> Paths may contain wildcard characters such as `**` (a directory or multiple levels of directories), `*` (a sequence of zero or more characters), or `?` (a single character). <br> If no exclude paths are specified, Pylance automatically excludes the following: `**/node_modules`, `**/\_\_pycache\_\_`, `.git` and any virtual environment directories. |
| extraPaths | [] | Specifies extra search paths for import resolution. <br> Accepts paths specified as strings and separated by commas if there are multiple paths. For example: `["path 1","path 2"]`. |
| importFormat | absolute | Defines the default format when auto importing modules. Accepted values are `absolute` or `relative`. |
| include | [] | Paths of directories or files that should be included in analysis. <br> If no paths are specified, Pylance defaults to the directory that contains the workspace root. <br> Paths may contain wildcard characters such as `**` (a directory or multiple levels of directories), `*` (a sequence of zero or more characters), or `?` (a single character). |
| fixAll | `[]` | A list of code actions to run when running the **Fix All** command or the `source.fixAll` code action. <br> Accepted values in this list: <ul><li> `source.unusedImports`: removes all unused imports in the open file</li> <li> `source.convertImportFormat`: converts the imports according to the `python.analysis.importFormat` setting </li> |
| includeAliasesFromUserFiles | false | Whether to include alias symbols from user files in auto-import suggestions and in the add import Quick Fix. When disabled, Pylance will offer the import suggestion from where the symbol is defined. When enabled, it'll also offer import suggestions from files where the symbol is imported (i.e. aliased). Available values are `true` and `false`. |
| ignore | [] | Paths of directories or files whose diagnostic output (errors and warnings) should be suppressed, even if they are an included file or within the transitive closure of an included file. <br> Paths may contain wildcard characters such as `**` (a directory or multiple levels of directories), `*` (a sequence of zero or more characters), or `?` (a single character). <br> If no value is provided, the value of `python.linting.ignorePatterns` (if set) will be used. |
| indexing | true | Used to specify whether Pylance should index user files as well as installed third party libraries at start up, to provide a more complete set of symbols in features such as auto imports, Quick Fixes, auto completions, etc. <br> Accepted values are `true` or `false`. <br> When set to `true`, by default Pylance indexes top-level symbols of installed packages (i.e., symbols in `__all__` under `package/__init__.py`), as well as all symbols from up to 2000 user files. <br> When set to `false`, Pylance will only display symbols already referenced or used in files that were previously opened in or loaded by the editor.    |
| inlayHints.callArgumentNames | false |  Whether to display inlay hints for call argument names.  Accepted values are `true` or `false`. |
| inlayHints.functionReturnTypes | false |  Whether to display inlay hints for function return types.  Accepted values are `true` or `false`. |
| inlayHints.pytestParameters | false | Whether to display inlay hints for pytest fixture argument types. Accepted values are `true` or `false`. |
| inlayHints.variableTypes | false | Whether to display inlay hints for variable types. Accepted values are `true` or `false`. |
| languageServerMode | default |  Offers predefined configurations to optimize Pylance's performance based on the development needs. <br> Available values are `default` and `light`. <br> When set to `default`, the language server delivers sufficient functionality for most machines without overloading the system. <br> When set to `light`, it enables a lightweight, memory-efficient setup. This mode disables various features to make Pylance function more like a streamlined text editor, and it's ideal for those who do not require the full breadth of IntelliSense capabilities and prefer Pylance to be as resource-friendly as possible. <br> Default setting values are overridden to the following by each mode:  <table> <tr> <th>Setting</th> <th>`light` mode</th> <th> `default` mode </th> </tr> <tr> <td>python.analysis.exclude</td> <td> ["**"]    </td> <td> [] </td>  <tr> <td>python.analysis.useLibraryCodeForTypes</td> <td>false</td> <td>true</td> <tr> <td> python.analysis.enablePytestSupport  </td> <td>false</td> <td>true </td>  <tr> <td> python.analysis.indexing </td> <td>false</td> <td>true </td></tr> </table> |
| logLevel | `Error` | Specifies the level of logging to be performed by the language server.<br> The possible levels of logging, in increasing level of information provided, are `Error`, `Warning`, `Information`, and `Trace`.|
| nodeArguments | `"--max-old-space-size=8192"` | Specifies custom arguments directly the custom Node.js executable defined by `python.analysis.nodeExecutable`. This can be used to allocate more memory or configure Node.js behavior. <br> Accepts a list of arguments supported by Node.js. Each `"arg=value"` should be separated by commas in the list. <br> Usage Example: ```"python.analysis.nodeArguments": ["--max-old-space-size=8192"]``` |
| nodeExecutable | `""` | Specifies the Node.js executable to use, which allows Pylance to allocate more memory.  <br> Accepted values are strings with executable paths, an empty string or `"auto"`. <br> When set to an empty string, Pylance will use VS Code's node executable. When set to `"auto"`, it will automatically download [Node.js](https://nodejs.org/dist/).|
| packageIndexDepths | [] |  Used to override how many levels under installed packages to index on a per package basis. <br> By default, only top-level modules are indexed (depth = 1). <br> To index submodules, increase depth by 1 for each level of submodule you want to index. <br> Accepted values are tuples of objects like ```{"name": "package name (str)", "depth": "depth to scan (int)", "includeAllSymbols": "whether to include all symbols (bool)"}```. <br> If `includeAllSymbols` is set to `false`, only symbols in each package's `__all__` are included. When it's set to `true`, Pylance will index every module/top level symbol declarations in the file. <br> Usage example: ```[{"name": "sklearn", "depth": 2, "includeAllSymbols": true}, {"name": "matplotlib", "depth": 3, "includeAllSymbols": false}]``` |
| stubPath | ./typings | Specifies a path to a directory that contains custom type stubs. Each package's type stub file(s) are expected to be in its own subdirectory. |
| typeCheckingMode | off | Specifies the level of type checking analysis to perform. <br> Available values are `off`, `basic`, and `strict`. <br> When set to `off` no type checking analysis is conducted; unresolved imports/variables diagnostics are produced. <br> When set to `basic` non-type checking-related rules (all rules in `off`), as well as basic type checking rules are used. <br> When set to `strict` all type checking rules at the highest severity of error (including all rules in `off` and `basic` categories) are used. |
| useLibraryCodeForTypes | true | Parses the source code for a package when a type stub is not found. Available values are `true` and `false`. |
| userFileIndexingLimit | 2000 | Sets the maximum number of user files for Pylance to index in the workspace. When set to -1, Pylance will index all files. <br> Note that indexing files is a performance-intensive task. |

**Diagnostic severity rules**

This section details all the available rules that can be customized using the `python.analysis.diagnosticSeverityOverrides` setting as shown in the following example.

```json
{
    "python.analysis.diagnosticSeverityOverrides": {
        "reportUnboundVariable": "information",
        "reportImplicitStringConcatenation": "warning"
    }
}
```

| Value | Description |
| --- | ---|
| reportAssertAlwaysTrue | Diagnostics for 'assert' statement that will probably always assert. This can be indicative of a programming error.  |
| reportCallInDefaultInitializer | Diagnostics for function calls within a default value initialization expression. Such calls can mask expensive operations that are performed at module initialization time. |
| reportConstantRedefinition | Diagnostics for attempts to redefine variables whose names are all-caps with underscores and numerals. |
| reportDuplicateImport | Diagnostics for an imported symbol or module that is imported more than once. |
| reportFunctionMemberAccess | Diagnostics for member accesses on functions.  |
| reportGeneralTypeIssues | Diagnostics for general type inconsistencies, unsupported operations, argument/parameter mismatches, etc. This covers all of the basic type-checking rules not covered by other rules. It does not include syntax errors.  |
| reportImportCycles | Diagnostics for cyclical import chains. These are not errors in Python, but they do slow down type analysis and often hint at architectural layering issues. Generally, they should be avoided. |
| reportImplicitStringConcatenation | Diagnostics for two or more string literals that follow each other, indicating an implicit concatenation. This is considered a bad practice and often masks bugs such as missing commas. |
| reportIncompatibleMethodOverride | Diagnostics for methods that override a method of the same name in a base class in an incompatible manner (wrong number of parameters, incompatible parameter types, or incompatible return type). |
| reportIncompatibleVariableOverride | Diagnostics for class variable declarations that override a symbol of the same name in a base class with a type that is incompatible with the base class symbol type.  |
| reportInvalidStringEscapeSequence | Diagnostics for invalid escape sequences used within string literals. The Python specification indicates that such sequences will generate a syntax error in future versions. |
| reportInvalidStubStatement | Diagnostics for statements that should not appear within a stub file. |
| reportInvalidTypeVarUse | Diagnostics for improper use of type variables in a function signature. |
| reportMissingImports | Diagnostics for imports that have no corresponding imported python file or type stub file.  |
| reportMissingModuleSource | Diagnostics for imports that have no corresponding source file. This happens when a type stub is found, but the module source file was not found, indicating that the code may fail at runtime when using this execution environment. Type checking will be done using the type stub. |
| reportMissingTypeArgument | Diagnostics for when a generic class is used without providing explicit or implicit type arguments. |
| reportMissingTypeStubs | Diagnostics for imports that have no corresponding type stub file (either a typeshed file or a custom type stub). The type checker requires type stubs to do its best job at analysis. |
| reportOptionalCall | Diagnostics for an attempt to call a variable with an Optional type. |
| reportOptionalContextManager | Diagnostics for an attempt to use an Optional type as a context manager (as a parameter to a with statement). |
| reportOptionalIterable | Diagnostics for an attempt to use an Optional type as an iterable value (e.g. within a for statement). |
| reportOptionalMemberAccess | Diagnostics for an attempt to access a member of a variable with an Optional type. |
| reportOptionalOperand | Diagnostics for an attempt to use an Optional type as an operand to a binary or unary operator (like '+', '==', 'or', 'not'). |
| reportOptionalSubscript | Diagnostics for an attempt to subscript (index) a variable with an Optional type. |
| reportPrivateUsage | Diagnostics for incorrect usage of private or protected variables or functions. Protected class members begin with a single underscore `_` and can be accessed only by subclasses. Private class members begin with a double underscore but do not end in a double underscore and can be accessed only within the declaring class. Variables and functions declared outside of a class are considered private if their names start with either a single or double underscore, and they cannot be accessed outside of the declaring module. |
| reportPropertyTypeMismatch | Diagnostics for properties where the type of the value passed to the setter is not assignable to the value returned by the getter. Such mismatches violate the intended use of properties, which are meant to act like variables. |
| reportSelfClsParameterName | Diagnostics for a missing or misnamed “self” parameter in instance methods and “cls” parameter in class methods. Instance methods in metaclasses (classes that derive from “type”) are allowed to use “cls” for instance methods. |
| reportUndefinedVariable | Diagnostics for undefined variables. |
| reportUnboundVariable | Diagnostics for unbound and possibly unbound variables.  |
| reportUnknownArgumentType | Diagnostics for call arguments for functions or methods that have an unknown type. |
| reportUnknownLambdaType | Diagnostics for input or return parameters for lambdas that have an unknown type. |
| reportUnknownMemberType | Diagnostics for class or instance variables that have an unknown type. |
| reportUnknownParameterType | Diagnostics for input or return parameters for functions or methods that have an unknown type. |
| reportUnknownVariableType | Diagnostics for variables that have an unknown type. |
| reportUnnecessaryCast | Diagnostics for 'cast' calls that are statically determined to be unnecessary. Such calls are sometimes indicative of a programming error. |
| reportUnnecessaryIsInstance | Diagnostics for 'isinstance' or 'issubclass' calls where the result is statically determined to be always true or always false. Such calls are often indicative of a programming error.  |
| reportUnusedCallResult | Diagnostics for call expressions whose results are not consumed and are not None. |
| reportUnusedClass | Diagnostics for a class with a private name (starting with an underscore) that is not accessed. |
| reportUnusedCoroutine | Diagnostics for call expressions that return a Coroutine and whose results are not consumed. |
| reportUnusedFunction | Diagnostics for a function or method with a private name (starting with an underscore) that is not accessed. |
| reportUnusedImport | Diagnostics for an imported symbol that is not referenced within that file. |
| reportUnusedVariable | Diagnostics for a variable that is not accessed. |
| reportUnsupportedDunderAll | Diagnostics for unsupported operations performed on `__all__`. |
| reportWildcardImportFromLibrary | Diagnostics for a wildcard import from an external library. |

## AutoComplete settings

| Setting<br/>(python.autoComplete.) | Default | Description | See also |
| --- | --- | --- | --- |
| extraPaths | `[]` | Specifies locations of additional packages for which to load autocomplete data. | [Editing](/docs/python/editing.md#autocomplete-and-intellisense) |

## Predefined variables

The Python extension settings support predefined variables. Similar to the general VS Code settings, variables use the **${variableName}** syntax. Specifically, the extension supports the following variables:

- **${cwd}** - the task runner's current working directory on startup
- **${workspaceFolder}** - the path of the folder opened in VS Code
- **${workspaceRootFolderName}** - the name of the folder opened in VS Code without any slashes (/)
- **${workspaceFolderBasename}** - the name of the folder opened in VS Code without any slashes (/)
- **${file}** - the current opened file
- **${relativeFile}** - the current opened file relative to `workspaceFolder`
- **${relativeFileDirname}** - the current opened file's dirname relative to `workspaceFolder`
- **${fileBasename}** - the current opened file's basename
- **${fileBasenameNoExtension}** - the current opened file's basename with no file extension
- **${fileDirname}** - the current opened file's dirname
- **${fileExtname}** - the current opened file's extension

- **${lineNumber}** - the current selected line number in the active file
- **${selectedText}** - the current selected text in the active file
- **${execPath}** - the path to the running VS Code executable

For additional information about predefined variables and example usages, see the [Variables reference](/docs/reference/variables-reference.md) in the general VS Code docs.

## Next steps

- [Python environments](/docs/python/environments.md) - Control which Python interpreter is used for editing and debugging.
- [Editing code](/docs/python/editing.md) - Learn about autocomplete, IntelliSense, formatting, and refactoring for Python.
- [Linting](/docs/python/linting.md) - Enable, configure, and apply a variety of Python linters.
- [Debugging](/docs/python/debugging.md) - Learn to debug Python both locally and remotely.
- [Testing](/docs/python/testing.md) - Configure test environments and discover, run, and debug tests.
