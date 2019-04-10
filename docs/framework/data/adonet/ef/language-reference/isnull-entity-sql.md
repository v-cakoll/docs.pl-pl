---
title: ISNULL (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: aaecce3ff74d64b8e07b31329ced5b5e581fca5b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295097"
---
# <a name="isnull-entity-sql"></a>ISNULL (jednostka SQL)
Określa, czy wyrażenie zapytania o wartości null.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne wyrażenie prawidłowe zapytanie. Nie może być kolekcją, elementów członkowskich kolekcji lub typ rekordu w kolekcji właściwości typu.  
  
 NIE  
 Neguje EDM. Wartość logiczna wynikiem jest wartość NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli `expression` zwraca wartość null; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `IS NULL` do ustalenia, czy element sprzężenie zewnętrzne jest wartość null:  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 Użyj `IS NULL` można sprawdzić, czy członek jest rzeczywista wartość:  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 W poniższej tabeli przedstawiono zachowania `IS NULL` przez niektóre wzorce. Wszystkie wyjątki są zgłaszane po stronie klienta, przed wywołaniem pobiera dostawcy:  
  
|Wzorzec|Zachowanie|  
|-------------|--------------|  
|wartość null jest puste|Zwraca `true`.|  
|TRAKTUJ (wartość null dla obiektu AS) IS NULL|Zwraca `true`.|  
|TRAKTUJ (o wartości null ComplexType AS) IS NULL|Zgłasza błąd.|  
|TRAKTUJ (o wartości null RowType AS) IS NULL|Zgłasza błąd.|  
|Obiekt EntityType ma wartość NULL|Zwraca `true` lub `false`.|  
|ComplexType ma wartość NULL|Zgłasza błąd.|  
|RowType ma wartość NULL|Zgłasza błąd.|  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora IS NOT NULL, aby określić, jeśli wyrażenie zapytania nie ma wartości null. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do języka Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
