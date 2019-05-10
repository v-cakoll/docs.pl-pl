---
title: Nie można odczytać rozdzielonych pól, ponieważ podwójny cudzysłów nie jest dozwolonym ogranicznikiem, gdy EscapeQuotes jest ustawiona na wartość True
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: ca764d5258daf54a7149661549a78b3aca709718
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619802"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>Nie można odczytać rozdzielonych pól, ponieważ podwójny cudzysłów nie jest dozwolonym ogranicznikiem, gdy EscapeQuotes jest ustawiona na wartość True
`TextFieldParser` Nie można odczytać z pliku, ponieważ znak cudzysłowu (") została podana jako ogranicznika i `EscapeQuotes` ustawiono `True`.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Ustaw `EscapeQuotes` do `False`.  
  
## <a name="see-also"></a>Zobacz także

- [TextFieldParser.SetDelimiters Method](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [TextFieldParser.Delimiters Property](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [Instrukcje: Odczyt z plików tekstowych rozdzielonych przecinkami](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [TextFieldParser, obiekt](../../visual-basic/language-reference/objects/textfieldparser-object.md)
