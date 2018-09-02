---
title: Nie można odczytać rozdzielonych pól, ponieważ podwójny cudzysłów nie jest dozwolonym ogranicznikiem, gdy EscapeQuotes jest ustawiona na wartość True
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: faa42c2fec5851857496b321dbdb53c16c43e8c1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389653"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>Nie można odczytać rozdzielonych pól, ponieważ podwójny cudzysłów nie jest dozwolonym ogranicznikiem, gdy EscapeQuotes jest ustawiona na wartość True
`TextFieldParser` Nie można odczytać z pliku, ponieważ znak cudzysłowu (") została podana jako ogranicznika i `EscapeQuotes` ustawiono `True`.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Ustaw `EscapeQuotes` do `False`.  
  
## <a name="see-also"></a>Zobacz też  
 [TextFieldParser.SetDelimiters Method](https://msdn.microsoft.com/library/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)  
 [TextFieldParser.Delimiters Property](https://msdn.microsoft.com/library/4eb18f4d-3011-40a9-b668-be93eed0444f)  
 [Instrukcje: odczyt z rozdzielonych przecinkami plików testowych](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [TextFieldParser, obiekt](../../visual-basic/language-reference/objects/textfieldparser-object.md)
