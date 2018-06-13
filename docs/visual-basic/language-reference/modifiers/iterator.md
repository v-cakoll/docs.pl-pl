---
title: Iterator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 565508046b3fa2dc52acf8c5204153beffc15d9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599515"
---
# <a name="iterator-visual-basic"></a>Iterator (Visual Basic)
Określa, że funkcja lub `Get` akcesor jest iteratora.  
  
## <a name="remarks"></a>Uwagi  
 *Iterator* wykonuje niestandardowych iteracji w kolekcji. Używa iteratora [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instrukcji, aby zwracany był każdy element w kolekcji jednego naraz. Gdy `Yield` osiągnięciu instrukcji, są przechowywane w bieżącej lokalizacji w kodzie. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.  
  
 Iteratora można zaimplementować jako funkcję lub `Get` akcesor definicji właściwości. `Iterator` Modyfikator pojawia się w deklaracji funkcji iteracyjnej lub `Get` dostępu.  
  
 Wywołaj iteratora z kodu klienta przy użyciu [For Each... Następna instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 Zwracany typ funkcji iteracyjnej lub `Get` dostępu może być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Iterator nie mogą zawierać `ByRef` parametrów.  
  
 Iterator nie może wystąpić w zdarzenia, konstruktora wystąpienia, statycznego konstruktora lub destruktora statycznych.  
  
 Iteratora można funkcji anonimowej. Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="usage"></a>Użycie  
 `Iterator` Modyfikatora można używać w tych sytuacjach:  
  
-   [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano funkcji iteracyjnej. Funkcja iteratora ma `Yield` instrukcji, która znajduje się wewnątrz [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) pętli. Każdej iteracji [dla każdego](../../../visual-basic/language-reference/statements/for-each-next-statement.md) treść instrukcji w `Main` tworzy wywołanie `Power` funkcji iteracyjnej. Każde wywołanie funkcji iteracyjnej przechodzi do następnego wykonywanie `Yield` instrukcja, która występuje w ciągu następnej iteracji `For…Next` pętli.  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_1.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano `Get` dostępu, który jest iteratora. `Iterator` Jest modyfikatora w deklaracji właściwości.  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_2.vb)]  
  
 Aby uzyskać dodatkowe przykłady, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>  
 [Iteratory](../../programming-guide/concepts/iterators.md)  
 [Yield, instrukcja](../../../visual-basic/language-reference/statements/yield-statement.md)
