---
title: Wyrażenia lambda
description: Dowiedz się, aby używać wyrażeń lambda, które są bloków kodu wykonywalnego, które mogą być przekazywane jako argumenty.
ms.author: ronpet
author: rpetrusha
ms.date: 11/22/2016
ms.assetid: b6a0539a-8ce5-4da7-adcf-44be345a2714
ms.openlocfilehash: 2469e8a0fbf8181a720201637ab5ac5ef02055d4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523528"
---
# <a name="lambda-expressions"></a>Wyrażenia lambda #

A *wyrażenia lambda* to blok kodu (wyrażenia lub blok instrukcji), który jest traktowany jako obiekt. Może być przekazywany jako argument do metody, a także mogą być zwrócone przez funkcję wywołania metody. Wyrażenia lambda są często używane do:

- Przekazywanie kodu, który jest wykonywany do metod asynchronicznych, takich jak <xref:System.Threading.Tasks.Task.Run(System.Action)>.

- Zapisywanie [wyrażenia zapytań LINQ](linq/index.md).

- Tworzenie [drzew wyrażeń](expression-trees-building.md).

Wyrażenia lambda są kod, który może być reprezentowany jako obiekt delegowany lub jako drzewo wyrażenia, który kompiluje do delegata. Typ delegata określonego wyrażenia lambda jest zależna od jego parametrów i zwracają wartość. Wyrażenia lambda, które nie zwracają wartości odpowiadają określonym `Action` delegować, w zależności od jego liczba parametrów. Wyrażenia lambda, które zwracają wartości odpowiadają określonym `Func` delegować, w zależności od jego liczba parametrów. Na przykład, wyrażenie lambda, która ma dwa parametry, ale nie zwraca żadnej wartości odnosi się do <xref:System.Action%602> delegować. Wyrażenie lambda, która ma jeden parametr i zwraca wartość odpowiada <xref:System.Func%602> delegować.

Używa wyrażenia lambda `=>`, [operatora deklaracji lambda](language-reference/operators/lambda-operator.md), aby oddzielić listą parametrów lambda z jego kodu wykonywalnego. Aby utworzyć wyrażenie lambda, należy określić parametry wejściowe (jeśli istnieją) po lewej stronie operatora lambda i umieścić blok wyrażenia lub instrukcji po drugiej stronie. Na przykład, wyrażenie lambda jednowierszowego `x => x * x` określa parametr o nazwie `x` i zwraca wartość `x` kwadratów. To wyrażenie można przypisać do typu delegata, tak jak pokazano w poniższym przykładzie:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda1.cs#1)]

Lub można je przekazać bezpośrednio jako argumentu metody:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda2.cs#2)]

## <a name="expression-lambdas"></a>Lambdy wyrażeń ##

 Wyrażenie lambda z wyrażeniem po prawej stronie = > — operator jest wywoływana *wyrażenia lambda*. Lambdy wyrażeń są często używane w konstrukcji [drzew wyrażeń](expression-trees.md). Lambda wyrażenia zwraca wynik wyrażenia i ma następującą podstawową formę:

```csharp
(input parameters) => expression
```

Nawiasy są opcjonalne tylko wtedy, gdy lambda ma jeden parametr wejściowy; w przeciwnym razie są wymagane. Określanie braku parametrów wejściowych za pomocą pustych nawiasów:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#1)]

Jeśli liczba parametrów wejściowych wynosi dwa lub więcej, te parametry są rozdzielane przecinkami i umieszczone w nawiasach:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#2)]

Zazwyczaj kompilator używa wnioskowanie o typie przy określaniu typów parametrów. Jednak czasami jest trudne lub niemożliwe do kompilatorowi na wywnioskowanie typów wejściowych. W takiej sytuacji możesz jawnie określić typy, jak w poniższym przykładzie:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#3)]

Należy zauważyć, że w poprzednim przykładzie treść wyrażenia lambda może składać się z wywołania metody. Jednak w przypadku tworzenia drzew wyrażeń, które będą obliczane poza programem .NET Framework, takich jak programu SQL Server lub Entity Framework (EF), możesz powinien punktowanych za pomocą wywołań metod w wyrażeniach lambda, ponieważ te metody mogą nie mają znaczenia poza kontekstem implementacji .NET. Jeśli zdecydujesz się używać wywołań metod, w tym przypadku, należy sprawdzić je dokładnie w celu zapewnienia, że pomyślnie rozpoznane wywołania metody.

