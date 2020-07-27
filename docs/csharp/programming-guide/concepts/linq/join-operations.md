---
title: :::no-loc(Join):::Operacje (C#)
description: Sprzężenie dwóch źródeł danych kojarzy obiekty z obiektami, które współużytkują atrybut w różnych źródłach danych. Dowiedz się więcej o metodach dołączania w strukturze LINQ w języku C#.
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- ':::no-loc(Join):::'
- ':::no-loc(GroupJoin):::'
ms.openlocfilehash: 1b453f1752edf0cc126f8e27dbdd9e91ad9143f3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165694"
---
# <a name="no-locjoin-operations-c"></a>:::no-loc(Join):::Operacje (C#)

*Sprzężenie* dwóch źródeł danych to skojarzenie obiektów w jednym źródle danych z obiektami, które współużytkują wspólny atrybut w innym źródle danych.  
  
 :::no-loc(Join):::w przypadku zapytań, które są przeznaczone dla źródeł danych, których relacje między sobą nie mogą być przestrzegane bezpośrednio, jest ważna operacja. W programowaniu zorientowanym obiektowo może to oznaczać korelację między obiektami, które nie są modelowane, takimi jak odwrotny kierunek relacji jednokierunkowej. Przykładem relacji jednokierunkowej jest Klasa klienta, która ma właściwość typu miasto, ale Klasa miasto nie ma właściwości, która jest kolekcją obiektów klienta. Jeśli masz listę obiektów miast i chcesz znaleźć wszystkich klientów w poszczególnych miejscowościach, możesz użyć operacji JOIN, aby je znaleźć.  
  
 Metody join podane w środowisku LINQ Framework to <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> i <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A> . Metody te wykonują equijoins lub sprzężeń pasujących do dwóch źródeł danych na podstawie równości kluczy. (W przypadku porównania język Transact-SQL obsługuje operatory sprzężenia inne niż "Equals", na przykład operator "Less"). W terminologii relacyjnej bazy danych <xref:System.Linq.Enumerable.:::no-loc(Join):::%2A> implementuje sprzężenie wewnętrzne, typ sprzężenia, w którym zwracane są tylko te obiekty, które mają dopasowanie w innym zestawie danych. <xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A>Metoda nie ma bezpośredniego odpowiednika w warunkach relacyjnych baz danych, ale implementuje nadzbiór sprzężeń wewnętrznych i Lewe sprzężenia zewnętrzne. Lewe sprzężenie zewnętrzne to sprzężenie zwracające każdy element pierwszego (lewego) źródła danych, nawet jeśli nie ma skorelowanych elementów w innym źródle danych.  
  
 Na poniższej ilustracji przedstawiono widok koncepcyjny dwóch zestawów i elementów w tych zestawach, które znajdują się w sprzężeniu wewnętrznym lub w lewym sprzężeniu zewnętrznym.  
  
 ![Dwa nakładające się okręgi przedstawiające wewnętrzne&#47;zewnętrzne.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia zapytania C#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|:::no-loc(Join):::|:::no-loc(Join):::s dwie sekwencje oparte na funkcjach selektora kluczy i wyodrębniających pary wartości.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.:::no-loc(Join):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(Join):::%2A?displayProperty=nameWithType>|  
|:::no-loc(GroupJoin):::|:::no-loc(Join):::s dwie sekwencje oparte na funkcjach selektora kluczy i grupuje wyniki dla każdego elementu.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.:::no-loc(GroupJoin):::%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania
  
### :::no-loc(Join):::  
  
W poniższym przykładzie zastosowano `join … in … on … equals …` klauzulę, aby dołączyć dwie sekwencje w oparciu o określoną wartość:
  
[!code-csharp[:::no-loc(Join):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(Join):::)]  

### :::no-loc(GroupJoin):::  

W poniższym przykładzie zastosowano `join … in … on … equals … into …` klauzulę, aby przyłączyć dwie sekwencje w oparciu o określoną wartość i grupy wyników dopasowania dla każdego elementu:
  
[!code-csharp[:::no-loc(GroupJoin):::](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQ:::no-loc(Join):::Operation/CS/:::no-loc(Join):::Operation.cs#:::no-loc(GroupJoin):::)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>
- [Standardowe operatory zapytań — Omówienie (C#)](./standard-query-operators-overview.md)
- [Typy anonimowe](../../classes-and-structs/anonymous-types.md)
- [Formułowanie :::no-loc(Join)::: zapytań i innych produktów](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [Klauzula join](../../../language-reference/keywords/join-clause.md)
- [:::no-loc(Join):::za pomocą kluczy złożonych](../../../linq/join-by-using-composite-keys.md)
- [Jak dołączyć zawartość z niepodobnych plików (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md)
- [Kolejność wyników klauzuli join](../../../linq/order-the-results-of-a-join-clause.md)
- [Wykonywanie niestandardowych operacji sprzęgania](../../../linq/perform-custom-join-operations.md)
- [Wykonywanie sprzężeń grupowanych](../../../linq/perform-grouped-joins.md)
- [Wykonywanie sprzężeń wewnętrznych](../../../linq/perform-inner-joins.md)
- [Wykonywanie lewych sprzężeń zewnętrznych](../../../linq/perform-left-outer-joins.md)
- [Jak wypełnić kolekcje obiektów z wielu źródeł (LINQ) (C#)](./how-to-populate-object-collections-from-multiple-sources-linq.md)
