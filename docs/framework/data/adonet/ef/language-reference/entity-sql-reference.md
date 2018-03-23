---
title: Odwołanie do jednostki SQL
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61ce7ee1-ffe2-477d-8a9f-835b0a11d900
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: ac05ec8a8732da383a4e33e84c669aa29660a0da
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="entity-sql-reference"></a>Odwołanie do jednostki SQL
Ta sekcja zawiera [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tematy referencyjne. Ten temat zawiera podsumowanie i grup [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory według kategorii.  
  
## <a name="arithmetic-operators"></a>Operatory arytmetyczne  
 Operatory arytmetyczne wykonywania operacji matematycznych na dwóch wyrażeniach co najmniej jeden typ danych liczbowych. W poniższej tabeli wymieniono [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory arytmetyczne.  
  
|Operator|Zastosowanie|  
|--------------|---------|  
|[+ (Dodaj)](../../../../../../docs/framework/data/adonet/ef/language-reference/add.md)|Dodatek.|  
|"/ (Dzielenie)"|Podział.|  
|[% (Modulo)](../../../../../../docs/framework/data/adonet/ef/language-reference/modulo-entity-sql.md)|Zwraca resztę z dzielenia.|  
|[* (Mnożenie)](../../../../../../docs/framework/data/adonet/ef/language-reference/multiply-entity-sql.md)|Mnożenia.|  
|[- (Ujemne)](../../../../../../docs/framework/data/adonet/ef/language-reference/negative-entity-sql.md)|Negacja.|  
|[- (Odejmowanie)](../../../../../../docs/framework/data/adonet/ef/language-reference/subtract-entity-sql.md)|Odejmowanie.|  
  
## <a name="canonical-functions"></a>Canonical funkcji  
 Canonical funkcje są obsługiwane przez wszystkich dostawców danych i mogą być używane przez wszystkie technologie wykonywanie zapytania. W poniższej tabeli wymieniono funkcje kanonicznej.  
  
|Funkcja|Typ|  
|--------------|----------|  
|[Canonical funkcji SQL agregacji jednostki](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|W tym artykule omówiono agregacji [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.|  
|[Funkcje matematyczne Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|W tym artykule omówiono matematyczne [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.|  
|[Funkcje ciągów Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|W tym artykule omówiono ciąg [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.|  
|[Funkcji daty i godziny Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|W tym artykule omówiono Data i godzina [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.|  
|[Funkcje bitowe Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|W tym artykule omówiono bitowo [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji.|  
|[Inne funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)|W tym artykule omówiono funkcje nie są sklasyfikowane jako bitowe, daty/godziny, ciąg, matematyczne lub agregacji.|  
  
## <a name="comparison-operators"></a>Operatory porównania  
 Operatory porównania są definiowane dla następujących typów: `Byte`, `Int16`, `Int32`, `Int64`, `Double`, `Single`, `Decimal`, `String`, `DateTime`, `Date`, `Time` , `DateTimeOffset`. Promocja typu niejawnego występuje operandy przed zastosowaniem operator porównania. Operatory porównania yield zawsze wartościami logicznymi. Gdy co najmniej jeden z argumentów jest `null`, wynikiem jest `null`.  
  
 Równości i nierówności są definiowane dla dowolnego typu obiektu, który ma tożsamość, takich jak `Boolean` typu. Niepierwotne obiekty o tożsamości są traktowane jako równe, jeśli mają tej samej tożsamości. W poniższej tabeli wymieniono [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatory porównania.  
  
|Operator|Opis|  
|--------------|-----------------|  
|[= (Równa się)](../../../../../../docs/framework/data/adonet/ef/language-reference/equals-entity-sql.md)|Porównuje równość dwóch wyrażeń.|  
|[> (Większe niż)](../../../../../../docs/framework/data/adonet/ef/language-reference/greater-than-entity-sql.md)|Porównuje dwa wyrażenia w celu określenia, czy wyrażenie po lewej stronie ma wartość większą niż prawe wyrażenie.|  
|[>= (Większe niż lub równe)](../../../../../../docs/framework/data/adonet/ef/language-reference/greater-than-or-equal-to-entity-sql.md)|Porównuje dwa wyrażenia, aby sprawdzić, czy po lewej stronie wyrażenia jest wartość większa niż lub równa prawe wyrażenie.|  
|[IS &#91;NOT&#93; NULL](../../../../../../docs/framework/data/adonet/ef/language-reference/isnull-entity-sql.md)|Określa, czy wyrażenie kwerendy jest null.|  
|[< (Mniejsze niż)](../../../../../../docs/framework/data/adonet/ef/language-reference/less-than-entity-sql.md)|Porównuje dwa wyrażenia w celu określenia, czy wyrażenie po lewej stronie ma wartość mniejszą niż prawe wyrażenie.|  
|[<= (Mniejsze niż lub równe)](../../../../../../docs/framework/data/adonet/ef/language-reference/less-than-or-equal-to-entity-sql.md)|Porównuje dwa wyrażenia, aby określić, czy wyrażenie po lewej stronie ma wartość mniejszą niż lub równe prawe wyrażenie.|  
|[&#91;NOT&#93; BETWEEN](../../../../../../docs/framework/data/adonet/ef/language-reference/between-entity-sql.md)|Określa, czy wyrażenie wynikiem jest wartość w określonym zakresie.|  
|[!= (Nie równa się)](../../../../../../docs/framework/data/adonet/ef/language-reference/not-equal-to-entity-sql.md)|Porównuje dwa wyrażenia, aby określić, czy po lewej stronie wyrażenia nie jest równa prawe wyrażenie.|  
|[&#91;NOT&#93; LIKE](../../../../../../docs/framework/data/adonet/ef/language-reference/like-entity-sql.md)|Określa, czy dany ciąg znaków jest zgodna z określonym wzorcem.|  
  
## <a name="logical-and-case-expression-operators"></a>Operatory logiczne i Case wyrażenia  
 Operatory logiczne sprawdzić prawdy warunku. Wyrażenie CASE ocenia zestaw wyrażeń logicznych w celu ustalenia wyniku. W poniższej tabeli wymieniono operatorów logicznych i wielkość wyrażenia.  
  
|Operator|Opis|  
|--------------|-----------------|  
|[& & (Logiczne i)](../../../../../../docs/framework/data/adonet/ef/language-reference/and-entity-sql.md)|Operatora logicznego AND.|  
|[!, (NEGACJA)](../../../../../../docs/framework/data/adonet/ef/language-reference/not-entity-sql.md)|NEGACJA.|  
|[&#124;&#124;(Logiczne lub)](../../../../../../docs/framework/data/adonet/ef/language-reference/or-entity-sql.md)|Operatora logicznego OR.|  
|[CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)|Ocenia zestaw wyrażeń logicznych w celu ustalenia wyniku.|  
|[THEN](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)|Wynik [podczas](http://msdn.microsoft.com/library/6233fe9f-00b0-460e-8372-64e138a5f998) klauzuli gdy zwraca wartość true.|  
  
## <a name="query-operators"></a>Operatory zapytań  
 Operatory zapytań są używane do definiowania wyrażenia zapytania, które zwracają dane jednostki. W poniższej tabeli wymieniono operatorów zapytań.  
  
|Operator|Zastosowanie|  
|--------------|---------|  
|[FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)|Określa kolekcję, która jest używana w [wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) instrukcje.|  
|[GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)|Określa grupę, do których obiektów które zwróconych przez kwerendę ([wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) zostaną umieszczone wyrażenia.|  
|[GroupPartition](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md)|Zwraca kolekcję wartości argumentu, przewidywane wyłączanie partycji grupy, do którego odnosi się agregacji.|  
|[HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md)|Określa warunek wyszukiwania dla grupy lub agregacja.|  
|[LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)|Używane z [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli, aby wykonał stronicowania fizycznych.|  
|[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)|Określa porządek sortowania, jaka jest używana na obiekty zwrócone w [wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) instrukcji.|  
|[SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)|Określa elementy w projekcji, z którego są zwracane przez zapytanie.|  
|[SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)|Używane z [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli, aby wykonał stronicowania fizycznych.|  
|[TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)|Określa, że tylko pierwszy zestaw wierszy zostaną zwrócone w wyniku zapytania.|  
|[WHERE](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md)|Warunkowe filtrów danych zwracanych przez zapytanie.|  
  
## <a name="reference-operators"></a>Odwołanie do operatorów  
 Odwołanie ma postać wskaźnika logiczne (klucz obcy) do określonej jednostki w zestawie określonej jednostki. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje następujące operatory utworzenia deconstruct i przejdź do odwołania.  
  
|Operator|Zastosowanie|  
|--------------|---------|  
|[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)|Tworzy odwołania do jednostki w zestawie jednostek.|  
|[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)|Wyłuskań wartość odniesienia i daje w wyniku tego usunąć odwołania do.|  
|[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)|Wyodrębnia klucza referencyjnego lub wyrażenie jednostki.|  
|[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)|Umożliwia przejście przez relację typu jeden jednostki do innego|  
|[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)|Zwraca odwołanie do wystąpienia jednostki.|  
  
## <a name="set-operators"></a>Operatory zestawów  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapewnia różne operacje zaawansowany zestaw. Obejmuje to podobne do operatorów języka Transact-SQL, takich jak UNION, INTERSECT i EXCEPT, operatorów i EXISTS. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] obsługuje również operatory wyeliminowania zduplikowanych (SET), członkostwo testowania (ruch PRZYCHODZĄCY) i sprzężeń (połączenie). W poniższej tabeli wymieniono [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ustawić operatorów.  
  
|Operator|Zastosowanie|  
|--------------|---------|  
|[ANYELEMENT](../../../../../../docs/framework/data/adonet/ef/language-reference/anyelement-entity-sql.md)|Wyodrębnia element z kolekcji wielowartościowych.|  
|[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)|Zwraca kolekcję wszystkie unikatowe wartości w wyrażeniu kwerendy do lewego operandu EXCEPT, które nie są również zwracane w wyrażeniu zapytania z prawej strony argument EXCEPT.|  
|[&#91;NOT&#93; EXISTS](../../../../../../docs/framework/data/adonet/ef/language-reference/exists-entity-sql.md)|Określa, czy kolekcja jest pusta.|  
|[FLATTEN](../../../../../../docs/framework/data/adonet/ef/language-reference/flatten-entity-sql.md)|Konwertuje kolekcję spłaszczonych kolekcją kolekcji.|  
|[&#91;NOT&#93; IN](../../../../../../docs/framework/data/adonet/ef/language-reference/in-entity-sql.md)|Określa, czy wartość odpowiada wartości w kolekcji.|  
|[INTERSECT](../../../../../../docs/framework/data/adonet/ef/language-reference/intersect-entity-sql.md)|Zwraca kolekcję różne wartości, które są zwracane przez wyrażenia zapytania po lewej stronie i prawej krawędzi argument INTERSECT.|  
|[OVERLAPS](../../../../../../docs/framework/data/adonet/ef/language-reference/overlaps-entity-sql.md)|Określa, czy dwie kolekcje mają wspólne elementy.|  
|[SET](../../../../../../docs/framework/data/adonet/ef/language-reference/set-entity-sql.md)|Umożliwia przekonwertowanie kolekcji obiektów do zestawu przez reaguje nowej kolekcji z wszystkie zduplikowane elementy usunięte.|  
|[UNION](../../../../../../docs/framework/data/adonet/ef/language-reference/union-entity-sql.md)|Łączy wyniki dwóch lub więcej kwerend w jednej kolekcji.|  
  
## <a name="type-operators"></a>Operatory typu  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] udostępnia operacje zezwalających na typ wyrażenia (wartość) utworzone, proszeni i manipulowanie. W poniższej tabeli wymieniono operatory, które są używane do współpracy z typami.  
  
|Operator|Zastosowanie|  
|--------------|---------|  
|[CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)|Konwertuje wyrażenie jednego typu danych na inny.|  
|[COLLECTION](../../../../../../docs/framework/data/adonet/ef/language-reference/collection-entity-sql.md)|Używane w [funkcja](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) operację, aby zadeklarować zbiór typy jednostek i typów złożonych.|  
|[IS &#91;NOT&#93; OF](../../../../../../docs/framework/data/adonet/ef/language-reference/isof-entity-sql.md)|Określa, czy typ wyrażenia jest określonego typu lub jednego z jego podtypach.|  
|[OFTYPE](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md)|Zwraca kolekcję obiektów z wyrażenia zapytania, który jest określonego typu.|  
|[Konstruktor typu nazwanego](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md)|Używany do tworzenia wystąpień typów jednostek i typów złożonych.|  
|[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md)|Tworzy wystąpienie zestaw wielokrotny na podstawie listy wartości.|  
|[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)|Tworzy rekordy anonimowe, strukturę typu z co najmniej jedną wartość.|  
|[TREAT](../../../../../../docs/framework/data/adonet/ef/language-reference/treat-entity-sql.md)|Traktuje obiektu określonego typu podstawowego jako obiekt określonego typu pochodnego.|  
  
## <a name="other-operators"></a>Inne operatory  
 W poniższej tabeli wymieniono innych [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatorów.  
  
|Operator|Zastosowanie|  
|--------------|---------|  
|[+ (Łączenie ciągów)](../../../../../../docs/framework/data/adonet/ef/language-reference/string-concatenation-entity-sql.md)|Używany do ciągów w [!INCLUDE[esql](../../../../../../includes/esql-md.md)].|  
|[. (Dostęp do elementu członkowskiego)](../../../../../../docs/framework/data/adonet/ef/language-reference/member-access-entity-sql.md)|Używane do uzyskania dostępu do wartości właściwości lub pola wystąpienia typu strukturalnego modelu koncepcyjnego.|  
|[-- (Komentarz)](../../../../../../docs/framework/data/adonet/ef/language-reference/comment-entity-sql.md)|Obejmują [!INCLUDE[esql](../../../../../../includes/esql-md.md)] komentarze.|  
|[FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)|Definiuje funkcję śródwierszową, które mogą być wykonywane w kwerendzie SQL jednostki.|  
  
## <a name="see-also"></a>Zobacz też  
 [Jednostki języka SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
