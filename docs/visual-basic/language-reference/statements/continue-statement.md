---
title: Continue — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 9ee5fb19db6eafeb7e4bed12935d0b950d6368d6
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005106"
---
# <a name="continue-statement-visual-basic"></a>Continue — Instrukcja (Visual Basic)
Natychmiast przenosi kontrolę do następnej iteracji pętli.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Uwagi  
 Można dokonać transferu z wewnątrz pętli `Do`, `For` lub `While` do następnej iteracji tej pętli. Kontrolka natychmiast przechodzi do testu warunku pętli, który jest równoważny do przenoszenia do instrukcji `For` lub `While` lub do instrukcji `Do` lub `Loop`, która zawiera klauzulę `Until` lub `While`.  
  
 Można użyć `Continue` w dowolnej lokalizacji w pętli, która umożliwia transfery. Reguły zezwalające na transfer kontroli są takie same jak w przypadku [instrukcji goto](../../../visual-basic/language-reference/statements/goto-statement.md).  
  
 Na przykład jeśli pętla jest całkowicie zawarta w bloku `Try`, blok `Catch` lub blok `Finally`, można użyć `Continue` do przetransferowania z pętli. Jeśli z drugiej strony, struktura `Try`... `End Try` jest zawarta w pętli, nie można użyć `Continue` do transferowania kontroli z bloku `Finally` i można jej użyć do przetransferowania z `Try` lub `Catch` bloków tylko wtedy, gdy transfer jest całkowicie z @no_ Struktura _T-6... `End Try`.  
  
 Jeśli istnieją zagnieżdżone pętle tego samego typu, na przykład pętla `Do` w innej pętli `Do`, instrukcja `Continue Do` przeskakuje do następnej iteracji wewnętrznej pętli `Do`, która ją zawiera. Nie można użyć `Continue`, aby przejść do następnej iteracji zawierającej pętlę tego samego typu.  
  
 Jeśli istnieją zagnieżdżone pętle różnych typów, na przykład pętla `Do` w pętli `For`, można przejść do następnej iteracji każdej pętli, używając `Continue Do` lub `Continue For`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu używa instrukcji `Continue While`, aby przejść do następnej kolumny tablicy, Jeśli dzielnik jest równy zero. @No__t-0 jest wewnątrz pętli `For`. Przesyła do `While col < lastcol` instrukcji, która jest następną iteracją wewnętrznej pętli `While`, która zawiera pętlę `For`.  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Zobacz także

- [Do...Loop, instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [While...End While, instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
