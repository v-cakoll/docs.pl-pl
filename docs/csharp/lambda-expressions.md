---
title: "Wyrażenia lambda"
description: "Odchudzona można użyć wyrażenia lambda, które są bloki kodu wykonywalnego, które mogą być przekazywane jako argumenty."
keywords: ".NET, .NET core, wyrażenia lambda, wyrażenia lambda, obiektów delegowanych"
ms-author: ronpet
author: rpetrusha
ms.date: 11/22/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b6a0539a-8ce5-4da7-adcf-44be345a2714
ms.openlocfilehash: 1a97d830c675c8e3980eddae78f3face279ec6dc
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2017
---
# <a name="lambda-expressions"></a>Wyrażenia lambda #

A *wyrażenia lambda* to blok kodu (wyrażenia lub blok instrukcji), który jest traktowany jako obiekt. Mogą być przekazywane jako argument do metody, a także może być zwracany przez metodę wywołania. Wyrażenia lambda są często używane dla:

- Przekazywanie kod, który ma zostać wykonana do metod asynchronicznych, takich jak <xref:System.Threading.Tasks.Task.Run(System.Action)>.

- Zapisywanie [wyrażenia zapytań LINQ](linq/index.md).

- Tworzenie [drzew wyrażeń](expression-trees-building.md).

Wyrażenia lambda są kodu, który może być reprezentowany jako pełnomocnik lub jako drzewo wyrażenia, który kompiluje się do delegata. Typ delegata określonego wyrażenia lambda zależy od jego parametrów i zwracać wartość. Wyrażenia lambda, które nie zwracają wartości odpowiadają określonym `Action` delegować, w zależności od jego liczby parametrów. Wyrażenia lambda, które zwracają wartość odpowiada określonym `Func` delegować, w zależności od jego liczby parametrów. Na przykład, wyrażenie lambda, która ma dwa parametry, ale nie zwraca wartości odpowiada <xref:System.Action%602> delegowanie. Wyrażenie lambda, który ma jeden parametr i zwraca wartość odpowiada <xref:System.Func%602> delegowanie.

Wyrażenie lambda `=>`, [operator deklaracji lambda](language-reference/operators/lambda-operator.md), aby oddzielić listy parametrów lambda z jego kodu wykonywalnego. Aby utworzyć wyrażenie lambda, należy określić parametry wejściowe (jeśli istnieją) po lewej stronie operatora lambda i umieść blok wyrażenia lub instrukcji z drugiej strony. Na przykład, wyrażenie lambda jednowierszowego `x => x * x` określa parametr o nazwie `x` i zwraca wartość `x` kwadratów. To wyrażenie można przypisać do typu delegata, tak jak pokazano w poniższym przykładzie:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda1.cs#1)]

Lub przekaż go bezpośrednio jako argument metody:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda2.cs#2)]

## <a name="expression-lambdas"></a>Wyrażenia lambda ##

 Wyrażenia lambda za pomocą wyrażenia po prawej stronie = > — operator jest wywoływana *wyrażenia lambda*. Wyrażenia lambda są często używane w konstrukcji [drzew wyrażeń](expression-trees.md). Lambda wyrażenia zwraca wynik wyrażenia i ma następującą podstawową formę:

```csharp
(input parameters) => expression
```

Nawiasy są opcjonalne tylko wtedy, gdy lambda ma jeden parametr wejściowy; w przeciwnym razie są wymagane. Określanie braku parametrów wejściowych za pomocą pustych nawiasów:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#1)]

Jeśli liczba parametrów wejściowych wynosi dwa lub więcej, te parametry są rozdzielane przecinkami i umieszczone w nawiasach:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#2)]

Zwykle kompilator używa wnioskowanie o typie przy określaniu typów parametrów. Jednak czasami jest trudne lub niemożliwe dla kompilatora w celu uwzględnienia typów wejściowych. W takiej sytuacji możesz określić typy jawnie, jak w poniższym przykładzie:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#3)]

Należy zauważyć, że w poprzednim przykładzie treść wyrażenia lambda może składać się z wywołania metody. Jednak w przypadku tworzenia drzewa wyrażeń, które są oceniane poza programu .NET Framework, takich jak w programie SQL Server lub Entity Framework (EF), użytkownik powinien zaniechania przy użyciu wywołania metody w wyrażeniach lambda, ponieważ te metody mogą mieć znaczenia poza kontekstem implementacji .NET. Jeśli chcesz użyć w tym przypadku wywołania metody, należy sprawdzić je, aby dokładnie upewnij się, że pomyślnie rozpoznane wywołania metody.

