---
title: '- Mieszczon (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: d4e4c1449b665e6dea22bfcc0ee2277478b4da1a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251052"
---
# <a name="-divide-entity-sql"></a>/(Dzielenie) (Entity SQL)
Dzieli jedną liczbę przez inną.  
  
## <a name="syntax"></a>Składnia  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a>Argumenty  
 `dividend`  
 Wyrażenie liczbowe do podzielenia. `dividend`jest dowolnym prawidłowym wyrażeniem dowolnego typu danych liczbowych.  
  
 `divisor`  
 Wyrażenie liczbowe dzielące dywidendę przez. `divisor`jest dowolnym prawidłowym wyrażeniem dowolnego typu danych liczbowych.  
  
## <a name="result-types"></a>Typy wyników  
 Typ danych, który wynika z promocji typu niejawnego dwóch argumentów. Aby uzyskać więcej informacji na temat niejawnego podwyższania poziomu, zobacz [typu System](type-system-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora arytmetycznego w celu podzielenia jednej liczby przez inną. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
