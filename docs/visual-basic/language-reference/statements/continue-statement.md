---
title: Continue, instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: fd604b281a590073a5e76398788d7648cadd145c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382097"
---
# <a name="continue-statement-visual-basic"></a>Continue — Instrukcja (Visual Basic)
Natychmiast przenosi kontrolę do następnej iteracji pętli.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Uwagi  
 Można przenieść z wewnątrz `Do` , `For` lub `While` do następnej iteracji pętli. Kontrolka natychmiast przechodzi do testu warunku pętli, który jest równoznaczny z transferem do `For` instrukcji or lub `While` do `Do` instrukcji or, `Loop` która zawiera `Until` `While` klauzulę OR.  
  
 Można użyć `Continue` w dowolnej lokalizacji w pętli, która umożliwia transfery. Reguły zezwalające na transfer kontroli są takie same jak w przypadku [instrukcji goto](goto-statement.md).  
  
 Na przykład jeśli pętla znajduje się w całości w `Try` bloku, `Catch` bloku lub `Finally` bloku, można użyć `Continue` do przetransferowania z pętli. Jeśli z drugiej strony, `Try` Struktura... `End Try` jest zawarta w pętli, nie można użyć `Continue` programu do przeniesienia kontroli z `Finally` bloku i można użyć jej do przesłania poza `Try` lub tylko wtedy, `Catch` gdy przeniesiesz całkowicie poza `Try` strukturę... `End Try` .  
  
 Jeśli istnieją zagnieżdżone pętle tego samego typu, na przykład `Do` Pętla w innej `Do` pętli, `Continue Do` instrukcja przeskoczy do następnej iteracji wewnętrznej `Do` pętli, która ją zawiera. Nie można użyć, `Continue` Aby przejść do następnej iteracji zawierającej pętlę tego samego typu.  
  
 Jeśli istnieją zagnieżdżone pętle różnych typów, na przykład `Do` Pętla w `For` pętli, można przejść do następnej iteracji jednej pętli, używając `Continue Do` lub `Continue For` .  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu używa instrukcji, `Continue While` Aby przejść do następnej kolumny tablicy, Jeśli dzielnik ma wartość zero. `Continue While`Znajduje się wewnątrz `For` pętli. Przesyła do `While col < lastcol` instrukcji, która jest następną iteracją wewnętrznej `While` pętli, która zawiera `For` pętlę.  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Zobacz też

- [Do...Loop, instrukcja](do-loop-statement.md)
- [For...Next, instrukcja](for-next-statement.md)
- [While...End While, instrukcja](while-end-while-statement.md)
- [Try...Catch...Finally, instrukcja](try-catch-finally-statement.md)
