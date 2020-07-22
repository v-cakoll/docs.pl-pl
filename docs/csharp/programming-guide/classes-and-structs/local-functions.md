---
title: Funkcje lokalne — Przewodnik programowania w języku C#
description: Funkcje lokalne w języku C# to metody prywatne, które są zagnieżdżone w innym elemencie członkowskim i mogą być wywoływane z ich składowych.
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 9987d6d5ad57c1dceb3a4bffbae22a81c240c794
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864530"
---
# <a name="local-functions-c-programming-guide"></a>Funkcje lokalne (Przewodnik programowania w języku C#)

Począwszy od języka C# 7,0, C# obsługuje *funkcje lokalne*. Funkcje lokalne są prywatnymi metodami typu, które są zagnieżdżone w innym elemencie członkowskim. Mogą być wywoływane tylko z ich składowych. Funkcje lokalne można zadeklarować w i wywołać z:

- Metody, zwłaszcza metody iteratorów i metody asynchroniczne
- Konstruktory
- Metody dostępu do właściwości
- Metody dostępu zdarzeń
- Metody anonimowe
- Wyrażenia lambda
- Finalizatory
- Inne funkcje lokalne

Jednak funkcji lokalnych nie można deklarować wewnątrz elementu członkowskiego będącego w posiadaniu wyrażenia.

> [!NOTE]
> W niektórych przypadkach można użyć wyrażenia lambda, aby zaimplementować funkcje również obsługiwane przez funkcję lokalną. Aby zapoznać się z porównaniem, zobacz [funkcje lokalne a wyrażenia lambda](#local-functions-vs-lambda-expressions).

Funkcje lokalne sprawiają, że zamiar kodu jest przejrzysty. Każda osoba odczytująca kod może zobaczyć, że metoda nie jest wywoływana z wyjątkiem metody zawierającej. W przypadku projektów zespołowych uniemożliwiają one również innym deweloperom błędne wywoływanie metody bezpośrednio z innych miejsc w klasie lub strukturze.

## <a name="local-function-syntax"></a>Składnia funkcji lokalnych

Funkcja lokalna jest definiowana jako metoda zagnieżdżona wewnątrz składowej zawierającej. Jego definicja ma następującą składnię:

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Funkcje lokalne mogą używać modyfikatorów [Async](../../language-reference/keywords/async.md) i [UNSAFE](../../language-reference/keywords/unsafe.md) .

Należy zauważyć, że wszystkie zmienne lokalne, które są zdefiniowane w składowej zawierającej, łącznie z parametrami metody, są dostępne w funkcji lokalnej.

W przeciwieństwie do definicji metody lokalnej definicja funkcji nie może zawierać modyfikatora dostępu do składowej. Ponieważ wszystkie funkcje lokalne są prywatne, łącznie z modyfikatorem dostępu, takim jak `private` słowo kluczowe, generuje błąd kompilatora CS0106 "modyfikator" Private "jest nieprawidłowy dla tego elementu".

> [!NOTE]
> W systemach wcześniejszych niż C# 8,0 funkcja lokalna nie może zawierać `static` modyfikatora. Włączenie `static` słowa kluczowego generuje błąd kompilatora CS0106, "modyfikator" static "jest nieprawidłowy dla tego elementu".

Ponadto atrybuty nie mogą być stosowane do funkcji lokalnej ani do jej parametrów i parametrów typu.

W poniższym przykładzie zdefiniowano funkcję lokalną o nazwie `AppendPathSeparator` , która jest prywatna dla metody o nazwie `GetText` :

[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  

## <a name="local-functions-and-exceptions"></a>Lokalne funkcje i wyjątki

Jedną z użytecznych funkcji lokalnych funkcji jest możliwość natychmiastowego zezwolenia na korzystanie z wyjątków. W przypadku iteratorów metod wyjątki są nakierowane tylko wtedy, gdy zwracana sekwencja jest wyliczana, a nie podczas pobierania iteratora. W przypadku metod asynchronicznych wszystkie wyjątki zgłoszone w metodzie asynchronicznej są zaobserwowane, gdy zwracane zadanie jest oczekiwane.

W poniższym przykładzie zdefiniowano `OddSequence` metodę, która wylicza liczby nieparzyste między określonym zakresem. Ponieważ przekazuje liczbę większą niż 100 do `OddSequence` metody Enumerator, metoda zgłasza <xref:System.ArgumentOutOfRangeException> . Ponieważ dane wyjściowe z przykładu pokazują, powierzchnie wyjątków tylko w przypadku iteracji liczby, a nie podczas pobierania modułu wyliczającego.

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]

Zamiast tego można zgłosić wyjątek podczas sprawdzania poprawności i przed pobraniem iteratora, zwracając iterator z funkcji lokalnej, jak pokazano w poniższym przykładzie.

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Funkcji lokalnych można używać w podobny sposób, aby obsługiwać wyjątki poza operacją asynchroniczną. Zwykle wyjątki zgłoszone w metodzie asynchronicznej wymagają sprawdzenia wyjątków wewnętrznych <xref:System.AggregateException> . Funkcje lokalne umożliwiają szybkie i niepowodzenie wykonywania kodu oraz umożliwiają synchroniczną i zaobserwowany wyjątek.

W poniższym przykładzie zastosowano metodę asynchroniczną o nazwie `GetMultipleAsync` do pauzy przez określoną liczbę sekund i zwracają wartość, która jest losowo wielokrotnością tej liczby sekund. Maksymalne opóźnienie wynosi 5 sekund; <xref:System.ArgumentOutOfRangeException>wyniki, jeśli wartość jest większa niż 5. Jak pokazano na poniższym przykładzie, wyjątek, który jest generowany, gdy wartość 6 jest przekazana do `GetMultipleAsync` metody jest opakowany w <xref:System.AggregateException> po `GetMultipleAsync` rozpoczęciu wykonywania metody.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]

