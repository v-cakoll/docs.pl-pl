---
title: niezaznaczone słowo kluczowe — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: 6dad0dfd508fb390dd0a52d1b48d70b4c5725513
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713004"
---
# <a name="unchecked-c-reference"></a>unchecked (odwołanie w C#)

Słowo `unchecked` kluczowe służy do pomijania sprawdzania przepełnienia dla operacji arytmetycznych typu integralnego i konwersji.

W kontekście niezaznaczone, jeśli wyrażenie tworzy wartość, która znajduje się poza zakresem typu docelowego, przepełnienie nie jest oflagowane. Na przykład, ponieważ obliczenia w poniższym `unchecked` przykładzie są wykonywane w bloku lub wyrażeniu, fakt, że `int1` wynik jest zbyt duży dla liczby całkowitej jest ignorowany i jest przypisywany wartość -2,147,483,639.

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

Jeśli `unchecked` środowisko zostanie usunięte, wystąpi błąd kompilacji. Przepełnienie można wykryć w czasie kompilacji, ponieważ wszystkie warunki wyrażenia są stałe.

Wyrażenia zawierające terminy niestałe są domyślnie niezaznaczone w czasie kompilacji i czasie wykonywania. Zobacz [sprawdzone informacje](checked.md) dotyczące włączania sprawdzonego środowiska.

Ponieważ sprawdzanie przepełnienia zajmuje czas, użycie niezaznaczonego kodu w sytuacjach, gdy nie ma niebezpieczeństwa przepełnienia może zwiększyć wydajność. Jednak jeśli przepełnienie jest możliwe, należy użyć sprawdzonego środowiska.

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak używać słowa kluczowego. `unchecked`

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Checked i Unchecked](checked-and-unchecked.md)
- [Sprawdzane](checked.md)
