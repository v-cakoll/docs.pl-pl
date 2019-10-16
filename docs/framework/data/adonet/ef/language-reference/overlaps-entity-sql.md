---
title: NAKŁADAją się (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: bdee9281fd406a3d029d3a10536cbdd48d2f7a58
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319411"
---
# <a name="overlaps-entity-sql"></a>NAKŁADAją się (Entity SQL)
Określa, czy dwie kolekcje mają wspólne elementy.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję do porównania z kolekcją zwróconą z innego wyrażenia zapytania. Wszystkie wyrażenia muszą być tego samego typu lub wspólnego typu podstawowego lub pochodnego jako `expression`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`, jeśli dwie kolekcje mają wspólne elementy; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 NAKŁADAjące się funkcje zapewniają funkcję równoważną z następującymi:  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 NAKŁADAnie się jest jednym z operatorów ustawionych [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Wszystkie operatory zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] są oceniane od lewej do prawej. Aby uzyskać informacje o pierwszeństwie dla operatorów zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zobacz [except](except-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora NAKŁADAnia się, aby określić, czy dwie kolekcje mają wspólną wartość. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#OVERLAPS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#overlaps)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
