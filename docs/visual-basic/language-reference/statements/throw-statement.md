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
ms.openlocfilehash: 2494eac2f61f112f3ba6321ada7404f8cd618049
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766639"
---
# <a name="throw-statement-visual-basic"></a>Throw — Instrukcja (Visual Basic)
Zgłasza wyjątek w obrębie procedury.  
  
## <a name="syntax"></a>Składnia  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a>Część  
 `expression`  
 Zawiera informacje dotyczące zgłoszenie wyjątku. Opcjonalny, gdy znajdują się w `Catch` instrukcji, w przeciwnym razie jest to wymagane.  
  
## <a name="remarks"></a>Uwagi  
 `Throw` Instrukcji zgłasza wyjątek, który może obsłużyć kodem obsługi wyjątków strukturalnych (`Try`... `Catch`... `Finally`) lub bez struktury kodu obsługi wyjątków (`On Error GoTo`). Możesz użyć `Throw` instrukcję w celu przechwytywania błędów w kodzie, ponieważ Visual Basic przesunięte stos wywołań, aż znajdzie odpowiedni kod obsługi wyjątków.  
  
 A `Throw` instrukcji za pomocą wyrażenia nie można używać tylko w `Catch` instrukcji, w którym instrukcji case ponownie zgłasza wyjątek, aktualnie obsługiwany przez `Catch` instrukcji.  
  
 `Throw` Instrukcji przywraca stos wywołań dla `expression` wyjątku. Jeśli `expression` nie zostanie podany, stos wywołań pozostanie niezmieniona. Możesz uzyskać dostęp stos wywołań dla wyjątku za pomocą <xref:System.Exception.StackTrace%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy kod używa `Throw` instrukcję, aby zgłosić wyjątek:  
  
 [!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]  
  
## <a name="requirements"></a>Wymagania  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Moduł:** `Interaction`  
  
 **Zestaw:** Visual Basic Runtime Library (w pliku Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Zobacz także

- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [On Error, instrukcja](../../../visual-basic/language-reference/statements/on-error-statement.md)
