---
title: Wyniki kwerendy grupowej (LINQ w języku C#)
description: Dowiedz się, jak grupować wyniki za pomocą LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: 577a358c31fcf5346e7aab7a2e2b6be10fd1beff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688465"
---
# <a name="group-query-results"></a>Grupowanie wyników zapytania

Grouping jest jedną z najpotężniejszych możliwości LINQ. W poniższych przykładach przedstawiono sposób grupowania danych na różne sposoby:

- Przez jedną właściwość.

- Przez pierwszą literę właściwości ciągu.

- Według obliczonego zakresu liczbowego.

- Przez predykat logiczny lub inne wyrażenie.

- Przez klucz złożony.

Ponadto ostatnie dwa zapytania projektu ich wyniki do nowego typu anonimowego, który zawiera tylko imię i nazwisko studenta. Aby uzyskać więcej informacji, zobacz [klauzulę group](../language-reference/keywords/group-clause.md).

## <a name="example"></a>Przykład

Wszystkie przykłady w tym temacie użyć następujących klas pomocnika i źródeł danych.

[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak grupować elementy źródłowe przy użyciu pojedynczej właściwości elementu jako klucza grupy. W tym przypadku kluczem `string`jest , nazwisko ucznia. Możliwe jest również użycie podciągu dla klucza. Operacja grupowania używa domyślnego porównania równości dla typu.

Wklej następującą `StudentClass` metodę do klasy. Zmień instrukcję wywołującą `sc.GroupBySingleProperty()`w metodzie na `Main` .

[!code-csharp[csProgGuideLINQ#17](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak grupować elementy źródłowe przy użyciu czegoś innego niż właściwość obiektu dla klucza grupy. W tym przykładzie kluczem jest pierwsza litera nazwiska ucznia.

Wklej następującą `StudentClass` metodę do klasy. Zmień instrukcję wywołującą `sc.GroupBySubstring()`w metodzie na `Main` .

[!code-csharp[csProgGuideLINQ#18](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak grupować elementy źródłowe przy użyciu zakresu liczbowego jako klucza grupy. Kwerenda następnie wyświetla wyniki do typu anonimowego, który zawiera tylko imię i nazwisko oraz zakres percentyla, do którego należy uczeń. Typ anonimowy jest używany, ponieważ nie jest `Student` konieczne użycie kompletnego obiektu do wyświetlania wyników. `GetPercentile`jest funkcją pomocnika, która oblicza percentyl na podstawie średniego wyniku ucznia. Metoda zwraca wartość całkowitą z liczbą całkowitą z liczbą całkowitą z rzędu 0 do 10.

[!code-csharp[csProgGuideLINQ#50](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]

Wklej następującą `StudentClass` metodę do klasy. Zmień instrukcję wywołującą `sc.GroupByRange()`w metodzie na `Main` .

[!code-csharp[csProgGuideLINQ#19](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak grupować elementy źródłowe przy użyciu wyrażenia porównania logicznego. W tym przykładzie wyrażenie logiczne sprawdza, czy średni wynik egzaminu ucznia jest większy niż 75. Podobnie jak w poprzednich przykładach wyniki są rzutowane na typ anonimowy, ponieważ kompletny element źródłowy nie jest potrzebny. Należy zauważyć, że właściwości w typie `Key` anonimowym stają się właściwościami elementu członkowskiego i są dostępne według nazwy podczas wykonywania kwerendy.

Wklej następującą `StudentClass` metodę do klasy. Zmień instrukcję wywołującą `sc.GroupByBoolean()`w metodzie na `Main` .

[!code-csharp[csProgGuideLINQ#20](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać typu anonimowego do hermetyzacji klucza, który zawiera wiele wartości. W tym przykładzie pierwszą wartością klucza jest pierwsza litera nazwiska ucznia. Drugą wartością klucza jest wartość logiczna, która określa, czy uczeń uzyskał wynik powyżej 85 punktów na pierwszym egzaminie. Grupy można zamówić według dowolnej właściwości w kluczu.

Wklej następującą `StudentClass` metodę do klasy. Zmień instrukcję wywołującą `sc.GroupByCompositeKey()`w metodzie na `Main` .

[!code-csharp[csProgGuideLINQ#21](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.IGrouping%602>
- [Language Integrated Query (LINQ)](index.md)
- [group, klauzula](../language-reference/keywords/group-clause.md)
- [Typy anonimowe](../programming-guide/classes-and-structs/anonymous-types.md)
- [Wykonywanie podkwerendy w operacji grupowania](perform-a-subquery-on-a-grouping-operation.md)
- [Tworzenie grupy zagnieżdżonej](create-a-nested-group.md)
- [Grupowanie danych](../programming-guide/concepts/linq/grouping-data.md)