## <a name="statement-lambdas"></a>Instrukcji lambda ##

Lambda instrukcji jest podobna do lambdy wyrażenia, z tym że instrukcje są ujęte w nawiasy klamrowe:

```csharp
(input parameters) => { statement; }
```

Treść lambdy instrukcji może składać się z dowolnej liczby instrukcji, jednak w praktyce jest ich zwykle nie więcej niż dwie lub trzy.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/statement1.cs#1)]

Lambd instrukcji, podobnie jak metod anonimowych, nie można używać do tworzenia drzew wyrażeń.

## <a name="async-lambdas"></a>Asynchronicznych wyrażeń lambda ##

Można jednak łatwo tworzyć wyrażenia lambda i instrukcje zawierające przetwarzania asynchronicznego przy użyciu [async](language-reference/keywords/async.md) i [await](language-reference/keywords/await.md) słów kluczowych. Na przykład przykład wywołuje `ShowSquares` metodę, która działa w sposób asynchroniczny.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/async1.cs#1)]

Aby uzyskać więcej informacji o sposobie tworzenia i używania metody asynchroniczne, zobacz [programowanie asynchroniczne z async i await](programming-guide/concepts/async/index.md).

## <a name="lambda-expressions-and-tuples"></a>Wyrażenia lambda i spójnych kolekcji ##

Począwszy od wersji 7.0 C# w języku C# udostępnia wbudowaną obsługę spójnych kolekcji. Krotka można podać jako argument wyrażenia lambda, a w wyrażeniu lambda może również zwrócić spójnych kolekcji. W niektórych przypadkach kompilatora C# używa wnioskowanie o typie, aby określić typy składników spójnej kolekcji. 

Należy zdefiniować krotka umieszczając rozdzielana przecinkami lista składników w nawiasach. W poniższym przykładzie użyto krotki ze składnikami 5 do przekazania wyrażenia lambda, który podwaja każdej wartości i zwraca spójną kolekcję z 5 składniki zawierający wynik mnożenia sekwencji liczb.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples1.cs#1)]

Zwykle są nazywane pola krotka `Item1`, `Item2`itp. Można jednak zdefiniować krotka ze składnikami nazwanego, tak jak w poniższym przykładzie.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples2.cs#1)]

Aby uzyskać więcej informacji na obsługę krotek w języku C#, zobacz [typów C# krotki](tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Wyrażenia lambda z standardowych operatorów zapytań ##

LINQ do obiektów, między innymi implementacjami ma parametr wejściowy, którego typ jest jednym z <xref:System.Func%601> rodzina delegatów. Te obiekty delegowane używać parametrów typu, aby określić liczbę i typ parametrów wejściowych i typ zwracany delegata. `Func`Obiekty delegowane są bardzo przydatne w przypadku hermetyzując wyrażenia zdefiniowane przez użytkownika, które są stosowane do każdego elementu w zestawie danych źródłowych. Rozważmy na przykład <xref:System.Func%601> delegata, którego składnia jest następująca:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#1)]

Delegat można wdrożyć z kodem podobne do poniższych

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#2)]

gdzie `int` jest parametrem wejściowym i `bool` jest zwracana wartość. Wartość zwracana jest zawsze określona w ostatnim parametrze typu. Gdy następujące `Func` jest wywoływany delegat, zwraca wartość PRAWDA lub FAŁSZ, aby wskazać, czy parametr wejściowy jest równa 5:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#3)]

Może też podawać wyrażenia lambda, gdy typ argumentu jest <xref:System.Linq.Expressions.Expression%601>, na przykład w przypadku standardowych operatorów zapytań zdefiniowane w <xref:System.Linq.Queryable> typu. Po określeniu <xref:System.Linq.Expressions.Expression%601> kompilowania argument, wyrażenie lambda na drzewo wyrażenia. W poniższym przykładzie użyto [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) — operator zapytań standardowa.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#4)]

Kompilator może wywnioskować typ parametru wejściowego, ale można go również określić w sposób jawny. To wyrażenie lambda określonej liczby tych liczb całkowitych (`n`), który podzielony przez dwa, mieć reszty 1.

