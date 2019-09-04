---
title: = (Equals) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: ec87ec682e1773c001c225567a35b3cedc9c5aba
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251006"
---
# <a name="-equals-entity-sql"></a>= (Equals) (Entity SQL)
Porównuje równość dwóch wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie. Oba wyrażenia muszą mieć niejawnie wymienialne typy danych.  
  
## <a name="result-types"></a>Typy wyników  
 `true`Jeśli wyrażenie po lewej stronie jest równe wyrażeniu z prawej strony; w przeciwnym razie. `false`  
  
## <a name="remarks"></a>Uwagi  
 Operator = = jest równoważny z =.  
  
## <a name="example"></a>Przykład  
 Poniższy Entity SQL Query używa operatora porównania, aby porównać równość dwóch wyrażeń. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
