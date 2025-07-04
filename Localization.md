The PSAT extension and CLI are now available in 6 different languages:
- English (Default)
- Hindi
- Japanese
- Korean
- Portuguese (Brazil)
- Spanish

## Using PSAT extension in your language
To view PSAT in your preferred language, you can change the display language settings of your Chrome browser. Here are the steps for each operating system:

### Mac
To change the Chrome's display language on macOS, follow these steps:

1. On your Mac, choose Apple menu  > System Settings, 
2. Click General  in the sidebar
3. Click Language & Region on the right. (You may need to scroll down.)
4. Go to Applications
5. Click the Add button (+)
6. Choose Chrome and a language from the pop-up menus, then click Add.
7. Restart Chrome if necessary.

### Windows
To change the Chrome's display language on Windows, follow these steps:

1. Visit - `chrome://settings/languages`
2. Click on Add Languages.
3. Select the language you want to add.
4. Once the language is added, click the three dots to the right of the language.
5. Select "Display Google Chrome in this language" from options.
6. Once done relaunch the browser.


### Linux (Steps may vary depending on your Linux distribution)
To change the Chrome's display language on Ubuntu, follow these steps:

1. Open Settings.
2. Open "Language and Region".
3. Click on "Manage Installed Languages".
4. Click on "Install / Remove Languages".
5. Select your desired language from the list.
6. Open "Language and Region" again.
7. Click on language section and select your desired language.
8. Restart your system.

## Get PSAT CLI Reports in Your Language
To generate PSAT CLI reports in your preferred language, use `-l` or `--locale` option when running the command. By default, the language is set to English.

### Supported Languages

PSAT CLI currently supports the following languages with their respective language codes:
|        Language      |       Code          |
| -------------------- | ------------------- |
| English              | en (default)        |
| Hindi                | hi                  |
| Japanese             | ja                  |
| Korean               | ko                  |
| Portuguese (Brazil)  | pt-BR               |
| Spanish              | es                  |

### Setting Language in CLI

Here is an example of how to set the language when using PSAT CLI:

```bash
psat https://example.com -l hi
```
Here, `-l hi` sets the language to Hindi (hi).

Note that if you are using PSAT CLI by cloning the [repository](https://github.com/googlechromelabs/ps-analysis-tool), you would use the following:

```bash
npm run cli https://example.com -- -l hi
```
