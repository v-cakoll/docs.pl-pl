---
title: Z wyjątkiem (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: c4df8c2b72ee60a425c98c64a13a1e2d43d4506e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833863"
---
# <a name="except-entity-sql"></a>Z wyjątkiem (Entity SQL)
Zwraca kolekcję wszystkich odrębnych wartości z wyrażenia zapytania na lewo od operandu EXCEPT, które nie są zwracane z wyrażenia zapytania z prawej strony operandu EXCEPT. Wszystkie wyrażenia muszą być tego samego typu lub wspólnego typu podstawowego lub pochodnego jako `expression`.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję do porównania z kolekcją zwróconą z innego wyrażenia zapytania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kolekcja tego samego typu lub typowego typu podstawowego lub pochodnego jako `expression`.  
  
## <a name="remarks"></a>Uwagi  
 Oprócz tego jest jednym z operatorów ustawionych [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Wszystkie operatory zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] są oceniane od lewej do prawej. W poniższej tabeli przedstawiono pierwszeństwo operatorów zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
|Pierwszeństwo|Operatory|  
|----------------|---------------|  
|Najwyższy|INTERSECT|  
||UNION<br /><br /> UNION WSZYSTKO|  
||EXCEPT|  
|Okreolon|EXISTS<br /><br /> OVERLAPS<br /><br /> FLATTEN<br /><br /> SET|  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora EXCEPT do zwrócenia kolekcji wszelkich odrębnych wartości z dwóch wyrażeń zapytań. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#EXCEPT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#except)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
