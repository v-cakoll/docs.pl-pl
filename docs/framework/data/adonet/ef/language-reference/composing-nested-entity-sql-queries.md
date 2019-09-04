---
title: Tworzenie zagnieżdżonych zapytań w języku Entity SQL
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 3aa2e53b584eece9cc5e2d26791c78ffe33f9e35
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251149"
---
# <a name="composing-nested-entity-sql-queries"></a>Tworzenie zagnieżdżonych zapytań w języku Entity SQL
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]to bogaty język funkcjonalny. Blok [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstrukcyjny jest wyrażeniem. W przeciwieństwie do konwencjonalnych SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie jest ograniczony do zestawu wyników tabelarycznych: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje tworzenie złożonych wyrażeń, które mogą mieć literały, parametry lub wyrażenia zagnieżdżone. Wartość w wyrażeniu może być sparametryzowane lub składać się z innego wyrażenia.  
  
## <a name="nested-expressions"></a>Wyrażenia zagnieżdżone  
 Wyrażenie zagnieżdżone można umieścić wszędzie tam, gdzie wartość zwracanego typu jest akceptowana. Na przykład:  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 Zagnieżdżona kwerenda może być umieszczona w klauzuli projekcji. Na przykład:  
  
```  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 W [!INCLUDE[esql](../../../../../../includes/esql-md.md)]programie zapytania zagnieżdżone muszą zawsze być ujęte w nawiasy:  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 W poniższym przykładzie pokazano, jak prawidłowo zagnieżdżać wyrażenia [!INCLUDE[esql](../../../../../../includes/esql-md.md)]w: [Instrukcje: Porządkuj złożenie dwóch zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).  
  
## <a name="nested-queries-in-projection"></a>Zagnieżdżone zapytania w projekcji  
 Zagnieżdżone zapytania w klauzuli Project mogą zostać przetłumaczone na zapytania dotyczące produktu kartezjańskiego na serwerze. W przypadku niektórych serwerów zaplecza, w tym serwera magazynem, może to spowodować, że tabela TempDB będzie bardzo duża, co może negatywnie wpłynąć na wydajność serwera.  
  
 Oto przykład takiego zapytania:  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a>Porządkowanie zagnieżdżonych zapytań  
 W Entity Framework wyrażenie zagnieżdżone można umieścić w dowolnym miejscu zapytania. Ponieważ Entity SQL zapewnia dużą elastyczność podczas pisania zapytań, można napisać zapytanie zawierające kolejność zagnieżdżonych zapytań. Jednak kolejność zagnieżdżonych zapytań nie jest zachowywana.  
  
```  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](entity-sql-overview.md)
