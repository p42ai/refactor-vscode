The P42 JavaScript Assistant adds **[37 automated refactorings and code actions](https://p42.ai/documentation/code-action/) for JavaScript and TypeScript**.

It enhances the VS Code refactoring context menu and shows refactoring suggestions in your editor.

https://marketplace.visualstudio.com/items?itemName=p42ai.refactor

# User Interface

## Refactor Context Menu

The P42 refactorings are shown in the following menus:
* VS Code "Quick Fix..." context menu (default keyboard shortcuts on Mac: `CMD + .`, on Windows `CTRL + .`)
* VS Code "Refactor..." context menu (default keyboard shortcut: `CTRL + SHIFT + R`):

Example Refactoring Menu:

![Refactoring Context Menu Example](https://p42.ai/image/vscode/refactoring-menu.png)

## Keyboard Shortcuts

- Inline const: `CTRL + ALT + N`

## Refactoring Hints

Many P42 refactoring suggestions are also indicated as blue information underlines or hints in applicable code segments. They can be invoked as quick fixes. See Refactorings below for details.

![Nullish Coalescing Operator Example](https://p42.ai/image/vscode/feature-suggestion.png)

## Refactor Files and Folders in Bulk (P42+)

For files and folders in the Explorer, there is a new "Refactor... \[P42+\]" command that refactors files and folders in one go. You can select a refactoring from a dialog. The selected refactoring is then applied to the selected file or all files in the folder (and its subfolders).

This is a [P42+](https://p42.ai/p42-plus) feature. If you want to support the development of P42 and are interested in advanced functionality for teams, please check out [P42+ (for GitHub)](https://p42.ai/p42-plus).

### Recommended Bulk Refactoring Workflow

1. Get your workspace in a clean state, e.g. by committing or stashing your current changes or by switching to a clean branch.
2. Run the refactoring on the folders you want to update.
3. **Thoroughly review the individual changes in the diff viewer and revert or fix them as needed**. Modernizations need to cover many edge cases, so there is a chance that some changes may lose comments, break formatting, or affect the semantics. If you find bugs, please report them here: https://github.com/p42ai/refactor-vscode/issues
4. Run your test suites to ensure nothing broke unexpectedly.
5. Commit the changes.

![Refactor... Command](https://p42.ai/image/vscode/feature-refactor-menu.png)
![Refactor... Menu](https://p42.ai/image/vscode/feature-refactor-selector.png)

# Configuration

The 'p42.toml' file in the workspace root contains the P42 configuration.

Currently, individual refactorings can be enabled and disabled. By default, all refactorings are enabled.

## Disabling Refactorings

To disable a refactoring, add a section with "refactoring.$refactoring-id" and set enabled to false, for example:

```toml
[refactoring.optional-chaining]
enabled = false
```

The refactoring ids are displayed as grayed-out text in parentheses in the hover messages.

## Ignoring Statements

You can add a `// p42:ignore-next-statement` comment in a separate line before a statement to prevent P42 (for VS Code and for GitHub) from analysing the next statement and anything contained in it.

### Example

```js
if (example) {
  // p42:ignore-next-statement
  x = stringify(schema, { space: 2 }) + "\n";
}
```

In the above snippet, P42 will not analyse the statement `x = stringify(schema, { space: 2 }) + "\n";`.

## Ignoring Files

You can add a `// p42:ignore-file` comment at the beginning of the file (before the first code line). No suggestions etc. will be shown for ignored files.

# FAQ

- **Does P42 support Vue single file components?**
  No. P42 supports `.js`, `.mjs`, `.cjs`, `.jsx`, `.ts`, and `.tsx` files that contain TypeScript or JavaScript code (with or without JSX).

- **Does P42 support Flow type annotations?**
  No. P42 supports TypeScript.

- **Does P42 analyse my code in the P42 cloud?**
  No. When you use the P42 JavaScript Assistant for VS Code, your source code remains on your computer and all P42 code analysis happens on your computer. No code or other data is transferred to a cloud service by the P42 extension.

- **How can I disable a refactoring / suggestions?**
  You can disable them by adding a section in the `p42.config.toml` configuration file. See Configuration above.

# License

```
This software is offered free of charge by
P42 Software UG (haftungsbeschränkt), Pappelallee 78/79, 10437 Berlin, Germany.

The software may not be redistributed or sold without permission.

P42 Software UG (haftungsbeschränkt) is only liable for defects in accordance with applicable law.
```

# Open Source Libraries

See [DISCLAIMER.txt](https://raw.githubusercontent.com/p42ai/refactor-vscode/main/DISCLAIMER.txt).

# Feedback & Updates

If you want to provide feedback, e.g., which refactorings or functions you'd like to see in P42, or if you'd like to receive updates, you can follow us on [Twitter @p42ai](https://twitter.com/p42ai) or [LinkedIn](https://www.linkedin.com/company/p42-software).
