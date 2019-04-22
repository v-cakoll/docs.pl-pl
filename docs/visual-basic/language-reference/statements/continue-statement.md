---
title: Continue — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 5523be69f2901851c86f6c0263548e3577507ff9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835394"
---
# <a name="continue-statement-visual-basic"></a>Continue — Instrukcja (Visual Basic)
Kontrolka transferu bezpośrednio do następnej iteracji pętli.  
  
## <a name="syntax"></a>Składnia  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Uwagi  
 Można przenieść z wewnątrz `Do`, `For`, lub `While` pętli do następnej iteracji pętli tego. Kontrola przechodzi bezpośrednio do testu warunek pętli, który jest odpowiednikiem przesyłania do `For` lub `While` instrukcji lub `Do` lub `Loop` instrukcji, która zawiera `Until` lub `While` klauzuli.  
  
 Możesz użyć `Continue` w dowolnym miejscu w pętli, która umożliwia transfer. Zasady umożliwiające przekazywanie sterowania są takie same jak za pomocą [instrukcji GoTo](../../../visual-basic/language-reference/statements/goto-statement.md).  
  
 Na przykład, jeśli pętla jest całkowicie zawarte w ramach `Try` bloku, `Catch` bloku lub `Finally` bloku, możesz użyć `Continue` na przesyłanie wyjścia z pętli. Jeśli z drugiej strony, `Try`... `End Try` struktury jest zawarty w pętli, nie można użyć `Continue` Aby przekazać sterowanie z `Finally` bloku i służy do przeniesienia poza `Try` lub `Catch` zablokować tylko wtedy, gdy przeniesiesz całkowicie z `Try`... `End Try` struktury.  
  
 Jeśli na przykład masz zagnieżdżonej pętli tego samego typu `Do` pętli w innym `Do` pętli, `Continue Do` instrukcji przejdzie do następnej iteracji najbardziej wewnętrzną funkcją `Do` pętli, która go zawiera. Nie można użyć `Continue` aby przejść do następnej iteracji pętli zawierającego tego samego typu.  
  
 Jeśli na przykład masz zagnieżdżonej pętli różnych typów, `Do` pętli w ramach `For` pętli, możesz przejść do następnej iteracji pętli albo przy użyciu `Continue Do` lub `Continue For`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `Continue While` instrukcję, aby przejść do następnej kolumny tablicy, jeśli dzielnik jest równa zero. `Continue While` Znajduje się wewnątrz `For` pętli. Przesyłania do `While col < lastcol` instrukcji, co jest kolejną iterację najbardziej wewnętrzną funkcją `While` pętli, która zawiera `For` pętli.  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Zobacz także

- [Do...Loop, instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [While...End While, instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
