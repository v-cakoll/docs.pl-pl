---
title: Z (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 51f65896cb54a65756558d846e1fc940de5b9470
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="from-entity-sql"></a>Z (jednostka SQL)
Określa kolekcję używane w [wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) instrukcje.  
  
## <a name="syntax"></a>Składnia  
  
```  
FROM expression [ ,...n ] as C  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne wyrażenie prawidłowe zapytanie zwracające kolekcji do użycia jako źródło w `SELECT` instrukcji.  
  
## <a name="remarks"></a>Uwagi  
 A `FROM` klauzula jest rozdzielaną przecinkami listę co najmniej jeden `FROM` klauzuli elementów. `FROM` Klauzuli może służyć do określenia co najmniej jedno źródło dla `SELECT` instrukcji. Najprostsza forma `FROM` klauzula jest wyrażenie pojedynczego zapytania, które identyfikuje kolekcji i alias używany jako źródło w `SELECT` instrukcji, jak pokazano w poniższym przykładzie:  
  
 `FROM C as c`  
  
## <a name="from-clause-items"></a>W klauzuli elementów  
 Każdy `FROM` element klauzuli odwołuje się do kolekcji źródła w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje następujące rodzaje `FROM` elementów klauzuli: prosty `FROM` elementów klauzuli `JOIN FROM` elementów klauzuli i `APPLY FROM` klauzuli elementów. Każdy z tych `FROM` elementy klauzuli jest opisane bardziej szczegółowo w poniższych sekcjach.  
  
### <a name="simple-from-clause-item"></a>Prosty z klauzuli elementu  
 Najprostszą `FROM` element klauzuli jest jedno wyrażenie identyfikujące kolekcji i alias. Wyrażenie, które można po prostu zestaw jednostek lub podzapytaniu lub innego wyrażenia, który jest typem kolekcji. Oto przykład:  
  
```  
LOB.Customers as c  
```  
  
 Specyfikacja alias jest opcjonalne. Alternatywne specyfikacji powyższe z elementu klauzuli może być następująca:  
  
```  
LOB.Customers  
```  
  
 Jeśli jest określony żaden alias [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prób wygenerowania alias oparte na wyrażeniu kolekcji.  
  
### <a name="join-from-clause-item"></a>Dołączanie z klauzuli elementu  
 A `JOIN FROM` element klauzuli reprezentuje sprzężenia między dwiema `FROM` klauzuli elementów. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Obsługa wielu sprzężeń, sprzężenia wewnętrzne po lewej stronie i prawe sprzężenia zewnętrzne i pełne sprzężenia zewnętrzne. Wszystkie te sprzężeń są obsługiwane w podobny sposób, że są one obsługiwane w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]. Podobnie jak w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], dwa `FROM` klauzuli elementy objęte `JOIN` musi być niezależna. Oznacza to, że nie zostanie skorelowana. A `CROSS APPLY` lub `OUTER APPLY` może służyć do tych przypadkach.  
  
#### <a name="cross-joins"></a>Sprzężenia krzyżowe  
 A `CROSS JOIN` zapytania wyrażenie zwraca iloczyn kartezjański dwie kolekcje, jak pokazano w poniższym przykładzie:  
  
 `FROM C AS c CROSS JOIN D as d`  
  
#### <a name="inner-joins"></a>Sprzężenia wewnętrzne  
 `INNER JOIN` Tworzy ograniczonego iloczyn kartezjański dwie kolekcje, jak pokazano w poniższym przykładzie:  
  
 `FROM C AS c [INNER] JOIN D AS d ON e`  
  
 Każdy element kolekcji po lewej stronie łączyć się z każdym elementem kolekcji w prawo, gdzie kombinacji przetwarza poprzedniego wyrażenia zapytania `ON` warunek jest spełniony. Jeśli nie `ON` jest określony warunek, `INNER JOIN` jest degenerowana do `CROSS JOIN`.  
  
#### <a name="left-outer-joins-and-right-outer-joins"></a>Lewe sprzężenia zewnętrzne i prawe sprzężenia zewnętrzne  
 `OUTER JOIN` Zapytania wyrażenie zwraca iloczyn kartezjański ograniczonego dwie kolekcje, jak pokazano w poniższym przykładzie:  
  
 `FROM C AS c LEFT OUTER JOIN D AS d ON e`  
  
 Każdy element kolekcji po lewej stronie łączyć się z każdym elementem kolekcji w prawo, gdzie kombinacji przetwarza poprzedniego wyrażenia zapytania `ON` warunek jest spełniony. Jeśli `ON` jest spełniony warunek, wyrażenie nadal przetwarza jedno wystąpienie elementu po lewej stronie łączyć się względem elementu po prawej stronie o wartości null.  
  
 A `RIGHT OUTER JOIN` mogą być sformułowane w podobny sposób.  
  
#### <a name="full-outer-joins"></a>Tworzy sprzężenie zewnętrzne pełne  
 Jawne `FULL OUTER JOIN` tworzy ograniczonego iloczyn kartezjański dwie kolekcje, jak pokazano w poniższym przykładzie:  
  
 `FROM C AS c FULL OUTER JOIN D AS d ON e`  
  
 Każdy element kolekcji po lewej stronie łączyć się z każdym elementem kolekcji w prawo, gdzie kombinacji przetwarza poprzedniego wyrażenia zapytania `ON` warunek jest spełniony. Jeśli `ON` jest spełniony warunek, wyrażenie nadal przetwarza jedno wystąpienie elementu po lewej stronie łączyć się względem elementu po prawej stronie o wartości null. Przetwarza jedno wystąpienie elementu po prawej stronie łączyć się względem elementu po lewej stronie z wartość null.  
  
> [!NOTE]
>  W celu zachowania zgodności z SQL 92, w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] zewnętrzne — słowo kluczowe jest opcjonalna. W związku z tym `LEFT JOIN`, `RIGHT JOIN`, i `FULL JOIN` są synonimy `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, i `FULL OUTER JOIN`.  
  
### <a name="apply-clause-item"></a>Zastosuj element klauzuli  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje dwa rodzaje z `APPLY`: `CROSS APPLY` i `OUTER APPLY`.  
  
 A `CROSS APPLY` tworzy unikatowy parowanie każdego elementu w kolekcji po lewej stronie z elementem kolekcji utworzonej przez obliczenie wyrażenia po prawej stronie. Z `CROSS APPLY`, wyrażenie po prawej stronie jest funkcjonalnie zależny od elementu po lewej stronie, jak pokazano w poniższym przykładzie skojarzonej kolekcji:  
  
 `SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`  
  
 Zachowanie `CROSS APPLY` jest podobna do listy sprzężenia. Jeśli po prawej stronie wyrażenie ma pustą kolekcję, `CROSS APPLY` tworzy nie skojarzenie tego wystąpienia elementu po lewej stronie.  
  
 `OUTER APPLY` Podobny `CROSS APPLY`, z wyjątkiem sparowania nadal jest generowany nawet wtedy, gdy po prawej stronie wyrażenie ma pustą kolekcję. Poniżej przedstawiono przykład `OUTER APPLY`:  
  
 `SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`  
  
> [!NOTE]
>  W odróżnieniu od w [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], nie istnieje potrzeba jawnego unnest kroku w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
> [!NOTE]
>  `CROSS`i `OUTER APPLY` operatory zostały wprowadzone w systemie [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)]. W niektórych przypadkach potoku zapytanie może wygenerować języka Transact-SQL, który zawiera `CROSS APPLY` i/lub `OUTER APPLY` operatorów. Ponieważ niektórzy dostawcy wewnętrznej bazy danych, w tym wersje [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] wcześniejszy niż [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], nie obsługują tych operatorów, przetwarzanie takich zapytań nie można wykonać na tych dostawców wewnętrznej bazy danych.  
>   
>  Niektóre typowe scenariusze, które mogą prowadzić do obecności `CROSS APPLY` i/lub `OUTER APPLY` operatory w zapytaniu dane wyjściowe są następujące: podzapytania skorelowane z stronicowania; AnyElement w podzapytaniu skorelowane lub za pośrednictwem kolekcji utworzonej przez nawigacji; Używające grupowanie metod, które akceptują selektorem elementu; zapytań LINQ zapytanie, w którym `CROSS APPLY` lub `OUTER APPLY` zostały jawnie określone; kwerendę, która ma `DEREF` skonstruować za pośrednictwem `REF` utworzenia.  
  
