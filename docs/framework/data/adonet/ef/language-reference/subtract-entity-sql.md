---
title: '- Odjęt (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: 8b5cfee4c82757e55babdf1ad14f6cf3c743a5a2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249017"
---
# <a name="--subtract-entity-sql"></a>-(Odejmij) (Entity SQL)
Odejmuje dwie liczby.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression - expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie jednego z typów danych liczbowych.  
  
## <a name="result-types"></a>Typy wyników  
 Typ danych, który wynika z promocji typu niejawnego dwóch argumentów. Aby uzyskać więcej informacji na temat niejawnego podwyższania poziomu, zobacz [typu System](type-system-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora-arytmetycznego do odejmowania dwóch liczb. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#SUBTRACT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#subtract)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
