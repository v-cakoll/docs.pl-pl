---
title: Iterator
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 9d7eaf186bae544031487ce027505e1e0d4ae0f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351522"
---
# <a name="iterator-visual-basic"></a>Iterator (Visual Basic)
Określa, że metoda dostępu funkcji lub `Get` jest iteratorem.  
  
## <a name="remarks"></a>Uwagi  
 *Iterator* wykonuje niestandardową iterację w kolekcji. Iterator używa instrukcji [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) do zwrócenia każdego elementu w kolekcji po jednym naraz. Po osiągnięciu instrukcji `Yield` bieżąca lokalizacja w kodzie jest zachowywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.  
  
 Iterator może być zaimplementowany jako funkcja lub jako metoda dostępu `Get` definicji właściwości. Modyfikator `Iterator` pojawia się w deklaracji funkcji iteratora lub metody dostępu `Get`.  
  
 Należy wywołać iterator z kodu klienta przy użyciu [for each... Next — instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 Zwracany typ funkcji iteratora lub metody dostępu `Get` może być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>lub <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Iterator nie może mieć żadnych parametrów `ByRef`.  
  
 Iterator nie może wystąpić w zdarzeniu, konstruktorze wystąpień, konstruktorze statycznym lub destruktorze statycznym.  
  
 Iterator może być funkcją anonimową. Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="usage"></a>Użycie  
 Modyfikator `Iterator` może być używany w tych kontekstach:  
  
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje funkcję iteratora. Funkcja iteratora ma instrukcję `Yield`, która znajduje się wewnątrz elementu [... Następna](../../../visual-basic/language-reference/statements/for-next-statement.md) pętla. Każda iteracja [dla każdej](../../../visual-basic/language-reference/statements/for-each-next-statement.md) treści instrukcji w `Main` tworzy wywołanie funkcji iteratora `Power`. Każde wywołanie funkcji iteratora przechodzi do następnego wykonania instrukcji `Yield`, która występuje w następnej iteracji pętli `For…Next`.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład demonstruje metodę dostępu `Get`, która jest iteratorem. Modyfikator `Iterator` jest w deklaracji właściwości.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Aby uzyskać więcej przykładów, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [Iteratory](../../programming-guide/concepts/iterators.md)
- [Yield, instrukcja](../../../visual-basic/language-reference/statements/yield-statement.md)
