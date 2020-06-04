---
title: TextFieldParser nie obsługuje tokenów komentarzy zawierających odstępy
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: 51dc2b82d7f04c652e18173b8450b65c15ee6ec2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411899"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a>TextFieldParser nie obsługuje tokenów komentarzy zawierających odstępy
Podano token komentarza zawierający biały znak. `TextFieldParser`Program nie obsługuje tokenów komentarzy zawierających biały znak, chyba że odstęp występuje na początku tokenu. Białe miejsce występujące na początku tokenu jest ignorowane.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Podaj poprawny token komentarza.  
  
## <a name="see-also"></a>Zobacz też

- [TextFieldParser. CommentTokens — Właściwość](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A)
- [Analizowanie plików tekstowych za pomocą obiektu TextFieldParser](../developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [TextFieldParser — Obiekt](../language-reference/objects/textfieldparser-object.md)
