---
title: TryCast, operator
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: 8f0d4f612cd5a96e0b0ab7305c41e00790613cc8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406393"
---
# <a name="trycast-operator-visual-basic"></a>TryCast — Operator (Visual Basic)
Wprowadza operację konwersji typu, która nie zgłasza wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli próba konwersji nie powiedzie się, `CType` a `DirectCast` obie generują <xref:System.InvalidCastException> błędy. Może to niekorzystnie wpłynąć na wydajność aplikacji. `TryCast`Zwraca wartość [Nothing](../nothing.md), tak aby zamiast konieczności obsługiwać możliwy wyjątek, tylko test zwracanego wyniku jest wymagany `Nothing` .  
  
 Użyj `TryCast` słowa kluczowego w taki sam sposób, jak w przypadku użycia [funkcji CType](../functions/ctype-function.md) i słowa kluczowego [operatora DirectCast](directcast-operator.md) . Możesz podać wyrażenie jako pierwszy argument i typ, aby przekonwertować go na jako drugi argument. `TryCast`działa tylko w przypadku typów referencyjnych, takich jak klasy i interfejsy. Wymaga dziedziczenia lub relacji implementacji między dwoma typami. Oznacza to, że jeden typ musi dziedziczyć po lub zaimplementować inne.  
  
## <a name="errors-and-failures"></a>Błędy i błędy  
 `TryCast`generuje błąd kompilatora, jeśli wykryje, że nie istnieje relacja dziedziczenia lub implementacji. Ale brak błędu kompilatora nie gwarantuje pomyślnej konwersji. Jeśli żądana konwersja jest zawężana, może się nie powieść w czasie wykonywania. W takim przypadku `TryCast` zwraca wartość [Nothing](../nothing.md).  
  
## <a name="conversion-keywords"></a>Słowa kluczowe konwersji  
 Porównanie słów kluczowych konwersji typu jest następujące.  
  
|Słowo kluczowe|Typy danych|Relacja argumentu|Niepowodzenie czasu wykonywania|  
|---|---|---|---|  
|[CType — Funkcja](../functions/ctype-function.md)|Wszystkie typy danych|Konwersja rozszerzająca lub zawężania musi być zdefiniowana między dwoma typami danych|Generuje<xref:System.InvalidCastException>|  
|[DirectCast, operator](directcast-operator.md)|Wszystkie typy danych|Jeden typ musi dziedziczyć po lub zaimplementować inny typ|Generuje<xref:System.InvalidCastException>|  
|`TryCast`|Tylko typy referencyjne|Jeden typ musi dziedziczyć po lub zaimplementować inny typ|Zwraca wartość [Nothing](../nothing.md)|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `TryCast` .  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz też

- [Rozszerzanie i zwężanie konwersji](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Konwersje jawne i niejawne](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