Poniższy przykład tworzy sekwencję, który zawiera wszystkie elementy w `numbers` tablica, która poprzedzać 9, ponieważ jest to pierwszy numer w sekwencji, które nie spełniają warunek.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#5)]

W poniższym przykładzie wiele parametrów wejściowych ujęte w nawiasy. Metoda zwraca wszystkie elementy w tablicy liczb, aż do napotkania numer, którego wartość jest mniejsza niż jego porządkowym w tablicy.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#6)]

## <a name="type-inference-in-lambda-expressions"></a>Wnioskowanie o typie w wyrażeniach lambda ##

Podczas pisania wyrażeń lambda, często nie trzeba określać typ dla parametrów wejściowych, ponieważ kompilator może wnioskować o typie na podstawie treści lambda, typy parametrów i innych czynników, zgodnie z opisem w specyfikacji języka C#. Dla większości standardowych operatorów zapytań pierwszy element danych wejściowych jest typem elementów w sekwencji źródłowej. Wyszukując `IEnumerable<Customer>`, następnie wejściowego zmiennej jest wywnioskowany jako `Customer` obiektu, co oznacza, że masz dostęp do właściwości i metod:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/infer1.cs#1)]

Ogólne zasady wnioskowanie o typie dla wyrażeń lambda są:

- Wyrażenie lambda musi zawierać taką samą liczbę parametrów jak typ delegata.

- Każdy argument wejściowy w wyrażeniu lambda musi być umożliwiają niejawnej konwersji na jego odpowiadającego mu parametru delegowanego.

- Wartość zwracana wyrażenia lambda (jeżeli istnieje) musi umożliwiać niejawną konwersję na zwracany typ delegata.

Należy zauważyć, że wyrażenia lambda same w sobie nie mają typu, ponieważ system typów wspólnych nie obejmuje wewnętrznej koncepcji „wyrażenia lambda”. Jednak czasami wygodnie jest mówić potocznie o „typie” wyrażenia lambda. W takich przypadkach typ odwołuje się do typu delegata lub <xref:System.Linq.Expressions.Expression> wpisz jest konwertowane Wyrażenie lambda.

## <a name="variable-scope-in-lambda-expressions"></a>Zakres zmiennych w wyrażeniach lambda ##

Wyrażenia lambda, może się odwoływać do *zmienne zewnętrzne* (zobacz [metod anonimowych](programming-guide/statements-expressions-operators/anonymous-methods.md)) w zakresie w metodę, która definiuje funkcję lambda, lub w zakresie w typie, który zawiera wyrażenie lambda. Przechwytywane w ten sposób zmienne są przechowywane do użytku w wyrażeniu lambda, nawet gdyby w innym wypadku te zmienne znalazłyby się poza zakresem i zostałyby usunięte w ramach odśmiecania pamięci. Zewnętrzna zmienna musi być zdecydowanie przypisana, aby można jej było użyć w wyrażeniu lambda. W poniższym przykładzie pokazano tych reguł.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/scope.cs#1)]

 Do zakresu zmiennych w wyrażeniach lambda są stosowane następujące reguły:

- Zmienna, która jest przechwytywana, nie będzie usuwana w ramach odśmiecania pamięci, dopóki odwołujący się do niej delegat nie będzie podlegał odśmiecaniu pamięci.

- Zmienne zawarte w wyrażeniu lambda nie są widoczne w metodzie zewnętrznej.

- Wyrażenia lambda nie może bezpośrednio przechwytywania `ref` lub `out` parametru z metody otaczającej.

- Instrukcja return w wyrażeniu lambda nie powoduje wykonania instrukcji return w otaczającej go metodzie.

- Wyrażenia lambda nie może zawierać `goto` instrukcji, `break` instrukcji lub `continue` instrukcji, która znajduje się wewnątrz funkcji lambda w przypadku docelowej instrukcji skok poza blokiem. Błędem jest również instrukcja skoku poza blok funkcji lambda, jeśli obiekt docelowy znajduje się wewnątrz bloku.

## <a name="see-also"></a>Zobacz także ##

[LINQ (zapytania o języku zintegrowanym)](../standard/using-linq.md)   
[Metody anonimowe](programming-guide/statements-expressions-operators/anonymous-methods.md)   
[Drzewa wyrażeń](expression-trees.md)
