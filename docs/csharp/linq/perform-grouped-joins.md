---
title: Wykonywanie sprzężeń grupowanych (LINQ w języku C)Perform grouped joins (LINQ in C#)
description: Dowiedz się, jak wykonywać sprzężenia grupowe przy użyciu LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: dfb75b55336d8ca486d5f10b187e955d20cd06fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61689141"
---
# <a name="perform-grouped-joins"></a>Wykonywanie sprzężeń grupowanych

Sprzężenie grupy jest przydatne do tworzenia hierarchicznych struktur danych. Łączy każdy element z pierwszej kolekcji z zestawem skorelowanych elementów z drugiej kolekcji.

Na przykład klasa lub tabela relacyjnej bazy danych o nazwie `Student` może zawierać dwa pola: `Id` i `Name`. Druga klasa lub relacyjna `Course` tabela bazy `StudentId` danych `CourseTitle`o nazwie może zawierać dwa pola: i . Dołączanie grupy z tych dwóch źródeł `Student.Id` `Course.StudentId`danych, na `Student` podstawie dopasowania `Course` i , będzie grupować każdy z kolekcji obiektów (które mogą być puste).

> [!NOTE]
> Każdy element pierwszej kolekcji pojawia się w zestawie wyników sprzężenia grupy, niezależnie od tego, czy skorelowane elementy znajdują się w drugiej kolekcji. W przypadku, gdy nie znaleziono skorelowanych elementów, sekwencja skorelowanych elementów dla tego elementu jest pusta. Selektor wyników ma zatem dostęp do każdego elementu pierwszej kolekcji. Różni się to od selektora wyników w sprzężeniu niegrupowym, który nie może uzyskać dostępu do elementów z pierwszej kolekcji, które nie mają dopasowania w drugiej kolekcji.

Pierwszy przykład w tym artykule pokazuje, jak wykonać sprzężenie grupy. Drugi przykład pokazuje, jak używać sprzężenia grupy do tworzenia elementów XML.

## <a name="example---group-join"></a>Przykład — dołączanie do grupy

Poniższy przykład wykonuje sprzężenie grupy `Person` obiektów `Pet` typu `Person` i `Pet.Owner` na podstawie pasujące jawłaściwości. W przeciwieństwie do sprzężenia niegrupowego, które spowodowałoby parę elementów dla każdego dopasowania, sprzężenie grupy tworzy tylko jeden `Person` wynikowy obiekt dla każdego elementu pierwszej kolekcji, który w tym przykładzie jest obiektem. Odpowiednie elementy z drugiej kolekcji, które `Pet` w tym przykładzie są obiekty, są zgrupowane w kolekcji. Na koniec funkcja selektora wyników tworzy typ anonimowy `Person.FirstName` dla każdego `Pet` dopasowania, który składa się z i kolekcji obiektów.

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a>Przykład — dołączanie grupowe w celu utworzenia języka XML

Sprzężenia grupowe są idealne do tworzenia Języka XML przy użyciu LINQ do XML. Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że zamiast tworzyć typy anonimowe, funkcja selektora wyników tworzy elementy XML reprezentujące połączone obiekty.

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [Wykonywanie sprzężeń wewnętrznych](perform-inner-joins.md)
- [Wykonywanie lewych sprzężeń zewnętrznych](perform-left-outer-joins.md)
- [Typy anonimowe](../programming-guide/classes-and-structs/anonymous-types.md)
