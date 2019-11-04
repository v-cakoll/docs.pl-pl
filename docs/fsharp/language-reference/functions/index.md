---
title: Funkcje
description: Dowiedz się więcej F# o funkcjach w programie oraz o sposobie F# obsługi wspólnych konstrukcji programowania funkcjonalnego.
ms.date: 05/16/2016
ms.openlocfilehash: c6b8307f51ffcdc77fe4352b2305fca1f247ccbb
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423953"
---
# <a name="functions"></a>Funkcje

Funkcje są podstawową jednostką wykonywania programu w dowolnym języku programowania. Podobnie jak w innych językach, F# funkcja ma nazwę, może mieć parametry i przyjmować argumenty i ma treść. F#obsługuje również konstrukcje programowania funkcjonalnego, takie jak traktowanie funkcji jako wartości, za pomocą funkcji nienazwanych w wyrażeniach, skład funkcji do tworzenia nowych funkcji, funkcji rozwinięte i niejawnej definicji funkcji w formie częściowej stosowanie argumentów funkcji.

Można definiować funkcje za pomocą słowa kluczowego `let` lub, jeśli funkcja jest cykliczna, kombinacji słowa kluczowego `let rec`.

## <a name="syntax"></a>Składnia

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a>Uwagi

*Nazwa funkcji* jest identyfikatorem, który reprezentuje funkcję. *Lista parametrów* składa się z kolejnych parametrów, które są rozdzielone spacjami. Można określić typ jawny dla każdego parametru, zgodnie z opisem w sekcji parametry. Jeśli nie określisz określonego typu argumentu, kompilator próbuje wywnioskować typ z treści funkcji. *Treść funkcji* składa się z wyrażenia. Wyrażenie, które składa się z treści funkcji jest zwykle wyrażeniem złożonym składającym się z szeregu wyrażeń, które skutkują w ostatecznym wyrażeniu, które jest wartością zwracaną. *Typ zwracany* jest dwukropek, po którym następuje typ i jest opcjonalny. Jeśli nie określisz jawnie typu wartości zwracanej, kompilator określi typ zwracany z wyrażenia końcowego.

Prosta definicja funkcji jest podobna do następującej:

```fsharp
let f x = x + 1
```

W poprzednim przykładzie nazwa funkcji jest `f`, argument jest `x`, który ma `int`typu, treść funkcji jest `x + 1`, a zwracana wartość jest typu `int`.

Funkcje mogą być oznaczone `inline`. Aby uzyskać informacje na temat `inline`, zobacz [funkcje wbudowane](../functions/inline-functions.md).

## <a name="scope"></a>Zakres

Na dowolnym poziomie zakresu innym niż zakres modułu nie jest to błąd, aby ponownie użyć wartości lub nazwy funkcji. Jeśli ponownie używasz nazwy, nazwa zadeklarowana w dalszej części zaciemnienia nazwy zadeklarowanej wcześniej. Jednak w zakresie najwyższego poziomu w module nazwy muszą być unikatowe. Na przykład poniższy kod generuje błąd, gdy pojawia się on w zakresie modułu, ale nie gdy pojawia się wewnątrz funkcji:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

Jednak następujący kod jest akceptowalny na dowolnym poziomie zakresu:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet102.fs)]

### <a name="parameters"></a>Parametry

Nazwy parametrów są wyświetlane po nazwie funkcji. Możesz określić typ dla parametru, jak pokazano w następującym przykładzie:

```fsharp
let f (x : int) = x + 1
```

Jeśli określisz typ, następuje jego nazwa i jest oddzielona od nazwy średnikami. W przypadku pominięcia typu parametru typ parametru zostanie wywnioskowany przez kompilator. Na przykład w poniższej definicji funkcji argument `x` jest wywnioskowany jako typ `int`, ponieważ 1 jest typu `int`.

```fsharp
let f x = x + 1
```

Jednak kompilator podejmie próbę przeprowadzenia funkcji jako ogólnej, jak to możliwe. Na przykład Zwróć uwagę na następujący kod:

