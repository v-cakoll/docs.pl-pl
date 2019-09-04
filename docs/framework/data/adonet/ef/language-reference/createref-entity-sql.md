---
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: cbaea82108dd3debcca972ca15dea248227330ac
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251103"
---
# <a name="createref-entity-sql"></a>CREATEREF (Entity SQL)
W obiekcie EntitySet są przywoływane odwołania do jednostki.  
  
## <a name="syntax"></a>Składnia  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a>Argumenty  
 `entityset_identifier`  
 Identyfikator obiektu EntitySet, a nie literału ciągu.  
  
 `row_typed_expression`  
 Wyrażenie z określonym wierszem, które odnosi się do właściwości klucza typu jednostki.  
  
## <a name="remarks"></a>Uwagi  
 `row_typed_expression`muszą być strukturalnie równoważne z typem klucza dla jednostki. Oznacza to, że musi mieć taką samą liczbę i typy pól w tej samej kolejności co klucze jednostek.  
  
 W poniższym przykładzie zamówienia i BadOrders są zarówno obiektem EntitySet typu Order, jak i przyjmuje się, że są one właściwością Single Key kolejności. W przykładzie pokazano, jak możemy utworzyć odwołanie do jednostki w BadOrders. Należy zauważyć, że odwołanie może być zawieszonego.  Oznacza to, że odwołanie może nie identyfikować określonej jednostki. W takich przypadkach `DEREF` operacja na tym odwołaniu zwraca wartość null.  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie Entity SQL używa operatora CREATEREF do tworzenia odwołań do jednostki w zestawie jednostek. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [DEREF](deref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [REF](ref-entity-sql.md)
