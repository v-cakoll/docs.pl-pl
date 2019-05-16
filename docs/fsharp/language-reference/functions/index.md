---
title: Funkcje
description: Dowiedz się więcej o funkcji w F# i w jaki sposób F# obsługuje typowych konstrukcji programowania funkcjonalnego.
ms.date: 05/16/2016
ms.openlocfilehash: f68a36de7af2bdb803b0b633929aa472806f61aa
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645401"
---
# <a name="functions"></a>Funkcje

Funkcje są podstawową jednostką wykonywanie programu w dowolnym języku programowania. Tak jak w innych językach F# funkcji o nazwie, mogą mieć parametry i argumenty take i ma treść. F#obsługuje również konstrukcji programowania funkcjonalnego, takich jak traktowanie funkcje jako wartości, przy użyciu nazwy funkcji w wyrażeniach kompozycja funkcji w celu utworzenia nowych funkcji, funkcje rozwinięte i definicję niejawną funkcji za pomocą częściowego Stosowanie argumentów funkcji.

Funkcje są definiowane za pomocą `let` — słowo kluczowe, lub, jeśli funkcja jest cykliczna, `let rec` kombinacja słów kluczowych.

## <a name="syntax"></a>Składnia

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a>Uwagi

*Nazwy funkcji* jest identyfikatorem, który reprezentuje funkcję. *Listy parametrów* składa się z kolejnymi parametry, które są rozdzielone spacjami. Można określić jawnego typu dla każdego parametru, zgodnie z opisem w sekcji parametrów. Jeśli nie określisz typ określonego argumentu, kompilator spróbuje wywnioskować typu w treści funkcji. *Treści funkcji* składa się z wyrażenia. Wyrażenie, które stanowi treści funkcji jest zazwyczaj wyrażeniem złożonym, składający się z liczby wyrażeń, które skutkują ostatniego wyrażenia, która jest zwracana wartość. *Zwracanego typu* jest dwukropek następuje typu i jest opcjonalne. Jeśli nie zostanie jawnie typ wartości zwracanej, kompilator Określa typ zwracany z ostatniego wyrażenia.

Jest definicją prostej funkcji podobny do następującego:

```fsharp
let f x = x + 1
```

W poprzednim przykładzie nazwą funkcji jest `f`, argument jest `x`, która ma typ `int`, treści funkcji jest `x + 1`, i wartość zwracana jest typu `int`.

Funkcje mogą zostać oznaczone jako `inline`. Aby uzyskać informacje o `inline`, zobacz [funkcji śródwierszowych](../functions/inline-functions.md).

## <a name="scope"></a>Scope

Na dowolnym poziomie zakresu innego niż zakres modułu nie jest błąd, aby ponownie użyć nazwy wartości lub funkcji. Ponowne użycie nazwy później zgłoszonej nazwy zasłania nazwa zadeklarowanej wcześniej. Jednak w zakresie najwyższego poziomu w module, nazwy muszą być unikatowe. Na przykład poniższy kod generuje błąd, gdy się pojawi się w zakresie modułu, ale nie w przypadku, gdy się pojawi się wewnątrz funkcji:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

Ale poniższy kod jest dopuszczalne na dowolnym poziomie zakresu:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet102.fs)]

### <a name="parameters"></a>Parametry

Nazwy parametrów są wyświetlane po nazwie funkcji. Typ parametru, można określić, jak pokazano w poniższym przykładzie:

```fsharp
let f (x : int) = x + 1
```

Jeśli zostanie określony, następuje nazwa parametru i jest oddzielone od nazwy dwukropkiem. Jeżeli pominięto typu dla parametru typu parametru jest wnioskowany przez kompilator. Na przykład w poniższej definicji funkcji argument `x` jest wnioskowany typ `int` ponieważ 1 jest kolumną typu `int`.

```fsharp
let f x = x + 1
```

Jednak kompilator nawiązania funkcji jako ogólny, jak to możliwe. Na przykład należy zwrócić uwagę następujący kod:

```fsharp
let f x = (x, x)
```

Funkcja tworzy spójną kolekcję z jednym argumentem dowolnego typu. Ponieważ typ nie jest określony, funkcja może służyć za pomocą dowolnego typu argumentu. Aby uzyskać więcej informacji, zobacz [automatyczna Generalizacja](../generics/automatic-generalization.md).

## <a name="function-bodies"></a>Funkcja fragmentów

Treść funkcji może zawierać definicje zmiennych lokalnych i funkcje. Takie zmienne i funkcje są w zakresie treści bieżącej funkcji, ale nie poza nim. Jeśli masz włączoną opcją uproszczone składni, należy użyć wcięcia do wskazywania definicję w treści funkcji, jak pokazano w poniższym przykładzie:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

Aby uzyskać więcej informacji, zobacz [wytycznych formatowanie kodu](../code-formatting-guidelines.md) i [Pełna składnia](../verbose-syntax.md).

## <a name="return-values"></a>Wartości zwrócone

Kompilator używa ostatniego wyrażenia w treści funkcji do określenia typu i wartości zwracanej. Kompilator może wywnioskować typ ostatniego wyrażenia z poprzednich wyrażeń. W funkcji `cylinderVolume`, jak pokazano w poprzedniej sekcji, a typ `pi` jest określana na podstawie typ literału `3.14159` jako `float`. Kompilator używa typ `pi` można określić typu wyrażenia `h * pi * r * r` jako `float`. W związku z tym, ogólną zwracany typ funkcji jest `float`.

