---
title: Iterator
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: bb19289c69f4c523363e88e91a58f37d232b07df
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396236"
---
# <a name="iterator-visual-basic"></a>Iterator (Visual Basic)
Określa, że funkcja lub `Get` metoda dostępu jest iteratorem.  
  
## <a name="remarks"></a>Uwagi  
 *Iterator* wykonuje niestandardową iterację w kolekcji. Iterator używa instrukcji [Yield](../statements/yield-statement.md) do zwrócenia każdego elementu w kolekcji po jednym naraz. Po `Yield` osiągnięciu instrukcji bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.  
  
 Iterator można zaimplementować jako funkcję lub jako `Get` metodę dostępu do definicji właściwości. `Iterator`Modyfikator pojawia się w deklaracji funkcji iteratora lub `Get` metody dostępu.  
  
 Należy wywołać iterator z kodu klienta przy użyciu [for each... Next — instrukcja](../statements/for-each-next-statement.md).  
  
 Zwracanym typem funkcji iteratora lub `Get` metody dostępu może być <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> , lub <xref:System.Collections.Generic.IEnumerator%601> .  
  
 Iterator nie może mieć żadnych `ByRef` parametrów.  
  
 Iterator nie może wystąpić w zdarzeniu, konstruktorze wystąpień, konstruktorze statycznym lub destruktorze statycznym.  
  
 Iterator może być funkcją anonimową. Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="usage"></a>Użycie  
 `Iterator`Modyfikator może być używany w tych kontekstach:  
  
- [Function, instrukcja](../statements/function-statement.md)  
  
- [Property — Instrukcja](../statements/property-statement.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje funkcję iteratora. Funkcja iteratora zawiera `Yield` instrukcję, która znajduje się wewnątrz elementu [... Następna](../statements/for-next-statement.md) pętla. Każda iteracja [dla każdej](../statements/for-each-next-statement.md) treści instrukcji w programie `Main` tworzy wywołanie `Power` funkcji iteratora. Każde wywołanie funkcji iteratora przechodzi do następnego wykonania `Yield` instrukcji, która występuje w następnej iteracji `For…Next` pętli.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje `Get` metodę dostępu, która jest iteratorem. `Iterator`Modyfikator znajduje się w deklaracji właściwości.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Aby uzyskać więcej przykładów, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [Iteratory](../../programming-guide/concepts/iterators.md)
- [Yield, instrukcja](../statements/yield-statement.md)
