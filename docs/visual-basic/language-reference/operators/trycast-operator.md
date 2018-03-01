---
title: "TryCast — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6be11b49eb3b9d98e3bf147e9b1026d4ffc860c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="trycast-operator-visual-basic"></a>TryCast — Operator (Visual Basic)
Wprowadza operację konwersji typu, która zgłosiła wyjątek.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli próba konwersji nie powiedzie się, `CType` i `DirectCast` zarówno throw <xref:System.InvalidCastException> błędu. Może to negatywnie wpłynąć na wydajność aplikacji. `TryCast`Zwraca [nic](../../../visual-basic/language-reference/nothing.md), dzięki czemu zamiast do obsługi wyjątku możliwe, należy tylko testowe zwrócony wynik przed `Nothing`.  
  
 Możesz użyć `TryCast` — słowo kluczowe tak samo jak [CType — funkcja](../../../visual-basic/language-reference/functions/ctype-function.md) i [operatora DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) — słowo kluczowe. Należy podać wyrażenie jako pierwszego argumentu oraz typ konwertować jako drugi argument. `TryCast`działa tylko w typach referencyjnych, takich jak klasy i interfejsy. Wymaga to dziedziczenia lub implementacji relacji między tymi dwoma typami. Oznacza to, że jeden typ musi dziedziczyć lub implementować innych.  
  
## <a name="errors-and-failures"></a>Błędów i niepowodzeń  
 `TryCast`generuje błąd kompilatora, jeśli wykryje, że żadna dziedziczenia lub implementacji relacja nie istnieje. Jednak brak wystąpi błąd kompilatora nie gwarantuje pomyślne konwersji. Jeśli żądany konwersja jest zawężenie, może nie działać w czasie wykonywania. W takim przypadku `TryCast` zwraca [nic](../../../visual-basic/language-reference/nothing.md).  
  
## <a name="conversion-keywords"></a>Słowa kluczowe konwersji  
 Poniżej przedstawiono porównanie słowa kluczowe konwersji typu.  
  
|Słowo kluczowe|Typy danych|Argument relacji|Błąd czasu wykonywania|  
|---|---|---|---|  
|[CType — funkcja](../../../visual-basic/language-reference/functions/ctype-function.md)|Wszystkie typy danych|Rozszerzanie i zwężanie konwersji muszą być zdefiniowane między dwoma typami|Zgłasza wyjątek<xref:System.InvalidCastException>|  
|[DirectCast — Operator](../../../visual-basic/language-reference/operators/directcast-operator.md)|Wszystkie typy danych|Jeden typ musi dziedziczyć lub implementować typ innych|Zgłasza wyjątek<xref:System.InvalidCastException>|  
|`TryCast`|Tylko typy odwołań|Jeden typ musi dziedziczyć lub implementować typ innych|Zwraca [nic](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `TryCast`.  
  
 [!code-vb[VbVbalrKeywords#6](../../../visual-basic/language-reference/codesnippet/VisualBasic/trycast-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
