---
title: Funkcje (F#)
description: 'Poznaj funkcje F # oraz jak F # obsługuje typowych narzędzi programistycznych funkcjonalności.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4cdab85dd63cc74a4c6e7abf660f8f32cc088120
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="functions"></a>Funkcje

Funkcje są podstawową jednostkę wykonywania programu w dowolnym języku programowania. Jak w innych językach funkcja F # o nazwie, może mieć parametry i argumenty podjęcia i ma treść. F # obsługuje również funkcjonalności narzędzi programistycznych, takich jak traktowanie funkcje jako wartości, przy użyciu funkcji bez nazwy w wyrażeniach kompozycja funkcji do utworzenia nowych funkcji, funkcje rozwinięte i niejawnego definiowania funkcji i częściowe Stosowanie argumentów funkcji.

Należy zdefiniować przy użyciu funkcji `let` — słowo kluczowe, lub, jeśli funkcja jest rekursywny, `let rec` kombinacja słów kluczowych.


## <a name="syntax"></a>Składnia

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a>Uwagi
*Nazwy funkcji* jest identyfikatorem, który reprezentuje funkcję. *Listy parametrów* składa się z kolejnymi parametrów, które są rozdzielone spacjami. Zgodnie z opisem w sekcji Parametry można określić jawnego typu dla każdego parametru. Jeśli nie określisz typu określonego argumentu, kompilator próbuje wnioskować o typie z treści funkcji. *Treści funkcji* składa się z wyrażenia. Wyrażenie, które tworzą treść funkcji jest zwykle wyrażenia złożone składający się z liczby wyrażeń, które kulminacyjny w wyrażeniu końcowym, która jest zwracana wartość. *Zwracanego typu* dwukropek następuje typ i jest opcjonalne. Jeśli nie zostanie jawnie typ zwracanej wartości, kompilator Określa typ zwracany z ostatniego wyrażenia.

Definicja funkcji prostego podobny do następującego:

```fsharp
let f x = x + 1
```

W poprzednim przykładzie nazwa funkcji jest `f`, argument jest `x`, który ma typ `int`, treść funkcji jest `x + 1`, i jest zwracana wartość typu `int`.

Funkcje mogą być oznaczane `inline`. Aby uzyskać informacje o `inline`, zobacz [funkcji śródwierszowych](../functions/inline-functions.md).


## <a name="scope"></a>Zakres
Na dowolnym poziomie zakresu innego niż zakres modułu nie jest błąd, aby ponownie użyć nazwy wartości lub funkcji. Ponowne użycie nazwy, nazwa zadeklarowana później zasłania nazwa zadeklarowana wcześniej. Jednak w zakresie najwyższego poziomu w module, nazwy muszą być unikatowe. Na przykład poniższy kod tworzy błąd, gdy znajduje się na zakres modułu, a nie wydaje się wewnątrz funkcji:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

Ale następujący kod na dowolnym poziomie zakresu:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet102.fs)]
    
#### <a name="parameters"></a>Parametry
Nazwy parametrów są wyświetlane po nazwie funkcji. Typ parametru, można określić, jak pokazano w poniższym przykładzie:

```fsharp
let f (x : int) = x + 1
```

Jeśli określisz typu następuje nazwa parametru, a jest oddzielona od nazwy dwukropkiem. W przypadku pominięcia typ parametru, typ parametru jest wykryta przez kompilator. Na przykład w definicji funkcji następujący argument `x` jest wartością typu `int` ponieważ 1 jest typu `int`.

```fsharp
let f x = x + 1
```

Jednak kompilator nawiązania funkcji co. Na przykład należy uwzględnić następujący kod:

```fsharp
let f x = (x, x)
```

Funkcja tworzy spójną kolekcję z jednym argumentem dowolnego typu. Ponieważ typ nie jest określony, można użyć funkcji, w przypadku każdego typu argumentu. Aby uzyskać więcej informacji, zobacz [automatyczna Generalizacja](../generics/automatic-generalization.md).


## <a name="function-bodies"></a>Funkcja fragmentów
Treść funkcji może zawierać definicje zmiennych lokalnych i funkcje. Tych zmiennych i funkcji znajdują się w zakresie w treści bieżącej funkcji, ale nie poza nią. Jeśli opcja lightweight — składnia włączone, należy użyć wcięcie do wskazywania definicję w treści funkcji, jak pokazano w poniższym przykładzie:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

Aby uzyskać więcej informacji, zobacz [wytyczne formatowania kodu](../code-formatting-guidelines.md) i [Pełna składnia](../verbose-syntax.md).


## <a name="return-values"></a>Wartości zwrócone
Kompilator używa ostatniego wyrażenia w treści funkcji do określenia typu i wartości zwracanej. Kompilator może wnioskować o typie ostatniego wyrażenia z poprzedniego wyrażenia. W funkcji `cylinderVolume`, podanymi w poprzedniej sekcji, typ `pi` zależy od typu literał `3.14159` jako `float`. Kompilator używa typu `pi` można określić typu wyrażenia `h * pi * r * r` jako `float`. W związku z tym jest ogólnie zwracany typ funkcji `float`.

Aby jawnie określić wartość zwracana, wpisz następujący kod:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

