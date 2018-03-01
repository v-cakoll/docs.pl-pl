---
title: "Call — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c72450fd6f931f36f640d3e384a6fd38d57a7a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="call-statement-visual-basic"></a>Call — Instrukcja (Visual Basic)
Przekazuje sterowanie do `Function`, `Sub`, lub procedury biblioteki dołączanej (dynamicznie DLL).  
  
## <a name="syntax"></a>Składnia  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>Części  
 `procedureName`  
 Wymagany. Nazwa wywoływanej procedury.  
  
 `argumentList`  
 Opcjonalny. Lista zmiennych lub wyrażeń reprezentujących argumenty, które są przekazywane do procedury, gdy jest wywoływana. Używanie wielu argumentów są oddzielone przecinkami. Jeśli dołączysz `argumentList`, musisz ją ująć go w nawiasach.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `Call` — słowo kluczowe po wywołaniu procedury. Dla większości wywołań procedur nie są wymagane do używania słowa kluczowego.  
  
 Zazwyczaj używają `Call` — słowo kluczowe po nazwie wyrażenia nie zaczyna się od identyfikatora. Użycie `Call` — słowo kluczowe do innych celów nie jest zalecane.  
  
 Jeśli procedura zwróci wartość, `Call` instrukcji odrzuca je.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia dwa przykłady gdzie `Call` — słowo kluczowe jest niezbędne wywołać procedurę. W obu przykładach wyrażenie wywoływanego nie zaczyna się od identyfikatora.  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [DECLARE — instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
