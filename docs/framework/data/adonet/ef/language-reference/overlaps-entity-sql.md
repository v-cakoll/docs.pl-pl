---
title: NAKŁADAją się (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: fef90beebf1c2723c767eaf5155542ad40d5fcb8
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249735"
---
# <a name="overlaps-entity-sql"></a>NAKŁADAją się (Entity SQL)
Określa, czy dwie kolekcje mają wspólne elementy.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję do porównania z kolekcją zwróconą z innego wyrażenia zapytania. Wszystkie wyrażenia muszą być tego samego typu lub według `expression`wspólnego typu podstawowego lub pochodnego.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli dwie kolekcje mają wspólne elementy; w przeciwnym razie. `false`  
  
## <a name="remarks"></a>Uwagi  
 NAKŁADAjące się funkcje zapewniają funkcję równoważną z następującymi:  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 Nakładanie się jest jednym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu. Wszystkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory zestawów są oceniane od lewej do prawej. Aby uzyskać informacje o pierwszeństwie dla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów zestawu, zobacz [except](except-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora NAKŁADAnia się, aby określić, czy dwie kolekcje mają wspólną wartość. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#OVERLAPS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#overlaps)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
