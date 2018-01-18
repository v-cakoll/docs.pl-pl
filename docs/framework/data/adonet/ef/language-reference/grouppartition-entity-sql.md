---
title: GROUPPARTITION (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 09d4d1e6d2e69d805c316f60e6d6e91d094e68cb
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="grouppartition-entity-sql"></a>GROUPPARTITION (jednostka SQL)
Zwraca kolekcję wartości argumentów, które są przewidywane poza bieżącą partycję grupy, do którego odnosi się agregacji. `GroupPartition` Agregacji jest oparte na grupach agregacji i nie ma opartego na kolekcji formy.  
  
## <a name="syntax"></a>Składnia  
  
```  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Wszelkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wyrażenia.  
  
## <a name="remarks"></a>Uwagi  
 Następujące zapytanie generuje listę produktów i kolekcję ilości wierszy w kolejności dla każdego produktu:  
  
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
  
 `GROUPPARTITION` Operator może być używany w połączeniu z funkcjami agregującymi zdefiniowane przez użytkownika.  
  
 `GROUPPARTITION`to specjalne operatora agregacji, który zawiera odwołanie do zestawu wejściowego grupowanych. To odwołanie można dowolne miejsce w zapytaniu gdzie GROUP BY znajduje się w zakresie. Na przykład  
  
```  
select p, GroupPartition(ol.Quantity) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 Regularne GROUP BY wyniki grupowanie są ukryte. Wyniki można używać tylko w funkcji agregującej. Aby wyświetlić wyniki grupowanie, masz służące do skorelowania wyniki grupowanie i ustawić przy użyciu podzapytania danych wejściowych. Następujące dwa zapytania są równoważne:  
  
```  
select p, (select q from GroupPartition(ol.Quantity) as q) from LOB.OrderLines as ol group by ol.Product as p  
select p, (select ol.Quantity as q from LOB.OrderLines as ol2 where ol2.Product = p) from LOB.OrderLines as ol group by ol.Product as p  
```  
  
 Jak pokazano w przykładzie, operatora agregacji GROUPPARTITION ułatwia odwołać się do danych wejściowych po grupowanie.  
  
 GROUPPARTITION operator można określić dowolną [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wyrażenie w operatorze wejściowych, jeśli używasz `expression` parametru.  
  
 Na przykład wszystkie następujące wyrażeń wejściowych do partycji grupy są prawidłowe:  
  
```  
select groupkey, GroupPartition(b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(1) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(a + b) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({a + b}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition({42}) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
select groupkey, GroupPartition(b > a) from {1,2,3} as a inner join {4,5,6} as b on true group by a as groupkey  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób użycia klauzuli GROUPPARTITION z klauzulą GROUP BY. Grupy klauzuli GROUP BY `SalesOrderHeader` jednostek według ich `Contact`. Klauzula GROUPPARTITION, a następnie projekty `TotalDue` właściwości dla każdej grupy, co w kolekcji miejsc dziesiętnych.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]