Jak kod napisano powyżej, kompilator stosuje **float** do całej funkcji; Jeśli chcesz zastosować je na typy parametrów, użyj następującego kodu:

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a>Wywołanie funkcji
Wywołania funkcji, określając nazwę funkcji, następuje spacja i następnie żadnych argumentów, które są rozdzielone spacjami. Na przykład, aby wywołać funkcję **cylinderVolume** i przypisz wynik do wartości **obj.**, wpisz następujący kod:

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a>Częściowe stosowanie argumentów
Jeśli podasz mniej niż określona liczba argumentów, utworzysz nową funkcję, która oczekuje pozostałych argumentów. Ta metoda obsługi argumentów jest określany jako *currying* i jest to cecha funkcjonalności języków programowania, takich jak F #. Na przykład, załóżmy, że korzystasz z dwóch rozmiary potoku: jeden z nich ma radius z **2.0** i innych ma radius z **3.0**. Można utworzyć funkcji określające wolumin potoku, w następujący sposób:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

Następnie musi dostarczać dodatkowego argumentu, zgodnie z potrzebami dla różnych długości potoku dwóch różnych rozmiarów:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet107.fs)]
    
## <a name="recursive-functions"></a>Funkcje rekursywne
*Funkcje rekursywne* są funkcje, które wywołują się. Wymagają one, że możesz określić **rec** następujące słowa kluczowego **let** — słowo kluczowe. Wywołania funkcji cyklicznej w treści funkcji tak samo, jak powodowałoby wywołanie wszystkie wywołania funkcji. Oblicza następujących funkcji recursive *n*th Fibonacci numer. Sekwencja numer Fibonacci wiadomo, że od momentu antyków i jest sekwencję, w którym każdą liczbę kolejnych to suma poprzednich dwóch liczb w sekwencji.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

Niektóre funkcje rekursywne może przepełnienie stosu program lub Niewydajne wykonania, jeśli użytkownik nie zapisuj je ostrożność i z funkcją rozpoznawanie specjalne technik, takich jak użycie akumulatorów i kontynuacje.


## <a name="function-values"></a>Wartości funkcji
W języku F # wszystkie funkcje są traktowane jako wartości. w rzeczywistości są określane jako *funkcji wartości*. Ponieważ funkcje wartości, użyciem jako argumenty do innych funkcji, lub w innych kontekstach, gdzie są używane wartości. Poniżej przedstawiono przykład funkcji, która przyjmuje wartość funkcji jako argument:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

Określ typ wartości funkcji przy użyciu `->` tokenu. Po lewej stronie token ten jest typem argumentu, a po prawej stronie jest zwracana wartość. W poprzednim przykładzie `apply1` to funkcja, która przyjmuje funkcji `transform` jako argument, gdzie `transform` jest funkcją, która przyjmuje całkowitą i zwraca inną liczbę całkowitą. Poniższy kod przedstawia sposób użycia `apply1`:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

Wartość `result` będzie 101 po poprzednim kodzie.

Używanie wielu argumentów są rozdzielone przez kolejne `->` tokeny, jak pokazano w poniższym przykładzie:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

Wynik jest 200.


## <a name="lambda-expressions"></a>Wyrażenia lambda
A *wyrażenia lambda* jest funkcja bez nazwy. W poprzednich przykładach, zamiast definiować o nazwie funkcji **przyrostu** i **mul**, można użyć wyrażenia lambda w następujący sposób:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

Zdefiniuj wyrażenia lambda za pomocą `fun` — słowo kluczowe. Wyrażenia lambda podobny definicji funkcji, z wyjątkiem zamiast `=` token, `->` tokenu jest używany do oddzielania listy argumentów z treści funkcji. W definicji funkcji regularnym można wywnioskować lub jawnie określone typy argumentów, a zwracany typ wyrażenia lambda jest wywnioskowany na podstawie typ ostatniego wyrażenia w treści. Aby uzyskać więcej informacji, zobacz [wyrażenia Lambda: `fun` — słowo kluczowe](../functions/lambda-expressions-the-fun-keyword.md).


## <a name="function-composition-and-pipelining"></a>Kompozycja funkcji i przetwarzanie potokowe
Funkcje języka F # może składać się z innych funkcji. Kompozycja dwie funkcje **function1** i **function2** jest innej funkcji, która reprezentuje stosowania **function1** po zastosowaniu **function2**:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

Wynik jest 202.

Przetwarzanie potokowe umożliwia wywołania funkcji, można je połączyć ze sobą jako kolejnych czynności. Przetwarzanie potokowe działa w następujący sposób:

```fsharp
let result = 100 |> function1 |> function2
```

Wynik jest ponownie 202.

Operatory kompozycji przyjmować dwie funkcje i zwracać funkcji; z kolei operatorów potoku funkcji i argument i zwracać wartość. W poniższym przykładzie kodu pokazano różnicę między operatorów potoku i kompozycji, pokazując różnice w funkcji podpisów i użycia.

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
Można przeciążać metod z typem, ale nie działa. Aby uzyskać więcej informacji, zobacz [metody](../members/methods.md).


## <a name="see-also"></a>Zobacz też
[Wartości](../values/index.md)

[Dokumentacja języka F#](../index.md)
