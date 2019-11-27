---
title: TryCast, operator
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: 53306575cfc385039be3939fd87cf993b4509af4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348213"
---
# <a name="trycast-operator-visual-basic"></a>TryCast — Operator (Visual Basic)
Wprowadza operację konwersji typu, która nie zgłasza wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli próba konwersji nie powiedzie się, `CType` i `DirectCast` zgłosić błąd <xref:System.InvalidCastException>. Może to niekorzystnie wpłynąć na wydajność aplikacji. `TryCast` zwraca wartość [Nothing](../../../visual-basic/language-reference/nothing.md), więc nie trzeba obsługiwać możliwego wyjątku, tylko test zwracanego wyniku dla `Nothing`.  
  
 Użyj słowa kluczowego `TryCast` w taki sam sposób, jak w przypadku użycia [funkcji CType](../../../visual-basic/language-reference/functions/ctype-function.md) i słowa kluczowego [operatora DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) . Możesz podać wyrażenie jako pierwszy argument i typ, aby przekonwertować go na jako drugi argument. `TryCast` działa tylko w przypadku typów referencyjnych, takich jak klasy i interfejsy. Wymaga dziedziczenia lub relacji implementacji między dwoma typami. Oznacza to, że jeden typ musi dziedziczyć po lub zaimplementować inne.  
  
## <a name="errors-and-failures"></a>Błędy i błędy  
 `TryCast` generuje błąd kompilatora, jeśli wykryje, że nie istnieje relacja dziedziczenia lub implementacji. Ale brak błędu kompilatora nie gwarantuje pomyślnej konwersji. Jeśli żądana konwersja jest zawężana, może się nie powieść w czasie wykonywania. W takim przypadku `TryCast` nie zwraca [żadnej](../../../visual-basic/language-reference/nothing.md)wartości.  
  
## <a name="conversion-keywords"></a>Słowa kluczowe konwersji  
 Porównanie słów kluczowych konwersji typu jest następujące.  
  
|Słowo kluczowe|Typy danych|Relacja argumentu|Niepowodzenie czasu wykonywania|  
|---|---|---|---|  
|[Funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md)|Wszystkie typy danych|Konwersja rozszerzająca lub zawężania musi być zdefiniowana między dwoma typami danych|Zgłasza <xref:System.InvalidCastException>|  
|[Operator DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md)|Wszystkie typy danych|Jeden typ musi dziedziczyć po lub zaimplementować inny typ|Zgłasza <xref:System.InvalidCastException>|  
|`TryCast`|Tylko typy referencyjne|Jeden typ musi dziedziczyć po lub zaimplementować inny typ|Zwraca wartość [Nothing](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `TryCast`.  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
