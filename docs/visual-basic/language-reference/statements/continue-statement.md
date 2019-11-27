---
title: Continue, instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 20140cafb68c7e5518bf3d5fa80e56ca1c1de2c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354108"
---
# <a name="continue-statement-visual-basic"></a>Continue — Instrukcja (Visual Basic)
Natychmiast przenosi kontrolę do następnej iteracji pętli.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Uwagi  
 Można dokonać transferu z wewnątrz pętli `Do`, `For`lub `While` do następnej iteracji tej pętli. Kontrolka natychmiast przechodzi do testu warunku pętli, który jest równoznaczny z transferem do instrukcji `For` lub `While` lub do instrukcji `Do` lub `Loop`, która zawiera klauzulę `Until` lub `While`.  
  
 `Continue` można użyć w dowolnej lokalizacji w pętli, która umożliwia transfery. Reguły zezwalające na transfer kontroli są takie same jak w przypadku [instrukcji goto](../../../visual-basic/language-reference/statements/goto-statement.md).  
  
 Na przykład jeśli pętla znajduje się w całości w bloku `Try`, blok `Catch` lub blok `Finally`, można użyć `Continue` do przetransferowania z pętli. Jeśli z drugiej strony, struktura `Try`...`End Try` jest zawarta w pętli, nie można użyć `Continue` do transferu kontroli z bloku `Finally` i można jej użyć do transferowania z `Try` lub `Catch` bloku tylko wtedy, gdy przeniesiesz całkowicie z `Try`...`End Try` Structure.  
  
 Jeśli istnieją zagnieżdżone pętle tego samego typu, na przykład pętla `Do` w innej pętli `Do`, instrukcja `Continue Do` pomija następną iterację wewnętrznej pętli `Do`, która ją zawiera. Nie można użyć `Continue`, aby przejść do następnej iteracji zawierającej pętlę tego samego typu.  
  
 Jeśli istnieją zagnieżdżone pętle różnych typów, na przykład pętla `Do` w pętli `For`, można przejść do następnej iteracji każdej pętli, używając `Continue Do` lub `Continue For`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu używa instrukcji `Continue While`, aby przejść do następnej kolumny tablicy, Jeśli dzielnik ma wartość zero. `Continue While` znajduje się wewnątrz pętli `For`. Przesyła do instrukcji `While col < lastcol`, która jest następną iteracją wewnętrznej pętli `While`, która zawiera pętlę `For`.  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Zobacz także

- [Do...Loop, instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [While...End While, instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
