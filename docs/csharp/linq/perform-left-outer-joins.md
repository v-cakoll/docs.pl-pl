---
title: Wykonanie lewych sprzężeń zewnętrznych (LINQ w C#)
description: Dowiedz się, jak wykonanie lewych sprzężeń zewnętrznych za pomocą LINQ w C#.
ms.date: 12/1/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: a4e6fb73a599d0212d72a585bba98630e828e21e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528943"
---
# <a name="perform-left-outer-joins"></a>Wykonanie lewych sprzężeń zewnętrznych

Lewe sprzężenie zewnętrzne jest elementem sprzężenia, w której każdy element pierwsza kolekcja jest zwracana, niezależnie od tego, czy ma żadnych elementów skorelowane w drugiej kolekcji. LINQ umożliwia wykonywanie lewe sprzężenie zewnętrzne, wywołując <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metody na wynikach sprzężenie grupy.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób użycia <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metody na wynikach sprzężenie grupy do wykonania lewego sprzężenia zewnętrznego.

Pierwszym krokiem podczas produkcji lewe sprzężenie zewnętrzne dwóch kolekcji jest wykonywanie sprzężenia wewnętrznego przy użyciu sprzężenie grupy. (Zobacz [wykonanie sprzężeń wewnętrznych](perform-inner-joins.md) objaśnienia dotyczące tego procesu.) W tym przykładzie lista `Person` obiektów jest wewnętrzny przyłączone do listy `Pet` na podstawie obiektów `Person` obiektu, który odpowiada `Pet.Owner`.

Drugim krokiem jest uwzględnienie każdego elementu pierwszej kolekcji (po lewej stronie) w zestawie, nawet jeśli ten element nie ma żadnych dopasowań w prawo kolekcji wyników. Jest to realizowane przez wywołanie metody <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> na każdej sekwencji zgodnych elementów z sprzężenie grupy. W tym przykładzie <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> jest wywoływana w każdej sekwencji zgodnych `Pet` obiektów. Metoda zwraca kolekcję, która zawiera pojedynczą, wartość domyślna, jeśli sekwencja zgodnych `Pet` obiektów jest pusta dla żadnego `Person` obiektu, zapewniając, że każdy `Person` obiekt jest reprezentowany w kolekcji wynik.

> [!NOTE]
> Wartość domyślna dla typu odwołania to `null`; w związku z tym, przykład sprawdza, czy odwołania zerowego przed uzyskaniem dostępu do każdego elementu `Pet` kolekcji.

[!code-csharp[CsLINQProgJoining#7](~/samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [Wykonywanie sprzężeń wewnętrznych](perform-inner-joins.md)
- [Wykonywanie sprzężeń grupowanych](perform-grouped-joins.md)
- [Typy anonimowe](../programming-guide/classes-and-structs/anonymous-types.md)
