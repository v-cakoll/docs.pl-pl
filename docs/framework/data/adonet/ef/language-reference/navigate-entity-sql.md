---
title: Przejdź (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 6ce88cecf210d8b3cf541fe7e870e19a59e344ec
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307333"
---
# <a name="navigate-entity-sql"></a>Przejdź (jednostka SQL)

Przechodzi przez relację między jednostkami.

## <a name="syntax"></a>Składnia

```
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a>Argumenty

`instance-expression` Wystąpienie jednostki.

`relationship-type` Nazwa typu relacji z pliku (CSDL) języka definicji schematu koncepcyjnego. `relationship-type` Jest kwalifikowana jako \<przestrzeni nazw >.\< Nazwa typu relacji >.

`to` Zakończenie relacji.

`from` Początek relacji.

## <a name="return-value"></a>Wartość zwracana

Jeśli kardynalność do końca wynosi 1, zwracaną wartością będzie `Ref<T>`. Jeśli kardynalność do końca n, zwracaną wartością będzie `Collection<Ref<T>>`.

## <a name="remarks"></a>Uwagi

Relacje są konstrukcje najwyższej jakości w Entity Data Model (EDM). Można ustanowić relacji między co najmniej dwóch typów jednostek, a użytkownicy mogą uzyskać dostęp za pośrednictwem relacji z jednej strony (jednostka) do innego. `from` i `to` są warunkowo opcjonalne, jeśli nie ma żadnych niejednoznaczności w rozpoznawanie w relacji.

Nawigacja jest prawidłowa w przestrzeni O i C.

Ogólna postać konstrukcję nawigacji jest następująca:

Przejdź (`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ]])

Na przykład:

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

Gdzie jest OrderCustomer `relationship`, i klienta i zamówienia są `to-end` (klienta) i `from-end` (zamówienie) relacji. Jeśli OrderCustomer została relacji n: 1, a typ wyniku wyrażenie navigate jest Ref\<klienta >.

Prostsze formularza to wyrażenie jest następująca:

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

Podobnie w zapytaniu o następującej postaci wyrażenie navigate dałby w efekcie kolekcji < Ref\<kolejności >>.

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

Wyrażenia wystąpienia musi być typem jednostki/ref.

## <a name="example"></a>Przykład

Następujące zapytanie SQL jednostki używa operatora przejdź do nawigacji w relacji między adres i SalesOrderHeader typów jednostek. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:

1. Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).

2. Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:

 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]

## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Instrukcje: Przejdź relacjach za pomocą operatora nawigowania](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)
