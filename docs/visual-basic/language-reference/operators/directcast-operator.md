---
title: DirectCast — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 628ce4f06b91d0f514f71dea3aad8ea0fee6dccf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821507"
---
# <a name="directcast-operator-visual-basic"></a>DirectCast — Operator (Visual Basic)
Wprowadza operację konwersji typu, na podstawie dziedziczenie lub wdrożenia.  
  
## <a name="remarks"></a>Uwagi  
 `DirectCast` nie używa języka Visual Basic pomocnika czasu wykonywania procedury konwersji, dzięki czemu umożliwia ona nieco większą wydajność niż `CType` podczas konwersji do i z typem danych `Object`.  
  
 Możesz użyć `DirectCast` podobny sposób, możesz użyć słowa kluczowego [funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md) i [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) — słowo kluczowe. Należy podać wyrażenie jako pierwszy argument i typ, aby przekonwertować go pod kątem jako drugi argument. `DirectCast` wymaga dziedziczenie lub implementacji relacji między tymi typami danych dwa argumenty. Oznacza to, że jeden typ musi dziedziczyć lub innych implementacji.  
  
## <a name="errors-and-failures"></a>Błędy i niepowodzenia  
 `DirectCast` generuje błąd kompilatora, jeśli wykryje, że istnieje żadna relacja dziedziczenie lub implementacji. Ale brak błąd kompilatora nie gwarantuje pomyślne konwersji. Jeśli żądany konwersji jest zawężenie, może nie działać w czasie wykonywania. Jeśli tak się stanie, środowisko wykonawcze zgłasza <xref:System.InvalidCastException> błędu.  
  
## <a name="conversion-keywords"></a>Słowa kluczowe konwersji  
 Porównanie słowa kluczowe konwersji typu, jest w następujący sposób.  
  
|Słowo kluczowe|Typy danych|Argument relacji|Błąd czasu wykonywania|  
|---|---|---|---|  
|[Funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md)|Wszystkie typy danych|Rozszerzanie i zwężanie konwersji muszą być zdefiniowane między dwoma typami danych|Zgłasza wyjątek <xref:System.InvalidCastException>|  
|`DirectCast`|Wszystkie typy danych|Jeden typ musi dziedziczyć lub implementował z innego typu|Zgłasza wyjątek <xref:System.InvalidCastException>|  
|[Operator TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md)|Tylko typy odwołań|Jeden typ musi dziedziczyć lub implementował z innego typu|Zwraca [nic](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano dwa przypadki użycia `DirectCast`, taki, który nie powiedzie się w czasie wykonywania i jedną, zakończy się pomyślnie.  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 W powyższym przykładzie środowiska wykonawczego typu `q` jest `Double`. `CType` zakończy się pomyślnie, ponieważ `Double` mogą być konwertowane na `Integer`. Jednak pierwszy `DirectCast` zakończy się niepowodzeniem w czasie wykonywania, ponieważ typ środowiska wykonawczego `Double` nie ma dziedziczenia relacji z `Integer`, nawet jeśli istnieje konwersji. Drugi `DirectCast` powiedzie się, ponieważ są konwertowane typu <xref:System.Windows.Forms.Form> na typ <xref:System.Windows.Forms.Control>, z którego <xref:System.Windows.Forms.Form> dziedziczy.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
