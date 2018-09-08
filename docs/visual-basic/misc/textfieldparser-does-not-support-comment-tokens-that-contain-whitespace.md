---
title: TextFieldParser nie obsługuje tokenami komentarzy, które zawierają odstęp
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: a8931d67cd728cf98bc4d83044c65fad6642b021
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44133665"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a>TextFieldParser nie obsługuje tokenami komentarzy, które zawierają odstęp
Podano tokenu komentarz, który zawiera biały znak. `TextFieldParser` Nie obsługuje tokenami komentarzy, zawierające biały znak, chyba że biały występuje na początku tokenu. Biały znak pojawiają się na początku token jest ignorowany.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Należy podać token prawidłowy komentarz.  
  
## <a name="see-also"></a>Zobacz także

- [Właściwość TextFieldParser.CommentTokens](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A)  
- [Analizowanie plików tekstowych za pomocą obiektu TextFieldParser](../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
- [TextFieldParser, obiekt](../../visual-basic/language-reference/objects/textfieldparser-object.md)
