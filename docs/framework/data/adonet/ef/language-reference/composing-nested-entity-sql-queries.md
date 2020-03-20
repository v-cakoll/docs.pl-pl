---
title: Tworzenie zagnieżdżonych zapytań w języku Entity SQL
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 6b2fc9a32fc30d205b9c33257bf98781cfa07499
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150392"
---
# <a name="composing-nested-entity-sql-queries"></a>Tworzenie zagnieżdżonych zapytań w języku Entity SQL
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]jest bogatym językiem funkcjonalnym. Budulcem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest wyrażenie. W przeciwieństwie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do konwencjonalnego SQL, nie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ogranicza się do zestaw wyników tabelaryczne: obsługuje tworzenie złożonych wyrażeń, które mogą mieć literały, parametry lub wyrażenia zagnieżdżone. Wartość w wyrażeniu może być sparametryzowana lub składa się z innego wyrażenia.  
  
## <a name="nested-expressions"></a>Wyrażenia zagnieżdżone  
 Wyrażenie zagnieżdżone można umieścić w dowolnym miejscu akceptowana jest wartość typu zwracanego przez niego. Przykład:  
  
```sql  
-- Returns a hierarchical collection of three elements at top-level.
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 Zagnieżdżone zapytanie można umieścić w klauzuli rzutowania. Przykład:  
  
```sql  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 W [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zagnieżdżone kwerendy muszą być zawsze ujęte w nawiasy:  
  
```sql  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 W poniższym przykładzie pokazano, jak [!INCLUDE[esql](../../../../../../includes/esql-md.md)]prawidłowo zagnieżdżać wyrażenia w : [Jak: Kolejność Unii dwóch zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).  
  
## <a name="nested-queries-in-projection"></a>Zagnieżdżone kwerendy w rzutach  
 Zagnieżdżone zapytania w klauzuli projektu mogą zostać przetłumaczone na zapytania produktów kartezjańskich na serwerze. W niektórych serwerach wewnętrznej bazy danych, w tym SQL Server, może to spowodować, że tabela TempDB uzyskać bardzo duże, co może niekorzystnie wpłynąć na wydajność serwera.  
  
 Oto przykład takiej kwerendy:  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a>Zamawianie zapytań zagnieżdżonych  
 W entity framework zagnieżdżone wyrażenie można umieścić w dowolnym miejscu w kwerendzie. Ponieważ entity SQL umożliwia dużą elastyczność w pisaniu zapytań, istnieje możliwość zapisu kwerendy, która zawiera kolejność zapytań zagnieżdżonych. Jednak kolejność kwerendy zagnieżdżonej nie jest zachowywana.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Omówienie jednostki SQL](entity-sql-overview.md)
