---
title: Operacje join (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
ms.openlocfilehash: 86d85c7de16887fbe3001dc548d940d9c114e634
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635603"
---
# <a name="join-operations-c"></a>Operacje join (C#)
*Sprzężenie* dwóch źródeł danych to skojarzenie obiektów w jednym źródle danych z obiektami, które współużytkują wspólny atrybut w innym źródle danych.  
  
 Łączenie jest ważną operacją w zapytaniach, które są przeznaczone dla źródeł danych, których relacje między sobą nie mogą być bezpośrednio używane. W programowaniu zorientowanym obiektowo może to oznaczać korelację między obiektami, które nie są modelowane, takimi jak odwrotny kierunek relacji jednokierunkowej. Przykładem relacji jednokierunkowej jest Klasa klienta, która ma właściwość typu miasto, ale Klasa miasto nie ma właściwości, która jest kolekcją obiektów klienta. Jeśli masz listę obiektów miast i chcesz znaleźć wszystkich klientów w poszczególnych miejscowościach, możesz użyć operacji JOIN, aby je znaleźć.  
  
 Metody join podane w środowisku LINQ Framework są <xref:System.Linq.Enumerable.Join%2A> i <xref:System.Linq.Enumerable.GroupJoin%2A>. Metody te wykonują equijoins lub sprzężeń pasujących do dwóch źródeł danych na podstawie równości kluczy. (W przypadku porównania język Transact-SQL obsługuje operatory sprzężenia inne niż "Equals", na przykład operator "Less"). W terminologii relacyjnej bazy danych <xref:System.Linq.Enumerable.Join%2A> implementuje sprzężenie wewnętrzne, typ sprzężenia, w którym zwracane są tylko te obiekty, które mają dopasowanie w innym zestawie danych. Metoda <xref:System.Linq.Enumerable.GroupJoin%2A> nie ma bezpośredniego odpowiednika w warunkach relacyjnej bazy danych, ale implementuje nadzbiór sprzężeń wewnętrznych i Lewe sprzężenia zewnętrzne. Lewe sprzężenie zewnętrzne to sprzężenie zwracające każdy element pierwszego (lewego) źródła danych, nawet jeśli nie ma skorelowanych elementów w innym źródle danych.  
  
 Na poniższej ilustracji przedstawiono widok koncepcyjny dwóch zestawów i elementów w tych zestawach, które znajdują się w sprzężeniu wewnętrznym lub w lewym sprzężeniu zewnętrznym.  
  
 ![Dwa nakładające się okręgi&#47;pokazujące wewnętrzną zewnętrzną.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|C#Składnia wyrażenia zapytania|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Łączenie|Łączy dwie sekwencje w oparciu o funkcje selektora kluczy i wyodrębnia pary wartości.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin —|Łączy dwie sekwencje w oparciu o funkcje selektora kluczy i grupuje wyniki dla każdego elementu.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>
- [Standardowe operatory zapytań — OmówienieC#()](./standard-query-operators-overview.md)
- [Typy anonimowe](../../classes-and-structs/anonymous-types.md)
- [Formułowanie połączeń i zapytań między produktami](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [join, klauzula](../../../language-reference/keywords/join-clause.md)
- [Sprzęganie za pomocą kluczy złożonych](../../../linq/join-by-using-composite-keys.md)
- [Jak dołączyć zawartość z niepodobnych plików (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md)
- [Kolejność wyników klauzuli join](../../../linq/order-the-results-of-a-join-clause.md)
- [Wykonywanie niestandardowych operacji łączenia](../../../linq/perform-custom-join-operations.md)
- [Wykonywanie sprzężeń grupowanych](../../../linq/perform-grouped-joins.md)
- [Wykonywanie sprzężeń wewnętrznych](../../../linq/perform-inner-joins.md)
- [Wykonywanie lewych sprzężeń zewnętrznych](../../../linq/perform-left-outer-joins.md)
- [Jak wypełnić kolekcje obiektów z wielu źródeł (LINQ) (C#)](./how-to-populate-object-collections-from-multiple-sources-linq.md)
