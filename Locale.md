The PSAT extension and CLI is now available in 6 different languages:
- English (Default)
- Hindi
- Spanish
- Japanese
- Korean
- Portuguese (Brazil)

## Using PSAT extension in your language
To view PSAT in your preferred language, you can change the language settings of your Chrome browser. Here are the steps for each operating system:

### Mac
To change the display language on macOS, follow these steps:

1. Open System Preferences.
2. In Genral settings, click on "Language and Region".
3. Switch to the "Apps" tab.
4. Click the "+" icon.
5. Choose Chrome from the application list.
6. Select your desired language from the list.
7. Restart Chrome if necessary.

### Windows (Steps may vary depending on your Windows version)
To change the display language on Windows, follow these steps:

1. Go to Settings > Time & Language > Language & region.
2. Add a preferred language: Click on "Add a language" under the preferred languages section and select your preferred language.
3. Choose the language you want to apply and click next.
4. Install and set as display language.

If your Windows licence does not support switching the display language.

You can directly change the language in Chrome:
1. Visit `chrome://settings/languages`.
2. Add the language you want.
3. Select it as the display language and relaunch the browser.


### Linux (Steps may vary depending on your Linux distribution)
To change the display language on Ubuntu, follow these steps:

1. Open Settings.
2. Open "Language and Region".
3. Click on "Manage Installed Languages".
4. Click on "Install / Remove Languages".
5. Select your desired language from the list.
6. Open "Language and Region" again.
7. Click on language section and select your desired language.
8. Restart your system.

## Get PSAT CLI Reports in Your Language
You can view PSAT CLI reports in your preferred language by using the `-l` or `--locale` option when running the command, by default the language is set to English.

### Supported Languages

PSAT CLI currently supports the following languages with their respective language codes:
|        Language      |       Code          |
| -------------------- | ------------------- |
| English              | en (default)        |
| Hindi                | hi                  |
| Spanish              | es                  |
| Japanese             | ja                  |
| Korean               | ko                  |
| Portuguese (Brazil)  | pt-BR               |

### Settings Laguage in CLI

Here is an example of how to set the language when using PSAT CLI:

```bash
psat https://example.com -l hi
```
Here, `-l hi` sets the language to Hindi (hi).

Note that if you are using PSAT CLI by cloning the [repository](https://github.com/googlechromelabs/ps-analysis-tool), you would use the following:

```bash
npm run cli https://example.com -- -l hi
```