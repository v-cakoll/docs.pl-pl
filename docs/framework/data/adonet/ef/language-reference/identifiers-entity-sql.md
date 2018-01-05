---
title: Identyfikatory (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d58a5edd-7b5c-48e1-b5d7-a326ff426aa4
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ebae7ad633273a9c33aa7ddcad1b11ad76d9046c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="identifiers-entity-sql"></a>Identyfikatory (jednostka SQL)
Identyfikatory są używane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] do reprezentowania aliasy wyrażenia zapytania, odwołań do zmiennych, właściwości obiektów, funkcje i tak dalej. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zawiera dwa rodzaje identyfikatorów: identyfikatory proste i identyfikatory w cudzysłowach.  
  
## <a name="simple-identifiers"></a>Proste identyfikatory  
 Prosty identyfikator w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest sekwencją alfanumeryczne oraz znaki podkreślenia. Pierwszy znak identyfikatora muszą być litery (a-z lub A-Z).  
  
## <a name="quoted-identifiers"></a>Identyfikatory w cudzysłowach  
 Identyfikatora ujętego w cudzysłów jest dowolną sekwencję znaków ujęta w nawiasy kwadratowe ([]). Let identyfikatory w cudzysłowach można określić identyfikatory z znaki, które nie są prawidłowe w identyfikatorach. Wszystkie znaki w nawiasach kwadratowych staje się częścią identyfikatora wszystkich spacji.  
  
 Identyfikatora ujętego w cudzysłów nie może zawierać następujących znaków:  
  
-   Nowy wiersz.  
  
-   Znaki powrotu karetki.  
  
-   Karty.  
  
-   BACKSPACE.  
  
