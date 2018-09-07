---
title: TextFieldParser nie obsługuje tokenami komentarzy, które zawierają odstęp
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: 2beda651dba952969593ffc7d64f01fd51ab7919
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44070891"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a>TextFieldParser nie obsługuje tokenami komentarzy, które zawierają odstęp
Podano tokenu komentarz, który zawiera biały znak. `TextFieldParser` Nie obsługuje tokenami komentarzy, zawierające biały znak, chyba że biały występuje na początku tokenu. Biały znak pojawiają się na początku token jest ignorowany.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Należy podać token prawidłowy komentarz.  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwość TextFieldParser.CommentTokens](https://msdn.microsoft.com/library/2e6b6435-4bee-4c14-a353-e8f2c82e2d61)  
 [Analizowanie plików tekstowych za pomocą obiektu TextFieldParser](../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 [TextFieldParser, obiekt](../../visual-basic/language-reference/objects/textfieldparser-object.md)
