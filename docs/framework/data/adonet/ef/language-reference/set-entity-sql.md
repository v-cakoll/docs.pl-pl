---
title: Ustaw (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 76999bcbbb3b63fd945d2048734c58d97de8baea
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249238"
---
# <a name="set-entity-sql"></a>Ustaw (Entity SQL)
Wyrażenie SET służy do konwertowania kolekcji obiektów do zestawu przez wypróbowanie nowej kolekcji z usuniętymi wszystkimi zduplikowanymi elementami.  
  
## <a name="syntax"></a>Składnia  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie `SET(c)` Set jest logicznie równoważne z następującą instrukcją SELECT:  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 `SET`jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu. Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej. Zobacz [z wyjątkiem](except-entity-sql.md) informacji o priorytecie dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu.  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa wyrażenia zestawu do konwertowania kolekcji obiektów na zestaw. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-primitivetype-results.md)typu pierwotnego.  
  
2. Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
