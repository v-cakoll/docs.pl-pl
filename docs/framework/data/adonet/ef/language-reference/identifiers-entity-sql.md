---
title: Identyfikatory (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d58a5edd-7b5c-48e1-b5d7-a326ff426aa4
ms.openlocfilehash: b467a42ed0a0083b9e72037f437dd70aa6b46390
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833710"
---
# <a name="identifiers-entity-sql"></a>Identyfikatory (Entity SQL)
Identyfikatory są używane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do reprezentowania aliasów wyrażenia zapytania, odwołań do zmiennych, właściwości obiektów, funkcji i tak dalej. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zawiera dwa rodzaje identyfikatorów: proste identyfikatory i identyfikatory ujęte w cudzysłów.  
  
## <a name="simple-identifiers"></a>Identyfikatory proste  
 Prosty identyfikator w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest sekwencją znaków alfanumerycznych i podkreślenia. Pierwszy znak identyfikatora musi być znakiem alfabetycznym (a-z lub A-Z).  
  
## <a name="quoted-identifiers"></a>Identyfikatory ujęte w cudzysłów  
 Identyfikator w cudzysłowie to dowolna sekwencja znaków ujęta w nawiasy kwadratowe ([]). Identyfikatory ujęte w cudzysłów umożliwiają określanie identyfikatorów z nieprawidłowymi znakami w identyfikatorach. Wszystkie znaki między nawiasami kwadratowymi stają się częścią identyfikatora, łącznie ze wszystkimi białymi znakami.  
  
 Identyfikator w cudzysłowie nie może zawierać następujących znaków:  
  
- Ani.  
  
- Znaki powrotu karetki.  
  
- Przedstawia.  
  
- Backspace.  
  
- Dodatkowe nawiasy kwadratowe (czyli nawiasy kwadratowe w nawiasach kwadratowych, które odróżnić identyfikator).  
  
 Identyfikator ujęty w cudzysłów może zawierać znaki Unicode.  
  
 Identyfikatory ujęte w cudzysłów umożliwiają tworzenie znaków nazw właściwości, które nie są prawidłowe w identyfikatorach, jak pokazano w następującym przykładzie:  
  
 `SELECT c.ContactName AS [Contact Name] FROM customers AS c`  
  
 Można również użyć identyfikatorów w cudzysłowie, aby określić identyfikator, który jest zastrzeżonym słowem kluczowym [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Na przykład, jeśli typ `Email` ma właściwość o nazwie "from", można odróżnić ją od zastrzeżonego słowa kluczowego FROM przy użyciu nawiasów kwadratowych w następujący sposób:  
  
 `SELECT e.[From] FROM emails AS e`  
  
 Możesz użyć identyfikatora w cudzysłowie po prawej stronie operatora kropki (.).  
  
 `SELECT t FROM ts as t WHERE t.[property] == 2`  
  
 Aby użyć nawiasu kwadratowego w identyfikatorze, należy dodać dodatkowy nawias kwadratowy. W poniższym przykładzie "`abc]`" jest identyfikatorem:  
  
 `SELECT t from ts as t WHERE t.[abc]]] == 2`  
  
 W przypadku semantyki porównania identyfikatora w cudzysłowie zobacz [wejściowy zestaw znaków](input-character-set-entity-sql.md).  
  
## <a name="aliasing-rules"></a>Reguły aliasowania  
 Zalecamy Określanie aliasów w kwerendach [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w razie konieczności, w tym następujących konstrukcji [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
- Pola konstruktora wierszy.  
  
- Elementy w klauzuli FROM w wyrażeniu zapytania.  
  
- Elementy w klauzuli SELECT w wyrażeniu zapytania.  
  
- Elementy w klauzuli GROUP BY w wyrażeniu zapytania.  
  
### <a name="valid-aliases"></a>Prawidłowe aliasy  
 Prawidłowe aliasy w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to każdy prosty identyfikator lub Identyfikator ujęty w cudzysłów.  
  
### <a name="alias-generation"></a>Generowanie aliasu  
 Jeśli w wyrażeniu zapytania [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie określono aliasu, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] podejmie próbę wygenerowania aliasu na podstawie następujących prostych reguł:  
  
- Jeśli wyrażenie zapytania (dla którego alias jest nieokreślony) jest identyfikatorem prostym lub w cudzysłowie, ten identyfikator jest używany jako alias. Na przykład, `ROW(a, [b])` staje się `ROW(a AS a, [b] AS [b])`.  
  
- Jeśli wyrażenie zapytania jest bardziej skomplikowanym wyrażeniem, ale ostatni składnik tego wyrażenia zapytania jest prostym identyfikatorem, ten identyfikator jest używany jako alias. Na przykład, `ROW(a.a1, b.[b1])` staje się `ROW(a.a1 AS a1, b.[b1] AS [b1])`.  
  
 Zaleca się, aby nie używać niejawnych aliasów, jeśli chcesz użyć nazwy aliasu później. W każdym aliasie (niejawny lub jawny) występuje konflikt lub powtarza się w tym samym zakresie, wystąpił błąd kompilacji. Niejawny alias przejdzie kompilację, nawet jeśli istnieje jawny lub niejawny alias o tej samej nazwie.  
  
 Aliasy niejawne są generowane automatycznie na podstawie danych wejściowych użytkownika. Na przykład poniższy wiersz kodu generuje nazwę jako alias dla obu kolumn i w związku z tym spowoduje konflikt.  
  
```sql  
SELECT product.NAME, person.NAME  
```  
  
 Następujący wiersz kodu, który używa jawnych aliasów, również zakończy się niepowodzeniem. Niepowodzenie będzie jednak bardziej widoczne, odczytując kod.  
  
```sql  
SELECT 1 AS X, 2 AS X …  
```  
  
## <a name="scoping-rules"></a>Reguły określania zakresu  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] definiuje reguły określania zakresu, które określają, kiedy określone zmienne są widoczne w języku zapytań. Niektóre wyrażenia lub instrukcje wprowadzają nowe nazwy. Reguły określania zakresu określają, gdzie mogą być używane te nazwy, a kiedy lub gdzie Nowa deklaracja o takiej samej nazwie jak inna może ukryć jej poprzednik.  
  
 Gdy nazwy są zdefiniowane w kwerendzie [!INCLUDE[esql](../../../../../../includes/esql-md.md)], są one określane jako zdefiniowane w zakresie. Zakres obejmuje cały region zapytania. Wszystkie wyrażenia lub odwołania do nazw w określonym zakresie mogą zobaczyć nazwy, które są zdefiniowane w tym zakresie. Przed rozpoczęciem i po zakończeniu zakresu nie można odwoływać się do nazw, które są zdefiniowane w zakresie.  
  
 Zakresy mogą być zagnieżdżane. Części [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wprowadzają nowe zakresy, które obejmują całe regiony, i te regiony mogą zawierać inne wyrażenia [!INCLUDE[esql](../../../../../../includes/esql-md.md)], które również wprowadzają zakresy. Gdy zakresy są zagnieżdżone, odwołania można wprowadzać do nazw, które są zdefiniowane w najbardziej wewnętrznym zakresie, który zawiera odwołanie. Odwołania można także wprowadzać do nazw, które są zdefiniowane w dowolnych zewnętrznych zakresach. Wszystkie dwa zakresy zdefiniowane w tym samym zakresie są uznawane za zakresy równorzędne. Nie można wprowadzać odwołań do nazw, które są zdefiniowane w ramach zakresów elementów równorzędnych.  
  
 Jeśli nazwa zadeklarowana w zakresie wewnętrznym jest zgodna z nazwą zadeklarowaną w zewnętrznym zakresie, odwołania w zakresie wewnętrznym lub w zakresach zadeklarowanych w tym zakresie odwołują się tylko do nowo zadeklarowanej nazwy. Nazwa w zewnętrznym zakresie jest ukryta.  
  
 Nawet w tym samym zakresie nazwy nie mogą być przywoływane przed zdefiniowaniem.  
  
 Nazwy globalne mogą istnieć jako część środowiska wykonawczego. Może to obejmować nazwy trwałych kolekcji lub zmiennych środowiskowych. Aby nazwa była globalna, musi być zadeklarowana w zewnętrznym zakresie.  
  
 Parametry nie należą do zakresu. Ponieważ odwołania do parametrów zawierają specjalną składnię, nazwy parametrów nigdy nie kolidują z innymi nazwami w zapytaniu.  
  
### <a name="query-expressions"></a>Wyrażenia kwerend  
 Wyrażenie zapytania [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wprowadza nowy zakres. Nazwy, które są zdefiniowane w klauzuli FROM, są wprowadzane do zakresu od w kolejności wyglądu, od lewej do prawej. Na liście sprzężenia wyrażenia mogą odwoływać się do nazw, które zostały zdefiniowane wcześniej na liście. Właściwości publiczne (pola i tak dalej) elementów identyfikowanych w klauzuli FROM nie są dodawane do zakresu od. Muszą zawsze być przywoływane przez nazwę kwalifikowaną aliasem. Zwykle wszystkie części wyrażenia SELECT są uwzględniane w obrębie zakresu.  
  
 Klauzula GROUP BY wprowadza również nowy zakres elementów równorzędnych. Każda grupa może mieć nazwę grupy odwołującą się do kolekcji elementów w grupie. Każde wyrażenie grupowania również wprowadzi nową nazwę w zakresie grupy. Ponadto do zakresu jest również dodawana wartość zagregowana (lub Grupa nazwana). Same wyrażenia grupujące znajdują się w zakresie od zakresu. Jednak gdy jest używana klauzula GROUP BY, klauzula SELECT-list (Projekcja), HAVING i klauzula ORDER BY są uznawane za należące do zakresu grupy, a nie z zakresu od. Agregacje otrzymują specjalne traktowanie, zgodnie z opisem na poniższej liście punktowanej.  
  
 Poniżej znajdują się dodatkowe uwagi dotyczące zakresów:  
  
- Lista wyboru może wprowadzać nowe nazwy do zakresu w kolejności. Wyrażenia projekcji po prawej stronie mogą odwoływać się do nazw znajdujących się po lewej stronie.  
  
- Klauzula ORDER BY może odwoływać się do nazw (aliasów) określonych na liście wyboru.  
  
- Kolejność oceny klauzul w wyrażeniu SELECT określa kolejność, w jakiej nazwy są wprowadzane do zakresu. Klauzula FROM jest szacowana jako pierwsza, po której następuje klauzula WHERE, klauzula GROUP BY, klauzula HAVING, klauzula SELECT, a finally klauzula ORDER BY.  
  
### <a name="aggregate-handling"></a>Obsługa agregacji  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje dwie formy agregacji: agregacje oparte na kolekcjach i agregacje oparte na grupach. Agregacje oparte na kolekcjach to preferowana konstrukcja w [!INCLUDE[esql](../../../../../../includes/esql-md.md)], a agregacje oparte na grupach są obsługiwane w celu zapewnienia zgodności z programem SQL.  
  
 Podczas rozpoznawania wartości zagregowanej [!INCLUDE[esql](../../../../../../includes/esql-md.md)] najpierw próbuje traktować ją jako agregację opartą na kolekcji. Jeśli to się nie powiedzie, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] przekształca zagregowane dane wejściowe w odwołanie do agregacji zagnieżdżania i próbuje rozwiązać to nowe wyrażenie, jak pokazano w poniższym przykładzie.  
  
 `AVG(t.c) becomes AVG(group..(t.c))`  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Omówienie jednostki SQL](entity-sql-overview.md)
- [Wejściowy zestaw znaków](input-character-set-entity-sql.md)
