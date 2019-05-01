---
title: GROUPPARTITION (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 9f0f917380e6422da753282216529580f87f1a1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774728"
---
# <a name="grouppartition-entity-sql"></a>GROUPPARTITION (jednostka SQL)
Zwraca kolekcję wartości argumentów, które są pokazane poza bieżącą partycję grupy, do którego odnosi się agregacji. `GroupPartition` Agregacji jest oparte na grupach agregacji i nie ma związanych z kolekcjami formy.  
  
## <a name="syntax"></a>Składnia  
  
```  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Wszelkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wyrażenia.  
  
## <a name="remarks"></a>Uwagi  
 Następujące zapytanie generuje listę produktów i zbiór ilości wierszy w kolejności dla każdego produktu:  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 Następujące dwa zapytania są semantycznie równe:  
  
```  
select p, Sum(GroupPartition(ol.Quantity)) from LOB.OrderLines as ol  
  group by ol.Product as p  
select p, Sum(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 `GROUPPARTITION` Operatora można używać w połączeniu z funkcjami agregującymi zdefiniowanych przez użytkownika.  
  
 `GROUPPARTITION` to specjalne aggregate-operator, który zawiera odwołanie do zestawu pogrupowanych danych wejściowych. Ta dokumentacja może służyć wszędzie w zapytaniu gdzie GROUP BY znajduje się w zakresie. Na przykład  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 Za pomocą regularnego GROUP BY wyniki grupowania są ukryte. Wyniki można używać tylko w funkcji agregującej. Aby wyświetlić wyniki grupowania, należy skorelować wyniki, grupowanie i ustawić za pomocą podzapytania danych wejściowych. Następujące dwa zapytania są równoważne:  
  
```  
select p, (select q from GroupPartition(ol.Quantity) as q) from LOB.OrderLines as ol group by ol.Product as p  
select p, (select ol.Quantity as q from LOB.OrderLines as ol2 where ol2.Product = p) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 Jak widać w przykładzie, aggregate-operator GROUPPARTITION sprawia, że łatwiej uzyskać odwołanie do ustawienia po grupowania danych wejściowych.  
  
 GROUPPARTITION operator można określić dowolną [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wyrażenie w operatorze danych wejściowych, gdy używasz `expression` parametru.  
  
 Na przykład wszystkie poniższe wyrażenia wejściowego do partycji grupy są prawidłowe:  
  
```  
select groupkey, GroupPartition(b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(1) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(a + b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({a + b}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({42}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(b > a) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób użycia klauzuli GROUPPARTITION z klauzuli GROUP BY. Grupy klauzuli GROUP BY `SalesOrderHeader` jednostek według ich `Contact`. Klauzula GROUPPARTITION, a następnie projekty `TotalDue` właściwości dla każdej grupy, wynikiem kolekcji miejsc po przecinku.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]