Aby jawnie określić wartość zwracaną, pisanie kodu w następujący sposób:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

Ponieważ kod został napisany powyżej, kompilator stosuje **float** do całej funkcji; Jeśli chodziło Ci o dotyczą również typy parametrów, użyj następującego kodu:

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a>Wywołanie funkcji

Możesz wywołać funkcji, określając nazwę funkcji, następuje spacja i następnie żadnych argumentów, które są rozdzielone spacjami. Na przykład, aby wywołać funkcję **cylinderVolume** i przypisz wynik do wartości **obj.**, należy napisać następujący kod:

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a>Częściowe stosowanie argumentów

Jeśli podasz mniej niż określoną liczbę argumentów, utworzysz nową funkcję, która oczekuje, że pozostałe argumenty. Ta metoda obsługi argumentów jest określany jako *currying* i jest to cecha funkcjonalności języków programowania, takich jak F#. Załóżmy, że pracujesz z dwóch rozmiarach potoku: jedna z nich ma promieniu **2.0** , a druga ma promieniu **3.0**. Można utworzyć funkcji, które określają ilość potoku w następujący sposób:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

Następnie będzie podać dodatkowy argument, zgodnie z potrzebami dla różnych długości potoku dwóch różnych rozmiarów:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet107.fs)]

## <a name="recursive-functions"></a>Funkcje rekursywne

*Funkcje rekursywne* funkcji, które wywołują się. Wymagają one, że podajesz **"rec"** następujące słowa kluczowego **umożliwiają** — słowo kluczowe. Wywołania funkcji cykliczne w treści funkcji, tak samo, jak powodowałoby wywołanie każde wywołanie funkcji. Oblicza następujących funkcji recursive *n*<sup>th</sup> Fibonacci numer. Sekwencja numer Fibonacci wiadomo, że od momentu antyków i sekwencja, w którym każdy kolejny numer to suma poprzednich dwóch liczb w sekwencji.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

Niektóre funkcje rekursywne może przepełnienie stosu program lub wykonać nieefektywnie, jeśli nie napiszesz ich ostrożnie i z świadomości technik specjalnych, takich jak użycie akumulatory i kontynuacji.

## <a name="function-values"></a>Wartości funkcji

W F#, wszystkie funkcje są traktowane jako wartości. w rzeczywistości są one znane jako *funkcji wartości*. Ponieważ funkcje są wartościami, ich może służyć jako argumenty do innych funkcji lub w innych kontekstach których wartości są używane. Poniżej znajduje się przykład funkcji, która przyjmuje wartość funkcji jako argumentem:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

Należy określić typ wartości funkcji za pomocą `->` tokenu. Po lewej stronie token ten jest typem argumentu, a po prawej stronie jest wartością zwracaną. W poprzednim przykładzie `apply1` jest funkcją, która przyjmuje funkcję `transform` jako argument, gdzie `transform` jest funkcją, która przyjmuje liczbę całkowitą i zwraca inną liczbę całkowitą. Poniższy kod przedstawia sposób użycia `apply1`:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

Wartość `result` będzie 101 po uruchomieniu poprzedniego kodu.

Wiele argumentów są rozdzielone przez kolejne `->` tokenów, jak pokazano w poniższym przykładzie:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

Wynik to 200.

## <a name="lambda-expressions"></a>Wyrażenia lambda

A *wyrażenia lambda* jest funkcją bez nazwy. W poprzednich przykładach, zamiast definiować nazwane funkcje **przyrostu** i **mul**, można użyć wyrażenia lambda w następujący sposób:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

Wyrażenia lambda są definiowane za pomocą `fun` — słowo kluczowe. Wyrażenia lambda przypomina definicji funkcji, chyba że zamiast `=` tokenu, `->` token jest używany do oddzielania na liście argumentów od treści funkcji. Tak jak w definicji funkcji regularnych typy argumentów można wywnioskować lub jawnie określony, a zwracany typ wyrażenia lambda jest wnioskowany z typu ostatniego wyrażenia w treści. Aby uzyskać więcej informacji, zobacz [wyrażenia Lambda: `fun` — Słowo kluczowe](../functions/lambda-expressions-the-fun-keyword.md).

## <a name="function-composition-and-pipelining"></a>Kompozycja funkcji i przetwarzanie potokowe

Funkcje w F# może składać się z innych funkcji. Kompozycja dwie funkcje **function1** i **function2** jest inną funkcję, która reprezentuje stosowania **function1** po zastosowaniu **function2**:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

Wynik jest 202.

Przetwarzanie potokowe umożliwia wywołania funkcji zostaną połączone jako kolejne czynności. Przetwarzanie potokowe działa w następujący sposób:

```fsharp
let result = 100 |> function1 |> function2
```

Wynik jest ponownie 202.

Operatory kompozycji mają dwie funkcje i zwrócić funkcję; z kolei operatorów potoku funkcji i argument i zwracają wartość. Poniższy przykład kodu pokazuje różnicę między operatorów potoku i kompozycji, pokazując różnice w sygnatur funkcji i użycia.

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

Możesz doprowadzić do przeciążenia metody typu, ale nie działa. Aby uzyskać więcej informacji, zobacz [metody](../members/methods.md).

## <a name="see-also"></a>Zobacz także

- [Wartości](../values/index.md)
- [Dokumentacja języka F#](../index.md)
