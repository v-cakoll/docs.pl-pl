---
title: '|| (LUB) (Jednostka SQL)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b44934aa0db73f872f0ab27a4c36c5c615855de1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="-or-entity-sql"></a>|| (LUB) (Jednostka SQL)
Łączy dwa `Boolean` wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `boolean_expression`  
 Prawidłowe wyrażenie, które zwraca `Boolean`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli jeden z warunków jest `true`; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 LUB [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatora logicznego. Służy do łączenia dwóch warunków. W przypadku więcej niż jeden operator w instrukcji lub operatory są oceniane po operatorach i. Można jednak zmienić kolejność obliczania za pomocą nawiasów.  
  
 Podwójne pionowych słupków (&#124; &#124;) ma te same funkcje co operatora OR.  
  
 W poniższej tabeli przedstawiono możliwe wartości wejściowych i zwracanych typów.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|WARTOŚĆ TRUE|WARTOŚĆ TRUE|WARTOŚĆ TRUE|  
|`FALSE`|WARTOŚĆ TRUE|FAŁSZ|NULL|  
|`NULL`|WARTOŚĆ TRUE|NULL|NULL|  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora OR do łączenia dwóch `Boolean` wyrażenia. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
