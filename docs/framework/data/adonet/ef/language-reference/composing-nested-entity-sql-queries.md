---
title: Tworzenie zapytań SQL zagnieżdżonych jednostki
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 92e3153350787ef75c48ee52f1b6c68e09e15b4b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760859"
---
# <a name="composing-nested-entity-sql-queries"></a>Tworzenie zapytań SQL zagnieżdżonych jednostki
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest bogaty język funkcjonalności. Blokiem konstrukcyjnym [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest wyrażenie. W przeciwieństwie do konwencjonalnych SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie jest ograniczone do zestawu wyników tabelarycznym: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje tworzenie złożonych wyrażeń, które mogą mieć literały, parametry lub zagnieżdżonych wyrażeń. Wartość w wyrażeniu można sparametryzowanych lub składa się z niektórych innych wyrażenia.  
  
## <a name="nested-expressions"></a>Zagnieżdżone wyrażenia  
 Zagnieżdżone wyrażenia można umieścić w dowolnym wartości typu, zwracana jest akceptowany. Na przykład:  
  
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
  
 W [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zapytania zagnieżdżone zawsze musi być ujęta w nawiasy:  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 W poniższym przykładzie pokazano sposób poprawnie zagnieździć wyrażenia w [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [porady: kolejność Unii o dwa zapytania](http://msdn.microsoft.com/library/853c583a-eaba-4400-830d-be974e735313).  
  
## <a name="nested-queries-in-projection"></a>Zapytania zagnieżdżone w projekcji  
 Zapytania zagnieżdżone w klauzuli projektu może pobrać przetłumaczyć iloczyn kartezjański zapytania na serwerze. W niektórych serwerów wewnętrznej bazy danych, w tym SQL Server może to spowodować tabeli bazy danych TempDB uzyskanie bardzo duży, które może niekorzystnie wpłynąć na wydajność serwera.  
  
 Poniżej przedstawiono przykład takiego kwerendy:  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a>Porządkowanie zapytania zagnieżdżone  
 W ramach jednostki zagnieżdżone wyrażenia można umieścić dowolne miejsce w zapytaniu. Ponieważ SQL jednostki pozwala dużą elastyczność w Pisanie zapytań, istnieje możliwość Napisz zapytanie, które zawiera kolejność kwerend zagnieżdżonych. Kolejność zapytanie zagnieżdżone nie są zachowywane.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
