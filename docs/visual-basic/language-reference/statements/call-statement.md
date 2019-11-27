---
title: Call, instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: 7de194ea23827e08c49f4519c1000708a4bd91b4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350161"
---
# <a name="call-statement-visual-basic"></a>Call — Instrukcja (Visual Basic)

Przenosi formant do procedury `Function`, `Sub`lub biblioteki dołączanej dynamicznie (DLL).  
  
## <a name="syntax"></a>Składnia  
  
```vb  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>Części  

|||
|---|---|
|`procedureName`|Wymagana. Nazwa procedury do wywołania.|
|`argumentList`|Opcjonalna. Lista zmiennych lub wyrażeń reprezentujących argumenty, które są przekazane do procedury po wywołaniu. Wiele argumentów jest oddzielonych przecinkami. Jeśli dołączysz `argumentList`, musisz ująć ją w nawiasy.|
|||
  
## <a name="remarks"></a>Uwagi

 Po wywołaniu procedury można użyć słowa kluczowego `Call`. W większości wywołań procedur użycie tego słowa kluczowego nie jest konieczne.

 Zwykle używasz słowa kluczowego `Call`, gdy wywoływane wyrażenie nie zaczyna się od identyfikatora. Użycie słowa kluczowego `Call` do innych celów nie jest zalecane.

 Jeśli procedura zwróci wartość, instrukcja `Call` odrzuca ją.

## <a name="example"></a>Przykład

 Poniższy kod przedstawia dwa przykłady, w których słowo kluczowe `Call` jest niezbędne do wywołania procedury. W obu przykładach wywoływane wyrażenie nie zaczyna się od identyfikatora.

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a>Zobacz także

- [Function, instrukcja](function-statement.md)
- [Sub, instrukcja](sub-statement.md)
- [Declare, instrukcja](declare-statement.md)
- [Wyrażenia lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
