---
title: Przejdź (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: c374261ad3702294f5720edb7881e21ba79d85bc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="navigate-entity-sql"></a>Przejdź (jednostka SQL)
Przechodzi przez relację między jednostkami.  
  
## <a name="syntax"></a>Składnia  
  
```  
navigate(instance-expresssion, [relationship-type], [to-end [, from-end] ])  
```  
  
## <a name="arguments"></a>Argumenty  
 `instance-expresssion`  
 Wystąpienie jednostki.  
  
 `relationship-type`  
 Nazwa typu relacji z pliku schematu koncepcyjnego definition language (CSDL). `relationship-type` Jest kwalifikowana jako \<przestrzeń nazw >.\< Nazwa typu relacji >.  
  
 `to`  
 Zakończenie relacji.  
  
 `from`  
 Początek relacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli kardynalność do końca wynosi 1, jest zwracana wartość `Ref<T>`. Jeśli kardynalność na koniec jest n, jest zwracana wartość `Collection<Ref<T>>`.  
  
## <a name="remarks"></a>Uwagi  
 Relacje są najwyższej jakości konstrukcje w [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM). Można utworzyć relacji między co najmniej dwa typy jednostek, a użytkownicy mogą uzyskać dostęp za pośrednictwem relacji z jednej strony (jednostka) do innego. `from` i `to` są warunkowo opcjonalny, gdy istnieje nie niejednoznaczności w rozpoznawania nazw w relacji.  
  
 Nawigacja jest prawidłowa w przestrzeni O i C.  
  
 Ogólny kształt konstrukcji nawigacji jest następujący:  
  
 Przejdź (`instance-expresssion`, `relationship-type`, [ `to-end` [, `from-end` ]])  
  
 Na przykład:  
  
```  
Select o.Id, navigate(o, OrderCustomer, Customer, Order)  
From LOB.Orders as o  
```  
  
 W przypadku OrderCustomer `relationship`, oraz klientów i kolejność są `to-end` (klienta) i `from-end` (kolejność) relacji. Jeśli OrderCustomer został relacji n: 1, a następnie typ wyniku wyrażenia Nawigacja jest Ref\<klienta >.  
  
 Prostsze formę to wyrażenie jest następujący:  
  
```  
Select o.Id, navigate(o, OrderCustomer)  
From LOB.Orders as o  
```  
  
 Podobnie, w kwerendzie mają następującą postać wyrażenia Nawigacja tworzy kolekcję < Ref\<kolejności >>.  
  
```  
Select c.Id, navigate(c, OrderCustomer, Order, Customer)  
From LOB.Customers as c  
```  
  
 Wyrażenia wystąpienia muszą być typu jednostki/ref.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki używa operatora przejdź do nawigacji w relacji między adres i SalesOrderHeader typów jednostek. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Porady: nawigowanie relacje z Przejdź — Operator](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)
