---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 9066f9fb68ce2c50e9523881cfa0dd930cd0b52e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319731"
---
# <a name="isnull-entity-sql"></a>ISNULL (Entity SQL)
Określa, czy wyrażenie zapytania ma wartość null.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie zapytania. Nie może być kolekcją, mieć składowe kolekcji lub typem rekordu z właściwościami typu kolekcji.  
  
 NIEMOŻLIWE  
 Negacja modelu EDM. Wynik wartości logicznej jest równy NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`, jeśli `expression` zwraca wartość null; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `IS NULL`, aby określić, czy element sprzężenia zewnętrznego ma wartość null:  
  
```sql  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 Użyj `IS NULL`, aby określić, czy element członkowski ma rzeczywistą wartość:  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 W poniższej tabeli przedstawiono zachowanie `IS NULL` w przypadku niektórych wzorców. Wszystkie wyjątki są zgłaszane po stronie klienta przed wywołaniem dostawcy:  
  
|Wzorzec|Zachowanie|  
|-------------|--------------|  
|wartość zerowa ma wartość NULL|Zwraca `true`.|  
|TRAKTOWANIe (null jako EntityType) ma wartość NULL|Zwraca `true`.|  
|TRAKTOWANIe (null jako ComplexType) ma wartość NULL|Zgłasza błąd.|  
|TRAKTOWANIe (null AS RowType) ma wartość NULL|Zgłasza błąd.|  
|Obiekt EntityType ma wartość NULL|Zwraca `true` lub `false`.|  
|ComplexType ma wartość NULL|Zgłasza błąd.|  
|RowType ma wartość NULL|Zgłasza błąd.|  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] używa operatora IS NOT NULL, aby określić, czy wyrażenie zapytania nie ma wartości null. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
