---
title: JoinOperacje (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: 6e2ec1a0c8120f6869b7c0a196b77d118762a8dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76868008"
---
# <a name="join-operations-c"></a>Dołącz do operacji (C#)

*Sprzężenie* dwóch źródeł danych jest skojarzenie m.in.  
  
 Łączenie jest ważną operacją w kwerendach docelowych źródeł danych, których relacje ze sobą nie mogą być śledzone bezpośrednio. W programowaniu obiektowym może to oznaczać korelację między obiektami, które nie są modelowane, takie jak kierunek wstecz relacji jednokierunkowej. Przykładem relacji jednokierunkowej jest Customer klasy, która ma właściwość typu Miasto, ale City klasa nie ma właściwości, która jest kolekcją Customer obiektów. Jeśli masz listę obiektów Miasta i chcesz znaleźć wszystkich klientów w każdym mieście, możesz użyć operacji sprzężenia, aby je znaleźć.  
  
 Metody sprzężenia podane w ramach <xref:System.Linq.Enumerable.Join%2A> <xref:System.Linq.Enumerable.GroupJoin%2A>LINQ są i . Metody te wykonują równoprzylega lub łączy, które pasują do dwóch źródeł danych na podstawie równości ich kluczy. (Dla porównania Transact-SQL obsługuje operatory sprzężenia inne niż "equals", na przykład operator "mniej niż").) W kategoriach relacyjnej bazy danych <xref:System.Linq.Enumerable.Join%2A> implementuje sprzężenia wewnętrznego, typ sprzężenia, w którym zwracane są tylko te obiekty, które mają dopasowanie w innym zestawie danych. Metoda <xref:System.Linq.Enumerable.GroupJoin%2A> nie ma bezpośredniego odpowiednika w kategoriach relacyjnej bazy danych, ale implementuje nadzbiór sprzężeń wewnętrznych i lewej sprzężenia zewnętrzne. Sprzężenie zewnętrzne lewe jest sprzężeniem, które zwraca każdy element pierwszego (po lewej) źródła danych, nawet jeśli nie ma skorelowanych elementów w innym źródle danych.  
  
 Na poniższej ilustracji przedstawiono widok koncepcyjny dwóch zestawów i elementów w tych zestawach, które są zawarte w sprzężenia wewnętrznym lub lewym sprzężenie zewnętrznym.  
  
 ![Dwa nakładające się okręgi przedstawiające wewnętrzne&#47;zewnętrzne.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia kwerendy c#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|Łączy dwie sekwencje na podstawie funkcji selektora kluczy i wyodrębnia pary wartości.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Łączy dwie sekwencje na podstawie funkcji selektora kluczy i grupuje wynikowe dopasowania dla każdego elementu.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażenia kwerendy
  
### Join  
  
W poniższym `join … in … on … equals …` przykładzie użyto klauzuli do przyłączenia dwóch sekwencji na podstawie określonej wartości:
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#Join)]  

### GroupJoin  

W poniższym `join … in … on … equals … into …` przykładzie użyto klauzuli do przyłączenia się do dwóch sekwencji na podstawie określonej wartości i grupuje wynikowe dopasowania dla każdego elementu:
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq>
- [Omówienie standardowych operatorów zapytań (C#)](./standard-query-operators-overview.md)
- [Typy anonimowe](../../classes-and-structs/anonymous-types.md)
- [Formułowanie połączeń i zapytań między produktami](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [klauzula sprzężenia](../../../language-reference/keywords/join-clause.md)
- [Joinza pomocą klawiszy kompozytowych](../../../linq/join-by-using-composite-keys.md)
- [Jak dołączyć zawartość z różnych plików (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md)
- [Kolejność wyników klauzuli join](../../../linq/order-the-results-of-a-join-clause.md)
- [Wykonywanie niestandardowych operacji sprzęgania](../../../linq/perform-custom-join-operations.md)
- [Wykonywanie sprzężeń grupowanych](../../../linq/perform-grouped-joins.md)
- [Wykonywanie sprzężeń wewnętrznych](../../../linq/perform-inner-joins.md)
- [Wykonywanie lewych sprzężeń zewnętrznych](../../../linq/perform-left-outer-joins.md)
- [Jak wypełnić kolekcje obiektów z wielu źródeł (LINQ) (C#)](./how-to-populate-object-collections-from-multiple-sources-linq.md)