## <a name="statement-lambdas"></a>Lambdy instrukcji ##

Lambda instrukcji jest podobna do lambdy wyrażenia, z tym że instrukcje są ujęte w nawiasy klamrowe:

```csharp
(input parameters) => { statement; }
```

Treść lambdy instrukcji może składać się z dowolnej liczby instrukcji, jednak w praktyce jest ich zwykle nie więcej niż dwie lub trzy.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/statement1.cs#1)]

Lambd instrukcji, podobnie jak metod anonimowych, nie można używać do tworzenia drzew wyrażeń.

## <a name="async-lambdas"></a>Lambdy asynchroniczne ##

Możesz łatwo tworzyć wyrażenia lambda i instrukcje, które zawierają Przetwarzanie asynchroniczne przy użyciu [async](language-reference/keywords/async.md) i [await](language-reference/keywords/await.md) słów kluczowych. Na przykład przykład wywołuje `ShowSquares` metodę, która działa w sposób asynchroniczny.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/async1.cs#1)]

Aby uzyskać więcej informacji na temat sposobu tworzenia i używania metod asynchronicznych, zobacz [programowanie asynchroniczne z async i await](programming-guide/concepts/async/index.md).

## <a name="lambda-expressions-and-tuples"></a>Wyrażenia lambda i krotki ##

Począwszy od języka C# 7.0 w języku C# udostępnia wbudowaną obsługę krotek. Spójna Kolekcja może zapewnić jako argument do wyrażenia lambda i Wyrażenie lambda może również zwracać krotki. W niektórych przypadkach kompilator języka C# używa wnioskowanie o typie, aby określić typy elementów krotki.

Należy zdefiniować krotki umieszczając rozdzielana przecinkami lista składników w nawiasach. W poniższym przykładzie użyto krotki 5 składnikom do przekazania w sekwencji liczb do wyrażenia lambda, rozwiązanie quorum zwiększa dwukrotnie każdej wartości, która zwraca spójną kolekcję z 5 składnikami, który zawiera wynik mnożenia.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples1.cs#1)]

Zazwyczaj są nazywane polami krotki `Item1`, `Item2`itp. Można jednak zdefiniować krotki ze składnikami nazwane, tak jak w poniższym przykładzie.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples2.cs#1)]

Aby uzyskać więcej informacji na temat obsługi krotkami w języku C#, zobacz [typy krotek języka C#](tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Lambdy ze standardowych operatorów zapytań ##

LINQ do obiektów, między innymi implementacjami posiada parametr wejściowy, którego typ jest jednym z <xref:System.Func%601> rodziny ogólnych delegatów. Ci delegaci używać parametrów typu, aby zdefiniować liczbę i typ parametrów danych wejściowych oraz zwracany typ delegata. `Func` Obiekty delegowane są bardzo przydatne do hermetyzowania wyrażeń zdefiniowanych przez użytkownika, które są stosowane do każdego elementu w zestawie danych źródłowych. Na przykład, rozważmy <xref:System.Func%601> delegata, w których składnia jest następująca:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#1)]

Pełnomocnik może być utworzone przy użyciu kodu, jak pokazano poniżej

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#2)]

gdzie `int` jest parametrem wejściowym i `bool` jest wartością zwracaną. Wartość zwracana jest zawsze określona w ostatnim parametrze typu. Gdy następujące `Func` obiekt delegowany jest wywoływany, zwracana jest wartość PRAWDA lub FAŁSZ, aby wskazać, czy parametr wejściowy jest równy 5:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#3)]

Można również dostarczyć Wyrażenie lambda, gdy typ argumentu jest <xref:System.Linq.Expressions.Expression%601>, na przykład w standardowych operatorów zapytań, które są zdefiniowane w <xref:System.Linq.Queryable> typu. Po określeniu <xref:System.Linq.Expressions.Expression%601> argument, wyrażenie lambda jest kompilowana do drzewa wyrażenie. W poniższym przykładzie użyto [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) standardowego operatora zapytania.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#4)]

Kompilator może wywnioskować typ parametru wejściowego, ale można go również określić w sposób jawny. To konkretne wyrażenie lambda liczy te liczby całkowite (`n`), które podzielone przez dwa, dają resztę 1.

