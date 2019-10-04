---
title: OD (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: 2334a30009d6bef9544d2ca1e0ab923a7441d6f2
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833818"
---
# <a name="from-entity-sql"></a>OD (Entity SQL)
Określa kolekcję używaną w instrukcjach [SELECT](select-entity-sql.md) .

## <a name="syntax"></a>Składnia

```sql
FROM expression [ ,...n ] AS C
```

## <a name="arguments"></a>Argumenty

`expression` \
Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję do użycia jako źródło w instrukcji `SELECT`.

## <a name="remarks"></a>Uwagi

Klauzula `FROM` jest rozdzielaną przecinkami listą elementów klauzuli `FROM`. Klauzula `FROM` może służyć do określenia jednego lub większej liczby źródeł dla instrukcji `SELECT`. Najprostsza forma klauzuli `FROM` to pojedyncze wyrażenie zapytania, które identyfikuje kolekcję i alias używany jako źródło w instrukcji `SELECT`, jak pokazano w następującym przykładzie:

`FROM C as c`

## <a name="from-clause-items"></a>Elementy klauzuli FROM

Każdy element klauzuli `FROM` odwołuje się do kolekcji źródłowej w zapytaniu [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje następujące klasy elementów klauzuli `FROM`: proste elementy klauzuli `FROM`, elementy klauzuli `JOIN FROM` i elementy klauzul `APPLY FROM`. Każdy z tych elementów klauzuli `FROM` został opisany bardziej szczegółowo w poniższych sekcjach.

### <a name="simple-from-clause-item"></a>Prosty element klauzuli FROM

Najprostszym elementem klauzuli `FROM` jest pojedyncze wyrażenie, które identyfikuje kolekcję i alias. Wyrażenie może po prostu być zestawem jednostek lub podzapytaniem albo innym wyrażeniem, które jest typem kolekcji. Oto przykład:

```sql
LOB.Customers as c
```

Specyfikacja aliasu jest opcjonalna. Alternatywna Specyfikacja powyższego elementu klauzuli FROM może być następująca:

```sql
LOB.Customers
```

Jeśli alias nie zostanie określony, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje wygenerować alias na podstawie wyrażenia kolekcji.

### <a name="join-from-clause-item"></a>Element klauzuli JOIN

Element klauzuli `JOIN FROM` reprezentuje sprzężenie między dwoma elementami klauzuli `FROM`. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje sprzężenia krzyżowe, sprzężenia wewnętrzne, sprzężenia zewnętrzne w lewo i w prawo oraz pełne sprzężenia zewnętrzne. Wszystkie te sprzężenia są obsługiwane podobne do sposobu, w jaki są obsługiwane w języku Transact-SQL. Podobnie jak w języku Transact-SQL, dwa elementy klauzuli `FROM` w `JOIN` muszą być niezależne. Oznacza to, że nie mogą być skorelowane. W takich przypadkach można użyć `CROSS APPLY` lub `OUTER APPLY`.

#### <a name="cross-joins"></a>Sprzężenia krzyżowe

Wyrażenie zapytania `CROSS JOIN` generuje produkt kartezjańskiego dwóch kolekcji, jak pokazano w następującym przykładzie:

`FROM C AS c CROSS JOIN D as d`

#### <a name="inner-joins"></a>Sprzężenia wewnętrzne

@No__t-0 tworzy ograniczony produkt kartezjańskiego dla dwóch kolekcji, jak pokazano w następującym przykładzie:

`FROM C AS c [INNER] JOIN D AS d ON e`

Poprzednie wyrażenie zapytania przetwarza kombinację każdego elementu kolekcji po lewej stronie dla każdego elementu kolekcji po prawej stronie, gdzie warunek `ON` ma wartość true. Jeśli nie określono żadnego warunku `ON`, `INNER JOIN` degeneruje do `CROSS JOIN`.

#### <a name="left-outer-joins-and-right-outer-joins"></a>Lewe sprzężenia zewnętrzne i prawe sprzężenia zewnętrzne

Wyrażenie zapytania `OUTER JOIN` tworzy ograniczony produkt kartezjańskiego dla dwóch kolekcji, jak pokazano w następującym przykładzie:

`FROM C AS c LEFT OUTER JOIN D AS d ON e`

Poprzednie wyrażenie zapytania przetwarza kombinację każdego elementu kolekcji po lewej stronie dla każdego elementu kolekcji po prawej stronie, gdzie warunek `ON` ma wartość true. Jeśli warunek `ON` ma wartość false, wyrażenie nadal przetwarza pojedyncze wystąpienie elementu w lewej parze względem elementu po prawej stronie z wartością null.

@No__t-0 może być wyrażona w podobny sposób.

#### <a name="full-outer-joins"></a>Pełne sprzężenia zewnętrzne

Jawny `FULL OUTER JOIN` tworzy ograniczony produkt kartezjańskiego dla dwóch kolekcji, jak pokazano w następującym przykładzie:

`FROM C AS c FULL OUTER JOIN D AS d ON e`

Poprzednie wyrażenie zapytania przetwarza kombinację każdego elementu kolekcji po lewej stronie dla każdego elementu kolekcji po prawej stronie, gdzie warunek `ON` ma wartość true. Jeśli warunek `ON` ma wartość false, wyrażenie nadal przetwarza jedno wystąpienie elementu w lewej parze względem elementu po prawej stronie z wartością null. Przetwarza także jedno wystąpienie elementu w prawej parze względem elementu po lewej stronie, z wartością null.

> [!NOTE]
> Aby zachować zgodność z SQL-92, w języku Transact-SQL słowo kluczowe OUTER jest opcjonalne. W związku z tym `LEFT JOIN`, `RIGHT JOIN` i `FULL JOIN` są synonimami dla `LEFT OUTER JOIN`, `RIGHT OUTER JOIN` i `FULL OUTER JOIN`.

### <a name="apply-clause-item"></a>APPLY — element klauzuli

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje dwa rodzaje `APPLY`: `CROSS APPLY` i `OUTER APPLY`.

@No__t-0 generuje unikatową parowanie każdego elementu kolekcji po lewej stronie z elementem kolekcji utworzonej przez obliczenie wyrażenia po prawej stronie. W przypadku `CROSS APPLY` wyrażenie po prawej stronie jest funkcjonalnie zależne od elementu po lewej stronie, jak pokazano w następującym przykładzie skojarzonej kolekcji:

`SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`

Zachowanie `CROSS APPLY` jest podobne do listy sprzężenia. Jeśli wyrażenie po prawej stronie zwróci pustą kolekcję, `CROSS APPLY` nie tworzy par dla tego wystąpienia elementu po lewej stronie.

@No__t-0 przypomina `CROSS APPLY`, z wyjątkiem tego, że parowanie jest nadal generowane nawet wtedy, gdy wyrażenie po prawej stronie oblicza pustą kolekcję. Poniżej znajduje się przykład `OUTER APPLY`:

`SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`

> [!NOTE]
> W przeciwieństwie do języka Transact-SQL nie ma potrzeby jawnego kroku unnesting w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].

> [!NOTE]
> Operatory `CROSS` i `OUTER APPLY` zostały wprowadzone w SQL Server 2005. W niektórych przypadkach potok zapytania może generować Transact-SQL, który zawiera `CROSS APPLY` i/lub operatory `OUTER APPLY`. Ponieważ niektórzy dostawcy zaplecza, w tym wersje SQL Server wcześniejsze niż SQL Server 2005, nie obsługują tych operatorów, takie zapytania nie mogą być wykonywane w tych dostawcach zaplecza.
>
> Niektóre typowe scenariusze, które mogą prowadzić do obecności operatorów `CROSS APPLY` i/lub `OUTER APPLY` w zapytaniu wyjściowym są następujące: skorelowane podzapytanie ze stronicowaniem; AnyElement za pomocą skorelowanego podzapytania lub kolekcji utworzonej przez nawigację; Zapytania LINQ używające metod grupowania, które akceptują selektor elementu; zapytanie, w którym jawnie określono `CROSS APPLY` lub `OUTER APPLY`; zapytanie, które ma konstrukcję `DEREF` dla konstrukcji `REF`.

## <a name="multiple-collections-in-the-from-clause"></a>Wiele kolekcji w klauzuli FROM

Klauzula `FROM` może zawierać więcej niż jedną kolekcję rozdzieloną przecinkami. W takich przypadkach przyjmuje się, że kolekcje są połączone ze sobą. Zastanów się nad nimi jako SPRZĘŻENIem KRZYŻowym.

W poniższym przykładzie `C` i `D` są kolekcjami niezależnymi, ale `c.Names` zależy od `C`.

```sql
FROM C AS c, D AS d, c.Names AS e
```

Poprzedni przykład jest logicznym odpowiednikiem poniższego przykładu:

`FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`

## <a name="left-correlation"></a>Lewa korelacja
 Elementy w klauzuli `FROM` mogą odwoływać się do elementów określonych w klauzulach wcześniejszych. W poniższym przykładzie `C` i `D` są kolekcjami niezależnymi, ale `c.Names` zależy od `C`:

```sql
from C as c, D as d, c.Names as e
```

Jest to logicznie równoważne z:

```sql
from (C as c join D as d) cross apply c.Names as e
```

## <a name="semantics"></a>Semantyki

Logicznie kolekcje w klauzuli `FROM` są założono, że jest częścią @no__t -1 sprzężenia krzyżowego (z wyjątkiem w przypadku 1-kierunkowego sprzężenia krzyżowego). Aliasy w klauzuli `FROM` są przetwarzane od lewej do prawej i są dodawane do bieżącego zakresu w celu późniejszego odwołania. Przyjęto klauzulę `FROM`, aby utworzyć zestaw wielokrotny wierszy. Dla każdego elementu w klauzuli `FROM` będzie dostępne jedno pole, które reprezentuje pojedynczy element z tego elementu kolekcji.

Klauzula `FROM` logicznie tworzy zestaw wielokrotny wierszy typu Row (c, d, e), gdzie pola c, d i e są zakładane jako typ elementu `C`, `D` i `c.Names`.

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] wprowadza alias dla każdego prostego elementu klauzuli `FROM` w zakresie. Na przykład, w poniższym fragmencie kodu klauzuli, nazwy wprowadzone do zakresu to c, d i e.

```sql
from (C as c join D as d) cross apply c.Names as e
```

W [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (w przeciwieństwie do języka Transact-SQL) klauzula `FROM` wprowadza tylko aliasy do zakresu. Wszystkie odwołania do kolumn (właściwości) tych kolekcji muszą być kwalifikowane przy użyciu aliasu.

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

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Wyrażenia zapytania](query-expressions-entity-sql.md)
- [Typy strukturalne dopuszczające wartości Null](nullable-structured-types-entity-sql.md)
