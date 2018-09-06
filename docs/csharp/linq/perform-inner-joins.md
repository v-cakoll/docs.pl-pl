---
title: Wykonanie sprzężeń wewnętrznych (LINQ w C#)
description: Dowiedz się, jak wykonanie sprzężeń wewnętrznych za pomocą LINQ w C#.
ms.date: 12/1/2016
ms.assetid: 45bceed6-f549-4114-a9b1-b44feb497742
ms.openlocfilehash: 2f6aad30dc8278ce1bb88bacc19b27deaa0288c7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43746850"
---
# <a name="perform-inner-joins"></a>Wykonanie sprzężeń wewnętrznych

W warunkach relacyjnej bazy danych *sprzężenia wewnętrznego* tworzy zestaw wyników, w której każdy element pierwszej kolekcji pojawia się jeden raz dla każdego pasującego elementu w drugim zbiorze. Jeśli element z pierwszej kolekcji nie ma pasujących elementów, nie ma w zestawie wyników. <xref:System.Linq.Enumerable.Join%2A> Metody, która jest wywoływana przez `join` klauzuli w języku C#, implementuje sprzężenia wewnętrznego.

W tym artykule pokazano, jak wykonać cztery wariantów sprzężenie wewnętrzne:

- Proste sprzężenie wewnętrzne koreluje elementy z dwóch źródeł danych na podstawie prostego klucza.

- Sprzężenie wewnętrzne, które jest skorelowane elementy z dwóch źródeł danych na podstawie *złożonego* klucza. Klucz złożony, który jest klucz, który składa się z więcej niż jedną wartość, umożliwia korelowanie elementy oparte na więcej niż jednej właściwości.

- A *łączenia wielu* które sprzężenia kolejne operacje są dołączane do siebie nawzajem.

- Sprzężenie wewnętrzne, który jest implementowany przy użyciu sprzężenie grupy.

## <a name="example---simple-key-join"></a>Przykład — proste sprzężenia klucza

Poniższy przykład tworzy dwie kolekcje, które zawierają obiekty z dwóch typów zdefiniowanych przez użytkownika `Person` i `Pet`. Zapytanie używa `join` klauzuli w języku C#, aby dopasować `Person` obiekty z `Pet` obiekty, których `Owner` jest fakt, że `Person`. `select` Klauzuli w języku C# definiuje, jak będzie wyglądać obiekty wynikowe. W tym przykładzie obiekty wynikowe są typy anonimowe, które składają się z właścicielem imię i imię zwierzęcia.

[!code-csharp[CsLINQProgJoining#1](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_1.cs)]

Należy pamiętać, że `Person` którego `LastName` jest "Huff" nie ma zestawu wyników, ponieważ istnieje nie `Pet` obiekt, który ma `Pet.Owner` równa `Person`.

## <a name="example---composite-key-join"></a>Przykład — sprzężenia kluczy złożonych

Zamiast korelacji elementy oparte na tylko jedną właściwość, klucz złożony służy do porównywania elementów na podstawie wielu właściwości. Aby to zrobić, należy określić funkcję selektora kluczy dla każdej kolekcji zwracany typ anonimowy, który składa się z właściwości, które chcesz porównać. Jeśli etykiety właściwości muszą mieć taką samą etykietę w każdy klucz typu anonimowego. Właściwości również musi znajdować się w tej samej kolejności.

W poniższym przykładzie użyto listę `Employee` obiekty i listy `Student` obiektów, aby określić pracowników, którzy także są studentów. Oba typy mają `FirstName` i `LastName` właściwości typu <xref:System.String>. Funkcje, które tworzyć klucze sprzężenia z każdej listy elementów zwracają typ anonimowy, który składa się z `FirstName` i `LastName` właściwości każdego elementu. Operacja join porównuje te klucze złożone pod kątem równości i zwraca pary obiektów z każdej listy, jeśli imię i nazwisko są takie same.

[!code-csharp[CsLINQProgJoining#2](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_2.cs)]

## <a name="example---multiple-join"></a>Przykład — wiele sprzężenia

Dowolna liczba operacji łączenia można dołączyć do siebie, aby wykonać wiele sprzężenia. Każdy `join` klauzuli w języku C# jest określonym źródłem danych przy użyciu wyników poprzedniego sprzężenia.

Poniższy przykład tworzy trzy kolekcje: Lista `Person` obiektów, listę `Cat` obiekty i listy `Dog` obiektów.

Pierwszy `join` klauzuli w języku C# jest zgodny, osoby i kotów na podstawie `Person` dopasowania obiektu `Cat.Owner`. Zwraca sekwencję typów anonimowych, zawierające `Person` obiektu i `Cat.Name`.

Drugi `join` klauzuli w języku C# jest anonimowe typy zwracane przez pierwsze sprzężenie z `Dog` obiektów w podanej listy psy, oparte na klucz złożony, który składa się z `Owner` właściwości typu `Person`, od pierwszej litera zwierzęcia nazwy. Zwraca sekwencję typów anonimowych, zawierające `Cat.Name` i `Dog.Name` właściwości z każdego pasującą parę. Ponieważ jest to sprzężenie wewnętrzne, zwracane są tylko te obiekty z pierwszego źródła danych, które mają odpowiednika w drugiej źródła danych.

[!code-csharp[CsLINQProgJoining#3](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_3.cs)]

## <a name="example---inner-join-by-using-grouped-join"></a>Przykład — sprzężenia wewnętrznego przy użyciu pogrupowane sprzężenia

Poniższy przykład pokazuje, jak zaimplementować sprzężenia wewnętrznego przy użyciu sprzężenie grupy.

W `query1`, lista `Person` obiektów jest przyłączone do grupy lista `Pet` na podstawie obiektów `Person` dopasowania `Pet.Owner` właściwości. Sprzężenie grupy tworzy kolekcję grup pośrednich, gdzie każda grupa składa się z `Person` obiektu i sekwencji zgodnych `Pet` obiektów.

Dodając sekundy `from` klauzula zapytania tej sekwencji jest połączone (lub spłaszczone) w jednej sekwencji dłużej. Typ elementów ostatniej sekwencji jest określany przez `select` klauzuli. W tym przykładzie, że typ jest typ anonimowy, który składa się z `Person.FirstName` i `Pet.Name` właściwości dla każdego pasującą parę.

Wynik `query1` jest odpowiednikiem zestawu wyników, który może uzyskać za pomocą `join` klauzuli bez `into` klauzuli w celu wykonania sprzężenia wewnętrznego. `query2` Zmiennej pokazuje to zapytanie równoważne.

[!code-csharp[CsLINQProgJoining#4](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_4.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.Enumerable.Join%2A>  
- <xref:System.Linq.Enumerable.GroupJoin%2A>  
- [Wykonywanie sprzężeń grupowanych](perform-grouped-joins.md)  
- [Wykonywanie lewych sprzężeń zewnętrznych](perform-left-outer-joins.md)  
- [Typy anonimowe](../programming-guide/classes-and-structs/anonymous-types.md)  