Poniższy przykład tworzy sekwencję zawierającą wszystkie elementy w `numbers` tablica, która poprzedzać 9, ponieważ jest to pierwszy numer w sekwencji, która nie spełnia warunku.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#5)]

W poniższym przykładzie określono wiele parametrów danych wejściowych, umieszczając je w nawiasach. Metoda zwraca wszystkie elementy w tablicy liczb, dopóki nie napotka liczby, w których wartość jest mniejsza niż jej porządkowym w tablicy.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#6)]

## <a name="type-inference-in-lambda-expressions"></a>Wnioskowanie o typie w wyrażeniach lambda ##

Podczas pisania wyrażeń lambda, często nie trzeba określać typu parametrów wejściowych, ponieważ kompilator może wywnioskować typ bazując na treść lambda, typy parametrów i innych czynników, jak opisano w specyfikacji języka C#. Dla większości standardowych operatorów zapytań pierwszy element danych wejściowych jest typem elementów w sekwencji źródłowej. Jeśli jest wykonywane zapytanie `IEnumerable<Customer>`, a następnie wywnioskowana jest zmienna wejściowa jest `Customer` obiektu, co oznacza, że masz dostęp do metod i właściwości:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/infer1.cs#1)]

Ogólne zasady wnioskowanie o typie dla wyrażeń lambda są:

- Wyrażenie lambda musi zawierać taką samą liczbę parametrów jak typ delegata.

- Każdy argument wejściowy w wyrażeniu lambda musi umożliwiać niejawną konwersję, aby odpowiadający mu parametr delegata.

- Wartość zwracana wyrażenia lambda (jeżeli istnieje) musi umożliwiać niejawną konwersję na zwracany typ delegata.

Należy zauważyć, że wyrażenia lambda same w sobie nie mają typu, ponieważ system typów wspólnych nie obejmuje wewnętrznej koncepcji „wyrażenia lambda”. Jednak czasami wygodnie jest mówić potocznie o „typie” wyrażenia lambda. W takich przypadkach typ odnosi się do typu delegata lub <xref:System.Linq.Expressions.Expression> typ do którego jest konwertowane Wyrażenie lambda.

## <a name="variable-scope-in-lambda-expressions"></a>Zakres zmiennych w wyrażeniach lambda ##

Wyrażenia lambda mogą odwoływać się do *zmiennych zewnętrznych* (zobacz [anonimowymi](programming-guide/statements-expressions-operators/anonymous-methods.md)) znajdujących się w zakresie metody definiującej funkcję lambda lub w zakresie typu, który zawiera wyrażenie lambda. Przechwytywane w ten sposób zmienne są przechowywane do użytku w wyrażeniu lambda, nawet gdyby w innym wypadku te zmienne znalazłyby się poza zakresem i zostałyby usunięte w ramach odśmiecania pamięci. Zewnętrzna zmienna musi być zdecydowanie przypisana, aby można jej było użyć w wyrażeniu lambda. W poniższym przykładzie pokazano te reguły.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/scope.cs#1)]

 Do zakresu zmiennych w wyrażeniach lambda są stosowane następujące reguły:

- Zmienna, która jest przechwytywana, nie będzie usuwana w ramach odśmiecania pamięci, dopóki odwołujący się do niej delegat nie będzie podlegał odśmiecaniu pamięci.

- Zmienne zawarte w wyrażeniu lambda nie są widoczne w metodzie zewnętrznej.

- Wyrażenie lambda nie może bezpośrednio przechwycić `in`, `ref`, lub `out` parametr z otaczającym metody.

- Instrukcja return w wyrażeniu lambda nie powoduje wykonania instrukcji return w otaczającej go metodzie.

- Wyrażenie lambda nie może zawierać `goto` instrukcji `break` instrukcji lub `continue` instrukcję, która znajduje się wewnątrz funkcji lambda, jeśli obiekt docelowy instrukcji jump leży poza blokiem. Błędem jest również instrukcja skoku poza blok funkcji lambda, jeśli obiekt docelowy znajduje się wewnątrz bloku.

## <a name="see-also"></a>Zobacz także ##

- [LINQ (Language-Integrated Query)](../standard/using-linq.md)
- [Metody anonimowe](programming-guide/statements-expressions-operators/anonymous-methods.md)
- [Drzewa wyrażeń](expression-trees.md)
