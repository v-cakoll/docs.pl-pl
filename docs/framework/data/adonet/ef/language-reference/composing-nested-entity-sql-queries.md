---
title: Tworzenie zagnieżdżonych zapytań jednostki SQL
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: b5fc39a25b5b8592117348b150da9d82454a1562
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827321"
---
# <a name="composing-nested-entity-sql-queries"></a>Tworzenie zagnieżdżonych zapytań jednostki SQL
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest bogaty język funkcjonalności. Elementem składowym [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest wyrażeniem. W przeciwieństwie do poziomu konwencjonalnego SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie jest ograniczona do zestawu wyniku tabelarycznym: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje tworzenie złożonych wyrażeń, które mogą mieć literały, parametry lub zagnieżdżonych wyrażeń. Wartości w wyrażeniu można ustawiać parametry lub składa się z niektóre inne wyrażenie.  
  
## <a name="nested-expressions"></a>Nested Expressions  
 Zagnieżdżone wyrażenie można umieścić w dowolnym miejscu wartości typu, zwracana jest akceptowany. Na przykład:  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 Zapytanie zagnieżdżone można umieścić w klauzuli projekcji. Na przykład:  
  
```  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 W [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zapytań zagnieżdżonej zawsze muszą być ujęte w nawiasach:  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 Poniższy przykład pokazuje, jak poprawnie zagnieździć wyrażeń w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [Instrukcje: Kolejność sumę dwóch zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).  
  
## <a name="nested-queries-in-projection"></a>Zapytania zagnieżdżone w projekcji  
 Zapytania zagnieżdżone w klauzuli projektu może uzyskać przetłumaczone na zapytania formułuje iloczyn na serwerze. W niektórych serwerów wewnętrznej bazy danych, w tym SQL Server może to spowodować tabeli bazy danych TempDB, aby stać się bardzo duże, który może niekorzystnie wpłynąć na wydajność serwera.  
  
 Oto przykład w przypadku takiego zapytania:  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a>Określanie kolejności zapytań zagnieżdżonej  
 Platformy Entity Framework zagnieżdżone wyrażenie można umieścić dowolne miejsce w zapytaniu. Ponieważ jednostka SQL pozwala na większą elastyczność w pisaniu zapytań, istnieje możliwość napisania zapytanie, które zawiera kolejność zapytań zagnieżdżonej. Kolejność zapytanie zagnieżdżone nie są zachowywane.  
  
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
- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
