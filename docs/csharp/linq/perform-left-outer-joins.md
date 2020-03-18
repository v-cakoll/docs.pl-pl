---
title: Wykonywanie sprzężeń lewych zewnętrznych (LINQ w języku C)Perform left outer joins (LINQ in C#)
description: Dowiedz się, jak wykonywać sprzężenia zewnętrzne lewe przy użyciu LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: cc08a1c8670623a10d1e0bf10221d02037a8d7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688582"
---
# <a name="perform-left-outer-joins"></a>Wykonywanie lewych sprzężeń zewnętrznych

Sprzężenie zewnętrzne lewe jest sprzężenie, w którym każdy element pierwszej kolekcji jest zwracany, niezależnie od tego, czy ma żadnych skorelowanych elementów w drugiej kolekcji. Linq służy do wykonywania sprzężenia <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> zewnętrznego w lewo, wywołując metodę na wyniki sprzężenia grupy.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metody na wyniki sprzężenia grupy do wykonywania sprzężenia zewnętrznego lewej.

Pierwszym krokiem w produkcji lewego sprzężenia zewnętrznego dwóch kolekcji jest wykonanie sprzężenia wewnętrznego przy użyciu sprzężenia grupy. (Zobacz [Wykonywanie sprzężeń wewnętrznych,](perform-inner-joins.md) aby uzyskać wyjaśnienie tego procesu). W tym przykładzie lista `Person` obiektów jest wewnętrznie przyłączona do listy `Pet` obiektów na podstawie `Person` obiektu, który pasuje `Pet.Owner`do .

Drugim krokiem jest uwzględnienie każdego elementu pierwszej (po lewej) kolekcji w zestawie wyników, nawet jeśli ten element nie ma żadnych dopasowań w prawej kolekcji. Jest to realizowane <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> przez wywołanie każdej sekwencji pasujących elementów z grupy sprzężenia. W tym <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> przykładzie jest wywoływana `Pet` na każdej sekwencji pasujących obiektów. Metoda zwraca kolekcję, która zawiera pojedynczą, wartość `Pet` domyślną, `Person` jeśli sekwencja pasujących `Person` obiektów jest pusta dla dowolnego obiektu, zapewniając w ten sposób, że każdy obiekt jest reprezentowany w kolekcji wyników.

> [!NOTE]
> Wartością domyślną dla `null`typu odwołania jest; w związku z tym przykład sprawdza dla odwołania `Pet` null przed uzyskując dostęp do każdego elementu każdej kolekcji.

[!code-csharp[CsLINQProgJoining#7](~/samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [Wykonywanie sprzężeń wewnętrznych](perform-inner-joins.md)
- [Wykonywanie sprzężeń grupowanych](perform-grouped-joins.md)
- [Typy anonimowe](../programming-guide/classes-and-structs/anonymous-types.md)
