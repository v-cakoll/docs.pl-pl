---
title: Nawigacja (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 09128a367a02e1f9b206a9cc068987166c76381b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319542"
---
# <a name="navigate-entity-sql"></a>Nawigacja (Entity SQL)

Nawiguje nad relacją ustanowioną między jednostkami.

## <a name="syntax"></a>Składnia

```sql
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a>Argumenty

`instance-expression` wystąpienie jednostki.

`relationship-type` nazwa typu relacji z pliku koncepcyjnego języka definicji schematu (CSDL). @No__t-0 jest kwalifikowana jako \<namespace >. \<relationship type name >.

`to` koniec relacji.

`from` początek relacji.

## <a name="return-value"></a>Wartość zwracana

Jeśli Kardynalność do końca wynosi 1, wartość zwracana będzie `Ref<T>`. Jeśli Kardynalność do końca to n, wartość zwracana będzie `Collection<Ref<T>>`.

## <a name="remarks"></a>Uwagi

Relacje to konstrukcje pierwszej klasy w Entity Data Model (EDM). Relacje można ustanawiać między dwoma lub większą liczbą typów jednostek, a użytkownicy mogą przechodzić przez relację od jednego końca (jednostki) do innej. `from` i `to` są warunkowo opcjonalne, gdy w ramach rozpoznawania nazw nie występuje niejednoznaczność.

NAWIGOWANIe jest prawidłowe w miejscu i O i C.

Ogólny formularz konstrukcji nawigacyjnej jest następujący:

Przejdź do (`instance-expression`, `relationship-type`, [`to-end` [, `from-end`]])

Na przykład:

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

Gdzie OrderCustomer jest `relationship`, a klient i zamówienie to `to-end` (klient) i `from-end` (kolejność) relacji. Jeśli OrderCustomer była relacją n:1, typ wyniku wyrażenia nawigacji to ref @ no__t-0Customer >.

Prostszy formularz tego wyrażenia jest następujący:

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

Podobnie w przypadku zapytania w następującej postaci wyrażenie nawigacji spowoduje utworzenie kolekcji < ref @ no__t-0Order > >.

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

Wyrażenie wystąpienia musi być typu jednostki/odwołania.

## <a name="example"></a>Przykład

Poniższe zapytanie Entity SQL używa operatora nawigacji, aby nawigować przez relację między typami jednostek Address i SalesOrderHeader. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:

1. Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).

2. Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:

 [!code-sql[DP EntityServices Concepts#NAVIGATE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#navigate)]

## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Instrukcje: nawigowanie po relacjach za pomocą operatora nawigacji](navigate-entity-sql.md)
