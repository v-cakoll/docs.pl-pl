---
title: = (Równa się) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 101dccd40e9197c7cf0795ccb80ded367676842d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150315"
---
# <a name="-equals-entity-sql"></a>= (Równa się) (Entity SQL)
Porównuje równość dwóch wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
expression = expression  
-- or
expression == expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie. Oba wyrażenia muszą mieć niejawnie konwertowane typy danych.  
  
## <a name="result-types"></a>Typy wyników  
 `true`jeśli wyrażenie lewe jest równe prawemu wyrażeniu; w `false`przeciwnym razie , .  
  
## <a name="remarks"></a>Uwagi  
 Operator == jest odpowiednikiem =.  
  
## <a name="example"></a>Przykład  
 Następująca kwerenda SQL jednostki używa = operator porównania, aby porównać równość dwóch wyrażeń. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą [w : Jak: Wykonać kwerendę, która zwraca wyniki structuraltype](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następującą kwerendę jako `ExecuteStructuralTypeQuery` argument do metody:  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
