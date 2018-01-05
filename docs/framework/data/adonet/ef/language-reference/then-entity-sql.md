---
title: "NASTĘPNIE (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ecf46b122ec5411913891aa1e33bee071044d032
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="then-entity-sql"></a>NASTĘPNIE (jednostka SQL)
Wynik klauzuli WHEN podczas daje w wyniku `true`.  
  
## <a name="syntax"></a>Składnia  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `when_expression`  
 Prawidłowe wyrażenie logiczne.  
  
 `then_expression`  
 Dowolne wyrażenie prawidłową kwerendę, która zwraca kolekcję.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `when_expression` daje w wyniku wartość `true`, wynikiem jest odpowiednie `then-expression`. Jeśli żadna z WHEN warunki są spełnione, `else-expression` oceny. Jednak w przypadku nie `else-expression`, wynikiem jest wartość null.  
  
 Na przykład zobacz [przypadku](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki użyto wyrażenia CASE można obliczyć zestawu `Boolean` wyrażenia. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Zobacz też  
 [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
