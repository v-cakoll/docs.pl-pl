---
title: "Dołącz do operacji (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 158d035985dae0d1c1daf0f276a9df7b913f2263
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="join-operations-c"></a>Dołącz do operacji (C#)
A *sprzężenia* dwóch źródeł danych jest skojarzenie obiektów w jedno źródło danych z obiektami, które mają wspólny atrybut w innym źródłem danych.  
  
 Sprzęganie jest ważne operacji w zapytaniach, które odnoszą się do źródła danych, w której relacje między sobą nie mogą występować bezpośrednio. W programowanie zorientowane obiektowo, może to oznaczać korelacji między obiektami, które nie w modelu, takie jak Wstecz kierunek relacji jednokierunkowe. Przykładem jednokierunkowa relacja jest klasy klienta, która ma właściwość typu Miasto, ale klasa miasta nie ma właściwości, która jest kolekcją obiektów klienta. Jeśli masz listę obiektów mieście i chcesz wyszukać wszystkich klientów w każdemu miastu, można użyć operacji sprzężenia je znaleźć.  
  
 Metody sprzężenia w ramach składnika LINQ to <xref:System.Linq.Enumerable.Join%2A> i <xref:System.Linq.Enumerable.GroupJoin%2A>. Te metody wykonywania equijoins lub sprzężenia, które odpowiada równość kluczy dwóch źródeł danych. (Porównanie, języka Transact-SQL obsługuje join operatorów innych niż "równa się", na przykład "poniżej" operator). W warunkach relacyjnej bazy danych <xref:System.Linq.Enumerable.Join%2A> wykonuje sprzężenie wewnętrzne, typ sprzężenia w zwracane są tylko te obiekty, które mają odpowiednika w zestawie danych. <xref:System.Linq.Enumerable.GroupJoin%2A> — Metoda nie ma bezpośredniego odpowiednika w kategoriach relacyjnej bazy danych, ale implementuje podzbiorem sprzężenia wewnętrzne i lewe sprzężenia zewnętrzne. Lewe sprzężenie zewnętrzne jest sprzężenia, które zwraca każdy element pierwszego źródła danych (po lewej), nawet jeśli go nie ma żadnych skorelowane elementów w źródle danych.  
  
 Na poniższej ilustracji przedstawiono koncepcję dwóch zestawów i elementów w obrębie tych zestawów, które znajdują się w przypadku sprzężenia wewnętrznego lub lewe sprzężenie zewnętrzne.  
  
 ![Dwie nakładające się okręgi przedstawiający wewnętrzny &#47; zewnętrzne. ] (../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia zapytania C#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Łączenie|Łączy dwie sekwencje oparta na funkcjach selektora kluczy i wyodrębnia par wartości.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Tworzy sprzężenie dwóch sekwencji na podstawie funkcji selektora kluczy i grup znalezione wyniki dla każdego elementu.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq>  
 [Operatory standardowe zapytań — omówienie (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Typy anonimowe](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [Sformułować sprzężenia i iloczyn wektorowy zapytania](http://msdn.microsoft.com/library/d8072ede-0521-4670-9bec-1778ceeb875b)  
 [JOIN — klauzula](../../../../csharp/language-reference/keywords/join-clause.md)  
 [Porady: sprzęganie za pomocą kluczy złożonych](../../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)  
 [Porady: łączenie zawartości niepodobnych plików (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)  
 [Porady: kolejność wyników klauzuli Join](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
 [Porady: wykonywanie niestandardowych operacji łączenia](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)  
 [Porady: wykonanie sprzężeń grupowanych](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)  
 [Porady: wykonanie sprzężeń wewnętrznych](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)  
 [Porady: wykonanie lewych sprzężeń zewnętrznych](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)  
 [Porady: wypełnianie kolekcji Object z wielu źródeł (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
