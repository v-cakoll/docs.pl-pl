---
title: Wykonanie sprzężeń grupowanych (LINQ w C#)
description: Dowiedz się, jak wykonanie sprzężeń grupowanych za pomocą LINQ w C#.
ms.date: 12/1/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: d52aa8f75a1868c26f6a965553bf8047518bb447
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404005"
---
# <a name="perform-grouped-joins"></a>Wykonanie sprzężeń grupowanych

Sprzężenie grupy jest przydatne do tworzenia struktur danych hierarchicznych. Pary on każdy element z kolekcji pierwszy zestaw elementów skorelowane z drugiej kolekcji.

Na przykład klasa lub tabela relacyjna baza danych o nazwie `Student` może zawierać dwóch pól: `Id` i `Name`. Tabela drugiej klasy lub relacyjnej bazy danych o nazwie `Course` może zawierać dwóch pól: `StudentId` i `CourseTitle`. Grupowe z tych dwóch źródeł danych, na podstawie zgodności `Student.Id` i `Course.StudentId`, czy każda grupa `Student` z kolekcją `Course` obiektów, (które mogą być puste).

> [!NOTE]
> Każdy element pierwszej kolekcji pojawia się w zestawie wyników grupowe, niezależnie od tego, czy elementy skorelowane znajdują się w drugiej kolekcji. W przypadku, gdzie znajdują się żadnych elementów skorelowany sekwencji elementów skorelowany dla tego elementu jest pusty. Selektor wynik zatem ma dostęp do każdego elementu pierwszej kolekcji. To różni się od selektor wynik sprzężenia-group, którego nie można uzyskać dostęp do elementów z pierwszej kolekcji, która ma niezgodności w drugiej kolekcji.

Pierwszy przykład w tym artykule pokazano, jak wykonać sprzężenie grupy. Drugi przykład przedstawia sposób użycia sprzężenie grupy do tworzenia elementów XML.

## <a name="example---group-join"></a>Przykład — łączenie grupowe

Poniższy przykład wykonuje sprzężenie grupy obiektów typu `Person` i `Pet` na podstawie `Person` dopasowania `Pet.Owner` właściwości. W odróżnieniu od sprzężenia-group dałby w efekcie pary elementów dla każdego dopasowania, łączenie grupy tworzy tylko jeden obiekt wynikowy dla każdego elementu pierwszej kolekcji, czyli w tym przykładzie `Person` obiektu. Odpowiednie elementy z kolekcji drugi, będące w tym przykładzie `Pet` obiektów są grupowane w kolekcji. Ponadto funkcja selektor result tworzy typu anonimowego dla każdego dopasowania, która składa się z `Person.FirstName` i kolekcji `Pet` obiektów.

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a>Przykład — łączenie grupowe tworzenie kodu XML

Sprzężenia grupowane są doskonałe do tworzenia XML za pomocą LINQ to XML. Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że zamiast tworzyć typy anonimowe, funkcja selektor result tworzy elementy XML, które reprezentują dołączonym do obiektów.

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a>Zobacz także

<xref:System.Linq.Enumerable.Join%2A>  
<xref:System.Linq.Enumerable.GroupJoin%2A>  
[Wykonywanie sprzężeń wewnętrznych](perform-inner-joins.md)  
[Wykonywanie lewych sprzężeń zewnętrznych](perform-left-outer-joins.md)  
[Typy anonimowe](../programming-guide/classes-and-structs/anonymous-types.md)  