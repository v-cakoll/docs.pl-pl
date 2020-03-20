---
title: ISNULL (Jednostka SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: b3fc2484e80b637ed5841375985f7bae476bbbf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150203"
---
# <a name="isnull-entity-sql"></a>ISNULL (Jednostka SQL)
Określa, czy wyrażenie kwerendy ma wartość null.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie kwerendy. Nie może być kolekcją, mają członków kolekcji lub typu rekordu z właściwościami typu kolekcji.  
  
 NOT  
 Neguje EDM. Wynik logiczny wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`jeśli `expression` zwraca wartość null; w `false`przeciwnym razie , .  
  
## <a name="remarks"></a>Uwagi  
 Służy `IS NULL` do określenia, czy element sprzężenia zewnętrznego ma wartość null:  
  
```sql  
select c
      from LOB.Customers as c left outer join LOB.Orders as o
                              on c.ID = o.CustomerID
      where o is not null and o.OrderQuantity = @x  
```  
  
 Służy `IS NULL` do określenia, czy element członkowski ma rzeczywistą wartość:  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 W poniższej tabeli `IS NULL` przedstawiono zachowanie ponad niektóre wzorce. Wszystkie wyjątki są generowane od strony klienta, zanim dostawca zostanie wywołany:  
  
|Wzorce|Zachowanie|  
|-------------|--------------|  
|wartość null jest zerowa|Zwraca wartość `true`.|  
|TREAT (null AS EntityType) MA WARTOŚĆ NULL|Zwraca wartość `true`.|  
|TREAT (null AS ComplexType) MA WARTOŚĆ NULL|Zgłasza błąd.|  
|TREAT (null AS RowType) MA WARTOŚĆ NULL|Zgłasza błąd.|  
|Typ encji ma wartość NULL|Zwraca `true` `false`lub .|  
|Typ kompleksu JEST NULL|Zgłasza błąd.|  
|Typ wiersza ma wartość null|Zgłasza błąd.|  
  
## <a name="example"></a>Przykład  
 Następująca [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kwerenda używa operatora IS NOT NULL do określenia, czy wyrażenie kwerendy nie ma wartości null. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:  
  
1. Postępuj zgodnie z procedurą [w : Jak: Wykonać kwerendę, która zwraca wyniki structuraltype](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Przekaż następującą kwerendę jako `ExecuteStructuralTypeQuery` argument do metody:  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
