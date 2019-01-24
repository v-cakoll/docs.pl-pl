---
title: CREATEREF (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: bdf1c34f8a050764e8f8766da25076a7c1c361ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505084"
---
# <a name="createref-entity-sql"></a>CREATEREF (jednostka SQL)
Fabricates odwołania do jednostki w obiekcie entityset.  
  
## <a name="syntax"></a>Składnia  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a>Argumenty  
 `entityset_identifier`  
 Identyfikator obiektu entityset nie literału ciągu.  
  
 `row_typed_expression`  
 Wpisane wiersza wyrażenie, które odnosi się do właściwości kluczy tego typu jednostki.  
  
## <a name="remarks"></a>Uwagi  
 `row_typed_expression` musi być strukturalnie odpowiednikiem typu klucza jednostki. Oznacza to musi on mieć tej samej liczby i typy pól w tej samej kolejności, jak klucze jednostek.  
  
 W poniższym przykładzie zamówień i BadOrders są oba zestawy jednostek typu zamówienia, a identyfikator zakłada, że jedną właściwość klucza zamówienia. W przykładzie pokazano, jak firma Microsoft może zwrócić odwołanie do jednostki w BadOrders. Należy zauważyć, że odwołanie może dangling.  Oznacza to odwołanie, nie może faktycznie zidentyfikować określonej jednostki. W takich przypadkach `DEREF` operacji dla tego odwołania zwraca wartość null.  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatorze CREATEREF do przeznaczeniem odwołania do jednostki w zestawie jednostek. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a>Zobacz także
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
- [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
