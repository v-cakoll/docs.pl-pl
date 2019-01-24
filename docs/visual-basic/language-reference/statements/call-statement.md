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
ms.openlocfilehash: e706650ac6da84d9b4e77fc549811e731be61b92
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594164"
---
# <a name="call-statement-visual-basic"></a>Call — Instrukcja (Visual Basic)
Przekazuje sterowanie do `Function`, `Sub`, lub procedury biblioteki dołączanej dynamicznie (DLL).  
  
## <a name="syntax"></a>Składnia  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>Części  
|||
|---|---|
|`procedureName`|Wymagana. Nazwa procedury do wywołania.|
|`argumentList`|Opcjonalna. Lista zmiennych lub wyrażeń reprezentujących argumenty, które są przekazywane do procedury, gdy jest wywoływana. Wiele argumentów są oddzielone przecinkami. Jeśli dołączysz `argumentList`, należy ująć je w nawiasach.|
|||
  
## <a name="remarks"></a>Uwagi  
 Słowa kluczowego `Call` można użyć podczas wywoływania procedury. W większości wywołań procedur użycie tego słowa kluczowego nie jest konieczne.  
  
 Słowa kluczowego `Call` zazwyczaj używa się, gdy wyrażenie nie zaczyna się od identyfikatora. Użycie słowa `Call` w innym celu nie jest zalecane.  
  
 Jeśli procedura zwróci wartość, instrukcja `Call` ją odrzuci.  
  
## <a name="example"></a>Przykład  
 W przykładowym kodzie poniżej przedstawiono dwie sytuacje, w których słowo kluczowe `Call` jest niezbędne do wywołania procedury. W obu przykładach wywoływane wyrażenie nie zaczyna się od identyfikatora.  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
