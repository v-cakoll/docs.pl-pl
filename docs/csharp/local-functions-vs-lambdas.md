---
title: Funkcje lokalne, a wyrażenia lambda
description: Dowiedz się, dlaczego funkcje lokalne może być lepszym rozwiązaniem niż wyrażenia lambda.
ms.date: 06/27/2016
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.openlocfilehash: 0dfd34c5637bb4b8ae64a66e1ca1164fddec2cd7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="local-functions-compared-to-lambda-expressions"></a>Funkcje lokalne w porównaniu do wyrażenia lambda

Na pierwszy rzut oka [funkcje lokalne](programming-guide/classes-and-structs/local-functions.md) i [wyrażenia lambda](lambda-expressions.md) są bardzo podobne. W wielu przypadkach wybór między za pomocą wyrażenia lambda i funkcje lokalne polega na styl i osobistych preferencji. Istnieją jednak rzeczywistych różnice, w których można użyć jednej lub drugiej, który należy zwrócić uwagę.

Przeanalizujmy różnice między funkcji lokalnej i implementacje wyrażenia lambda silni algorytmu. Pierwszy wersji przy użyciu funkcji lokalnego:

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Natomiast tę implementację przy użyciu wersji, który używa wyrażenia lambda:

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Funkcje lokalne mają nazwy. Wyrażenia lambda są anonimowe metody, które są przypisane do zmiennych, które są `Func` lub `Action` typów. W deklaracji funkcji lokalnej typy argumentów i typ zwracany są częścią deklaracji funkcji. Zamiast część treści lambda wyrażenia, typy argumentów i typ zwracany są częścią deklaracji zmiennej typu wyrażenia lambda. Te dwie różnice może skutkować jaśniejszy kodu.

Funkcje lokalnego mają różne zasady dotyczące przypisania określoną niż wyrażenia lambda. Deklaracji funkcji lokalnej można odwoływać się z dowolnego miejsca kodu, w którym znajduje się w zakresie. Wyrażenia lambda musi być przypisany do zmiennej delegata, zanim można uzyskać dostępu do (lub wywoływanym za pośrednictwem delgate odwołania do wyrażenia lambda.) Powiadomienie, że utworzonych za pomocą wyrażenia lambda musi zadeklarować i zainicjuj wyrażenia lambda `nthFactorial` przed zdefiniowaniem go. W ten sposób nie powoduje błąd kompilacji dla przywołującego `nthFactorial` przed przypisaniem go.
Te różnice oznacza, że algorytmy cykliczne są łatwiejsze do utworzenia przy użyciu funkcji lokalnego. Można zadeklarować i zdefiniować funkcja lokalna, który wywołuje sam siebie. Wyrażenia lambda musi zadeklarować i przypisać wartość domyślną, aby można było ponownie przypisany do treści, która odwołuje się do tego samego wyrażenia lambda.

Ostateczne przypisania zasad dotyczy również zmienne, które są przechwytywane przez lokalny epression funkcji lub lamdba. Zarówno funkcje lokalne i reguł wyrażeń lambda popytu przechwyconych zmiennych są zdecydowanie przypisania w punkcie po przekonwertowaniu lokalnego funkcji lub wyrażenie lambda do delegata. Różnica polega na tym, że wyrażenia lambda są konwertowane na delegatów, jeśli są deklarowane jako. Funkcje lokalne są konwertowane na delegatów tylko wtedy, gdy jest używany jako pełnomocnik. Jeśli zadeklarowania funkcji lokalne, a tylko odwołania wywołując jak metody, nie zostanie przekonwertowany do delegata. Tej reguły można zadeklarowania funkcji lokalnych w dowolnej lokalizacji w otaczającym zakresie. Jest często stosowanym rozwiązaniem Zadeklaruj funkcje lokalne na końcu metody nadrzędnego po wszelkich instrukcjach return.

Trzecie kompilator może wykonywać analizy statycznej, który zapewnia funkcje lokalnego można zdecydowanie przypisać przechwyconych zmiennych w otaczającym zakresie. Rozważmy następujący przykład:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Kompilator może określić, że `LocalFunction` ostatecznie przypisuje `y` po wywołaniu. Ponieważ `LocalFunction` jest wywoływana przed `return` instrukcji, `y` definitiely przydzielono `return` instrukcji.

Analizy, który włącza analizę przykład umożliwia czwarty różnicy.
W zależności od ich użycia funkcje lokalne mogą uniknąć Alokacje sterty zawsze są niezbędne dla wyrażeń lambda. Jeśli funkcja lokalna nigdy nie jest konwertowany na delegata i Brak zmiennych przechwycone przez funkcję lokalne są przechwytywane przez inne wyrażenia lambda lub funkcje lokalne, które są konwertowane na obiekty delegowane, kompilator można uniknąć Alokacje sterty. 

Należy wziąć pod uwagę w tym przykładzie asynchronicznych:

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

Zawiera zamknięcia dla tego wyrażenia lambda `address`, `index` i `name` zmiennych. W przypadku funkcje lokalne, może być obiekt, który implementuje zamknięcia `struct` typu. Tego typu struct zostaną przekazane przez odwołanie do funkcji lokalnej. Różnica w implementacji czy zapisać przy alokacji.

Konkretyzacja niezbędne dla wyrażeń lambda oznacza alokacji dodatkową pamięć, które mogą być współczynnik wydajności w ścieżkach kodu wrażliwego na czas.
Funkcje lokalne nie nakładu tego. W powyższym przykładzie wersja funkcje lokalne ma 2 alokacji mniej niż wersja wyrażenia lambda.

> [!NOTE]
> Funkcja lokalna odpowiednikiem ta metoda używa również klasy do zamknięcia. Czy zamknięcia dla funkcji lokalnej jest zaimplementowany jako `class` lub `struct` jest szczegóły implementacji. Funkcja lokalna może używać `struct` należy zawsze użyje lambda `class`.

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

Jedną z zalet końcowego nie zostało to pokazane w tym przykładzie jest można zaimplementować jako Iteratory przy użyciu funkcji lokalnego `yield return` składnię, aby utworzyć sekwencję wartości. `yield return` Instrukcji jest niedozwolone w wyrażeniach lambda.

Funkcje lokalne mogą wydawać się nadmiarowe do wyrażenia lambda, ich faktycznie służyć do różnych celów i mają różnych zastosowań.
Funkcje lokalne są bardziej efektywne w przypadku, gdy chcesz zapisać funkcję, która jest wywoływana tylko w kontekście innej metody.
