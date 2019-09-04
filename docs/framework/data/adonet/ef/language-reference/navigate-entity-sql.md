---
title: Nawigacja (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 2c6c2ae4c593da1d5fe8cdf3015eb0e31e4b12b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249935"
---
# <a name="navigate-entity-sql"></a>Nawigacja (Entity SQL)

Nawiguje nad relacją ustanowioną między jednostkami.

## <a name="syntax"></a>Składnia

```
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a>Argumenty

`instance-expression`Wystąpienie jednostki.

`relationship-type`Nazwa typu relacji z pliku języka definicji schematu koncepcyjnego (CSDL). Jest kwalifikowana jako \<przestrzeń nazw >.\< `relationship-type` Nazwa typu relacji >.

`to`Koniec relacji.

`from`Początek relacji.

## <a name="return-value"></a>Wartość zwracana

Jeśli Kardynalność do końca wynosi 1, wartość zwracana będzie `Ref<T>`. Jeśli Kardynalność do końca to n, wartość zwracana będzie `Collection<Ref<T>>`.

## <a name="remarks"></a>Uwagi

Relacje to konstrukcje pierwszej klasy w Entity Data Model (EDM). Relacje można ustanawiać między dwoma lub większą liczbą typów jednostek, a użytkownicy mogą przechodzić przez relację od jednego końca (jednostki) do innej. `from`i `to` są warunkowo opcjonalne, gdy w relacji nie ma niejednoznaczności rozpoznawania nazw.

NAWIGOWANIe jest prawidłowe w miejscu i O i C.

Ogólny formularz konstrukcji nawigacyjnej jest następujący:

Nawiguj (`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ]])

Na przykład:

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

Gdzie OrderCustomer to `relationship`, a klient i zamówienie `to-end` to (klient) i `from-end` (zamówienie) relacji. Jeśli OrderCustomer była relacją n:1, typ wyniku wyrażenia nawigacji to ref\<Customer >.

Prostszy formularz tego wyrażenia jest następujący:

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

Podobnie w przypadku zapytania w następującej postaci wyrażenie nawigacji spowoduje utworzenie kolekcji < kolejności ref\<> >.

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

Wyrażenie wystąpienia musi być typu jednostki/odwołania.

## <a name="example"></a>Przykład

Poniższe zapytanie Entity SQL używa operatora nawigacji, aby nawigować przez relację między typami jednostek Address i SalesOrderHeader. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:

1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.

2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:

 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]

## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Instrukcje: Nawigowanie po relacjach za pomocą operatora nawigacji](navigate-entity-sql.md)
