---
title: OD (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: 36e3059869ed048bd7c5294c4f5f5407288610b2
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489943"
---
# <a name="from-entity-sql"></a>OD (jednostka SQL)
Określa kolekcję używane w [wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
FROM expression [ ,...n ] as C  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne wyrażenie prawidłowe zapytanie, które daje kolekcję do użycia jako źródło w `SELECT` instrukcji.  
  
## <a name="remarks"></a>Uwagi  
 A `FROM` klauzula jest rozdzielaną przecinkami listę co najmniej jeden `FROM` elementów w klauzuli. `FROM` Klauzuli może służyć do określania jednego lub kilku źródeł dla `SELECT` instrukcji. Najprostsza forma `FROM` klauzula jest wyrażenie jednego zapytania, które identyfikuje kolekcję i alias używany jako źródło w `SELECT` instrukcji, jak pokazano w poniższym przykładzie:  
  
 `FROM C as c`  
  
## <a name="from-clause-items"></a>Z elementów — klauzula  
 Każdy `FROM` element klauzuli odwołuje się do kolekcji źródłowej, w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje następujące klasy `FROM` elementy klauzuli: proste `FROM` elementy klauzuli `JOIN FROM` elementy klauzuli i `APPLY FROM` elementów w klauzuli. Każda z tych `FROM` elementy klauzula jest opisany bardziej szczegółowo w poniższych sekcjach.  
  
### <a name="simple-from-clause-item"></a>Prosty element klauzuli FROM  
 Najprostsze `FROM` element klauzuli jest pojedyncze wyrażenie określające kolekcji i alias. Wyrażenie można po prostu zestaw jednostek lub podzapytania lub innego wyrażenia, który jest typem kolekcji. Oto przykład:  
  
```  
LOB.Customers as c  
```  
  
 Specyfikacja aliasu jest opcjonalne. Alternatywne specyfikacji powyżej element klauzuli from może być następująca:  
  
```  
LOB.Customers  
```  
  
 Jeśli brak aliasu jest określony, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] spróbuje go wygenerować alias oparte na wyrażeniu kolekcji.  
  
### <a name="join-from-clause-item"></a>Dołącz element klauzuli FROM  
 A `JOIN FROM` element klauzuli reprezentuje sprzężenia między dwoma `FROM` elementów w klauzuli. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Obsługa wielu sprzężeń wewnętrznych, po lewej stronie i prawe sprzężenia zewnętrzne, filtrami czasowymi i klauzule full outer JOIN. Wszystkie te sprzężeń są obsługiwane w podobny sposób, że są one obsługiwane w języku Transact-SQL. Tak jak w języku Transact-SQL, dwa `FROM` klauzuli elementy zaangażowany w `JOIN` muszą być niezależne. Oznacza to nie może zostać skorelowane. A `CROSS APPLY` lub `OUTER APPLY` może służyć w tych przypadkach.  
  
#### <a name="cross-joins"></a>Sprzężenia krzyżowe  
 A `CROSS JOIN` zapytania wyrażenie powoduje formułuje iloczyn kartezjański dwie kolekcje, jak pokazano w poniższym przykładzie:  
  
 `FROM C AS c CROSS JOIN D as d`  
  
#### <a name="inner-joins"></a>Sprzężenia wewnętrzne  
 `INNER JOIN` Tworzy ograniczone formułuje iloczyn kartezjański dwie kolekcje, jak pokazano w poniższym przykładzie:  
  
 `FROM C AS c [INNER] JOIN D AS d ON e`  
  
 Poprzednie wyrażenie zapytania przetwarza kombinacji każdy element kolekcji po lewej stronie porównywane każdy element kolekcji o tym, gdzie po prawej stronie `ON` warunek jest prawdziwy. Jeśli nie `ON` jest określony warunek, `INNER JOIN` jest degenerowana do `CROSS JOIN`.  
  
#### <a name="left-outer-joins-and-right-outer-joins"></a>LEFT lewych sprzężeń zewnętrznych i prawe sprzężenia zewnętrzne  
 `OUTER JOIN` Zapytania wyrażenie powoduje ograniczone formułuje iloczyn kartezjański dwie kolekcje, jak pokazano w poniższym przykładzie:  
  
 `FROM C AS c LEFT OUTER JOIN D AS d ON e`  
  
 Poprzednie wyrażenie zapytania przetwarza kombinacji każdy element kolekcji po lewej stronie porównywane każdy element kolekcji o tym, gdzie po prawej stronie `ON` warunek jest prawdziwy. Jeśli `ON` warunek jest fałszywy, wyrażenie nadal przetwarza jedno wystąpienie elementu po lewej stronie porównywane elementu po prawej stronie przy użyciu wartość null.  
  
 A `RIGHT OUTER JOIN` mogą być wyrażone w podobny sposób.  
  
#### <a name="full-outer-joins"></a>Sprzężenia pełne zewnętrzne  
 Jawnie `FULL OUTER JOIN` tworzy ograniczone formułuje iloczyn kartezjański dwie kolekcje, jak pokazano w poniższym przykładzie:  
  
 `FROM C AS c FULL OUTER JOIN D AS d ON e`  
  
 Poprzednie wyrażenie zapytania przetwarza kombinacji każdy element kolekcji po lewej stronie porównywane każdy element kolekcji o tym, gdzie po prawej stronie `ON` warunek jest prawdziwy. Jeśli `ON` warunek jest fałszywy, wyrażenie nadal przetwarza jedno wystąpienie elementu po lewej stronie porównywane elementu po prawej stronie przy użyciu wartość null. Przetwarza jedno wystąpienie elementu po prawej stronie porównywane elementu po lewej stronie, za pomocą wartość null.  
  
> [!NOTE]
>  Aby zachować zgodność z SQL-92 w języku Transact-SQL — słowo kluczowe zewnętrzne jest opcjonalne. W związku z tym `LEFT JOIN`, `RIGHT JOIN`, i `FULL JOIN` są synonimy `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, i `FULL OUTER JOIN`.  
  
### <a name="apply-clause-item"></a>Zastosuj element klauzuli  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje dwa rodzaje z `APPLY`: `CROSS APPLY` i `OUTER APPLY`.  
  
 A `CROSS APPLY` generuje unikatowy parowanie każdego elementu kolekcji po lewej stronie, z elementem kolekcji utworzone przez obliczenie wyrażenia po prawej stronie. Za pomocą `CROSS APPLY`, wyrażenie po prawej stronie jest funkcjonalnie zależny od elementu po lewej stronie, jak pokazano w poniższym przykładzie skojarzonej kolekcji:  
  
 `SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`  
  
 Zachowanie `CROSS APPLY` jest podobna do listy dołączania. Jeśli po prawej stronie wyrażenie ma pustą kolekcję, `CROSS APPLY` tworzy nie skojarzenie tego wystąpienia elementu po lewej stronie.  
  
 `OUTER APPLY` Przypomina `CROSS APPLY`, z wyjątkiem parowanie nadal jest generowany, nawet wtedy, gdy po prawej stronie wyrażenie ma pustą kolekcję. Oto przykład `OUTER APPLY`:  
  
 `SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`  
  
> [!NOTE]
>  W odróżnieniu od w języku Transact-SQL, nie ma potrzeby kroku jawne unnest w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
> [!NOTE]
>  `CROSS` i `OUTER APPLY` operatory zostały wprowadzone w [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)]. W niektórych przypadkach potoku zapytania może powodować generowanie języka Transact-SQL, który zawiera `CROSS APPLY` i/lub `OUTER APPLY` operatorów. Ponieważ niektórzy dostawcy wewnętrznej bazy danych, w tym wersje programu SQL Server starszych niż [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], nie obsługuje tych operatorów, takich zapytań nie można wykonać na tych dostawców wewnętrznej bazy danych.  
>   
>  Niektóre typowe scenariusze, które mogą prowadzić do występowania `CROSS APPLY` i/lub `OUTER APPLY` operatory w zapytaniu dane wyjściowe są następujące: skorelowane podzapytanie za pomocą stronicowania; AnyElement za pośrednictwem skorelowane podzapytanie lub kolekcję produkowane przez nawigacji; LINQ zapytania używające grupowanie metod, które akceptują selektor elementu; zapytanie, w którym `CROSS APPLY` lub `OUTER APPLY` są jawnie określone, zapytania, które zawiera `DEREF` skonstruować za pośrednictwem `REF` konstruowania.  
  
## <a name="multiple-collections-in-the-from-clause"></a>Wieloma kolekcjami w FROM — klauzula  
 `FROM` Klauzula może zawierać więcej niż jedną kolekcję, oddzielonych przecinkami. W takich przypadkach kolekcje są uznawane za mają zostać połączone ze sobą. Należy traktować je jako sposób n sprzężenia KRZYŻOWEGO.  
  
 W poniższym przykładzie `C` i `D` są kolekcjami niezależne, ale `c.Names` jest zależny od `C`.  
  
```  
FROM C AS c, D AS d, c.Names AS e  
```  
  
 Poprzedni przykład jest logicznie równoważne do poniższego przykładu:  
  
 `FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`  
  
## <a name="left-correlation"></a>Lewa korelacja  
 Elementy w `FROM` klauzuli mogą odwoływać się do elementów określone w klauzulach wcześniej. W poniższym przykładzie `C` i `D` są kolekcjami niezależne, ale `c.Names` jest zależny od `C`:  
  
```  
from C as c, D as d, c.Names as e  
```  
  
 To jest logicznie równoważne:  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
## <a name="semantics"></a>Semantyka  
 Logicznie kolekcji w `FROM` klauzuli będą traktowani jako część `n`— sprzężenie sposób krzyżowe (z wyjątkiem w przypadku 1-sposób cross join). Aliasy w `FROM` klauzuli są przetwarzane od lewej do prawej i są dodawane do bieżącego zakresu do późniejszego wykorzystania. `FROM` Klauzuli założono, że generuje multiset wierszy. Będzie istniało jedno pole dla każdego elementu w `FROM` klauzula, która reprezentuje pojedynczy element z tego elementu kolekcji.  
  
 `FROM` Klauzuli logicznie tworzy zestaw wielokrotny wiersze typu wiersza (c, d, e) gdzie pola c, d i e są rozpatrywane typu elementu `C`, `D`, i `c.Names`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wprowadzono alias dla każdego prostej `FROM` element klauzuli w zakresie. Na przykład w następujących poleceń w klauzuli fragment, nazwy wprowadzone do zakresu są c, d i e.  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
 W [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (w przeciwieństwie do języka Transact-SQL) `FROM` klauzuli tylko wprowadza aliasów do zakresu. Wszystkie odwołania do tych kolekcji kolumn (właściwości) musi być kwalifikowana z aliasem.  
  
## <a name="pulling-up-keys-from-nested-queries"></a>Ściąganie klucze z zapytań zagnieżdżonej  
 Niektórych rodzajów zapytań, które wymagają ściąganie klucze z zapytań zagnieżdżonej nie są obsługiwane. Na przykład następujące zapytanie jest prawidłowy:  
  
```  
select c.Orders from Customers as c   
```  
  
 Jednakże następujące zapytanie jest nieprawidłowe, ponieważ zapytanie zagnieżdżone nie ma żadnych kluczy:  
  
```  
select {1} from {2, 3}  
```  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Wyrażenia zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
- [Typy strukturalne dopuszczające wartości Null](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
