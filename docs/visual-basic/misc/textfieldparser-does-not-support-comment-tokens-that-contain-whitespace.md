---
title: Parametr TextFieldParser nie obsługuje tokenów komentarzy, które zawierają odstępu
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: ed22ac435a5cd46288f9854ae711b7fad354f624
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-whitespace"></a>Parametr TextFieldParser nie obsługuje tokenów komentarzy, które zawierają odstępu
Podano tokenu komentarz, który zawiera biały znak. `TextFieldParser` Nie obsługuje tokenów komentarzy, które zawierają biały znak, chyba że biały znak występuje na początku tokenu. Biały znak występujących na początku token jest ignorowana.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Podaj poprawne tokenem.  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwość TextFieldParser.CommentTokens](http://msdn.microsoft.com/library/2e6b6435-4bee-4c14-a353-e8f2c82e2d61)  
 [Analizowanie plików tekstowych za pomocą obiektu TextFieldParser](../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 [TextFieldParser, obiekt](../../visual-basic/language-reference/objects/textfieldparser-object.md)
