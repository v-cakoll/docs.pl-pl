---
title: GROUPPARTITION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 19df566c254a3f3202eb3554ab43ee0d7c944181
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833755"
---
# <a name="grouppartition-entity-sql"></a>GROUPPARTITION (Entity SQL)
Zwraca kolekcję wartości argumentów, które są rzutowane na bieżącą partycję grupy, z którą jest powiązana agregacja. Agregacja `GroupPartition` jest agregacją opartą na grupach i nie ma formy opartej na kolekcji.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne wyrażenie [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="remarks"></a>Uwagi  
 Następujące zapytanie tworzy listę produktów i zbiór ilości wierszy zamówień dla każdego produktu:  
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
```  
  
 Następujące dwa zapytania są semantycznie równe:  
  
```sql  
SELECT p, Sum(GroupPartition(ol.Quantity)) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
SELET p, Sum(ol.Quantity) FROM LOB.OrderLines AS ol
  group by ol.Product as p  
```  
  
 Operatora `GROUPPARTITION` można używać w połączeniu z funkcjami agregującymi zdefiniowanymi przez użytkownika.  
  
`GROUPPARTITION` jest specjalnym operatorem agregującym, który przechowuje odwołanie do zgrupowanego zestawu danych wejściowych. Tego odwołania można użyć w dowolnym miejscu w zapytaniu, w którym Grupuj według znajduje się w zakresie. Na przykład:
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 W przypadku zwykłego `GROUP BY` wyniki grupowania są ukryte. Wyniki można używać tylko w funkcji agregującej. Aby wyświetlić wyniki grupowania, należy skorelować wyniki grupowania i zestawu wejściowego za pomocą podzapytania... Następujące dwa zapytania są równoważne:  
  
```sql  
SELET p, (SELECT q FROM GroupPartition(ol.Quantity) AS q) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
SELECT p, (SELECT ol.Quantity AS q FROM LOB.OrderLines AS ol2 WHERE ol2.Product = p) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 Jak pokazano na przykładzie, operator agregujący GROUPPARTITION ułatwia uzyskanie odwołania do zestawu wejściowego po grupowaniu.  
  
 Operator GROUPPARTITION może określić dowolne wyrażenie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w danych wejściowych operatora, gdy używany jest parametr `expression`.  
  
 Dla wystąpienia wszystkie następujące wyrażenia wejściowe do partycji grupy są prawidłowe:  
  
```sql  
SELECT groupkey, GroupPartition(b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(1) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(a + b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition({a + b}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition({42}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition(b > a) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać klauzuli GROUPPARTITION z klauzulą GROUP BY. Klauzula GROUP BY grupuje jednostki `SalesOrderHeader` według ich `Contact`. Klauzula GROUPPARTITION następnie projektuje Właściwość `TotalDue` dla każdej grupy, co skutkuje kolekcją miejsc dziesiętnych.  
  
 [!code-sql[DP EntityServices Concepts#Collection_GroupPartition](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#collection_grouppartition)]
