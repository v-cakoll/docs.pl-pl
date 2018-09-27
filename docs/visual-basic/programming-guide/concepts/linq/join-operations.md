---
title: Dołącz do operacji (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 39ab4854-ac84-4738-9d0b-3cb79be84db4
ms.openlocfilehash: 660b6d04e0a807a3072cff51d885999545052018
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47237140"
---
# <a name="join-operations-visual-basic"></a>Dołącz do operacji (Visual Basic)
A *sprzężenia* dwóch źródeł danych jest skojarzenie obiektów w jednym źródle danych z obiektów mających wspólny atrybut w innym źródle danych.  
  
 Łączenie jest operacją ważne w zapytaniach, przeznaczonych dla źródeł danych, w której relacje ze sobą nie mogą występować bezpośrednio. W programowanie zorientowane obiektowo, może to oznaczać korelacji między obiektami, które nie w modelu, takie jak Wstecz kierunek relacji jednokierunkowe. Przykładem jednokierunkowa relacja jest klasą klienta, która ma właściwość typu Miasto, ale klasa miasta nie ma właściwości, który jest kolekcją obiektów klienta. Jeśli masz listę obiektów, miasta i chcesz znaleźć wszystkich klientów w każde Miasto, można użyć operacji tworzenia sprzężenia je znaleźć.  
  
 Metody sprzężenia dostarczane w ramach programu LINQ to <xref:System.Linq.Enumerable.Join%2A> i <xref:System.Linq.Enumerable.GroupJoin%2A>. Te metody wykonywania equijoins lub sprzężenia, które odpowiadają dwa źródła danych oparte na równości kluczy. (Dla porównania języka Transact-SQL obsługuje operatory sprzężenia innych niż "równa się", na przykład "less than" operator.) W warunkach relacyjnej bazy danych <xref:System.Linq.Enumerable.Join%2A> implementuje sprzężenie wewnętrzne, a typ sprzężenia w zwracane są tylko te obiekty, które mają odpowiedniki w zestawie danych. <xref:System.Linq.Enumerable.GroupJoin%2A> Metoda nie ma bezpośredniego odpowiednika w warunkach relacyjnej bazy danych, ale implementuje nadzbiorem sprzężenia wewnętrzne lewych sprzężeń zewnętrznych. Lewe sprzężenie zewnętrzne jest sprzężenia, która zwraca każdy element pierwszego źródła danych (po lewej stronie), nawet wtedy, gdy go nie ma żadnych elementów skorelowane w źródle danych.  
  
 Na poniższej ilustracji przedstawiono koncepcyjny widok dwa zestawy i elementów w obrębie tych zestawów, które są zawarte w sprzężenie wewnętrzne lub lewego sprzężenia zewnętrznego.  
  
 ![Dwa nakładających się okręgów przedstawiający wewnętrzny&#47;zewnętrznego. ](../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażeń języka Visual Basic|Więcej informacji|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Łączenie|Łączy dwie sekwencje, w oparciu o funkcje przełącznika kluczowego i wyodrębnia par wartości.|`From x In …, y In … Where x.a = y.a`<br /><br /> —lub—<br /><br /> `Join … [As …]In … On …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|Groupjoin —|Łączy dwie sekwencje, w oparciu o funkcje przełącznika kluczowego i grupy znalezione wyniki dla każdego elementu.|`Group Join … In … On …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>  
- [Omówienie operatorów standardowej kwerendy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
- [Formułowanie połączeń i zapytań między produktami](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)  
- [Join, klauzula](../../../../visual-basic/language-reference/queries/join-clause.md)  
- [Porady: łączenie zawartości niepodobnych plików (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)  
- [Porady: wypełnianie kolekcji Object z wielu źródeł (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
