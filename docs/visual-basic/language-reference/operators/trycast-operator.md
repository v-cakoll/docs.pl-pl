---
title: TryCast — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: c0eea4565d5040bb00743fc7864ac15b0fccdea9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013468"
---
# <a name="trycast-operator-visual-basic"></a>TryCast — Operator (Visual Basic)
Wprowadza operację konwersji typu, która nie zgłasza wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli próba konwersji nie powiedzie się, `CType` i `DirectCast` zarówno throw <xref:System.InvalidCastException> błędu. Może to negatywnie wpłynąć na wydajność aplikacji. `TryCast` Zwraca [nic](../../../visual-basic/language-reference/nothing.md), dzięki czemu nie trzeba obsłużyć wyjątek to możliwe, należy tylko przetestować zwracany wynik względem `Nothing`.  
  
 Możesz użyć `TryCast` taki sam sposób, możesz użyć słowa kluczowego [funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md) i [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) — słowo kluczowe. Należy podać wyrażenie jako pierwszy argument i typ, aby przekonwertować go pod kątem jako drugi argument. `TryCast` działa tylko na typy odwołań, takich jak klasy i interfejsy. Wymaga to dziedziczenie lub implementacji relacji między tymi dwoma typami. Oznacza to, że jeden typ musi dziedziczyć lub innych implementacji.  
  
## <a name="errors-and-failures"></a>Błędy i niepowodzenia  
 `TryCast` generuje błąd kompilatora, jeśli wykryje, że istnieje żadna relacja dziedziczenie lub implementacji. Ale brak błąd kompilatora nie gwarantuje pomyślne konwersji. Jeśli żądany konwersji jest zawężenie, może nie działać w czasie wykonywania. W takim przypadku `TryCast` zwraca [nic](../../../visual-basic/language-reference/nothing.md).  
  
## <a name="conversion-keywords"></a>Słowa kluczowe konwersji  
 Porównanie słowa kluczowe konwersji typu, jest w następujący sposób.  
  
|Słowo kluczowe|Typy danych|Argument relacji|Błąd czasu wykonywania|  
|---|---|---|---|  
|[Funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md)|Wszystkie typy danych|Rozszerzanie i zwężanie konwersji muszą być zdefiniowane między dwoma typami danych|Zgłasza wyjątek <xref:System.InvalidCastException>|  
|[Operator DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md)|Wszystkie typy danych|Jeden typ musi dziedziczyć lub implementował z innego typu|Zgłasza wyjątek <xref:System.InvalidCastException>|  
|`TryCast`|Tylko typy odwołań|Jeden typ musi dziedziczyć lub implementował z innego typu|Zwraca [nic](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `TryCast`.  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
