---
title: ZESTAW (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e70db99157e0bc49e1548d18c8fccfa44af42356
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="set-entity-sql"></a>ZESTAW (jednostka SQL)
Wyrażenie zestawu jest używana do konwertowania kolekcji obiektów do zestawu przez reaguje nowej kolekcji z wszystkie zduplikowane elementy usunięte.  
  
## <a name="syntax"></a>Składnia  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne wyrażenie prawidłową kwerendę, która zwraca kolekcję.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie zestawu `SET(c)` jest odpowiednikiem logicznie następującą instrukcję select:  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 `SET`jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ustawić operatorów. Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej. Zobacz [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) pierwszeństwo informacji dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ustawić operatorów.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki użyto wyrażenia zestawu do przekonwertowania kolekcji obiektów do zestawu. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
