---
title: Operator (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: a30306539d45c3718d2e948e9717997bbe2104fa
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250086"
---
# <a name="modulo-entity-sql"></a>Operator (Entity SQL)
Zwraca resztę jednego wyrażenia podzieloną przez inny.  
  
## <a name="syntax"></a>Składnia  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>Argumenty  
 `dividend`  
 Wyrażenie liczbowe do podzielenia. `dividend`jest dowolnym prawidłowym wyrażeniem dowolnego typu danych liczbowych.  
  
 `divisor`  
 Wyrażenie liczbowe dzielące dywidendę przez. `divisor`jest dowolnym prawidłowym wyrażeniem dowolnego typu danych liczbowych.  
  
## <a name="result-types"></a>Typy wyników  
 Edm.Int32  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora arytmetycznego% do zwrócenia reszty jednego wyrażenia podzielonego przez inny. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
