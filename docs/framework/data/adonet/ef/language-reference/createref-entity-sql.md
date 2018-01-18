---
title: CREATEREF (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8de4266277be31fd51411d4b994f1b5de45f13df
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="createref-entity-sql"></a>CREATEREF (jednostka SQL)
Fabricates odwołania do jednostki w obiekcie entityset.  
  
## <a name="syntax"></a>Składnia  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a>Argumenty  
 `entityset_identifier`  
 Identyfikator obiektu entityset nie literału ciągu.  
  
 `row_typed_expression`  
 Wyrażenie typu wiersz odpowiada właściwości klucza typu jednostki.  
  
## <a name="remarks"></a>Uwagi  
 `row_typed_expression`musi być równoważna strukturę do typu klucza dla jednostki. Oznacza to musi mieć tego samego liczbę i typy pól w takiej samej kolejności jak kluczy jednostek.  
  
 W poniższym przykładzie zleceń i BadOrders są oba zestawy jednostek typu kolejności i identyfikator zakłada, że jedną właściwość klucza zlecenia. Jak może utworzyć odwołania do jednostki w BadOrders pokazano w przykładzie. Należy pamiętać, że może być dangling odwołania.  Oznacza to, że odwołanie, nie może faktycznie zidentyfikować określonej jednostki. W takich przypadkach `DEREF` operacji dla tego odwołania zwraca wartość null.  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki nawiązywał operatorze CREATEREF przeznaczeniem odwołania do jednostki w zestawie jednostek. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