-   Dodatkowe nawiasy kwadratowe (to znaczy nawiasy kwadratowe w nawiasach kwadratowych, które odróżniać identyfikator).  
  
 Podane identyfikator może zawierać znaków Unicode.  
  
 Identyfikatory w cudzysłowach umożliwiają tworzenie znaków nazwy właściwości, które nie są prawidłowe w identyfikatorach, jak pokazano w poniższym przykładzie:  
  
 `SELECT c.ContactName AS [Contact Name] FROM customers AS c`  
  
 Umożliwia także identyfikatory w cudzysłowach określić identyfikator, który jest zarezerwowanym słowem kluczowym z [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Na przykład jeśli typ `Email` ma właściwość o nazwie "Od", można odróżnić go z zastrzeżonym słowem kluczowym z, za pomocą nawiasów kwadratowych, w następujący sposób:  
  
 `SELECT e.[From] FROM emails AS e`  
  
 Po prawej stronie operator kropki (.), można użyć identyfikatora ujętego w cudzysłów.  
  
 `SELECT t FROM ts as t WHERE t.[property] == 2`  
  
 Aby używać nawias kwadratowy w identyfikatorze, Dodaj dodatkowe nawiasu kwadratowego. W poniższym przykładzie "`abc]`" jest identyfikatorem:  
  
 `SELECT t from ts as t WHERE t.[abc]]] == 2`  
  
 Aby semantykę porównania identyfikatora ujętego w cudzysłów, zobacz [zestaw znaków wprowadzania](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).  
  
## <a name="aliasing-rules"></a>Zasady aliasowania  
 Zaleca się określenie aliasów w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] odpytuje zawsze, gdy potrzebne, takie jak [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tworzy:  
  
-   Pola konstruktorze wierszy.  
  
-   Elementy w klauzuli FROM w wyrażeniu kwerendy.  
  
-   Elementy w klauzuli SELECT w wyrażeniu kwerendy.  
  
-   Elementy w klauzuli GROUP BY w wyrażeniu kwerendy.  
  
### <a name="valid-aliases"></a>Nieprawidłowa aliasów  
 Nieprawidłowa aliasy w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prostego identyfikatora lub identyfikatora ujętego w cudzysłów.  
  
### <a name="alias-generation"></a>Generowanie aliasu  
 Jeśli alias nie został określony w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania wyrażenia [!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje wygenerować na podstawie następujących reguł proste alias:  
  
-   Jeśli wyrażenie kwerendy (dla którego alias jest nieokreślony) jest prostą lub podane identyfikator, ten identyfikator jest używany jako alias. Na przykład, `ROW(a, [b])` staje się `ROW(a AS a, [b] AS [b])`.  
  
-   Jeśli wyrażenie kwerendy jest bardziej złożone wyrażenie, ale ostatniej części tego wyrażenia zapytania jest prostym identyfikatorem, że identyfikator jest używany jako alias. Na przykład, `ROW(a.a1, b.[b1])` staje się `ROW(a.a1 AS a1, b.[b1] AS [b1])`.  
  
 Zaleca się, że należy używać niejawne aliasów, jeśli chcesz później użyć aliasu. W dowolnym momencie konfliktów aliasów (bezpośredniego lub pośredniego) lub czy jest powtarzany w tym samym zakresie, nastąpi błąd kompilacji. Alias niejawne zostaną spełnione kompilacji, nawet jeśli dostępny jest jawnych ani niejawnych aliasu o takiej samej nazwie.  
  
 Niejawne aliasy są automatycznie wygenerowany w oparciu o dane wejściowe użytkownika. Na przykład następujący wiersz kodu wygeneruje nazwę jako alias dla obu kolumn i w związku z tym spowoduje konflikt.  
  
```  
SELECT product.NAME, person.NAME  
```  
  
 Następujący wiersz kodu, który używa jawnego aliasy, również zakończy się niepowodzeniem. Jednak awarii będzie bardziej oczywista odczytując kod.  
  
```  
SELECT 1 AS X, 2 AS X …  
```  
  
## <a name="scoping-rules"></a>Zakres reguły  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Definiuje reguły zakresu, które ustalania momentu konkretnym zmienne są widoczne w języku zapytań. Niektóre wyrażenia lub instrukcji przedstawiono nowe nazwy. Określania zakresu reguły określają, których można używać tych nazw, a jeśli lub gdy nowe oświadczenie o takiej samej nazwie, jak inny można ukryć jego poprzednik.  
  
 Gdy nazwy są określane w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania, są one określane w zakresie zdefiniowania. Zakres obejmuje całego regionu zapytania. Wszystkie wyrażenia lub nazwę odwołania w ramach określonego zakresu można wyświetlić nazwy, które są zdefiniowane w tym zakresie. Przed rozpoczęciem zakresu i po jej zakończeniu, nie można przywołać nazw, które są zdefiniowane w ramach zakresu.  
  
 Zakresy mogą być zagnieżdżone. Części [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wprowadzić nowe zakresy, obejmujące cały regionów, a tych regionów może zawierać inne [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wyrażeń, które również wprowadzać zakresów. Kiedy zakresy są zagnieżdżone, można nawiązać odwołania do nazwy, które są zdefiniowane w najbardziej zakresu, który zawiera odwołanie. Odwołania dotyczące również wszystkie nazwy, które są zdefiniowane w żadnych zakresów zewnętrzne. Wszelkie dwa zakresy zdefiniowanego w tym samym zakresie są traktowane jako element równorzędny zakresów. Nie można wprowadzić odwołuje się do nazw, które są zdefiniowane w ramach tego samego poziomu zakresów.  
  
 Jeśli nazwa zadeklarowana w zakresie wewnętrznym odpowiada nazwie zadeklarowana w zakresie zewnętrznym, odwołań w zakresie wewnętrznym lub w zakresach zadeklarowany w tym zakresie odwoływać się tylko do nowo zadeklarowana nazwa. Nazwa w zewnętrznym zakresie jest ukryty.  
  
 Nawet w ramach tego samego zakresu nie można przywołać nazwy, zanim nie zostaną zdefiniowane.  
  
 Nazwy globalne może istnieć jako część środowiska wykonawczego. Może to obejmować nazwy kolekcji trwałe lub zmienne środowiskowe. Dla nazwy będzie globalnym musi być zadeklarowana w zakresie najbardziej zewnętrznego.  
  
 Parametry nie są w zakresie. Odwołania do parametrów zawiera specjalne składni, nazwy parametrów nigdy nie będzie kolidują z innych nazw w zapytaniu.  
  
### <a name="query-expressions"></a>Wyrażenia zapytań  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Zapytania wyrażenie wprowadzono nowy zakres. Nazwy, które są zdefiniowane w klauzuli FROM są wprowadzane z zakresu w kolejności wyświetlania, od lewej do prawej. Na liście łączenia wyrażenia mogą odwoływać się do nazw, które zostały zdefiniowane wcześniej na liście. Właściwości publiczne (pola i tak dalej) elementów określonych w klauzuli FROM nie są dodawane do zakresu od. One musi być zawsze odwołuje się nazwa kwalifikowana alias. Zwykle wszystkie części Wybierz wyrażenie, które są traktowane jako w zakresie od.  
  
 W klauzuli GROUP BY wprowadza również nowego zakresu tego samego poziomu. Każda grupa może mieć nazwę grupy, która odwołuje się do kolekcji elementów w grupie. Każde wyrażenie grupowania przedstawiono również nową nazwę w zakresie grupy. Ponadto zagnieżdżania agregacji (lub nazwaną grupę) jest także dodawane do zakresu. Wyrażenia grupowania, same znajdują się w zakresie od. Jednak użycie klauzuli GROUP BY (Projekcja) liście instrukcji select, klauzuli HAVING i klauzuli ORDER BY są uważane za w ramach zakresu grupy, a nie z zakresu. Agreguje traktowane specjalne, zgodnie z opisem na poniższej liście.  
  
 Poniżej przedstawiono dodatkowe uwagi dotyczące zakresów:  
  
-   Na liście wybierz można wprowadzać nowe nazwy do zakresu, w kolejności. Wyrażenia projekcji z prawej strony mogą odwoływać się do nazwy zaprojektowana po lewej stronie.  
  
-   W klauzuli ORDER BY może odwoływać się do nazwy (aliasy) określone na liście wyboru.  
  
-   Kolejność klauzul w wyrażeniu wybierz określa porządek, że nazwy są wprowadzane do zakresu. Klauzula FROM jest oceniany, najpierw następuje klauzuli WHERE, klauzuli GROUP BY w klauzuli HAVING, klauzuli SELECT i finally w klauzuli ORDER BY.  
  
### <a name="aggregate-handling"></a>Obsługa agregacji  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]obsługuje dwa rodzaje agreguje: opartego na kolekcji wartości zagregowanych i agreguje oparte na grupach. Agreguje opartego na kolekcji są preferowane konstrukcja [!INCLUDE[esql](../../../../../../includes/esql-md.md)], i na podstawie grupy agregacje są obsługiwane w przypadku zgodności SQL.  
  
 Podczas rozpoznawania agregacji, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] po raz pierwszy próbuje zaliczenie agregacji opartego na kolekcji. W przypadku niepowodzenia [!INCLUDE[esql](../../../../../../includes/esql-md.md)] przekształca agregacji danych wejściowych do odwołania do wartości zagregowanej zestawu i próbuje rozpoznać tego wyrażenia nowego, jak pokazano w poniższym przykładzie.  
  
 `AVG(t.c) becomes AVG(group..(t.c))`  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Wejściowy zestaw znaków](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)
