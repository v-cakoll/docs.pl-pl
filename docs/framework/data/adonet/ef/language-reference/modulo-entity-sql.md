---
title: (Modulo) (Jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: ad7b76c1479906e9dcd875407e75475b55d5ae16
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="modulo-entity-sql"></a>(Modulo) (Jednostka SQL)
Zwraca resztę z jednego wyrażenia podzielona przez inny.  
  
## <a name="syntax"></a>Składnia  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>Argumenty  
 `dividend`  
 Wyrażenie liczbowe do dzielenia. `dividend` jest dowolne prawidłowe wyrażenie jednego z typów numerycznych.  
  
 `divisor`  
 Wyrażenie liczbowe do dzielenia dzielna przez. `divisor` jest dowolne prawidłowe wyrażenie jednego z typów numerycznych.  
  
## <a name="result-types"></a>Typy wyników  
 Edm.Int32  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki użyto operatora arytmetycznego %, która zwraca pozostałej części jedno wyrażenie podzielona przez inny. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
