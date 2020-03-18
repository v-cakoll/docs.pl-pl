---
title: Wykonywanie sprzężeń wewnętrznych (LINQ w języku C)Perform inner joins (LINQ in C#)
description: Dowiedz się, jak wykonywać sprzężenia wewnętrzne przy użyciu LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: 45bceed6-f549-4114-a9b1-b44feb497742
ms.openlocfilehash: a3e8e9bd97ec630797bc48a3302b27ed45d9103e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659842"
---
# <a name="perform-inner-joins"></a>Wykonywanie sprzężeń wewnętrznych

W kategoriach relacyjnej bazy danych *sprzężenia wewnętrznego* daje zestaw wyników, w którym każdy element pierwszej kolekcji pojawia się jeden raz dla każdego pasującego elementu w drugiej kolekcji. Jeśli element w pierwszej kolekcji nie ma pasujących elementów, nie pojawia się w zestawie wyników. Metoda, <xref:System.Linq.Enumerable.Join%2A> która jest wywoływana przez klauzulę w języku `join` C#, implementuje sprzężenie wewnętrzne.

Z tego artykułu dowiesz się, jak wykonać cztery odmiany sprzężenia wewnętrznego:

- Proste sprzężenie wewnętrzne, które koreluje elementy z dwóch źródeł danych na podstawie prostego klucza.

- Sprzężenie wewnętrzne, które koreluje elementy z dwóch źródeł danych na podstawie klucza *złożonego.* Klucz złożony, który jest kluczem, który składa się z więcej niż jednej wartości, umożliwia skorelowanie elementów na podstawie więcej niż jednej właściwości.

- *Sprzężenie wielokrotne,* w którym kolejne operacje sprzężenia są dołączane do siebie.

- Sprzężenie wewnętrzne, które jest implementowane przy użyciu sprzężenia grupy.

## <a name="example---simple-key-join"></a>Przykład — proste sprzężenie klucza

Poniższy przykład tworzy dwie kolekcje, które zawierają obiekty `Person` `Pet`dwóch typów zdefiniowanych przez użytkownika i . Kwerenda używa `join` klauzuli w `Person` języku `Pet` C# do dopasowania obiektów z obiektami, których `Owner` jest . `Person` Klauzula `select` w języku C# definiuje, jak będą wyglądać wynikowe obiekty. W tym przykładzie wynikowe obiekty są typy anonimowe, które składają się z imienia właściciela i nazwy zwierzęcia.

[!code-csharp[CsLINQProgJoining#1](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_1.cs)]

Należy zauważyć, `Person` `LastName` że obiekt, którego jest "Huff" nie `Pet` pojawia się `Pet.Owner` w `Person`zestawie wyników, ponieważ nie ma żadnego obiektu, który jest równy temu .

## <a name="example---composite-key-join"></a>Przykład — sprzężenie klucza złożonego

Zamiast korelować elementy oparte na tylko jednej właściwości, można użyć klucza złożonego do porównania elementów na podstawie wielu właściwości. W tym celu należy określić funkcję selektora kluczy dla każdej kolekcji, aby zwrócić typ anonimowy, który składa się z właściwości, które chcesz porównać. Jeśli etykiety właściwości, muszą mieć tę samą etykietę w typie anonimowym każdego klucza. Właściwości muszą również występować w tej samej kolejności.

W poniższym przykładzie `Employee` użyto listy `Student` obiektów i listy obiektów, aby określić, którzy pracownicy są również studentami. Oba te typy `FirstName` mają `LastName` i właściwość <xref:System.String>typu . Funkcje, które tworzą klucze sprzężenia z elementów każdej listy `FirstName` `LastName` zwracają typ anonimowy, który składa się z i właściwości każdego elementu. Operacja sprzężenia porównuje te klucze złożone dla równości i zwraca pary obiektów z każdej listy, gdzie zarówno imię, jak i nazwisko są zgodne.

[!code-csharp[CsLINQProgJoining#2](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_2.cs)]

## <a name="example---multiple-join"></a>Przykład — sprzężenie wielokrotne

Dowolną liczbę operacji sprzężenia można dołączyć do siebie, aby wykonać sprzężenie wielokrotne. Każda `join` klauzula w języku C# koreluje określonego źródła danych z wynikami poprzedniego sprzężenia.

Poniższy przykład tworzy trzy kolekcje: listę `Person` obiektów, listę `Cat` obiektów `Dog` i listę obiektów.

Pierwsza `join` klauzula w języku C# `Person` pasuje `Cat.Owner`do osób i kotów na podstawie dopasowania obiektu . Zwraca sekwencję typów anonimowych, `Person` które `Cat.Name`zawierają obiekt i .

Druga `join` klauzula w języku C# koreluje typy `Dog` anonimowe zwracane przez pierwsze sprzężenie z obiektami `Owner` na `Person`dostarczonej liście psów, na podstawie klucza złożonego, który składa się z właściwości typu i pierwszej litery nazwy zwierzęcia. Zwraca sekwencję typów anonimowych, `Cat.Name` `Dog.Name` które zawierają i właściwości z każdej pasującej pary. Ponieważ jest to sprzężenie wewnętrzne, zwracane są tylko te obiekty z pierwszego źródła danych, które mają dopasowanie w drugim źródle danych.

[!code-csharp[CsLINQProgJoining#3](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_3.cs)]

## <a name="example---inner-join-by-using-grouped-join"></a>Przykład — sprzężenie wewnętrzne przy użyciu sprzężenia zgrupowanego

W poniższym przykładzie pokazano, jak zaimplementować sprzężenie wewnętrzne przy użyciu sprzężenia grupy.

W `query1`, lista `Person` obiektów jest przyłączona `Pet` do grupy `Person` do `Pet.Owner` listy obiektów na podstawie pasującej właściwości. Sprzężenie grupy tworzy kolekcję grup pośrednich, `Person` gdzie każda grupa `Pet` składa się z obiektu i sekwencji pasujących obiektów.

Dodając drugą `from` klauzulę do kwerendy, ta sekwencja sekwencji jest łączona (lub spłaszczona) w jedną dłuższą sekwencję. Typ elementów końcowej sekwencji jest określony `select` przez klauzulę. W tym przykładzie tego typu jest typem `Person.FirstName` `Pet.Name` anonimowym, który składa się z i właściwości dla każdej pasującej pary.

Wynik `query1` jest odpowiednikiem zestawu wyników, które zostałyby `join` uzyskane `into` przy użyciu klauzuli bez klauzuli do wykonania sprzężenia wewnętrznego. Zmienna `query2` demonstruje to równoważne zapytanie.

[!code-csharp[CsLINQProgJoining#4](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_4.cs)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [Wykonywanie sprzężeń grupowanych](perform-grouped-joins.md)
- [Wykonywanie lewych sprzężeń zewnętrznych](perform-left-outer-joins.md)
- [Typy anonimowe](../programming-guide/classes-and-structs/anonymous-types.md)
