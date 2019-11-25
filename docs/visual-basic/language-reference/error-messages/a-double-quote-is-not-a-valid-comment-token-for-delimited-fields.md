---
title: Podwójny cudzysłów nie jest prawidłowym tokenem dla rozdzielonych pól, jeżeli parametr EscapeQuote ma wartość ustawioną na True
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
ms.openlocfilehash: df7868c510eaacbad1d4421259234f4187f60cd7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976217"
---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a>Podwójny cudzysłów nie jest prawidłowym tokenem dla rozdzielonych pól, jeżeli parametr EscapeQuote ma wartość ustawioną na True

Jako ogranicznika dla `TextFieldParser`podano znak cudzysłowu, ale `EscapeQuotes` jest ustawiona na `True`.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Ustaw `EscapeQuotes` na `False`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- [Instrukcje: odczyt z rozdzielonych przecinkami plików testowych](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
