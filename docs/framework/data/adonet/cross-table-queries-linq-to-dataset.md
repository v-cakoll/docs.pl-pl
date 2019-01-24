---
title: Wielotabelowe (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
ms.openlocfilehash: 117043a461779dee19f1c99361c44a33f5904993
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583525"
---
# <a name="cross-table-queries-linq-to-dataset"></a>Wielotabelowe (LINQ to DataSet)
Oprócz wykonywania zapytań pojedynczej tabeli, można również wykonać wielotabelowe w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Jest to wykonywane przy użyciu *sprzężenia*. Sprzężenie jest skojarzenie obiektów w jednym źródle danych z obiektami, które udostępniać wspólny atrybut w innym źródle danych, takie jak produkt lub skontaktuj się z identyfikatora. W programowanie zorientowane obiektowo relacje między obiektami są stosunkowo łatwo można przejść, ponieważ każdy obiekt ma element członkowski, który odwołuje się do innego obiektu. W tabelach zewnętrznej bazy danych jednak nawigowanie po relacjach nie jest tak proste. Tabele bazy danych nie zawierają wbudowane relacji. W takich przypadkach operacja join może służyć do dopasowania elementy z każdego źródła. Na przykład biorąc pod uwagę dwie tabele, które zawierają informacje o produkcie i informacji o sprzedaży, można użyć operacji tworzenia sprzężenia do dopasowania informacji o sprzedaży i produkty do tego samego zamówienia sprzedaży.  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] Framework zawiera dwa operatory, sprzężenia <xref:System.Linq.Enumerable.Join%2A> i <xref:System.Linq.Enumerable.GroupJoin%2A>. Wykonaj te operatory *sprzężeniami*: oznacza to, sprzężenia, które odpowiadają dwóch źródeł, tylko wtedy, gdy ich klucze są takie same. (Natomiast [!INCLUDE[tsql](../../../../includes/tsql-md.md)] innych niż operatory sprzężenia obsługuje `equals`, takich jak `less than` operator.)  
  
 W warunkach relacyjnej bazy danych <xref:System.Linq.Enumerable.Join%2A> implementuje sprzężenia wewnętrznego. Sprzężenie wewnętrzne to rodzaj sprzężenia w zwracane są tylko te obiekty, które mają pasujących przeciwny zestawu danych.  
  
 <xref:System.Linq.Enumerable.GroupJoin%2A> Operatory mają bezpośredniego odpowiednika w warunkach relacyjnej bazy danych; implementują nadzbiorem sprzężenia wewnętrzne lewych sprzężeń zewnętrznych. Lewe sprzężenie zewnętrzne jest sprzężenie zwracające każdego elementu pierwszej kolekcji (po lewej stronie), nawet wtedy, gdy go nie ma żadnych elementów skorelowane w drugiej kolekcji.  
  
 Aby uzyskać więcej informacji na temat sprzężenia, zobacz [operacji Join](https://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje tradycyjnych przyłączenia `SalesOrderHeader` i `SalesOrderDetail` tabel z przykładowej bazy danych AdventureWorks uzyskać zamówienia online z sierpień.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>Zobacz także
- [Wykonywanie zapytania do zestawów danych](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [Zapytania jednotabelowe](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
- [Wykonywanie zapytania do typizowanych zestawów danych](../../../../docs/framework/data/adonet/querying-typed-datasets.md)
- [Operacje połączone](https://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107)
- [Przykłady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
