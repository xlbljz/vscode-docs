---
ContentId: 0e62b3c9-6c13-4a71-a942-63d37c8f47d1
DateApproved: 3/12/2025
MetaDescription: Testing C# with C# Dev Kit in Visual Studio Code
---
# Testing with C# Dev Kit

Testing in C# in Visual Studio Code is enabled by the C# Dev Kit extension. It's a lightweight extension to enhance your C# development experience.

## Overview

The extension supports the following test frameworks:

- [xUnit](https://learn.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test)
- [NUnit](https://learn.microsoft.com/dotnet/core/testing/unit-testing-with-nunit)
- [MSTest](https://learn.microsoft.com/dotnet/core/testing/unit-testing-with-mstest)

The C# Dev Kit extension provides the following features:

- Run/Debug tests cases
- View test report
- View tests in Testing Explorer

## Requirements

- [.NET 6.0 SDK or later](https://dotnet.microsoft.com/download)
- Visual Studio Code (version 1.58.0 or later)
- [C# Dev Kit](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csdevkit)

## Project setup

> Note: If you have already set up your C# test framework in your project, you can skip to the Features section.

### Enable testing and adding test framework packages to your project

You can enable a test framework for your project with just a few steps in the Solution Explorer:

**xUnit**

Open the Command Palette and select **.NET:New Project..** then select **xUnit Test Project** and provide name and location for the new project. This will create a new project and directory that uses xUnit as the test library and configures the test runner by adding the following `<PackageReference />` elements to the project file.

- Microsoft.NET.Test.Sdk
- xunit
- xunit.runner.visualstudio
- coverlet.collector

From the Terminal, run the following command:

```bash
dotnet add [location of your test csproj file] reference [location of the csproj file for project to be tested]
```

**NUnit**

Open the Command Palette and select **.NET:New Project..** then select **NUnit3 Test Project** and provide name and location for the new project. This will create a new project and directory that uses NUnit as the test library and configures the test runner by adding the following `<PackageReference />` elements to the project file.

- Microsoft.NET.Test.Sdk
- nunit
- NUnit3TestAdapter

From the Terminal, run the following command:
```bash
dotnet add [location of your test csproj file] reference [location of the csproj file for project to be tested]
```

**MSTest**

Open the Command Palette and select **.NET:New Project..** then select **MSTest Test Project** and provide name and location for the new project. This will create a new project and directory that uses MSTest as the test library and configures the test runner by adding the following `<PackageReference />` elements to the project file.

- Microsoft.NET.Test.Sdk
- MSTest.TestAdapter
- MSTest.TestFramework
- coverlet.collector

From the Terminal, run the following command:

```bash
dotnet add [location of your test csproj file] reference [location of the csproj file for project to be tested]
```

## Features

### Run/Debug test cases

Once you have written test cases, you will need to perform a build of your test project for them to be recognized as a test. Open the Command Palette and select **.NET: Build**. This will build your project.

[C# Dev Kit](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csdevkit) will generate shortcuts (the green play button) on the left side of the class and method definition. To run the target test cases, select the green play button. You can also right-click on it to see more options.

### Test Explorer

The Test Explorer is a tree view to show all the test cases in your workspace. You can select the beaker button on the left-side Activity Bar of Visual Studio Code to open it. You can also run/debug your test cases and view their test results from there. If you have not performed a build of your project, select the **Refresh Tests** button to perform a build and discover all of your tests.

### Code coverage in C# Dev Kit
C# Dev Kit now supports code coverage via the VS Code Code Coverage APIs. This feature allows you to measure the effectiveness of your tests by showing which lines of code are executed during testing and which are not.


Code coverage is a metric that tracks the percentage of your codebase executed by automated tests. It helps identify untested
sections of code and improves the quality of your testing by ensuring comprehensive coverage.


> **Note**: To enable code coverage, ensure you have the latest version of C# Dev Kit installed.

To run your tests with code coverage, follow these steps:
  - 1. Open the Test Explorer from the Activity Bar.
  - 2. Select and Run Your Tests with Coverage: choose the tests you want to run and execute them with coverage.
  - 3. View coverage data: code coverage data is automatically generated and displayed alongside your test results in the Test Explorer.

If you have generated a coverage report and want to view the result in VS Code:
  - 1. Use the Command Palette: Open the Command Palette (`kb(workbench.action.showCommands)`) and search for "Test: Show Coverage" to access the coverage data.
  - 2. View code coverage highlighted in the editor:
      - Green lines: Indicate tested code.
      - Red lines: Indicate untested code.
  - 3. Test Explorer summary: The Test Explorer provides an overall coverage summary and allows you to explore specific files or methods that require additional testing.

To improve test coverage of your code:
  - Examine the coverage report (in the Test Explorer or editor) to identify areas marked in red,
indicating untested code.
  - Create new tests to cover the untested areas highlighted in the report.
  - Rerun the tests and review the updated coverage to ensure your code is well-tested.


### View test results

After running/debugging the test cases the state of the related test items will be updated in both editor decorations and the Test Explorer.

![View test results](images/testing/view-test-results.png)

You can select the links in the stack trace to navigate to the source location.

### VS Code testing commands

There are testing commands (for example, **Run All Tests**) that can be found by searching for **Test:** in the Command Palette (`kb(workbench.action.showCommands)`).

![Testing command in Command Palette](images/testing/testing-command.png)

### VS Code testing settings

There are VS Code settings specific to testing that can be found by searching for **Testing** in the Settings editor (`kb(workbench.action.openSettings)`).

![Testing settings](images/testing/testing-settings.png)
