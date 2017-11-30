---
title: ANYELEMENT (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 518ac4bc1ba6842a4b5e5f3b1f0771495752859c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="anyelement-entity-sql"></a>ANYELEMENT (jednostka SQL)
Wyodrębnia element z kolekcji wielowartościowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Wszystkie prawidłowe zapytanie zwracające można wyodrębnić elementu z kolekcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Pojedynczy element w kolekcji lub dowolnego elementu, jeśli kolekcja zawiera więcej niż jeden; Jeśli kolekcja jest pusty, zwraca `null`. Jeśli `collection` jest kolekcją typu `Collection<T>`, następnie `ANYELEMENT(collection)` jest prawidłowe wyrażenie zwracające wystąpienia typu `T`.  
  
## <a name="remarks"></a>Uwagi  
 ANYELEMENT wyodrębnia dowolnego elementu z kolekcji wielowartościowych. Na przykład poniższy przykład próbuje wyodrębnić elementu pojedyncza ze zbioru `Customers`.  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora ANYELEMENT można wyodrębnić elementu z kolekcji wielowartościowych. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Typy dopuszczające wartości zerowe strukturalnych](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
