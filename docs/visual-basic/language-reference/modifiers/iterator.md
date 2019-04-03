---
title: Iterator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 499949d1f4c20e1f465355bd076ba39f1496779b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822703"
---
# <a name="iterator-visual-basic"></a>Iterator (Visual Basic)
Określa, że funkcja lub `Get` metody dostępu jest iteratorem.  
  
## <a name="remarks"></a>Uwagi  
 *Iteratora* wykonywania niestandardowych iteracji przez kolekcję. Używa iteratora [uzyskanie](../../../visual-basic/language-reference/statements/yield-statement.md) instrukcja zwraca każdy element w jednej kolekcji w danym momencie. Gdy `Yield` osiągnięta zostanie instrukcja, bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.  
  
 Iterator można zaimplementować jako funkcję lub `Get` akcesor definicji właściwości. `Iterator` Modyfikator pojawia się w deklaracji funkcji iteratora lub `Get` metody dostępu.  
  
 Wywołujesz iterację z poziomu kodu klienta przy użyciu [For Each... Następna instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 Zwracany typ funkcji iteratora lub `Get` dostępu mogą być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Iterator nie może zawierać żadnych `ByRef` parametrów.  
  
 Iterator nie może wystąpić w zdarzeń, konstruktora wystąpienia, statyczny Konstruktor lub destruktor statyczne.  
  
 Iteracją może być funkcją anonimową. Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="usage"></a>Użycie  
 `Iterator` Modyfikator mogą być używane w tych kontekstach:  
  
-   [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano funkcji iteratora. Funkcja iteratora ma `Yield` instrukcji, która znajduje się wewnątrz [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) pętli. Każda iteracja [dla każdego](../../../visual-basic/language-reference/statements/for-each-next-statement.md) treść instrukcji w `Main` tworzy wywołanie `Power` funkcji iteratora. Każde wywołanie funkcji iteratora przechodzi do następnego wykonania `Yield` instrukcję, która występuje w ciągu następnej iteracji `For…Next` pętli.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano `Get` metodę dostępu, która jest iteratorem. `Iterator` Modyfikator znajduje się w deklaracji właściwości.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Aby uzyskać więcej przykładów, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [Iteratory](../../programming-guide/concepts/iterators.md)
- [Yield, instrukcja](../../../visual-basic/language-reference/statements/yield-statement.md)
