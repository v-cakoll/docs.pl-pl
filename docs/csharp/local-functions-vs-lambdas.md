---
title: Funkcje lokalne a wyrażenia lambda
description: Dowiedz się, dlaczego funkcje lokalne mogą być lepszym wyborem niż wyrażenia lambda.
ms.date: 06/27/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.openlocfilehash: a644b6868a37b3d6231a514dc37030cae062785a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038800"
---
# <a name="local-functions-compared-to-lambda-expressions"></a>Funkcje lokalne w porównaniu z wyrażeniami lambda

Na pierwszy rzut oka [funkcje lokalne](programming-guide/classes-and-structs/local-functions.md) i [wyrażenia lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) są bardzo podobne. W wielu przypadkach wybór między wyrażeniami lambda i funkcjami lokalnymi jest kwestią stylu i preferencji osobistych. Istnieją jednak rzeczywiste różnice w tym, gdzie można korzystać z jednej z nich lub drugiej.

Sprawdźmy różnice między funkcją lokalną a implementacją wyrażenia lambda algorytmu silnia. Pierwsza wersja przy użyciu funkcji lokalnej:

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Kontrast tej implementacji z wersją, która używa wyrażeń lambda:

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Funkcje lokalne mają nazwy. Wyrażenia lambda są metodami anonimowymi przypisanymi do zmiennych, które są `Func` lub `Action`. Gdy deklarujesz funkcję lokalną, typy argumentów i typ zwracany są częścią deklaracji funkcji. Zamiast być częścią treści wyrażenia lambda, typy argumentów i typ zwracany są częścią deklaracji typu zmiennej wyrażenia lambda. Te dwie różnice mogą spowodować wyraźniejszy kod.

Funkcje lokalne mają różne reguły dla określonego przypisania niż wyrażenia lambda. Deklaracja funkcji lokalnej może być przywoływana z dowolnego miejsca w kodzie, w którym znajduje się w zakresie. Wyrażenie lambda musi być przypisane do zmiennej delegata, zanim będzie można uzyskać do niej dostęp (lub wywołać za pomocą delegata odwołującego się do wyrażenia lambda). Należy zauważyć, że wersja używająca wyrażenia lambda musi deklarować i inicjować wyrażenie lambda, `nthFactorial` przed jego zdefiniowaniem. Nie powoduje to błędu czasu kompilacji dla odwołania `nthFactorial` przed przypisaniem.
Różnice te oznaczają, że algorytmy cykliczne są łatwiejsze do tworzenia przy użyciu funkcji lokalnych. Można zadeklarować i zdefiniować funkcję lokalną, która wywołuje samą siebie. Wyrażenia lambda muszą być zadeklarowane i przypisane do wartości domyślnej przed ponownym przypisaniem do treści, która odwołuje się do tego samego wyrażenia lambda.

Określone reguły przypisywania mają wpływ na wszystkie zmienne, które są przechwytywane przez funkcję lokalną lub wyrażenie lambda. Zarówno funkcja lokalna, jak i reguły wyrażenia lambda wymagają, aby wszystkie przechwycone zmienne były ostatecznie przypisane w punkcie, gdy funkcja lokalna lub wyrażenie lambda są konwertowane na delegata. Różnica polega na tym, że wyrażenia lambda są konwertowane na delegatów po ich zadeklarowaniu. Funkcja lokalna jest konwertowana na delegatów tylko wtedy, gdy jest używana jako delegat. Jeśli zadeklarujesz funkcję lokalną i odwołujesz się do niej tylko przez wywołanie jej jako metody, nie zostanie ona przekonwertowana na delegata. Ta reguła umożliwia zadeklarować funkcję lokalną w dowolnej wygodnej lokalizacji w jej zasięgu. Często deklaruje funkcje lokalne na końcu metody nadrzędnej po dowolnych instrukcjach Return.

Po trzecie kompilator może wykonać analizę statyczną, która umożliwia lokalne funkcje, aby ostatecznie przypisywać przechwycone zmienne w zakresie otaczającym. Rozważmy następujący przykład:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Kompilator może określić, że w `LocalFunction` ostatecznie przypisuje `y` po wywołaniu. Ponieważ `LocalFunction` jest wywoływana przed instrukcją `return`, `y` jest ostatecznie przypisana w instrukcji `return`.

Analiza, która umożliwia przykładową analizę, włącza czwartą różnicę.
W zależności od ich użycia funkcje lokalne mogą uniknąć przydziałów sterty, które są zawsze niezbędne dla wyrażeń lambda. Jeśli funkcja lokalna nigdy nie jest konwertowana na delegata, a żadna ze zmiennych przechwyconych przez funkcję lokalną nie zostanie przechwycona przez inne wyrażenia lambda lub funkcje lokalne, które są konwertowane na delegatów, kompilator może uniknąć przydziałów sterty. 

Rozważmy ten przykład asynchroniczny:

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

Zamknięcie tego wyrażenia lambda zawiera zmienne `address`, `index` i `name`. W przypadku funkcji lokalnych obiekt implementujący zamknięcie może być typem `struct`. Ten typ struktury zostałby przesłany przez odwołanie do funkcji lokalnej. Różnica w implementacji spowodowałaby zapisanie alokacji.

Wystąpienie niezbędne dla wyrażeń lambda oznacza dodatkowe alokacje pamięci, które mogą być czynnikiem wydajności w ścieżkach kodu o kluczowym znaczeniu.
Funkcja lokalna nie wiąże się z tym obciążeniem. W powyższym przykładzie wersja funkcji lokalnych ma 2 mniejsze alokacje niż wersja wyrażenia lambda.

> [!NOTE]
> Funkcja lokalna równoważna tej metody używa również klasy do zamykania. Czy zamknięcie funkcji lokalnej jest zaimplementowane jako `class`, czy `struct` jest szczegółami implementacji. Funkcja lokalna może używać `struct`, podczas gdy wyrażenie lambda zawsze będzie używać `class`.

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

Jedną z końcowych zalet nie pokazanych w tym przykładzie jest to, że funkcje lokalne mogą być implementowane jako Iteratory, przy użyciu składni `yield return` w celu utworzenia sekwencji wartości. Instrukcja `yield return` nie jest dozwolona w wyrażeniach lambda.

Podczas gdy funkcje lokalne mogą wydawać się nadmiarowe w wyrażeniach lambda, są one w rzeczywistości wykorzystywane do różnych celów i mają różne zastosowania.
Funkcje lokalne są wydajniejsze w przypadku, gdy chcesz napisać funkcję, która jest wywoływana tylko z kontekstu innej metody.
