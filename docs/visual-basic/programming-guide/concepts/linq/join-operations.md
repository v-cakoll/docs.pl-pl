---
title: "Dołącz do operacji (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 39ab4854-ac84-4738-9d0b-3cb79be84db4
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21ff2c466db223720edf00be91c3516c641762ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="join-operations-visual-basic"></a>Dołącz do operacji (Visual Basic)
A *sprzężenia* dwóch źródeł danych jest skojarzenie obiektów w jedno źródło danych z obiektami, które mają wspólny atrybut w innym źródłem danych.  
  
 Sprzęganie jest ważne operacji w zapytaniach, które odnoszą się do źródła danych, w której relacje między sobą nie mogą występować bezpośrednio. W programowanie zorientowane obiektowo, może to oznaczać korelacji między obiektami, które nie w modelu, takie jak Wstecz kierunek relacji jednokierunkowe. Przykładem jednokierunkowa relacja jest klasy klienta, która ma właściwość typu Miasto, ale klasa miasta nie ma właściwości, która jest kolekcją obiektów klienta. Jeśli masz listę obiektów mieście i chcesz wyszukać wszystkich klientów w każdemu miastu, można użyć operacji sprzężenia je znaleźć.  
  
 Metody sprzężenia w ramach składnika LINQ to <xref:System.Linq.Enumerable.Join%2A> i <xref:System.Linq.Enumerable.GroupJoin%2A>. Te metody wykonywania equijoins lub sprzężenia, które odpowiada równość kluczy dwóch źródeł danych. (Porównanie, języka Transact-SQL obsługuje join operatorów innych niż "równa się", na przykład "poniżej" operator). W warunkach relacyjnej bazy danych <xref:System.Linq.Enumerable.Join%2A> wykonuje sprzężenie wewnętrzne, typ sprzężenia w zwracane są tylko te obiekty, które mają odpowiednika w zestawie danych. <xref:System.Linq.Enumerable.GroupJoin%2A> — Metoda nie ma bezpośredniego odpowiednika w kategoriach relacyjnej bazy danych, ale implementuje podzbiorem sprzężenia wewnętrzne i lewe sprzężenia zewnętrzne. Lewe sprzężenie zewnętrzne jest sprzężenia, które zwraca każdy element pierwszego źródła danych (po lewej), nawet jeśli go nie ma żadnych skorelowane elementów w źródle danych.  
  
 Na poniższej ilustracji przedstawiono koncepcję dwóch zestawów i elementów w obrębie tych zestawów, które znajdują się w przypadku sprzężenia wewnętrznego lub lewe sprzężenie zewnętrzne.  
  
 ![Dwie nakładające się okręgi przedstawiający wewnętrzny &#47; zewnętrzne. ] (../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażeń języka Visual Basic|Więcej informacji|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Łączenie|Łączy dwie sekwencje oparta na funkcjach selektora kluczy i wyodrębnia par wartości.|`From x In …, y In … Where x.a = y.a`<br /><br /> —lub—<br /><br /> `Join … [As …]In … On …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Tworzy sprzężenie dwóch sekwencji na podstawie funkcji selektora kluczy i grup znalezione wyniki dla każdego elementu.|`Group Join … In … On …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq>  
 [Operatory standardowe zapytań — omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Sformułować sprzężenia i iloczyn wektorowy zapytania](http://msdn.microsoft.com/library/d8072ede-0521-4670-9bec-1778ceeb875b)  
 [JOIN — klauzula](../../../../visual-basic/language-reference/queries/join-clause.md)  
 [Porady: łączenie zawartości niepodobnych plików (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)  
 [Porady: wypełnianie kolekcji Object z wielu źródeł (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
