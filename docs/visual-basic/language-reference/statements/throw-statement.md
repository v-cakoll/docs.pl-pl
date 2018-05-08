---
title: Throw — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: cfa53b3585846da25711739fb7af4bde21746b29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="throw-statement-visual-basic"></a>Throw — Instrukcja (Visual Basic)
Zgłasza wyjątek w obrębie procedury.  
  
## <a name="syntax"></a>Składnia  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a>Część  
 `expression`  
 Zawiera informacje o wyjątku, który zostanie wygenerowany. Opcjonalny, gdy znajdującej się w `Catch` instrukcji, w przeciwnym razie jest to wymagane.  
  
## <a name="remarks"></a>Uwagi  
 `Throw` Instrukcji zgłasza wyjątek, który może obsługiwać kodem obsługi wyjątków strukturalnych (`Try`... `Catch`... `Finally`) lub bez struktury kod obsługi wyjątków (`On Error GoTo`). Można użyć `Throw` instrukcji pułapki błędów w kodzie, ponieważ Visual Basic umożliwia przeniesienie w górę stosu wywołań, aż do znalezienia odpowiedni kod obsługi wyjątków.  
  
 A `Throw` instrukcji za pomocą wyrażenia nie można użyć tylko w `Catch` instrukcji, w którym instrukcji case ponownie zgłasza wyjątek, w obecnie obsługiwane przez `Catch` instrukcji.  
  
 `Throw` Instrukcji resetuje stosie wywołań `expression` wyjątku. Jeśli `expression` nie zostanie podany, stos wywołań pozostanie niezmieniona. Dostęp można uzyskać stos wywołań dla wyjątku za pomocą <xref:System.Exception.StackTrace%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy kod używa `Throw` instrukcji, aby zgłosić wyjątek:  
  
 [!code-vb[VbVbalrStatements#84](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/throw-statement_1.vb)]  
  
## <a name="requirements"></a>Wymagania  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Moduł:** `Interaction`  
  
 **Zestaw:** Visual Basic Runtime Library (w pliku Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Zobacz też  
 [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [On Error, instrukcja](../../../visual-basic/language-reference/statements/on-error-statement.md)
