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
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603395"
---
# <a name="call-statement-visual-basic"></a>Call — Instrukcja (Visual Basic)
Przekazuje sterowanie do `Function`, `Sub`, lub procedury biblioteki dołączanej dynamicznie (DLL).

## <a name="syntax"></a>Składnia

```vb
[ Call ] procedureName [ (argumentList) ]
```

## <a name="parts"></a>Części
|||
|---|---|
|`procedureName`|Wymagane. Nazwa wywoływanej procedury.|
|`argumentList`|Opcjonalne. Lista zmiennych lub wyrażeń reprezentujących argumenty, które są przekazywane do procedury, gdy jest wywoływana. Używając wiele argumentów, oddziela się je przecinkami. Jeśli dołączysz `argumentList`, musisz ująć ją w nawiasy.|
|||

## <a name="remarks"></a>Uwagi
 Można użyć słowa kluczowego `Call` do wywołania procedury. Dla większości wywołań procedur nie jest wymagane używanie tego słowa kluczowego.

 Zazwyczaj używa się słowa kluczowego `Call`, gdy wyrażenie nie zaczyna się od identyfikatora. Użycie `Call` do innych celów nie jest zalecane.

 Jeśli procedura zwróci wartość, instrukcja `Call` je odrzuci.

## <a name="example"></a>Przykład
 Poniższy kod przedstawia dwa przykłady, gdzie słowo kluczowe `Call` jest niezbędne do wywołania procedury. W obu przykładach wyrażenie wywoływane nie zaczyna się od identyfikatora.

 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]

## <a name="see-also"></a>Zobacz też
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
 [Wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
