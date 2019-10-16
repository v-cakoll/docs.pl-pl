---
title: CZĘŚĆ wspólna (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: dc7338d176302b8683d541ab0dc715dd8d149c6f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319770"
---
# <a name="intersect-entity-sql"></a>CZĘŚĆ wspólna (Entity SQL)
Zwraca kolekcję wszelkich unikatowych wartości, które są zwracane przez wyrażenia zapytania po lewej stronie i po prawej stronie operandu INTERSECT. Wszystkie wyrażenia muszą być tego samego typu lub wspólnego typu podstawowego lub pochodnego jako `expression`.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję do porównania z kolekcją zwróconą z innego wyrażenia zapytania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kolekcja tego samego typu lub typowego typu podstawowego lub pochodnego jako `expression`.  
  
## <a name="remarks"></a>Uwagi  
 CZĘŚĆ wspólna jest jednym z operatorów zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Wszystkie operatory zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] są oceniane od lewej do prawej. Aby uzyskać informacje o pierwszeństwie dla operatorów zestawu [!INCLUDE[esql](../../../../../../includes/esql-md.md)], zobacz [except](except-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora INTERSECT do zwrócenia kolekcji wszelkich unikatowych wartości, które są zwracane przez wyrażenia zapytania po lewej i prawej stronie operandu INTERSECT. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#INTERSECT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#intersect)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
