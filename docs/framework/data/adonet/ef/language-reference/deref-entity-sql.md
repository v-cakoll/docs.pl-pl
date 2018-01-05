---
title: DEREF (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: bade65b36363aef1597ce4664e3e514141dee908
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="deref-entity-sql"></a>DEREF (jednostka SQL)
Wyłuskań wartość odniesienia i daje w wyniku tego usunąć odwołania do.  
  
## <a name="syntax"></a>Składnia  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne wyrażenie prawidłową kwerendę, która zwraca kolekcję.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość jednostek, do którego istnieje odwołanie.  
  
## <a name="remarks"></a>Uwagi  
 DEREF operator wyłuskań wartość odniesienia i daje w wyniku tego usunąć odwołania do. Na przykład jeśli `r` jest odwołaniem do typu ref\<T >, `Deref``(r)` jest wyrażeniem typu `T` który daje jednostki odwołuje się `r`. Jeśli wartość odwołania ma wartość null lub jest zawieszonego (to znaczy docelowego odwołania nie istnieje), wynik operatora DEREF ma wartość null.  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa DEREF operator, aby usunąć odwołania do wartości odwołania i usunąć odwołania do wyniku tego produktu. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do metody ExecutePrimitiveTypeQuery:  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [Typy strukturalne dopuszczające wartości Null](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
