---
title: Continue — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: eb8596c43bf6232eec4bcb844e6202c5de373404
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602726"
---
# <a name="continue-statement-visual-basic"></a>Continue — Instrukcja (Visual Basic)
Formant transferów bezpośrednio do następnej iteracji pętli.  
  
## <a name="syntax"></a>Składnia  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Uwagi  
 Można przenieść z wewnątrz `Do`, `For`, lub `While` pętli do następnej iteracji pętli tego. Kontrola przechodzi natychmiast w teście warunek pętli, który jest odpowiednikiem transferu do `For` lub `While` instrukcji lub `Do` lub `Loop` instrukcji, która zawiera `Until` lub `While` klauzuli.  
  
 Można użyć `Continue` w dowolnym miejscu w pętli, które umożliwia transferów. Zasady umożliwiające przekazanie sterowania są takie same jak z [instrukcji GoTo](../../../visual-basic/language-reference/statements/goto-statement.md).  
  
 Na przykład, jeśli jest całkowicie zawarte w pętli `Try` bloku, `Catch` bloku, lub `Finally` bloku, można użyć `Continue` do przeniesienia poza pętli. Jeśli z drugiej strony, `Try`... `End Try` struktury znajduje się w pętli, nie można użyć `Continue` do przekazywania kontroli z `Finally` blok i służy do przeniesienia poza `Try` lub `Catch` zablokować tylko wtedy, gdy transfer całkowicie poza `Try`... `End Try` struktury.  
  
 Jeśli na przykład masz pętle zagnieżdżone tego samego typu `Do` pętli w innym `Do` pętli, `Continue Do` instrukcji przejdzie do następnej iteracji najbardziej wewnętrzną funkcją `Do` pętli, która go zawiera. Nie można użyć `Continue` aby przejść do następnej iteracji pętli zawierającego tego samego typu.  
  
 Jeśli na przykład masz pętle zagnieżdżone o różnych typach `Do` pętli w ramach `For` pętli, możesz przejść do następnej iteracji pętli albo za pomocą `Continue Do` lub `Continue For`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `Continue While` instrukcji, aby przejść do następnej kolumnie tablicy, jeśli dzielnik jest równy zero. `Continue While` Znajduje się wewnątrz `For` pętli. Przekazuje do `While col < lastcol` instrukcja, która jest najbardziej wewnętrzną funkcją następnej iteracji `While` pętli, które zawiera `For` pętli.  
  
 [!code-vb[VbVbalrStatements#14](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/continue-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Do...Loop, instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [While...End While, instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
