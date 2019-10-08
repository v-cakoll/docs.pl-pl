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
ms.openlocfilehash: a04ebddc7db176188876da1082e1e6946e1e8eec
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005170"
---
# <a name="call-statement-visual-basic"></a>Call — Instrukcja (Visual Basic)

Przenosi kontrolę do procedury `Function`, `Sub` lub biblioteki dołączanej dynamicznie (DLL).  
  
## <a name="syntax"></a>Składnia  
  
```vb  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>Części  

|||
|---|---|
|`procedureName`|Wymagany. Nazwa procedury do wywołania.|
|`argumentList`|Opcjonalny. Lista zmiennych lub wyrażeń reprezentujących argumenty, które są przekazane do procedury po wywołaniu. Wiele argumentów jest oddzielonych przecinkami. Jeśli dołączysz `argumentList`, należy ująć ją w nawiasy.|
|||
  
## <a name="remarks"></a>Uwagi

 Po wywołaniu procedury można użyć słowa kluczowego `Call`. W przypadku większości wywołań procedur nie jest wymagane użycie tego słowa kluczowego.

 Użycie słowa kluczowego `Call` jest zazwyczaj możliwe, gdy wywołane wyrażenie nie zaczyna się od identyfikatora. Użycie słowa kluczowego `Call` do innych celów nie jest zalecane.

 Jeśli procedura zwróci wartość, instrukcja `Call` odrzuca ją.

## <a name="example"></a>Przykład

 Poniższy kod przedstawia dwa przykłady, w których słowo kluczowe `Call` jest niezbędne do wywołania procedury. W obu przykładach wywołane wyrażenie nie zaczyna się od identyfikatora.

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a>Zobacz także

- [Function, instrukcja](function-statement.md)
- [Sub, instrukcja](sub-statement.md)
- [Declare, instrukcja](declare-statement.md)
- [Wyrażenia lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