## <a name="multiple-collections-in-the-from-clause"></a>Wiele kolekcji w polu od klauzuli  
 `FROM` Klauzula może zawierać więcej niż jednej kolekcji, oddzielonych przecinkami. W takich przypadkach kolekcje uznaje, że mają zostać połączone ze sobą. Potraktować je jako n sposób sprzężenia KRZYŻOWEGO.  
  
 W poniższym przykładzie `C` i `D` są niezależne kolekcji, ale `c.Names` jest zależna od `C`.  
  
```  
FROM C AS c, D AS d, c.Names AS e  
```  
  
 Poprzedni przykład logicznie odpowiada do poniższego przykładu:  
  
 `FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`  
  
## <a name="left-correlation"></a>Lewa korelacja  
 Elementy w `FROM` klauzuli mogą odwoływać się do określonych w klauzulach starszych elementów. W poniższym przykładzie `C` i `D` są niezależne kolekcji, ale `c.Names` jest zależna od `C`:  
  
```  
from C as c, D as d, c.Names as e  
```  
  
 Jest to równoważne logicznie:  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
## <a name="semantics"></a>Semantyka  
 Logicznie, kolekcje w `FROM` klauzuli będą traktowani jako część `n`-sprzężenia krzyżowego sposób (z wyjątkiem w przypadku 1-sposób sprzężenie krzyżowe). Aliasy w `FROM` klauzul są przetwarzane po lewej do prawej i są dodawane do bieżącego zakresu do wykorzystania w późniejszym czasie. `FROM` Przyjęto, że klauzula utworzyć zestaw wielokrotny wierszy. Będzie jedno pole dla każdego elementu w `FROM` klauzuli, która reprezentuje jeden element z elementu kolekcji.  
  
 `FROM` Klauzuli logicznie tworzy zestaw wielokrotny, który wiersze typu wiersza (c, d, e) gdzie pól c, d i e są rozpatrywane typu elementu `C`, `D`, i `c.Names`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]wprowadzono alias dla każdego prosty `FROM` element klauzuli w zakresie. Na przykład poniższa z klauzuli fragment nazwy wprowadzane do zakresu są c, d i e.  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
 W [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (w przeciwieństwie do [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]), `FROM` klauzuli wprowadza tylko aliasów do zakresu. Wszystkie odwołania do tych kolekcji kolumn (właściwości) musi być kwalifikowana za alias.  
  
## <a name="pulling-up-keys-from-nested-queries"></a>Ściąganie zapasową kluczy z zapytania zagnieżdżone  
 Niektóre rodzaje zapytania wymagające ściąganie zapasową kluczy z zapytanie zagnieżdżone nie są obsługiwane. Na przykład następujące kwerendy jest nieprawidłowa:  
  
```  
select c.Orders from Customers as c   
```  
  
 Jednak poniższe zapytanie jest nieprawidłowe, ponieważ zapytanie zagnieżdżone nie ma żadnych kluczy:  
  
```  
select {1} from {2, 3}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Wyrażenia zapytań](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [Typy dopuszczające wartości zerowe strukturalnych](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
