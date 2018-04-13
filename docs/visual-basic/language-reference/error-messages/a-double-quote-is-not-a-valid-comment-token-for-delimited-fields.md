---
title: Podwójny cudzysłów nie jest prawidłowym tokenem dla rozdzielonych pól, jeżeli parametr EscapeQuote ma wartość ustawioną na True
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5677ee7415fe385805413ccbdec20762ac0573a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a>Podwójny cudzysłów nie jest prawidłowym tokenem dla rozdzielonych pól, jeżeli parametr EscapeQuote ma wartość ustawioną na True
Znak cudzysłowu zostały podane jako ogranicznik dla `TextFieldParser`, ale `EscapeQuotes` ma ustawioną wartość `True`.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Ustaw `EscapeQuotes` do `False`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>  
 [Porady: Odczyt z plików tekstowych rozdzielanych przecinkami](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
