---
title: "Wykonanie sprzężeń wewnętrznych"
description: "Jak wykonanie sprzężeń wewnętrznych."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 45bceed6-f549-4114-a9b1-b44feb497742
ms.openlocfilehash: fdf75c0b7195742bdce70566ebb3880bb0565f31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="perform-inner-joins"></a>Wykonanie sprzężeń wewnętrznych

W warunkach relacyjnej bazy danych *sprzężenia wewnętrznego* tworzy zestaw wyników, w którym każdy element pierwsza kolekcja pojawia się jeden raz dla każdego pasującego elementu w kolekcji drugiego. Jeśli element pierwsza kolekcja nie ma żadnych zgodnych elementów, nie jest widoczna w zestawie wyników. <xref:System.Linq.Enumerable.Join%2A> Metodę, która jest wywoływana przez `join` klauzuli w języku C#, wykonuje sprzężenie wewnętrzne.  
  
 W tym temacie pokazano, jak wykonać cztery odmiany sprzężenia wewnętrznego:  
  
-   Proste sprzężenie wewnętrzne są powiązane elementy z dwóch źródeł danych na podstawie prostego klucza.  
  
-   Sprzężenie wewnętrzne, które są powiązane elementy z dwóch źródeł danych na podstawie *złożonego* klucza. Klucz złożony, który jest klucz, który składa się z więcej niż jedną wartość, umożliwia korelowanie elementy na podstawie więcej niż jednej właściwości.  
  
-   A *wielu sprzężenia* które sprzężenia kolejnych operacji są dołączane do siebie.  
  
-   Sprzężenie wewnętrzne jest implementowane za pomocą sprzężenia grupy.  
  
## <a name="example"></a>Przykład  
  
## <a name="simple-key-join-example"></a>Prosty przykład klucza  
 Poniższy przykład tworzy dwie kolekcje, które zawierają obiekty dwa typy zdefiniowane przez użytkownika, `Person` i `Pet`. Zapytanie używa `join` klauzuli w języku C#, aby dopasować `Person` obiekty z `Pet` obiekty, których `Owner` jest to, że `Person`. `select` Klauzuli w języku C# definiuje wygląd obiektach wynikowych. W tym przykładzie obiekty wynikowe są typy anonimowe, które składają się z imieniem właściciela i zwierzaka.  
  
 [!code-csharp[CsLINQProgJoining#1](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_1.cs)]  
  
 Należy pamiętać, że `Person` którego `LastName` jest "Huff" nie ma zestawu wyników, ponieważ istnieje nie `Pet` obiektu, który ma `Pet.Owner` równą `Person`.  
  
## <a name="example"></a>Przykład  
  
## <a name="composite-key-join-example"></a>Przykład sprzężenia klucza złożonego  
 Zamiast korelowanie elementy oparte na tylko jedną właściwość, możesz użyć klucza złożonego do porównywania elementów na podstawie wielu właściwości. Aby to zrobić, należy określić funkcja selektora kluczy dla każdej kolekcji zwrócić typu anonimowego, która składa się z właściwości, które chcesz porównać. Jeśli etykieta właściwości, w obrębie typu anonimowego każdego klucza muszą mieć taką samą etykietę. Właściwości musi również występować w tej samej kolejności.  
  
 W poniższym przykładzie użyto listę `Employee` obiektów oraz listę `Student` określają pracowników, którzy są również studentów obiekty. Oba typy mają `FirstName` i `LastName` właściwości typu <xref:System.String>. Funkcje, które tworzenia kluczy sprzężenia od każdej listy elementów zwracają typu anonimowego, która składa się z `FirstName` i `LastName` właściwości każdego elementu. Operacji tworzenia sprzężenia porównuje te klucze złożone równości i zwraca pary obiektów z każdej listy, jeśli zarówno imię i nazwisko są takie same.  
  
 [!code-csharp[CsLINQProgJoining#2](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_2.cs)]  
  
## <a name="example"></a>Przykład  
  
## <a name="multiple-join-example"></a>Przykład wielu  
 Dowolna liczba operacji łączenia można dołączać do siebie do wykonywania wielu sprzężenia. Każdy `join` klauzuli w języku C# skorelowany określonego źródła danych z wynikami poprzedniej sprzężenia.  
  
 Poniższy przykład tworzy trzech zbiorów: Lista `Person` obiektów, listę `Cat` obiektów oraz listę `Dog` obiektów.  
  
 Pierwszy `join` osób i kotów na podstawie klauzuli w języku C# zgodne `Person` dopasowywanie obiektu `Cat.Owner`. Zwraca sekwencję typy anonimowe, które zawierają `Person` obiektu i `Cat.Name`.  
  
 Drugi `join` klauzuli w języku C# są powiązane typy anonimowe zwrócony przez pierwsze sprzężenie z `Dog` obiektów w podanej listy skalary, oparte na klucz złożony, który składa się z `Owner` właściwość typu `Person`, a pierwszy litera nazwy zwierzęcia. Zwraca sekwencję typy anonimowe, które zawierają `Cat.Name` i `Dog.Name` z każdej pary dopasowania właściwości. Ponieważ jest to sprzężenie wewnętrzne, zwracane są tylko te obiekty z pierwszego źródła danych, które mają odpowiednika w drugiej źródła danych.  
  
 [!code-csharp[CsLINQProgJoining#3](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_3.cs)]  
  
## <a name="example"></a>Przykład  
  
## <a name="inner-join-by-using-grouped-join-example"></a>Sprzężenie wewnętrzne przy użyciu grupowanych przykład  
 Poniższy przykład przedstawia sposobu wdrażania sprzężenie wewnętrzne za pomocą funkcji łączenia grupy.  
  
 W `query1`, listę `Person` obiektów jest przyłączony do grupy na liście `Pet` obiektów na podstawie `Person` dopasowania `Pet.Owner` właściwości. Dołącz do grupy tworzy kolekcję grup pośrednich, gdy każda grupa składa się z `Person` obiekt i sekwencji zgodnych `Pet` obiektów.  
  
 Dodając drugiej `from` klauzuli zapytanie, ta sekwencja sekwencji jest łączyć (lub jako spłaszczone) w jedną sekwencję dłużej. Typ elementu końcowego sekwencji jest określany przez `select` klauzuli. W tym przykładzie, że typ jest typu anonimowego, która składa się z `Person.FirstName` i `Pet.Name` właściwości dla każdej pary dopasowania.  
  
 Wynik `query1` jest odpowiednikiem zestaw wyników, który może uzyskać za pomocą `join` klauzuli bez `into` klauzuli do wykonania sprzężenia wewnętrznego. `query2` Zmiennej pokazano to odpowiednik zapytanie.  
  
 [!code-csharp[CsLINQProgJoining#4](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_4.cs)]  
  
## <a name="see-also"></a>Zobacz także  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [Wykonanie sprzężeń grupowanych](perform-grouped-joins.md)  
 [Wykonanie lewych sprzężeń zewnętrznych](perform-left-outer-joins.md)  
 [Typy anonimowe](../programming-guide/classes-and-structs/anonymous-types.md)  
 
