---
title: "Podstawowe informacje o wyrażeniach kwerend"
description: "Wprowadza pojęcia związane z wyrażenia zapytania"
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 027db1f8-346f-44d2-a16e-043fcea3a4e0
ms.openlocfilehash: 7a1cf9eea4c5d75c6bcb6d2f0d5f68a07e3158d0
ms.sourcegitcommit: 39b65a49271e082add68cb737b48fdbe09d24718
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2017
---
# <a name="query-expression-basics"></a>Podstawowe informacje o wyrażeniach kwerend

## <a name="what-is-a-query-and-what-does-it-do"></a>Co to jest kwerenda, i jakie zadania wykonuje? 

 A *zapytania* zestaw instrukcji w tym artykule opisano, jakie dane należy pobrać źródła danych danego (lub źródeł) i jakie kształt i organizacji zwróconych danych powinny mieć. Zapytanie różni się od wyników, które generuje.  
  
 Ogólnie rzecz biorąc źródło danych jest pogrupowane logicznie sekwencję elementów tego samego rodzaju. Na przykład w tabeli bazy danych SQL zawiera sekwencję wierszy. W pliku XML ma "sekwencji" elementów XML (chociaż są one zorganizowane hierarchicznie w strukturze drzewa). Kolekcja w pamięci zawiera sekwencję obiektów. 
  
 Z punktu widzenia aplikacji określonego typu i struktury oryginalnych danych źródłowych nie jest istotna. Źródło danych jako widzi aplikacji zawsze <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601> kolekcji. Na przykład w składniku LINQ to XML, źródło danych stają się widoczne jako `IEnumerable` \< <xref:System.Xml.Linq.XElement>>.  
  
 Mając tę sekwencję źródła, zapytania może wykonaj jedną z trzy czynności:  
  
