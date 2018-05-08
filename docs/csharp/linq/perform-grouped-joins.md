---
title: Wykonanie sprzężeń grupowanych
description: Jak wykonanie sprzężeń grupowanych.
ms.date: 12/1/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: fbdb1a69fa2f3b171935fa3a58cf9a045be0a494
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="perform-grouped-joins"></a>Wykonanie sprzężeń grupowanych

Dołącz do grupy jest przydatne w przypadku tworzenie struktury hierarchicznej danych. Każdy element z kolekcji pierwszy zestaw elementów skorelowane z druga kolekcja go pary.  
  
 Na przykład klasa lub tabela relacyjnej bazy danych o nazwie `Student` może zawierać dwóch pól: `Id` i `Name`. Tabela drugiej klasy lub relacyjnej bazy danych o nazwie `Course` może zawierać dwóch pól: `StudentId` i `CourseTitle`. Grupowe z tych dwóch źródeł danych, na podstawie zgodności `Student.Id` i `Course.StudentId`, czy grupa Każdy `Student` z kolekcją `Course` obiektów (które mogą być puste).  
  
> [!NOTE]
>  Każdy element pierwszej kolekcji znajduje się w zestawie wyników sprzężenia grupy niezależnie od tego, czy elementy skorelowane znajdują się w drugiej kolekcji. W przypadku których nie skorelowane znaleziono elementów sekwencji skorelowane elementów dla tego elementu jest pusta. Selektor wynik w związku z tym ma dostęp do każdego elementu pierwszej kolekcji. To różni się od selektora wyniku w sprzężeniu-group, którego nie można uzyskać dostęp do elementów z pierwszej kolekcji, która ma dopasowań w druga kolekcja.  
  
 Pierwszym przykładzie w tym temacie przedstawiono sposób wykonania sprzężenia grupy. Drugi przykład przedstawia sposób użycia sprzężenia grupy do tworzenia elementów XML.  
  
## <a name="example"></a>Przykład  
  
### <a name="group-join-example"></a>Przykład grupy  
 Poniższy przykład wykonuje sprzężenie grupy obiektów typu `Person` i `Pet` na podstawie `Person` dopasowania `Pet.Owner` właściwości. W odróżnieniu od sprzężenia-group dałby w efekcie dwa elementy dla każdego dopasowania, sprzężenia grupy tworzy tylko jeden obiekt wynikowy dla każdego elementu pierwszej kolekcji, czyli w tym przykładzie `Person` obiektu. Odpowiednie elementy z drugiej kolekcji, które w tym przykładzie są `Pet` obiekty są zgrupowane w kolekcji. Ponadto funkcja selektora wynik tworzy typu anonimowego dla każdego dopasowanie, które składa się z `Person.FirstName` i Kolekcja `Pet` obiektów.  
  
 [!code-csharp[CsLINQProgJoining#5](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]  
  
## <a name="example"></a>Przykład  
  
### <a name="group-join-to-create-xml-example"></a>Aby utworzyć przykład XML łączenie grupowe  
 Sprzężenia grupowane idealnie nadają się do tworzenia XML za pomocą LINQ do XML. Poniższy przykład jest podobny do poprzedniego przykładu, z wyjątkiem tego, że zamiast tworzyć typy anonimowe, funkcja selektora wynik tworzy elementów XML, które reprezentują przyłączonych obiektów.  
  
 [!code-csharp[CsLINQProgJoining#6](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]  
 
## <a name="see-also"></a>Zobacz także  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [Wykonywanie sprzężeń wewnętrznych](perform-inner-joins.md)  
 [Wykonywanie lewych sprzężeń zewnętrznych](perform-left-outer-joins.md)  
 [Typy anonimowe](../programming-guide/classes-and-structs/anonymous-types.md)  
 