```fsharp
let f x = (x, x)
```

Funkcja tworzy krotkę z jednego argumentu dowolnego typu. Ponieważ typ nie jest określony, funkcja może być używana z dowolnym typem argumentu. Aby uzyskać więcej informacji, zobacz [Automatyczne uogólnianie](../generics/automatic-generalization.md).

## <a name="function-bodies"></a>Funkcja fragmentów

Treść funkcji może zawierać definicje zmiennych lokalnych i funkcji. Takie zmienne i funkcje są w zakresie treści bieżącej funkcji, ale nie poza nią. Po włączeniu opcji składnia uproszczona należy użyć wcięcia, aby wskazać, że definicja znajduje się w treści funkcji, jak pokazano w następującym przykładzie:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

Aby uzyskać więcej informacji, zobacz [wskazówki dotyczące formatowania kodu](../../style-guide/formatting.md) i [Pełna składnia](../verbose-syntax.md).

## <a name="return-values"></a>Wartości zwrócone

Kompilator używa końcowego wyrażenia w treści funkcji, aby określić wartość zwracaną i typ. Kompilator może wywnioskować typ wyrażenia końcowego z poprzednich wyrażeń. W funkcji `cylinderVolume`, pokazanej w poprzedniej sekcji, typ `pi` jest określany na podstawie typu literału, `3.14159` `float`. Kompilator używa typu `pi`, aby określić typ `h * pi * r * r` wyrażenia, które ma być `float`. W związku z tym, cały zwracany typ funkcji jest `float`.

Aby jawnie określić wartość zwracaną, napisz kod w następujący sposób:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

Ponieważ kod jest pisany powyżej, kompilator stosuje **zmiennoprzecinkowe** do całej funkcji; Jeśli zamierzasz zastosować ją również do typów parametrów, użyj następującego kodu:

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a>Wywołanie funkcji

Możesz wywoływać funkcje, określając nazwę funkcji, a następnie spację, a następnie wszelkie argumenty oddzielone spacjami. Na przykład, aby wywołać funkcję **cylinderVolume** i przypisać wynik do wartości **vol**, Napisz następujący kod:

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a>Częściowe stosowanie argumentów

Jeśli podasz mniej niż określoną liczbę argumentów, utworzysz nową funkcję, która oczekuje pozostałych argumentów. Ta metoda obsługi argumentów jest nazywana *currying* i jest cechą języków programowania funkcjonalnego, takich jak F#. Załóżmy na przykład, że pracujesz z dwoma rozmiarami potoku: jeden ma promień **2,0** , a drugi ma promień **3,0**. Można utworzyć funkcje, które określają ilość potoku w następujący sposób:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

Następnie należy podać dodatkowy argument w miarę potrzeby dla różnych długości potoku dwóch różnych rozmiarów:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet107.fs)]

## <a name="recursive-functions"></a>Funkcje rekursywne

*Funkcje cykliczne* to funkcje, które wywołują siebie. Wymagają one określenia słowa kluczowego **Rec** po słowie kluczowym **Let** . Wywołaj funkcję cykliczną z poziomu treści funkcji tak samo jak w przypadku wywołania funkcji. Następująca funkcja cykliczna oblicza n-<sup>ty</sup> numer Fibonacci. Sekwencja numerów Fibonacci była znana od czasu zamknięcia i jest sekwencją, w której każdy kolejny numer jest sumą poprzednich dwóch numerów w sekwencji.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

Niektóre funkcje cykliczne mogą przepełniać stosy programu lub działać niewydajnie, jeśli nie napiszesz ich z opieką i z świadomością technik specjalnych, takich jak korzystanie z akumulatorów i kontynuacji.

## <a name="function-values"></a>Wartości funkcji

W F#programie wszystkie funkcje są uznawane za wartości; w rzeczywistości są one nazywane *wartościami funkcji*. Ponieważ funkcje są wartościami, mogą one być używane jako argumenty do innych funkcji lub w innych kontekstach, w których są używane wartości. Poniżej znajduje się przykład funkcji, która przyjmuje wartość funkcji jako argument:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

