---
title: Funkcje lokalne a wyrażenia lambda
description: Dowiedz się, dlaczego funkcje lokalne mogą być lepszym wyborem niż wyrażenia lambda.
ms.date: 06/27/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.openlocfilehash: 13cc3fe47bbcd6a465347a6c991b2006586c78fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173344"
---
# <a name="local-functions-compared-to-lambda-expressions"></a>Funkcje lokalne w porównaniu z wyrażeniami lambda

Na pierwszy rzut oka [funkcje lokalne](programming-guide/classes-and-structs/local-functions.md) i [wyrażenia lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) są bardzo podobne. W wielu przypadkach wybór między używaniem wyrażeń lambda a funkcjami lokalnymi jest kwestią stylu i osobistych preferencji. Istnieją jednak rzeczywiste różnice w tym, gdzie można użyć jednego lub drugiego, że należy pamiętać.

Przyjrzyjmy się różnice między funkcji lokalnej i lambda wyrażenie implementacje algorytmu czynnikowego. Najpierw wersja za pomocą funkcji lokalnej:

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Kontrast, że implementacja z wersją, która używa wyrażeń lambda:

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Funkcje lokalne mają nazwy. Wyrażenia lambda są metody anonimowe, które są przypisane `Func` `Action` do zmiennych, które są lub typy. Podczas deklarowania funkcji lokalnej typy argumentów i zwracane są częścią deklaracji funkcji. Zamiast być częścią treści wyrażenia lambda, typy argumentów i zwracane są częścią deklaracji typu zmiennego wyrażenia lambda. Te dwie różnice mogą spowodować jaśniejszy kod.

Funkcje lokalne mają inne reguły dla określonego przypisania niż wyrażenia lambda. Deklaracja funkcji lokalnej można odwoływać się z dowolnej lokalizacji kodu, gdzie jest w zakresie. Wyrażenie lambda musi być przypisane do zmiennej delegata, zanim będzie dostępny (lub wywoływany za pośrednictwem delegata odwołującego się do wyrażenia lambda). Należy zauważyć, że wersja przy użyciu wyrażenia lambda musi zadeklarować i zainicjować wyrażenie lambda, `nthFactorial` przed zdefiniowaniem go. Nie wykonanie tego powoduje błąd czasu kompilacji `nthFactorial` dla odwoływania się przed przypisaniem go.
Różnice te oznaczają, że algorytmy cykliczne są łatwiejsze do tworzenia przy użyciu funkcji lokalnych. Można zadeklarować i zdefiniować funkcję lokalną, która wywołuje się. Wyrażenia Lambda muszą być zadeklarowane i przypisane wartość domyślną, zanim będą mogły być ponownie przypisane do treści, która odwołuje się do tego samego wyrażenia lambda.

Reguły przypisania określonego również wpływać na wszystkie zmienne, które są przechwytywane przez funkcję lokalną lub lambda wyrażenie. Zarówno funkcje lokalne, jak i reguły wyrażenia lambda wymagają, aby wszystkie przechwycone zmienne były zdecydowanie przypisywane w punkcie, w którym funkcja lokalna lub wyrażenie lambda są konwertowane na pełnomocnika. Różnica polega na tym, że wyrażenia lambda są konwertowane na delegatów, gdy są one zadeklarowane. Funkcje lokalne są konwertowane na delegatów tylko wtedy, gdy są używane jako pełnomocnik. Jeśli deklarujesz funkcję lokalną i odwołujesz się do niej tylko, wywołując ją jak metodę, nie zostanie ona przekonwertowana na pełnomocnika. Ta reguła umożliwia zadeklarowanie funkcji lokalnej w dowolnej dogodnej lokalizacji w jej otaczającym zakresie. Często deklaruje się funkcje lokalne na końcu metody nadrzędnej, po wszystkich instrukcjach zwrotu.

Po trzecie kompilator może wykonać analizę statyczną, która umożliwia funkcje lokalne, aby zdecydowanie przypisać przechwycone zmienne w otaczającym zakresie. Rozważmy następujący przykład:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Kompilator można `LocalFunction` określić, `y` że zdecydowanie przypisuje po wywołaniu. Ponieważ `LocalFunction` jest wywoływana przed instrukcją, `return` `y` `return` jest zdecydowanie przypisany do instrukcji.

Analiza, która umożliwia analizę przykładową, umożliwia czwartą różnicę.
W zależności od ich użycia funkcje lokalne można uniknąć alokacji sterty, które są zawsze niezbędne dla wyrażeń lambda. Jeśli funkcja lokalna nigdy nie jest konwertowana na delegata, a żadna ze zmiennych przechwyconych przez funkcję lokalną nie jest przechwytywana przez inne lambdas lub funkcje lokalne, które są konwertowane na delegatów, kompilator może uniknąć alokacji sterty.

Rozważmy ten przykład asynchronii:

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

Zamknięcie dla tego wyrażenia lambda `index` `name` zawiera `address`, i zmienne. W przypadku funkcji lokalnych obiekt, który implementuje zamknięcie `struct` może być typem. Ten typ struktury będzie przekazywany przez odwołanie do funkcji lokalnej. Ta różnica we wdrażaniu pozwoli zaoszczędzić na alokacji.

Wystąpienie niezbędne dla wyrażeń lambda oznacza dodatkowe alokacje pamięci, które mogą być czynnikiem wydajności w ścieżkach kodu o krytycznym znaczeniu dla czasu.
Funkcje lokalne nie ponoszą tego narzutu. W powyższym przykładzie wersja funkcji lokalnych ma 2 mniej alokacji niż wersja wyrażenia lambda.

> [!NOTE]
> Odpowiednik funkcji lokalnej tej metody używa również klasy do zamknięcia. Czy zamknięcie dla funkcji lokalnej jest `class` implementowana `struct` jako lub a jest szczegół implementacji. Funkcja lokalna `struct` może używać, podczas gdy lambda zawsze będzie używać `class`.

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

Jedną z zalet końcowych nie wykazano w tym przykładzie jest, że `yield return` funkcje lokalne mogą być implementowane jako iteratory, przy użyciu składni do tworzenia sekwencji wartości. Instrukcja `yield return` nie jest dozwolone w wyrażeniach lambda.

Podczas gdy funkcje lokalne mogą wydawać się zbędne dla wyrażeń lambda, w rzeczywistości służą one różnym celom i mają różne zastosowania.
Funkcje lokalne są bardziej efektywne dla przypadku, gdy chcesz napisać funkcję, która jest wywoływana tylko z kontekstu innej metody.
