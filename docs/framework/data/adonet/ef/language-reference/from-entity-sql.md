---
title: OD (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: 3da9c9a2864219836c8aff6e0dc9e98656ba673f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043711"
---
# <a name="from-entity-sql"></a>OD (Entity SQL)
Określa kolekcję używaną w instrukcjach [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) .

## <a name="syntax"></a>Składnia

```
FROM expression [ ,...n ] as C
```

## <a name="arguments"></a>Argumenty

`expression` \
Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję do użycia jako źródło w `SELECT` instrukcji.

## <a name="remarks"></a>Uwagi

Klauzula jest rozdzielaną przecinkami listą `FROM` elementów klauzuli. `FROM` Klauzula może służyć do określenia co najmniej jednego źródła `SELECT` dla instrukcji. `FROM` Najprostsza forma `FROM` klauzuli to pojedyncze wyrażenie zapytania, które identyfikuje kolekcję i alias używany jako źródło `SELECT` w instrukcji, jak pokazano w następującym przykładzie:

`FROM C as c`

## <a name="from-clause-items"></a>Elementy klauzuli FROM

Każdy `FROM` element klauzuli odwołuje się do kolekcji źródłowej [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w zapytaniu. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje następujące klasy `FROM` elementów klauzuli: proste `FROM` elementy klauzuli, `JOIN FROM` elementy klauzuli i `APPLY FROM` klauzule. Każdy z tych `FROM` elementów klauzuli został opisany bardziej szczegółowo w poniższych sekcjach.

### <a name="simple-from-clause-item"></a>Prosty element klauzuli FROM

Element klauzuli `FROM` najprostsza jest pojedynczym wyrażeniem, które identyfikuje kolekcję i alias. Wyrażenie może po prostu być zestawem jednostek lub podzapytaniem albo innym wyrażeniem, które jest typem kolekcji. Oto przykład:

```sql
LOB.Customers as c
```

Specyfikacja aliasu jest opcjonalna. Alternatywna Specyfikacja powyższego elementu klauzuli FROM może być następująca:

```sql
LOB.Customers
```

Jeśli alias nie zostanie określony, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] program podejmie próbę wygenerowania aliasu na podstawie wyrażenia kolekcji.

### <a name="join-from-clause-item"></a>Element klauzuli JOIN

Element klauzuli reprezentuje sprzężenie między dwoma `FROM` elementami klauzuli. `JOIN FROM` [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje sprzężenia krzyżowe, sprzężenia wewnętrzne, sprzężenia zewnętrzne Left i Right oraz pełne sprzężenia zewnętrzne. Wszystkie te sprzężenia są obsługiwane podobne do sposobu, w jaki są obsługiwane w języku Transact-SQL. Podobnie jak w języku Transact-SQL, `FROM` dwie klauzule `JOIN` muszą być niezależne. Oznacza to, że nie mogą być skorelowane. A `CROSS APPLY` lub`OUTER APPLY` może być używany w takich przypadkach.

#### <a name="cross-joins"></a>Sprzężenia krzyżowe

Wyrażenie `CROSS JOIN` zapytania generuje produkt kartezjańskiego dwóch kolekcji, jak pokazano w następującym przykładzie:

`FROM C AS c CROSS JOIN D as d`

#### <a name="inner-joins"></a>Sprzężenia wewnętrzne

`INNER JOIN` Tworzy ograniczony produkt kartezjańskiego dla dwóch kolekcji, jak pokazano w następującym przykładzie:

`FROM C AS c [INNER] JOIN D AS d ON e`

Poprzednie wyrażenie zapytania przetwarza kombinację każdego elementu kolekcji po lewej stronie dla każdego elementu kolekcji po prawej stronie, gdzie `ON` warunek ma wartość true. Jeśli warunek `ON` nie zostanie określony `INNER JOIN` , degeneruje do `CROSS JOIN`.

#### <a name="left-outer-joins-and-right-outer-joins"></a>Lewe sprzężenia zewnętrzne i prawe sprzężenia zewnętrzne

Wyrażenie `OUTER JOIN` zapytania tworzy ograniczony produkt kartezjańskiego dla dwóch kolekcji, jak pokazano w następującym przykładzie:

`FROM C AS c LEFT OUTER JOIN D AS d ON e`

Poprzednie wyrażenie zapytania przetwarza kombinację każdego elementu kolekcji po lewej stronie dla każdego elementu kolekcji po prawej stronie, gdzie `ON` warunek ma wartość true. `ON` Jeśli warunek ma wartość false, wyrażenie nadal przetwarza pojedyncze wystąpienie elementu w lewej parze z elementem po prawej stronie, z wartością null.

A `RIGHT OUTER JOIN` może być wyrażona w podobny sposób.

#### <a name="full-outer-joins"></a>Pełne sprzężenia zewnętrzne

Jawne `FULL OUTER JOIN` tworzy ograniczony produkt kartezjańskiego dla dwóch kolekcji, jak pokazano w następującym przykładzie:

`FROM C AS c FULL OUTER JOIN D AS d ON e`

Poprzednie wyrażenie zapytania przetwarza kombinację każdego elementu kolekcji po lewej stronie dla każdego elementu kolekcji po prawej stronie, gdzie `ON` warunek ma wartość true. `ON` Jeśli warunek ma wartość false, wyrażenie nadal przetwarza jedno wystąpienie elementu w lewej parze względem elementu po prawej stronie, z wartością null. Przetwarza także jedno wystąpienie elementu w prawej parze względem elementu po lewej stronie, z wartością null.

> [!NOTE]
> Aby zachować zgodność z SQL-92, w języku Transact-SQL słowo kluczowe OUTER jest opcjonalne. `FULL JOIN` `RIGHT OUTER JOIN` `LEFT OUTER JOIN` `FULL OUTER JOIN`W związku z tym,, i są synonimami dla,, i. `LEFT JOIN` `RIGHT JOIN`

### <a name="apply-clause-item"></a>APPLY — element klauzuli

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje dwa rodzaje `APPLY`: `CROSS APPLY` i `OUTER APPLY`.

A `CROSS APPLY` tworzy unikatową parowanie każdego elementu kolekcji po lewej stronie z elementem kolekcji utworzonej przez obliczenie wyrażenia po prawej stronie. `CROSS APPLY`Wyrażenie po prawej stronie jest funkcjonalnie zależne od elementu po lewej stronie, jak pokazano w następującym przykładzie skojarzonej kolekcji:

`SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`

Zachowanie `CROSS APPLY` jest podobne do listy sprzężenia. Jeśli wyrażenie po prawej stronie zwraca pustą kolekcję, `CROSS APPLY` nie tworzy żadnych par dla tego wystąpienia elementu po lewej stronie.

`OUTER APPLY` Przypomina`CROSS APPLY`, z wyjątkiem tego, że parowanie jest nadal generowane nawet wtedy, gdy wyrażenie po prawej stronie oblicza pustą kolekcję. Oto przykład `OUTER APPLY`:

`SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`

> [!NOTE]
> W przeciwieństwie do języka Transact-SQL nie ma potrzeby jawnego kroku unnesting w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].

> [!NOTE]
> `CROSS`Operatory `OUTER APPLY` i zostały wprowadzone w SQL Server 2005. W niektórych przypadkach potok zapytania może generować Transact-SQL, które zawierają `CROSS APPLY` operatory i/lub. `OUTER APPLY` Ponieważ niektórzy dostawcy zaplecza, w tym wersje SQL Server wcześniejsze niż SQL Server 2005, nie obsługują tych operatorów, takie zapytania nie mogą być wykonywane w tych dostawcach zaplecza.
>
> Niektóre typowe scenariusze, które mogą prowadzić do obecności `CROSS APPLY` i/lub `OUTER APPLY` operatorów w zapytaniu wyjściowym są następujące: skorelowane podzapytanie ze stronicowaniem; AnyElement za pomocą skorelowanego podzapytania lub kolekcji utworzonej przez nawigację; Zapytania LINQ używające metod grupowania, które akceptują selektor elementu; zapytanie, które `CROSS APPLY` jest jawnie określone `OUTER APPLY` lub jest zapytania, które `REF` ma `DEREF` konstrukcję w konstrukcji.

## <a name="multiple-collections-in-the-from-clause"></a>Wiele kolekcji w klauzuli FROM

`FROM` Klauzula może zawierać więcej niż jedną kolekcję oddzieloną przecinkami. W takich przypadkach przyjmuje się, że kolekcje są połączone ze sobą. Zastanów się nad nimi jako SPRZĘŻENIem KRZYŻowym.

W poniższym przykładzie `C` i `D` są niezależnymi kolekcjami `C`, `c.Names` ale jest zależne od.

```sql
FROM C AS c, D AS d, c.Names AS e
```

Poprzedni przykład jest logicznym odpowiednikiem poniższego przykładu:

`FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`

## <a name="left-correlation"></a>Lewa korelacja
 Elementy w `FROM` klauzuli mogą odwoływać się do elementów określonych w klauzulach wcześniejszych. W poniższym przykładzie `C` i `D` są niezależnymi kolekcjami `C`, `c.Names` ale jest zależne od:

```sql
from C as c, D as d, c.Names as e
```

Jest to logicznie równoważne z:

```sql
from (C as c join D as d) cross apply c.Names as e
```

## <a name="semantics"></a>Semantyki

Logicznie kolekcje w `FROM` klauzuli są zakładane jako część `n`sprzężenia krzyżowego (z wyjątkiem w przypadku 1-kierunkowego sprzężenia krzyżowego). Aliasy w `FROM` klauzuli są przetwarzane od lewej do prawej i są dodawane do bieżącego zakresu w celu późniejszego odwołania. Przyjęto, `FROM` że klauzula tworzy zestaw wielokrotny wierszy. Dla każdego elementu w `FROM` klauzuli, który reprezentuje pojedynczy element z tego elementu kolekcji, będzie jedno pole.

Klauzula logicznie tworzy zestaw wielokrotny wierszy typu Row (c, d, e), gdzie pola c, d i e są zakładane jako `C`typ elementu, `D`, i `c.Names`. `FROM`

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]wprowadza alias dla każdego elementu prostej `FROM` klauzuli w zakresie. Na przykład, w poniższym fragmencie kodu klauzuli, nazwy wprowadzone do zakresu to c, d i e.

```sql
from (C as c join D as d) cross apply c.Names as e
```

W [!INCLUDE[esql](../../../../../../includes/esql-md.md)] programie (w przeciwieństwie do języka Transact- `FROM` SQL) klauzula wprowadza tylko aliasy do zakresu. Wszystkie odwołania do kolumn (właściwości) tych kolekcji muszą być kwalifikowane przy użyciu aliasu.

## <a name="pulling-up-keys-from-nested-queries"></a>Ściąganie kluczy z zagnieżdżonych zapytań

Niektóre typy zapytań, które wymagają ściągania kluczy z zapytania zagnieżdżonego, nie są obsługiwane. Na przykład następujące zapytanie jest prawidłowe:

```sql
select c.Orders from Customers as c
```

Jednak następujące zapytanie jest nieprawidłowe, ponieważ zapytanie zagnieżdżone nie ma żadnych kluczy:

```sql
select {1} from {2, 3}
```

## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Wyrażenia zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
- [Typy strukturalne dopuszczające wartości Null](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
