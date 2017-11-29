---
title: Tabeli zapytania (LINQ do DataSet)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d0b829840257dc2b3b4bbf0b8c3a294a77060e2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="cross-table-queries-linq-to-dataset"></a>Tabeli zapytania (LINQ do DataSet)
Oprócz wykonywania zapytania w jednej tabeli, można również wykonywać zapytania między tabelami w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Jest to zrobić za pomocą *sprzężenia*. Sprzężenia jest skojarzenie obiektów w jedno źródło danych z obiektów, które udostępnianie wspólny atrybut w inne źródło danych, takich jak produkt, lub skontaktuj się z identyfikatorem. W programowanie zorientowane obiektowo relacje między obiektami są stosunkowo łatwa do nawigować, ponieważ każdy obiekt ma elementu członkowskiego, który odwołuje się do innego obiektu. W przypadku tabel zewnętrznych baz danych jednak nawigowanie po relacjach nie jest równie proste. Tabele bazy danych nie zawierają wbudowanych relacji. W takich przypadkach można operacji tworzenia sprzężenia zgodne elementy z każdego źródła. Przykładowo podana dwóch tabel, które zawierają informacje o produkcie i informacji o sprzedaży, można operacji tworzenia sprzężenia do dopasowania informacji o sprzedaży i produkty do tej samej kolejności sprzedaży.  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] Framework zapewnia dołączyć dwa operatory, <xref:System.Linq.Enumerable.Join%2A> i <xref:System.Linq.Enumerable.GroupJoin%2A>. Wykonaj te operatory *sprzężeniami*: oznacza to, sprzężenia, które pasują dwóch danych źródła tylko wtedy, gdy ich kluczy są takie same. (Natomiast [!INCLUDE[tsql](../../../../includes/tsql-md.md)] obsługuje dołączenia innych niż operatory `equals`, takich jak `less than` operatora.)  
  
 W warunkach relacyjnej bazy danych <xref:System.Linq.Enumerable.Join%2A> implementuje sprzężenia wewnętrznego. Typ sprzężenia jest sprzężenie wewnętrzne w zwracane są tylko te obiekty, które mają odpowiednika w przeciwną zestawu danych.  
  
 <xref:System.Linq.Enumerable.GroupJoin%2A> Operatory nie mają bezpośredniego odpowiednika w warunkach relacyjnej bazy danych; wdrażają podzbiorem sprzężenia wewnętrzne i lewe sprzężenia zewnętrzne. Lewe sprzężenie zewnętrzne jest sprzężenia, które zwraca każdy element pierwszej kolekcji (po lewej), nawet jeśli go nie ma żadnych elementów skorelowane w druga kolekcja.  
  
 Aby uzyskać więcej informacji na temat sprzężeń, zobacz [operacji Join](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje tradycyjnych przyłączenia `SalesOrderHeader` i `SalesOrderDetail` tabel z przykładowej bazy danych AdventureWorks uzyskanie zamówień online w ciągu miesiąca sierpnia.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wykonywanie zapytania zbiory danych](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [Zapytania pojedynczej tabeli](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 [Wykonywanie zapytania Typizowane zbiory danych](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 [Operacje połączone](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107)  
 [LINQ do DataSet przykłady](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
