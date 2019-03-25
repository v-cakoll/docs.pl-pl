---
title: Dołącz do operacji (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
ms.openlocfilehash: db42874becaf9760b7060d7f306cc20f950f143a
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411463"
---
# <a name="join-operations-c"></a>Dołącz do operacji (C#)
A *sprzężenia* dwóch źródeł danych jest skojarzenie obiektów w jednym źródle danych z obiektów mających wspólny atrybut w innym źródle danych.  
  
 Łączenie jest operacją ważne w zapytaniach, przeznaczonych dla źródeł danych, w której relacje ze sobą nie mogą występować bezpośrednio. W programowanie zorientowane obiektowo, może to oznaczać korelacji między obiektami, które nie w modelu, takie jak Wstecz kierunek relacji jednokierunkowe. Przykładem jednokierunkowa relacja jest klasą klienta, która ma właściwość typu Miasto, ale klasa miasta nie ma właściwości, który jest kolekcją obiektów klienta. Jeśli masz listę obiektów, miasta i chcesz znaleźć wszystkich klientów w każde Miasto, można użyć operacji tworzenia sprzężenia je znaleźć.  
  
 Metody sprzężenia dostarczane w ramach programu LINQ to <xref:System.Linq.Enumerable.Join%2A> i <xref:System.Linq.Enumerable.GroupJoin%2A>. Te metody wykonywania equijoins lub sprzężenia, które odpowiadają dwa źródła danych oparte na równości kluczy. (Dla porównania języka Transact-SQL obsługuje operatory sprzężenia innych niż "równa się", na przykład "less than" operator.) W warunkach relacyjnej bazy danych <xref:System.Linq.Enumerable.Join%2A> implementuje sprzężenie wewnętrzne, a typ sprzężenia w zwracane są tylko te obiekty, które mają odpowiedniki w zestawie danych. <xref:System.Linq.Enumerable.GroupJoin%2A> Metoda nie ma bezpośredniego odpowiednika w warunkach relacyjnej bazy danych, ale implementuje nadzbiorem sprzężenia wewnętrzne lewych sprzężeń zewnętrznych. Lewe sprzężenie zewnętrzne jest sprzężenia, która zwraca każdy element pierwszego źródła danych (po lewej stronie), nawet wtedy, gdy go nie ma żadnych elementów skorelowane w źródle danych.  
  
 Na poniższej ilustracji przedstawiono koncepcyjny widok dwa zestawy i elementów w obrębie tych zestawów, które są zawarte w sprzężenie wewnętrzne lub lewego sprzężenia zewnętrznego.  
  
 ![Dwa nakładających się okręgów przedstawiający wewnętrzny&#47;zewnętrznego.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażeń zapytania języka C#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Łączenie|Łączy dwie sekwencje, w oparciu o funkcje przełącznika kluczowego i wyodrębnia par wartości.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Łączy dwie sekwencje, w oparciu o funkcje przełącznika kluczowego i grupy znalezione wyniki dla każdego elementu.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>
- [Omówienie operatorów standardowej kwerendy (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Typy anonimowe](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [Formułowanie połączeń i zapytań między produktami](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [join, klauzula](../../../../csharp/language-reference/keywords/join-clause.md)
- [Instrukcje: Sprzęganie za pomocą kluczy złożonych](../../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)
- [Instrukcje: Łączenie zawartości niepodobnych plików (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)
- [Instrukcje: Kolejność wyników klauzuli Join](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)
- [Instrukcje: Wykonywanie niestandardowych operacji łączenia](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)
- [Instrukcje: Wykonanie sprzężeń grupowanych](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)
- [Instrukcje: Wykonanie sprzężeń wewnętrznych](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)
- [Instrukcje: Wykonanie lewych sprzężeń zewnętrznych](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)
- [Instrukcje: Wypełnianie kolekcji Object z wielu źródeł (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
