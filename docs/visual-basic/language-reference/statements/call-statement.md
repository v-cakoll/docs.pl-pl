---
title: Call — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: 2074f44aedf59f1570e73c898a9bf64e57034923
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="call-statement-visual-basic"></a>Call — Instrukcja (Visual Basic)
Przekazuje sterowanie do `Function`, `Sub`, lub procedury biblioteki dołączanej (dynamicznie DLL).  
  
## <a name="syntax"></a>Składnia  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>Części  
 `procedureName`  
 Wymagana. Nazwa wywoływanej procedury.  
  
 `argumentList`  
 Opcjonalna. Lista zmiennych lub wyrażeń reprezentujących argumenty, które są przekazywane do procedury, gdy jest wywoływana. Używanie wielu argumentów są oddzielone przecinkami. Jeśli dołączysz `argumentList`, musisz ją ująć go w nawiasach.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `Call` — słowo kluczowe po wywołaniu procedury. Dla większości wywołań procedur nie są wymagane do używania słowa kluczowego.  
  
 Zazwyczaj używają `Call` — słowo kluczowe po nazwie wyrażenia nie zaczyna się od identyfikatora. Użycie `Call` — słowo kluczowe do innych celów nie jest zalecane.  
  
 Jeśli procedura zwróci wartość, `Call` instrukcji odrzuca je.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia dwa przykłady gdzie `Call` — słowo kluczowe jest niezbędne wywołać procedurę. W obu przykładach wyrażenie wywoływanego nie zaczyna się od identyfikatora.  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
