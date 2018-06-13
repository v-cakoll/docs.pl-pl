---
title: INTERSECT (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: 98515ccf111bf78f49347f744a1226ca1957fbb6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761535"
---
# <a name="intersect-entity-sql"></a>INTERSECT (jednostka SQL)
Zwraca kolekcję różne wartości, które są zwracane przez wyrażenia zapytania po lewej stronie i prawej krawędzi argument INTERSECT. Wszystkie wyrażenia musi być tego samego typu lub wspólny podstawowej lub pochodny typ jako `expression`.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Wszystkie prawidłowe zapytanie zwracające kolekcja do porównania z kolekcji zwrócony z innym wyrażeniu zapytania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kolekcji tego samego typu lub wspólny podstawowej lub pochodny typ jako `expression`.  
  
## <a name="remarks"></a>Uwagi  
 INTERSECT jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ustawić operatorów. Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej. Pierwszeństwo informacji dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów, zobacz [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora INTERSECT do zwrócenia zbiór różne wartości, które są zwracane przez wyrażenia zapytania po lewej stronie i prawej krawędzi argument INTERSECT. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#INTERSECT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#intersect)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