Typ wartości funkcji można określić przy użyciu tokenu `->`. Po lewej stronie tego tokenu jest typem argumentu, a po prawej stronie jest wartością zwracaną. W poprzednim przykładzie `apply1` jest funkcją, która przyjmuje funkcję, `transform` jako argument, gdzie `transform` jest funkcją, która przyjmuje liczbę całkowitą i zwraca kolejną liczbę całkowitą. Poniższy kod ilustruje sposób używania `apply1`:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

Wartość `result` będzie 101 po powyższym kodzie.

Wiele argumentów jest rozdzielonych kolejnymi tokenami `->`, jak pokazano w następującym przykładzie:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

Wynikiem jest 200.

## <a name="lambda-expressions"></a>Wyrażenia lambda

*Wyrażenie lambda* jest funkcją bez nazwy. W poprzednich przykładach, zamiast definiować nazwane funkcje **Increment** i **MUL**, można użyć wyrażeń lambda w następujący sposób:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

Wyrażenia lambda można definiować za pomocą słowa kluczowego `fun`. Wyrażenie lambda przypomina definicję funkcji, z tą różnicą, że zamiast tokenu `=`, token `->` służy do rozdzielenia listy argumentów z treści funkcji. Podobnie jak w przypadku definicji funkcji regularnych, typy argumentów można wywnioskować lub określić jawnie, a zwracany typ wyrażenia lambda jest wywnioskowany na podstawie typu ostatniego wyrażenia w treści. Aby uzyskać więcej informacji, zobacz [wyrażenia lambda: słowo kluczowe `fun`](../functions/lambda-expressions-the-fun-keyword.md).

## <a name="function-composition-and-pipelining"></a>Kompozycja funkcji i przetwarzanie potokowe

Funkcje w F# programie mogą składać się z innych funkcji. Skład dwóch funkcji **function1** i **function2** jest kolejną funkcją, która reprezentuje aplikację **function1** , a następnie aplikację **function2**:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

Wynikiem jest 202.

Przetwarzanie potokowe umożliwia łączenie się z połączeniami funkcji w ramach kolejnych operacji. Potok działa w następujący sposób:

```fsharp
let result = 100 |> function1 |> function2
```

Wynik zostanie ponownie 202.

Operatory kompozycji mają dwie funkcje i zwracają funkcję; z kolei operatory potoku przyjmują funkcję i argument i zwracają wartość. Poniższy przykład kodu pokazuje różnicę między operatorami potoku i kompozycji, pokazując różnice w sygnaturach i użyciu funkcji.

```fsharp
// Function composition and pipeline operators compared.

let addOne x = x + 1
let timesTwo x = 2 * x

// Composition operator
// ( >> ) : ('T1 -> 'T2) -> ('T2 -> 'T3) -> 'T1 -> 'T3
let Compose2 = addOne >> timesTwo

// Backward composition operator
// ( << ) : ('T2 -> 'T3) -> ('T1 -> 'T2) -> 'T1 -> 'T3
let Compose1 = addOne << timesTwo

// Result is 5
let result1 = Compose1 2

// Result is 6
let result2 = Compose2 2

// Pipelining
// Pipeline operator
// ( |> ) : 'T1 -> ('T1 -> 'U) -> 'U
let Pipeline2 x = addOne x |> timesTwo

// Backward pipeline operator
// ( <| ) : ('T -> 'U) -> 'T -> 'U
let Pipeline1 x = addOne <| timesTwo x

// Result is 5
let result3 = Pipeline1 2

// Result is 6
let result4 = Pipeline2 2
```

## <a name="overloading-functions"></a>Przeładowywanie funkcji

Można przeciążać metody typu, ale nie Functions. Aby uzyskać więcej informacji, zobacz [metody](../members/methods.md).

## <a name="see-also"></a>Zobacz także

- [Wartości](../values/index.md)
- [Dokumentacja języka F#](../index.md)
