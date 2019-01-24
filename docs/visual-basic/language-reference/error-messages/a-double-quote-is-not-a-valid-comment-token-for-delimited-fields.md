---
title: Podwójny cudzysłów nie jest prawidłowym tokenem dla rozdzielonych pól, jeżeli parametr EscapeQuote ma wartość ustawioną na True
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
ms.openlocfilehash: 809cb2ab6e84f8c7f14f5a3b03dfc6142a31b5bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558972"
---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a>Podwójny cudzysłów nie jest prawidłowym tokenem dla rozdzielonych pól, jeżeli parametr EscapeQuote ma wartość ustawioną na True
Znak cudzysłowu została podana jako / / / ogranicznik `TextFieldParser`, ale `EscapeQuotes` ustawiono `True`.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Ustaw `EscapeQuotes` do `False`.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- [Instrukcje: Odczyt z plików tekstowych rozdzielonych przecinkami](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