Podobnie jak w iteratorze metody, możemy resłużyć kod z tego przykładu, aby przeprowadzić walidację przed wywołaniem metody asynchronicznej. Jak pokazano na poniższym przykładzie, <xref:System.ArgumentOutOfRangeException> nie jest opakowany w <xref:System.AggregateException> .

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]

## <a name="local-functions-vs-lambda-expressions"></a>Funkcje lokalne a wyrażenia lambda

Na pierwszy rzut oka funkcje lokalne i [wyrażenia lambda](../statements-expressions-operators/lambda-expressions.md) są bardzo podobne. W wielu przypadkach wybór między wyrażeniami lambda i funkcjami lokalnymi jest kwestią stylu i preferencji osobistych. Istnieją jednak rzeczywiste różnice w tym, gdzie można korzystać z jednej z nich lub drugiej.

Sprawdźmy różnice między funkcją lokalną a implementacją wyrażenia lambda algorytmu silnia. Pierwsza wersja przy użyciu funkcji lokalnej:

[!code-csharp[LocalFunctionFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Kontrast tej implementacji z wersją, która używa wyrażeń lambda:

[!code-csharp[26_LambdaFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Funkcje lokalne mają nazwy. Wyrażenia lambda są metodami anonimowymi przypisanymi do zmiennych, które są `Func` lub `Action` typami. Gdy deklarujesz funkcję lokalną, typy argumentów i typ zwracany są częścią deklaracji funkcji. Zamiast być częścią treści wyrażenia lambda, typy argumentów i typ zwracany są częścią deklaracji typu zmiennej wyrażenia lambda. Te dwie różnice mogą spowodować wyraźniejszy kod.

Funkcje lokalne mają różne reguły dla określonego przypisania niż wyrażenia lambda. Deklaracja funkcji lokalnej może być przywoływana z dowolnego miejsca w kodzie, w którym znajduje się w zakresie. Wyrażenie lambda musi być przypisane do zmiennej delegata, zanim będzie można uzyskać do niej dostęp (lub wywołać za pomocą delegata odwołującego się do wyrażenia lambda). Należy zauważyć, że wersja używająca wyrażenia lambda musi deklarować i inicjować wyrażenie lambda `nthFactorial` przed jego zdefiniowaniem. Nie powoduje to błędu czasu kompilacji dla odwołania `nthFactorial` przed przypisaniem. Różnice te oznaczają, że algorytmy cykliczne są łatwiejsze do tworzenia przy użyciu funkcji lokalnych. Można zadeklarować i zdefiniować funkcję lokalną, która wywołuje samą siebie. Wyrażenia lambda muszą być zadeklarowane i przypisane do wartości domyślnej przed ponownym przypisaniem do treści, która odwołuje się do tego samego wyrażenia lambda.

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

Kompilator może określić, że jest on `LocalFunction` przypisywany, `y` gdy jest wywoływany. Ponieważ `LocalFunction` jest wywoływana przed `return` instrukcją, `y` jest ostatecznie przypisana do `return` instrukcji.

Analiza, która umożliwia przykładową analizę, włącza czwartą różnicę. W zależności od ich użycia funkcje lokalne mogą uniknąć przydziałów sterty, które są zawsze niezbędne dla wyrażeń lambda. Jeśli funkcja lokalna nigdy nie jest konwertowana na delegata, a żadna ze zmiennych przechwyconych przez funkcję lokalną nie zostanie przechwycona przez inne wyrażenia lambda lub funkcje lokalne, które są konwertowane na delegatów, kompilator może uniknąć przydziałów sterty.

Rozważmy ten przykład asynchroniczny:

[!code-csharp[TaskLambdaExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

Zamknięcie tego wyrażenia lambda zawiera `address` `index` zmienne, i `name` . W przypadku funkcji lokalnych obiekt implementujący zamknięcie może być `struct` typem. Ten typ struktury zostałby przesłany przez odwołanie do funkcji lokalnej. Różnica w implementacji spowodowałaby zapisanie alokacji.

Wystąpienie niezbędne dla wyrażeń lambda oznacza dodatkowe alokacje pamięci, które mogą być czynnikiem wydajności w ścieżkach kodu o kluczowym znaczeniu. Funkcja lokalna nie wiąże się z tym obciążeniem. W powyższym przykładzie wersja funkcji lokalnych ma 2 mniejsze alokacje niż wersja wyrażenia lambda.

> [!NOTE]
> Funkcja lokalna równoważna tej metody używa również klasy do zamykania. Czy zamknięcie funkcji lokalnej jest zaimplementowane jako `class` `struct` szczegóły implementacji. Funkcja lokalna może używać `struct` wyrażenia lambda, które zawsze będzie używać `class` .

[!code-csharp[TaskLocalFunctionExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

Jedną z końcowych zalet nie pokazanych w tym przykładzie jest to, że funkcje lokalne można zaimplementować jako Iteratory, używając `yield return` składni w celu utworzenia sekwencji wartości. `yield return`Instrukcja jest niedozwolona w wyrażeniach lambda.

Podczas gdy funkcje lokalne mogą wydawać się nadmiarowe w wyrażeniach lambda, są one w rzeczywistości wykorzystywane do różnych celów i mają różne zastosowania. Funkcje lokalne są wydajniejsze w przypadku, gdy chcesz napisać funkcję, która jest wywoływana tylko z kontekstu innej metody.

## <a name="see-also"></a>Zobacz także

- [Metody](methods.md)
