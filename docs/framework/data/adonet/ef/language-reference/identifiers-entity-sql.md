---
title: Identyfikatory (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: d58a5edd-7b5c-48e1-b5d7-a326ff426aa4
ms.openlocfilehash: 702a9c69c37b572fde18dd57c44608678174fb15
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204903"
---
# <a name="identifiers-entity-sql"></a>Identyfikatory (jednostka SQL)
Identyfikatory są używane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do reprezentowania aliasy wyrażenie zapytania, odwołań do zmiennych, właściwości obiektów, funkcji i tak dalej. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zawiera dwa rodzaje identyfikatorów: proste identyfikatory oraz identyfikatory w cudzysłowach.  
  
## <a name="simple-identifiers"></a>Proste identyfikatory  
 W prostym identyfikatorem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest sekwencją alfanumeryczne i znaki podkreślenia. Pierwszy znak identyfikatora musi być znak alfabetyczny (a – z lub A – Z).  
  
## <a name="quoted-identifiers"></a>Identyfikatory w cudzysłowach  
 Cytowanego identyfikatora znak jest dowolną sekwencję znaków, ujęte w nawiasy kwadratowe ([]). Cytowane identyfikatory pozwalają określić identyfikatory znaków, które nie są prawidłowe w identyfikatorach. Wszystkie znaki między nawiasami kwadratowymi stają się częścią identyfikatora, w tym wszystkich odstępów.  
  
 Cytowanego identyfikatora nie może zawierać następujących znaków:  
  
-   Newline.  
  
-   Znaki powrotu karetki.  
  
-   Karty.  
  
-   Backspace.  
  
-   Dodatkowe nawiasy kwadratowe (oznacza to, że nawiasy kwadratowe wewnątrz nawiasów kwadratowych, które odróżnić identyfikator).  
  
 Podane identyfikator może zawierać znaków Unicode.  
  
 Identyfikatory w cudzysłowach umożliwiają tworzenie znaków nazwy właściwości, które nie są prawidłowe w identyfikatorach, jak pokazano w poniższym przykładzie:  
  
 `SELECT c.ContactName AS [Contact Name] FROM customers AS c`  
  
 Umożliwia także identyfikatory w cudzysłowach określić identyfikator, który jest zastrzeżonym słowem kluczowym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Na przykład jeśli typ `Email` ma właściwość o nazwie "Od", można odróżnić go od zastrzeżonego słowa kluczowego z, za pomocą nawiasów kwadratowych, w następujący sposób:  
  
 `SELECT e.[From] FROM emails AS e`  
  
 Po prawej stronie operatora kropka (.), można użyć cytowanego identyfikatora.  
  
 `SELECT t FROM ts as t WHERE t.[property] == 2`  
  
 Aby użyć nawias kwadratowy w identyfikatorze, należy dodać dodatkowy nawias kwadratowy. W poniższym przykładzie "`abc]`" to identyfikator:  
  
 `SELECT t from ts as t WHERE t.[abc]]] == 2`  
  
 Semantyka porównania cytowanego identyfikatora, można zobaczyć [zestaw znaków danych wejściowych](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).  
  
## <a name="aliasing-rules"></a>Zasady aliasowania  
 Firma Microsoft zaleca, określając aliasów w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania zawsze wtedy, gdy potrzebne, w tym następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstrukcji:  
  
-   Pola konstruktorze wierszy.  
  
-   Elementy w klauzuli FROM w wyrażeniu zapytania.  
  
-   Elementy w klauzuli SELECT w wyrażeniu zapytania.  
  
-   Elementy w klauzuli GROUP BY w wyrażeniu zapytania.  
  
### <a name="valid-aliases"></a>Prawidłowe aliasy  
 Prawidłowe aliasy w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prostym identyfikatorem lub cytowanego identyfikatora.  
  
### <a name="alias-generation"></a>Alias Generation  
 Jeśli brak aliasu jest określona w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wyrażeniu, zapytania [!INCLUDE[esql](../../../../../../includes/esql-md.md)] spróbuje wygenerować aliasem, na podstawie następujących reguł proste:  
  
-   Wyrażenia zapytania (w przypadku którego aliasu jest nieokreślony) w przypadku prostego lub cytowanego identyfikatora, ten identyfikator jest używany jako alias. Na przykład, `ROW(a, [b])` staje się `ROW(a AS a, [b] AS [b])`.  
  
-   Jeśli wyrażenie kwerendy jest bardziej złożonych wyrażeń, ale ostatni składnik to wyrażenie kwerendy jest prostym identyfikatorem, że identyfikator jest używany jako alias. Na przykład, `ROW(a.a1, b.[b1])` staje się `ROW(a.a1 AS a1, b.[b1] AS [b1])`.  
  
 Zaleca się, czy należy używać niejawne Tworzenie aliasów Jeśli chcesz później użyć nazwę aliasu. W dowolnym momencie konflikt aliasy (niejawny lub jawny) lub czy powtarza się w tym samym zakresie, nastąpi błąd kompilacji. Niejawne alias zostaną spełnione kompilacji, nawet jeśli dostępny jest aliasem jawnych lub niejawnych o takiej samej nazwie.  
  
 Niejawne aliasy są automatycznie wygenerowany na podstawie danych wejściowych użytkownika. Na przykład następujący wiersz kodu wygeneruje nazwę jako alias obie kolumny, a w związku z tym spowoduje konflikt.  
  
```  
SELECT product.NAME, person.NAME  
```  
  
 Następujący wiersz kodu, który używa jawnego aliasy, również zakończy się niepowodzeniem. Jednak błąd będą bardziej widoczny, zapoznając się kod.  
  
```  
SELECT 1 AS X, 2 AS X …  
```  
  
## <a name="scoping-rules"></a>Wyznaczanie zakresu reguły  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Definiuje reguły określania zakresów, które określają podczas określonego zmienne są widoczne w języku zapytań. Niektóre wyrażenia lub instrukcji wprowadzają nowe nazwy. Wyznaczanie zakresu reguły określają, gdzie te nazwy mogą być używane i po lub w którym nowe oświadczenie z taką samą nazwę jak inny można ukryć jego poprzednika.  
  
 Gdy nazwy są definiowane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania, ich mówi się, że można zdefiniować w obrębie zakresu. Zakres obejmuje cały region zapytania. Wszystkie wyrażenia lub nazwę odwołania w określonym zakresie zobaczyć nazwy, które są zdefiniowane w tym zakresie. Przed rozpoczęciem zakresu i po jej zakończeniu, nie może być przywoływany nazw, które są zdefiniowane w zakresie.  
  
 Zakresy mogą być zagnieżdżone. Części [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wprowadzają nowe zakresy, które obejmują całą regionów, a tych regionów może zawierać innych [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wyrażeń, które również wprowadzać zakresów. Jeśli zakresy są zagnieżdżone, odwołania może przyjąć nazwy, które są zdefiniowane w najbardziej wewnętrznego zakresu, który zawiera odwołanie do. Odwołania można również wprowadzić do żadnych nazw, które są zdefiniowane w żadnych zakresów zewnętrznych. Wszelkie dwa zakresy zdefiniowane w tym samym zakresie są traktowane jako element równorzędny zakresów. Nie można wprowadzać odwołania do nazwy, które są zdefiniowane w ramach tego samego poziomu zakresów.  
  
 Jeśli nazwa zadeklarowana w zakresie wewnętrznym pasuje nazwę zadeklarowana w zakresie zewnętrznym, odwołania w zakresie wewnętrznym lub w ramach zadeklarowany w tym zakresie zakresy dotyczą tylko nowo zadeklarowana nazwa. Nazwa w zewnętrznym zakresie jest ukryty.  
  
 Nawet w ramach tego samego zakresu nazwy nie może być przywoływany, zanim nie zostaną zdefiniowane.  
  
 Nazwy globalne może znajdować się w ramach środowiska wykonawczego. Może to obejmować nazwy kolekcji trwałe lub zmienne środowiskowe. Nazwa będzie globalnym musi być zadeklarowana w zakresie najbardziej zewnętrznej.  
  
 Parametry nie są w zakresie. Odwołania do parametrów zawiera specjalnej składni, nazwy parametrów nigdy nie będą kolidować z nazwami innych w zapytaniu.  
  
### <a name="query-expressions"></a>Wyrażenia kwerend  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Wyrażenie wprowadza nowy zakres kwerendy. Nazwy, które są zdefiniowane w klauzuli FROM są wprowadzane do z zakresu w kolejności występowania, od lewej do prawej. Na liście sprzężenia wyrażenia mogą odwoływać się do nazwy, które zostały zdefiniowane wcześniej na liście. Właściwości publiczne (pola i tak dalej) elementów określone w klauzuli FROM nie są dodawane do zakresu od. One muszą być zawsze przywoływane przez nazwę kwalifikowaną aliasu. Zazwyczaj wszystkie części Wybierz wyrażenie są uwzględniane w zakresie od.  
  
 W klauzuli GROUP BY wprowadza również nowy zakres element równorzędny. Każda grupa może mieć nazwę grupy, która odwołuje się do elementów w grupie. Każde wyrażenie grupowania przedstawiono również nową nazwę w zakresie grupy. Ponadto zagnieżdżonych agregacji (lub nazwanej grupy) jest także dodawane do zakresu. Wyrażenia grupowania, samodzielnie znajdują się w zakresie od. Jednak gdy jest używana klauzula GROUP BY, wybierz list (rzutowania), klauzuli HAVING i ORDER BY — klauzula są uznawane za w ramach danego zakresu grupy, a nie z zakresu. Agregacje otrzymują specjalnego traktowania, zgodnie z opisem w poniższej liście punktowanej.  
  
 Poniżej przedstawiono dodatkowe uwagi dotyczące zakresów:  
  
-   Na liście wybierz można wprowadzać nowe nazwy do zakresu, w kolejności. Wyrażenia projekcji po prawej stronie może odnosić się do nazwy przewidywany po lewej stronie.  
  
-   Klauzula ORDER BY mogą odwoływać się do określonych na liście wybierz nazwami (aliasami).  
  
-   Kolejność obliczania klauzule wewnątrz wyrażenia wybierz określa kolejność, w wprowadzenie nazwy do zakresu. Klauzula FROM jest stosowana jako pierwsza, a następnie klauzuli WHERE, klauzula GROUP BY, klauzula HAVING, klauzuli SELECT, a na końcu klauzuli ORDER BY.  
  
### <a name="aggregate-handling"></a>Obsługa agregacji  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje dwa rodzaje wartości zagregowane: agregacje związanych z kolekcjami i oparte na grupach agregacji. Agregacje opartego na kolekcji są preferowane konstrukcję w [!INCLUDE[esql](../../../../../../includes/esql-md.md)], i oparte na grupach wartości zagregowane są obsługiwane w przypadku zgodność bazy danych SQL.  
  
 Podczas rozpoznawania agregacji, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] po raz pierwszy próbuje traktowanie jej jako agregacja opartego na kolekcji. W przypadku niepowodzenia [!INCLUDE[esql](../../../../../../includes/esql-md.md)] przekształca agregacji danych wejściowych na odwołanie do zagregowania zagnieżdżanie i próbuje rozpoznać tego wyrażenia nowych, jak pokazano w poniższym przykładzie.  
  
 `AVG(t.c) becomes AVG(group..(t.c))`  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Wejściowy zestaw znaków](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)
