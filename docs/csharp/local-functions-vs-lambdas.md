---
title: Funkcje lokalne vs. wyrażenia lambda
description: Dowiedz się, dlaczego funkcje lokalne może być lepszym rozwiązaniem niż wyrażenia lambda.
ms.date: 06/27/2016
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.openlocfilehash: 2b98ebeeb3866779715fa629c2518f739e196ae8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740435"
---
# <a name="local-functions-compared-to-lambda-expressions"></a>Funkcje lokalne w porównaniu do wyrażenia lambda

Na pierwszy rzut oka [funkcje lokalne](programming-guide/classes-and-structs/local-functions.md) i [wyrażeń lambda](lambda-expressions.md) są bardzo podobne. W wielu przypadkach wybór między korzystaniem z wyrażenia lambda i funkcji lokalnych jest kwestią styl i osobistych preferencji. Istnieją jednak rzeczywistych różnic, w których można użyć jednej lub drugiej, należy pamiętać o.

Przeanalizujmy różnice między lokalnym funkcji i implementacji wyrażenia lambda silni algorytmu. Pierwszą wersję przy użyciu funkcji lokalnego:

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Porównaj tę implementację, wersji, który używa wyrażenia lambda:

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Funkcje lokalne mają nazwy. Wyrażenia lambda są metod anonimowych, które są przypisane do zmiennych, które są `Func` lub `Action` typów. Kiedy Deklarujesz funkcję lokalnego, typy argumentów i zwracanego typu są częścią deklaracji funkcji. Zamiast część treści lambda wyrażenia, typy argumentów i zwracanego typu należą deklaracji zmiennej typu wyrażenia lambda. Różnice te dwa może spowodować kod bardziej zrozumiały.

Funkcje lokalne mają różną asercja określonego przydziału niż wyrażenia lambda. Deklaracja funkcji lokalnych mogą być przywoływane z dowolnego miejsca kodu, gdzie są dostępne w zakresie. Wyrażenie lambda musi być przypisany do zmiennej delegata, zanim można uzyskać dostępu do (lub wywoływanym za pośrednictwem delegata, odwołuje się do wyrażenia lambda.) Zwróć uwagę, że wersji za pomocą wyrażenia lambda musi zadeklarować i zainicjować wyrażenia lambda `nthFactorial` przed zdefiniowaniem go. To nie powoduje to błąd czasu kompilacji do odwoływania się do `nthFactorial` przed przypisaniem go.
Te różnice oznacza, że cyklicznego algorytmy są łatwiej utworzyć przy użyciu funkcji lokalnych. Można zadeklarować i zdefiniuj funkcji lokalnej, który wywołuje sam siebie. Wyrażenia lambda należy zadeklarować i przypisać wartość domyślną, zanim zostaną ponownie przypisane do jednostki, który odwołuje się do tego samego wyrażenia lambda.

Asercja określonego przydziału reguły również wpływać na wszystkie zmienne, które są przechwytywane przez lokalny funkcja lub wyrażenie lambda. Funkcje lokalne i reguł wyrażeń lambda popytu, że wszystkie przechwycone zmienne zdecydowanie są przypisywane w punkcie, po przekonwertowaniu lokalnej funkcja lub wyrażenie lambda do delegata. Różnica polega na tym, że wyrażenia lambda są konwertowane na delegatów, gdy są one zgłoszone. Funkcje lokalne są konwertowane do delegatów tylko wtedy, gdy jest używany jako pełnomocnik. Jeśli zadeklarujesz funkcją lokalną i odwoływać wywołując jak metody, nie będzie można przekonwertować na delegata. Tej reguły można zadeklarować funkcji lokalnej w dowolnym miejscu wygodny w jej zasięgu. Są często do deklarowania funkcji lokalnych na końcu metody nadrzędnego po dowolnej instrukcji return.

Po trzecie kompilator będzie mógł wykonać analizy statycznej, który umożliwia funkcji lokalnych zdecydowanie przypisać przechwyconych zmiennych w obejmującym zakresie. Rozważmy następujący przykład:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Kompilator można określić, że `LocalFunction` zdecydowanie przypisuje `y` po wywołaniu. Ponieważ `LocalFunction` jest wywoływana przed `return` instrukcji `y` zdecydowanie przydzielono `return` instrukcji.

Analizy, które włącza analizę przykład umożliwia czwarty różnica.
W zależności od ich użycie funkcji lokalnych można uniknąć alokacji stosu, które zawsze są niezbędne do wyrażenia lambda. Jeśli funkcja lokalna nigdy nie jest konwertowany na obiekt delegowany, a żaden z przechwycone przez funkcję Lokalne zmienne są przechwytywane przez inne wyrażenia lambda lub funkcji lokalnych, które są konwertowane na obiekty delegowane, kompilator można uniknąć alokacji sterty. 

Rozważmy następujący przykład async:

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

Zawiera zamknięcia dla tego wyrażenia lambda `address`, `index` i `name` zmiennych. W przypadku funkcji lokalnych, może być obiekt, który implementuje zamknięcia `struct` typu. Tego typu struktury zostaną przekazane przez odwołanie do funkcji lokalnej. Różnica w implementacji będzie zapisywać w alokacji.

Wystąpienia niezbędne dla wyrażeń lambda oznacza alokacje dodatkową pamięć, która może być czynnikiem wydajności ścieżek kodu wrażliwego na czas.
Funkcje lokalne nie są naliczane to obciążenie. W powyższym przykładzie wersja funkcji lokalnych ma 2 alokacje mniej niż wersja wyrażenia lambda.

> [!NOTE]
> Funkcja lokalna wielokrotność ta metoda używa również klasy do zamknięcia. Czy zamknięcia dla funkcji lokalnej jest implementowany jako `class` lub `struct` jest szczegółowo opisuje implementacja. Funkcja lokalna może używać `struct` natomiast lambda będzie zawsze używać `class`.

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

Jedną z zalet końcowego nie zostało to pokazane w tym przykładzie jest, można zaimplementować jako Iteratory, za pomocą funkcji lokalnych `yield return` składni, aby wygenerować je sekvence hodnot. `yield return` Instrukcji jest niedozwolone w wyrażeniach lambda.

Funkcje lokalne, może wydawać się nadmiarowe wyrażenia lambda, mogą faktycznie służyć do różnych celów i mają różne sposoby zastosowania.
Funkcje lokalne są bardziej efektywne w przypadku, gdy chcesz napisać funkcję, która jest wywoływana tylko w kontekście innej metody.
