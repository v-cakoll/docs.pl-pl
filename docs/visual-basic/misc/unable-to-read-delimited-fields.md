---
title: Nie można odczytać rozdzielonych pól, ponieważ podwójny cudzysłów nie jest dozwolonym ogranicznikiem, gdy EscapeQuotes jest ustawiona na wartość True
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: 66116e6f3d8338db3884cd375aeb880930c8d861
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33639288"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>Nie można odczytać rozdzielonych pól, ponieważ podwójny cudzysłów nie jest dozwolonym ogranicznikiem, gdy EscapeQuotes jest ustawiona na wartość True
`TextFieldParser` Nie można odczytać z pliku, ponieważ podano znak cudzysłowu (") jako ogranicznik i `EscapeQuotes` ma ustawioną wartość `True`.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Ustaw `EscapeQuotes` do `False`.  
  
## <a name="see-also"></a>Zobacz też  
 [TextFieldParser.SetDelimiters Method](http://msdn.microsoft.com/library/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)  
 [TextFieldParser.Delimiters Property](http://msdn.microsoft.com/library/4eb18f4d-3011-40a9-b668-be93eed0444f)  
 [Instrukcje: odczyt z rozdzielonych przecinkami plików testowych](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [TextFieldParser, obiekt](../../visual-basic/language-reference/objects/textfieldparser-object.md)
