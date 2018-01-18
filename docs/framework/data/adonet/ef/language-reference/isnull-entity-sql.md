---
title: ISNULL (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 57e90f013227f08ce365262da633a79d7abb5a8d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="isnull-entity-sql"></a>ISNULL (jednostka SQL)
Określa, czy wyrażenie kwerendy jest null.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne wyrażenie prawidłowe zapytanie. Nie może być kolekcją, mieć elementów członkowskich kolekcji lub typ rekordu z kolekcji właściwości typu.  
  
 NIE  
 Negacja EDM. Wartość logiczna wynik jest NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli `expression` zwraca wartość null; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `IS NULL` do ustalenia, czy element sprzężenie zewnętrzne jest pusty:  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 Użyj `IS NULL` ustalenie, jeśli element członkowski ma wartość rzeczywista:  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 W poniższej tabeli przedstawiono zachowania `IS NULL` przez niektóre wzorce. Wszystkie wyjątki są zgłaszane po stronie klienta przed wywołaniem pobiera dostawcy:  
  
|Wzorzec|Zachowanie|  
|-------------|--------------|  
|wartość null jest puste|Zwraca `true`.|  
|TRAKTUJ (wartość null dla obiektu AS) IS NULL|Zwraca `true`.|  
|TRAKTUJ (null AS ComplexType) IS NULL|Zwraca błąd.|  
|TRAKTUJ (null AS RowType) IS NULL|Zwraca błąd.|  
|Obiekt EntityType ma wartość NULL|Zwraca `true` lub `false`.|  
|Element ComplexType ma wartość NULL|Zwraca błąd.|  
|RowType ma wartość NULL|Zwraca błąd.|  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora IS NOT NULL, aby określić, czy wyrażenie zapytania nie jest zerowa. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
