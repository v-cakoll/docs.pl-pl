---
title: Operacje połączone
ms.date: 07/20/2015
ms.assetid: 39ab4854-ac84-4738-9d0b-3cb79be84db4
ms.openlocfilehash: b09574369185be13664276c2e84697fc4969c6f5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353293"
---
# <a name="join-operations-visual-basic"></a>Operacje join (Visual Basic)
*Sprzężenie* dwóch źródeł danych to skojarzenie obiektów w jednym źródle danych z obiektami, które współużytkują wspólny atrybut w innym źródle danych.  
  
 Łączenie jest ważną operacją w zapytaniach, które są przeznaczone dla źródeł danych, których relacje między sobą nie mogą być bezpośrednio używane. W programowaniu zorientowanym obiektowo może to oznaczać korelację między obiektami, które nie są modelowane, takimi jak odwrotny kierunek relacji jednokierunkowej. Przykładem relacji jednokierunkowej jest Klasa klienta, która ma właściwość typu miasto, ale Klasa miasto nie ma właściwości, która jest kolekcją obiektów klienta. Jeśli masz listę obiektów miast i chcesz znaleźć wszystkich klientów w poszczególnych miejscowościach, możesz użyć operacji JOIN, aby je znaleźć.  
  
 Metody join podane w środowisku LINQ Framework są <xref:System.Linq.Enumerable.Join%2A> i <xref:System.Linq.Enumerable.GroupJoin%2A>. Metody te wykonują equijoins lub sprzężeń pasujących do dwóch źródeł danych na podstawie równości kluczy. (W przypadku porównania język Transact-SQL obsługuje operatory sprzężenia inne niż "Equals", na przykład operator "Less"). W terminologii relacyjnej bazy danych <xref:System.Linq.Enumerable.Join%2A> implementuje sprzężenie wewnętrzne, typ sprzężenia, w którym zwracane są tylko te obiekty, które mają dopasowanie w innym zestawie danych. Metoda <xref:System.Linq.Enumerable.GroupJoin%2A> nie ma bezpośredniego odpowiednika w warunkach relacyjnej bazy danych, ale implementuje nadzbiór sprzężeń wewnętrznych i Lewe sprzężenia zewnętrzne. Lewe sprzężenie zewnętrzne to sprzężenie zwracające każdy element pierwszego (lewego) źródła danych, nawet jeśli nie ma skorelowanych elementów w innym źródle danych.  
  
 Na poniższej ilustracji przedstawiono widok koncepcyjny dwóch zestawów i elementów w tych zestawach, które znajdują się w sprzężeniu wewnętrznym lub w lewym sprzężeniu zewnętrznym.  
  
 ![Dwa nakładające się okręgi&#47;pokazujące wewnętrzną zewnętrzną.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia zapytania Visual Basic|Więcej informacji|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Join|Łączy dwie sekwencje w oparciu o funkcje selektora kluczy i wyodrębnia pary wartości.|`From x In …, y In … Where x.a = y.a`<br /><br /> —lub—<br /><br /> `Join … [As …]In … On …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin —|Łączy dwie sekwencje w oparciu o funkcje selektora kluczy i grupuje wyniki dla każdego elementu.|`Group Join … In … On …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>
- [Standardowe operatory zapytań — Omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Formułowanie połączeń i zapytań między produktami](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [Join, klauzula](../../../../visual-basic/language-reference/queries/join-clause.md)
- [Instrukcje: dołączanie zawartości z niepodobnych plików (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)
- [Instrukcje: wypełnianie kolekcji obiektów z wielu źródeł (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
