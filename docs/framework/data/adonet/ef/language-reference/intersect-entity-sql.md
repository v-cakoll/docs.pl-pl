---
title: INTERSECT (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: 85b0abb03161b2df0cfc4ddf6cafc92fb7de9d95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780383"
---
# <a name="intersect-entity-sql"></a>INTERSECT (jednostka SQL)
Zwraca kolekcję różne wartości, które są zwracane przez wyrażenia zapytania po lewej stronie i prawej stronie operandu INTERSECT. Wszystkie wyrażenia musi być tego samego typu lub wspólnej podstawowej lub pochodny typ jako `expression`.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne wyrażenie prawidłowe zapytanie, które zwraca kolekcję do porównania z tą kolekcją zwrócony z innego wyrażenia zapytania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kolekcji tego samego typu lub wspólnej podstawowej lub pochodny typ jako `expression`.  
  
## <a name="remarks"></a>Uwagi  
 INTERSECT jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawu. Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są przetwarzane od lewej do prawej. Pierwszeństwo informacji dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zestaw operatorów, zobacz [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora INTERSECT zwrócić zbiór różne wartości, które są zwracane przez wyrażenia zapytania po lewej stronie i prawej stronie operandu INTERSECT. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#INTERSECT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#intersect)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
