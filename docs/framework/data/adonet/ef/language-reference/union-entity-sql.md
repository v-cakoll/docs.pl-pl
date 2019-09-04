---
title: Unia (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: 34eac0dfd28d39ec68f084ea10dd46693f44eea3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248799"
---
# <a name="union-entity-sql"></a>Unia (Entity SQL)
Łączy wyniki dwóch lub więcej zapytań w jedną kolekcję.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję w celu połączenia z kolekcją, wszystkie wyrażenia muszą być tego samego typu lub typu wspólnego lub pochodnego jako `expression`.  
  
 UNION  
 Określa, że wiele kolekcji ma być łączonych i zwracane jako pojedyncza kolekcja.  
  
 CAŁĄ  
 Określa, że wielokrotne kolekcje mają być połączone i zwracane jako pojedyncze kolekcje, w tym duplikaty. Jeśli nie zostanie określony, duplikaty są usuwane z kolekcji wyników.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kolekcja tego samego typu lub typowego typu podstawowego lub pochodnego jako `expression`.  
  
## <a name="remarks"></a>Uwagi  
 Unia jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu. Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej. Aby uzyskać informacje o pierwszeństwie dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu, zobacz [except](except-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora UNION ALL do łączenia wyników dwóch zapytań w jedną kolekcję. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
