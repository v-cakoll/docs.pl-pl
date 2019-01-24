---
title: 'Instrukcje: Reprezentacja tabel jako klas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 307356e056aae29af7c8ceafae0ca02604658aab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509613"
---
# <a name="how-to-represent-tables-as-classes"></a>Instrukcje: Reprezentacja tabel jako klas
Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu, aby określić klasę jako klasę jednostki skojarzonej z tabelą bazy danych.  
  
### <a name="to-map-a-class-to-a-database-table"></a>Aby zamapować klasę do tabeli bazy danych  
  
-   Dodaj <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu deklaracji klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy kod ustanawia `Customer` jak klasa jednostki, która jest skojarzona z `Customers` tabeli bazy danych.  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 Nie trzeba określać <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> nazwę można wywnioskować właściwość. Jeśli nie określisz nazwy, nazwa jest uznawana za tę taką samą nazwę jak właściwość lub pole.  
  
## <a name="see-also"></a>Zobacz także
- [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
