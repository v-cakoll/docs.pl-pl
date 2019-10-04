---
title: Tworzenie zagnieżdżonych zapytań w języku Entity SQL
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 0ab92c1e41c89f141c3cbd37be3e1e18e64d9666
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833915"
---
# <a name="composing-nested-entity-sql-queries"></a>Tworzenie zagnieżdżonych zapytań w języku Entity SQL
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] to bogaty język funkcjonalny. Blok konstrukcyjny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest wyrażeniem. W przeciwieństwie do konwencjonalnych SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie jest ograniczony do tabelarycznego zestawu wyników: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje redagowanie złożonych wyrażeń, które mogą mieć literały, parametry lub wyrażenia zagnieżdżone. Wartość w wyrażeniu może być sparametryzowane lub składać się z innego wyrażenia.  
  
## <a name="nested-expressions"></a>Wyrażenia zagnieżdżone  
 Wyrażenie zagnieżdżone można umieścić wszędzie tam, gdzie wartość zwracanego typu jest akceptowana. Na przykład:  
  
```sql  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 Zagnieżdżona kwerenda może być umieszczona w klauzuli projekcji. Na przykład:  
  
```sql  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 W [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania zagnieżdżone muszą zawsze być ujęte w nawiasy:  
  
```sql  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 W poniższym przykładzie pokazano, jak prawidłowo zagnieżdżać wyrażenia w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order Union of dwa zapytania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).  
  
## <a name="nested-queries-in-projection"></a>Zagnieżdżone zapytania w projekcji  
 Zagnieżdżone zapytania w klauzuli Project mogą zostać przetłumaczone na zapytania dotyczące produktu kartezjańskiego na serwerze. W przypadku niektórych serwerów zaplecza, w tym serwera magazynem, może to spowodować, że tabela TempDB będzie bardzo duża, co może negatywnie wpłynąć na wydajność serwera.  
  
 Oto przykład takiego zapytania:  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a>Porządkowanie zagnieżdżonych zapytań  
 W Entity Framework wyrażenie zagnieżdżone można umieścić w dowolnym miejscu zapytania. Ponieważ Entity SQL zapewnia dużą elastyczność podczas pisania zapytań, można napisać zapytanie zawierające kolejność zagnieżdżonych zapytań. Jednak kolejność zagnieżdżonych zapytań nie jest zachowywana.  
  
```sql  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](entity-sql-overview.md)
