---
title: '&amp;&amp;(A) (Jednostka SQL)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a132968c69320cdae1824bebdf51b764202084b1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="ampamp-and-entity-sql"></a>&amp;&amp;(A) (Jednostka SQL)
Zwraca `true` Jeśli oba wyrażenia są `true`; w przeciwnym razie `false` lub `NULL`.  
  
## <a name="syntax"></a>Składnia  
  
```  
boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `boolean_expression`  
 Dowolne prawidłowe wyrażenie zwracające wartość logiczną.  
  
## <a name="remarks"></a>Uwagi  
 Podwójne ampersandu (& &) mają te same funkcje co AND operator.  
  
 W poniższej tabeli przedstawiono możliwe wartości wejściowych i zwracanych typów.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|WARTOŚĆ TRUE|FAŁSZ|NULL|  
|`FALSE`|FAŁSZ|FAŁSZ|FAŁSZ|  
|`NULL`|NULL|FAŁSZ|NULL|  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki pokazano, jak można użyć operatora AND. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