-   Pobrać podzbioru elementów, aby utworzyć nową sekwencję bez modyfikowania poszczególne elementy. Zapytanie może sortowanie i grupowanie zwrócony sekwencji na różne sposoby, jak pokazano w poniższym przykładzie (założono `scores` jest `int[]`):  
  
     [!code-csharp[csrefQueryExpBasics#45](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_1.cs)]  
  
-   Pobrać sekwencję elementów, jak w poprzednim przykładzie, ale je na nowy typ obiektu transform. Na przykład zapytanie mogą pobrać tylko nazwisk z niektórych rekordów klientów w źródle danych. Lub może pobrać całego rekordu, a następnie użyć jej do utworzenia obiektu w pamięci innego typu, a nawet danych XML przed wygenerowaniem sekwencji wynik końcowy. W poniższym przykładzie przedstawiono projekcji z `int` do `string`. Należy pamiętać, nowy typ `highScoresQuery`.  
  
     [!code-csharp[csrefQueryExpBasics#46](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_2.cs)]  
  
-   Pobierz wartość singleton o źródle danych, takich jak:  
  
    -   Liczba elementów spełniających określony warunek.  
  
    -   Element, który ma największy lub co najmniej wartość.  
  
    -   Pierwszy element warunku lub Suma określonej wartości w określonym zestawie elementów. Na przykład następujące zapytanie zwraca liczbę wyników większa niż 80 z `scores` tablicy całkowitą:  
  
     [!code-csharp[csrefQueryExpBasics#47](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_3.cs)]  
  
     W poprzednim przykładzie, zwróć uwagę na użycie nawiasów wokół wyrażenia zapytania przed wywołaniem do `Count` metody. Można również express to przy użyciu nową zmienną do przechowywania konkretnych wynik. Ta technika jest bardziej przejrzysta, ponieważ przechowuje zmiennej, która przechowuje zapytania w oddzielnych przechowujący wynik zapytania.  
  
     [!code-csharp[csrefQueryExpBasics#48](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_4.cs)]  
  
 W poprzednim przykładzie zapytanie jest wykonywane w wywołaniu `Count`, ponieważ `Count` musi iterację w wynikach w celu ustalenia liczby elementów zwróconych przez `highScoresQuery`.  
  
## <a name="what-is-a-query-expression"></a>Co to jest wyrażenia zapytania?  

 A *zapytania wyrażenie* jest zapytaniem wyrażone w składni zapytania. Wyrażenia zapytania jest konstrukcji języka najwyższej jakości. Jest tak samo jak inne wyrażenie i mogą być używane w dowolnym kontekście, w którym wyrażenie C# jest poprawna. Wyrażenia zapytania zawiera zestaw klauzul napisany w składni deklaratywnej podobne do bazy danych SQL lub XQuery. Każdej klauzuli zawiera co najmniej jednego wyrażenia języka C# i wyrażenia te same jest wyrażenia zapytania lub zawiera wyrażenia zapytania.  
  
 Wyrażenia zapytania musi rozpoczynać się od [z](../language-reference/keywords/from-clause.md) klauzuli i musi się kończyć [wybierz](../language-reference/keywords/select-clause.md) lub [grupy](../language-reference/keywords/group-clause.md) klauzuli. Między pierwszą `from` klauzuli oraz za ostatni `select` lub `group` klauzuli może zawierać co najmniej jedną z klauzul opcjonalne: [gdzie](../language-reference/keywords/where-clause.md), [orderby](../language-reference/keywords/orderby-clause.md), [sprzężenia ](../language-reference/keywords/join-clause.md), [let](../language-reference/keywords/let-clause.md) i nawet dodatkowe [z](../language-reference/keywords/from-clause.md) klauzul. Można również użyć [do](../language-reference/keywords/into.md) — słowo kluczowe, aby włączyć wynik `join` lub `group` klauzuli służyć jako źródło dla klauzul dodatkowych kwerend w jednym wyrażeniu zapytania.  
  
### <a name="query-variable"></a>Zmienną zapytania  
 
 W składniku LINQ, zmienną zapytania jest żadnych zmiennej, która przechowuje *zapytania* zamiast *wyniki* zapytania. W szczególności zmienną zapytania jest zawsze typu wyliczalny, który utworzy sekwencję elementów, gdy jest on powtórzyć za pośrednictwem w `foreach` instrukcji lub bezpośrednie wywołanie jego `IEnumerator.MoveNext` metody.  
  
 Poniższy przykład kodu pokazuje wyrażenia prostego zapytania z jednego źródła danych, jedną klauzulę filtrowania jedną klauzulę porządkowania i nie przekształcania elementy źródłowe. `select` Klauzuli kończy się zapytania.  
  
 [!code-csharp[csrefQueryExpBasics#49](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_5.cs)]  
  
 W poprzednim przykładzie `scoreQuery` jest *zmienną zapytania* którego jest czasami określana jako just *zapytania*. Zmienną zapytania są przechowywane żadne dane rzeczywisty wynik, który jest tworzony w `foreach` pętli. I kiedy `foreach` wykonuje instrukcję, wyniki zapytania nie są zwracane przez zmienną zapytania `scoreQuery`. Zamiast są zwracane za pośrednictwem zmiennej iteracji `testScore`. `scoreQuery` Zmiennej można powtórzyć na sekundę `foreach` pętli. Takie same wyniki powoduje wygenerowanie tak długo, jak ten plik ani źródła danych został zmodyfikowany.  
  
 Zmienną zapytania mogą być przechowywane zapytania, które są jest wyrażone w składni zapytania lub składni metody lub kombinację obu. W poniższych przykładach zarówno `queryMajorCities` i `queryMajorCities2` są zmiennych zapytania:  
  
 [!code-csharp[csrefQueryExpBasics#50](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_6.cs)]  
  
 Z drugiej strony w poniższych dwóch przykładach pokazano zmiennych, które nie są zmiennymi zapytania, mimo że każda jest inicjowany z zapytania. Nie są one zmiennych zapytania, ponieważ zapisują wyników:  
  
 [!code-csharp[csrefQueryExpBasics#51](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_7.cs)]  
  
 Aby uzyskać więcej informacji o różnych sposobach express zapytań, zobacz [składnia zapytania i metody w technologii LINQ](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
#### <a name="explicit-and-implicit-typing-of-query-variables"></a>Jawne i niejawne, wpisując zmiennych zapytania  
 
 Ta dokumentacja zwykle zawiera jawnego typu zmienną zapytania aby pokazać relację typu zmienną zapytania i [klauzuli select](../language-reference/keywords/select-clause.md). Jednak umożliwia także [var](../language-reference/keywords/var.md) — słowo kluczowe nakazać kompilatora do wywnioskowania typu zmienną zapytania (lub lokalna zmienna) w czasie kompilacji. Na przykład przykład zapytania, które zostało przedstawione wcześniej w tym temacie może zostać wyrażona przy użyciu niejawnego wpisując:  
  
 [!code-csharp[csrefQueryExpBasics#52](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_8.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) i [relacje typu w składniku LINQ zapytania operacji](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
### <a name="starting-a-query-expression"></a>Uruchamianie wyrażenia zapytania  
 
 Wyrażenia zapytania musi rozpoczynać się od `from` klauzuli. Określa źródło danych, wraz z zmiennej zakresu. Zmienna zakresu reprezentuje każdy element w sekwencji źródłowej przejść wzdłuż sekwencji źródłowej. Zmienna zakresu jest silnie typizowane oparte na typ elementów w źródle danych. W poniższym przykładzie ponieważ `countries` jest tablicą `Country` obiekty, również jest typu zmienną zakresu `Country`. Ponieważ silnie jest typu zmienną zakresu, można użyć kropka można uzyskać dostępu do żadnych dostępnych elementów członkowskich tego typu.  
  
 [!code-csharp[csrefQueryExpBasics#53](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_9.cs)]  
  
 Zmienna zakresu znajduje się w zakresie, dopóki zapytanie zostanie zakończone średnikami lub z *kontynuacji* klauzuli.  
  
 Wyrażenia zapytania mogą zawierać wiele `from` klauzul. Użyj dodatkowych `from` klauzule podczas każdego elementu w sekwencji źródłowej jest elementem kolekcji lub zawiera on kolekcję. Załóżmy na przykład, że masz kolekcję `Country` obiektów, z których każdy zawiera kolekcję `City` obiektów o nazwie `Cities`. W zapytaniu `City` obiektów w każdej `Country`, użyj dwóch `from` klauzule, jak pokazano poniżej:  
  
 [!code-csharp[csrefQueryExpBasics#54](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_10.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [klauzuli from](../language-reference/keywords/from-clause.md).  
  
### <a name="ending-a-query-expression"></a>Zakończenie wyrażenia zapytania  
 
 Wyrażenia zapytania musi kończyć się albo `group` klauzuli lub `select` klauzuli.  
  
#### <a name="group-clause"></a>group — Klauzula  
 
 Użyj `group` klauzuli, aby utworzyć sekwencję grup są zorganizowane według klucza, który określisz. Klucz może być dowolnego typu danych. Na przykład poniższe zapytanie tworzy sekwencję grupy, która zawiera co najmniej jeden `Country` obiektów, którego klucz `char` wartość.  
  
 [!code-csharp[csrefQueryExpBasics#55](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_11.cs)]  
  
 Aby uzyskać więcej informacji na temat grupowania, zobacz [klauzuli group](../language-reference/keywords/group-clause.md).  
  
#### <a name="select-clause"></a>select — Klauzula  
 Użyj `select` klauzuli do produkcji wszystkich typów sekwencji. Prosty `select` klauzuli po prostu tworzy sekwencję tego samego typu obiektów jako obiekty, które są zawarte w źródle danych. W tym przykładzie źródło danych zawiera `Country` obiektów. `orderby` Tylko Sortuje elementy na nową kolejność w klauzuli i `select` klauzuli tworzy sekwencję kolejnos'ci `Country` obiektów.  
  
 [!code-csharp[csrefQueryExpBasics#56](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_12.cs)]  
  
 `select` Klauzuli może służyć do przekształcania danych źródłowych sekwencji nowych typów. Ta transformacja nosi również *projekcji*. W poniższym przykładzie `select` klauzuli *projekty* sekwencję typy anonimowe, która zawiera tylko podzbiór pól w oryginalnym elemencie. Należy pamiętać, że nowe obiekty są inicjowane za pomocą inicjatora obiektów.  
  
 [!code-csharp[csrefQueryExpBasics#57](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_13.cs)]  
  
 Aby uzyskać więcej informacji na temat wszystkich metod który `select` klauzuli może służyć do przekształcania źródła danych, zobacz [klauzuli select](../language-reference/keywords/select-clause.md).  
  
#### <a name="continuations-with-into"></a>Kontynuacje z "do"  
 
 Można użyć `into` — słowo kluczowe w `select` lub `group` klauzuli, aby utworzyć tymczasowy identyfikator, który przechowuje zapytania. W tym musi wykonywać operacje dodatkowe zapytania w zapytaniu po zgrupowaniu lub wybierz operacji. W poniższym przykładzie `countries` są pogrupowane według populacji w zakresach 10 milionów. Po tych grup zostaną utworzone, dodatkowe klauzul filtru się niektóre grupy, a następnie do sortowania grup w kolejności rosnącej kolejności. Aby wykonać te dodatkowe operacje, kontynuacji reprezentowany przez `countryGroup` jest wymagana.  
  
 [!code-csharp[csrefQueryExpBasics#58](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_14.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [do](../language-reference/keywords/into.md).  
  
### <a name="filtering-ordering-and-joining"></a>Filtrowanie, kolejność i dołączenie

 Między początkową `from` klauzul i zakończenie `select` lub `group` klauzuli, inne klauzule (`where`, `join`, `orderby`, `from`, `let`) są opcjonalne. Wszelkie opcjonalna klauzula może służyć zero lub wiele razy w treści wyrażenia zapytania.  
  
#### <a name="where-clause"></a>Klauzula where  

 Użyj `where` klauzuli, aby filtrować elementy z źródła danych oparte na co najmniej jednego wyrażenia predykatu. `where` Klauzuli w poniższym przykładzie ma jeden predykat z dwa warunki.  
  
 [!code-csharp[csrefQueryExpBasics#59](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_15.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [gdzie klauzuli](../language-reference/keywords/where-clause.md).  
  
#### <a name="orderby-clause"></a>Klauzula orderby

 Użyj `orderby` klauzuli sortowania wyników w porządku rosnącym lub malejącym. Można również określić kolejność sortowania dodatkowej. Poniższy przykład sortuje podstawowego `country` obiektów przy użyciu `Area` właściwości. Następnie wykonuje dodatkowej sortowania za pomocą `Population` właściwości.  
  
 [!code-csharp[csrefQueryExpBasics#60](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_16.cs)]  
  
 `ascending` — Słowo kluczowe jest opcjonalny; Jeśli nie kolejność jest określana jest domyślny porządek sortowania. Aby uzyskać więcej informacji, zobacz [klauzula orderby](../language-reference/keywords/orderby-clause.md).  
  
#### <a name="join-clause"></a>Klauzula join

 Użyj `join` klauzuli, aby skojarzyć i/lub połączyć elementy z jednego źródła danych z elementami z innego źródła danych na podstawie równości porównania między określone klucze w każdym elemencie. W składniku LINQ operacji łączenia są wykonywane na obiekty, których elementy mają różne typy sekwencji. Po dołączeniu dwóch sekwencji, należy użyć `select` lub `group` instrukcji, aby określić, który element mają być przechowywane w sekwencji danych wyjściowych. Umożliwia także typu anonimowego do łączenia z każdego zestawu skojarzonych elementów właściwości w nowy typ sekwencji danych wyjściowych. W poniższym przykładzie `prod` obiekty, których `Category` właściwość odpowiada jednej z kategorii w `categories` tablicy ciągów. Produkty których `Category` nie pasuje do dowolnego ciągu w `categories` są odfiltrowywane. `select` Nowy typ, którego właściwości są pobierane z obu projektów instrukcji `cat` i `prod`.  
  
 [!code-csharp[csrefQueryExpBasics#61](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_17.cs)]  
  
 Można również wykonywać sprzężenia grupy zapisując wyniki `join` operacji do zmiennej tymczasowej, za pomocą [do](../language-reference/keywords/into.md) — słowo kluczowe. Aby uzyskać więcej informacji, zobacz [klauzuli join](../language-reference/keywords/join-clause.md).  
  
#### <a name="let-clause"></a>Klauzula Let 

 Użyj `let` klauzuli, aby przechowywać wynik wyrażenia, takie jak wywołania metody w nowej zmiennej zakresu. W poniższym przykładzie zmienna zakresu `firstName` przechowuje pierwszy element tablicy ciągów, które są zwracane przez `Split`.  
  
 [!code-csharp[csrefQueryExpBasics#62](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_18.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [klauzula let](../language-reference/keywords/let-clause.md).  
  
### <a name="subqueries-in-a-query-expression"></a>Podzapytań w wyrażeniach kwerend  

 Sam zapytanie klauzula może zawierać wyrażenia zapytania jest czasami nazywany *podzapytania*. Każdy podzapytania rozpoczyna się od jego własnej `from` klauzuli, która nie musi wskazywać tego samego źródła danych, w pierwszym `from` klauzuli. Na przykład następujące zapytanie zawiera wyrażenia zapytania, który jest używany w instrukcji select, aby pobrać wyniki operacji grupowania.  
  
 [!code-csharp[csrefQueryExpBasics#63](../../../samples/snippets/csharp/concepts/linq/query-expression-basics_19.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: wykonanie podzapytania w operacji grupowania](perform-a-subquery-on-a-grouping-operation.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Podręcznik programowania C#](../programming-guide/index.md)  
 [Wyrażenia zapytań LINQ](index.md)  
 [Słowa kluczowe zapytania (LINQ)](../language-reference/keywords/query-keywords.md)  
 [Operatory standardowe zapytań — omówienie](../programming-guide/concepts/linq/standard-query-operators-overview.md)
