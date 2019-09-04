---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: d54c350196ad1ef7cfafa6d931d9d1ad8f267177
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250558"
---
# <a name="isnull-entity-sql"></a>ISNULL (Entity SQL)
Określa, czy wyrażenie zapytania ma wartość null.  
  
## <a name="syntax"></a>Składnia  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie zapytania. Nie może być kolekcją, mieć składowe kolekcji lub typem rekordu z właściwościami typu kolekcji.  
  
 NIEMOŻLIWE  
 Negacja modelu EDM. Wynik wartości logicznej jest równy NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli `expression` zwraca wartość null; `false`w przeciwnym razie.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `IS NULL` , aby określić, czy element sprzężenia zewnętrznego ma wartość null:  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 Użyj `IS NULL` , aby określić, czy element członkowski ma rzeczywistą wartość:  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 W poniższej tabeli przedstawiono zachowanie `IS NULL` niektórych wzorców. Wszystkie wyjątki są zgłaszane po stronie klienta przed wywołaniem dostawcy:  
  
|Wzorzec|Zachowanie|  
|-------------|--------------|  
|wartość zerowa ma wartość NULL|Zwraca `true`wartość.|  
|TRAKTOWANIe (null jako EntityType) ma wartość NULL|Zwraca `true`wartość.|  
|TRAKTOWANIe (null jako ComplexType) ma wartość NULL|Zgłasza błąd.|  
|TRAKTOWANIe (null AS RowType) ma wartość NULL|Zgłasza błąd.|  
|Obiekt EntityType ma wartość NULL|Zwraca `true` lub `false`.|  
|ComplexType ma wartość NULL|Zgłasza błąd.|  
|RowType ma wartość NULL|Zgłasza błąd.|  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora is not null, aby określić, czy wyrażenie zapytania nie ma wartości null. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.  
  
2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
