Snap! Below the Line DeCal Final Project 
Language Auto Detection
by Noriaki Oji and Karen Lin

Our goal is to obtain the user's browser language and set Snap's default language to automatically reflect the user's native tongue.

This project is a response to mquinson's issue #258 on the official Snap! GitHub repository.

This project is done exclusively in gui.js. 

Here are the steps we took: 

1. Created the function IDE_Morph.prototype.getBrowswerLanguage in Line 3394 to detect user language using
window.navigator.userLanguage || window.navigator.language

"navigator.userLanguage" is used for IE, "navigator.language" for Safari/Chrome/Firefox.

This method will return a language code such as en-us (English) or zh-tw (traditional Chinese). 

2. Truncated language code

A majority of Snap! translation files use only the first two letters of the language code, so we shortened the language code obtained by the browser using lang.substring(0,2);  

3. Called this.getBrowserLanguage(); on line 1738, instead of allowing Snap! to set the default language to English. 

Upon loading of the Snap! page, the default language will be in English. With the implementation of language auto detection, the program will detect the user's browser language and reload Snap! to reflect that language.  

Users still have the option of changing languages through the settings menu. 

