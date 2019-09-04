---
title: Góra (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 8b55519b7f95deb6463af4c0a6a2a53975e5b5a2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248972"
---
# <a name="top-entity-sql"></a>Góra (Entity SQL)

Klauzula SELECT może mieć opcjonalną podklauzulę TOP, która znajduje się po opcjonalnym modyfikatorze ALL/DISTINCT. Podklauzula TOP określa, że tylko pierwszy zestaw wierszy zostanie zwrócony z wyniku zapytania.

## <a name="syntax"></a>Składnia

```
[ TOP (n) ]
```

## <a name="arguments"></a>Argumenty

`n`Wyrażenie liczbowe określające liczbę wierszy, które mają zostać zwrócone. `n`może być pojedynczym literałem numerycznym lub pojedynczym parametrem.

## <a name="remarks"></a>Uwagi

Wyrażenie TOP musi być pojedynczym literałem numerycznym lub pojedynczym parametrem. W przypadku użycia literału stałego typ literału musi być niejawnie awansowany do modelu EDM. Int64 (Byte, Int16, Int32 lub Int64 lub dowolnego typu dostawcy, który jest mapowany do typu, który jest promocyjny do modelu EDM. Int64), a jego wartość musi być większa lub równa zero. W przeciwnym razie zostanie wygenerowany wyjątek. Jeśli parametr jest używany jako wyrażenie, typ parametru musi również być niejawnie awansowany do EDM. Int64, ale nie będzie można zweryfikować rzeczywistej wartości parametru podczas kompilacji, ponieważ wartości parametrów są opóźnione.

Poniżej znajduje się przykład stałego wyrażenia TOP:

```sql
select distinct top(10) c.a1, c.a2 from T as a
```

Poniżej znajduje się przykład sparametryzowanego wyrażenia TOP:

```sql
select distinct top(@topParam) c.a1, c.a2 from T as a
```

Góra nie jest deterministyczna, chyba że zapytanie jest sortowane. Jeśli potrzebujesz deterministycznych wyników, użyj podklauzul [Skip](skip-entity-sql.md) i [Limit](limit-entity-sql.md) w klauzuli [order by](order-by-entity-sql.md) . Wartość TOP i SKIP/LIMIT wykluczają się wzajemnie.

## <a name="example"></a>Przykład

Poniższe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa góry, aby określić pierwszy wiersz, który ma zostać zwrócony z wyniku zapytania. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:

1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.

2. Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:

    [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]

## <a name="see-also"></a>Zobacz także

- [SELECT](select-entity-sql.md)
- [SKIP](skip-entity-sql.md)
- [LIMIT](limit-entity-sql.md)
- [ORDER BY](order-by-entity-sql.md)
- [Odwołanie do jednostki SQL](entity-sql-reference.md)
