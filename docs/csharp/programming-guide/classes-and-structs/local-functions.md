---
title: Funkcje lokalne — przewodnik programowania języka C#
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 200fbd097b7c71a1cd392d62622955528a80fd66
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102947"
---
# <a name="local-functions-c-programming-guide"></a>Funkcje lokalne (Przewodnik programowania języka C#)

Począwszy od języka C# 7.0, C# obsługuje *funkcje lokalne*. Funkcje lokalne są metody prywatne typu, które są zagnieżdżone w innym elementem członkowskim. Można je wywołać tylko od ich zawierającego członka. Funkcje lokalne mogą być zadeklarowane i wywoływane z:

- Metody, zwłaszcza metody iteratora i metody asynchronizowania
- Konstruktorów
- Akcesory
- Akcesory zdarzeń
- Metody anonimowe
- Wyrażenia lambda
- Finalizatory
- Inne funkcje lokalne

Jednak funkcje lokalne nie można zadeklarować wewnątrz elementu członkowskiego wyrażeń.

> [!NOTE]
> W niektórych przypadkach można użyć wyrażenia lambda do zaimplementowania funkcji obsługiwanych również przez funkcję lokalną. Dla porównania zobacz [Funkcje lokalne a wyrażenia lambda](#local-functions-vs-lambda-expressions).

Funkcje lokalne sprawiają, że intencja kodu jest wyczyszczona. Każdy, kto czyta kod może zobaczyć, że metoda nie jest wywoływana z wyjątkiem metody zawierającej. W przypadku projektów zespołowych uniemożliwiają one innemu deweloperowi omyłkowo wywołanie metody bezpośrednio z innego miejsca w klasie lub strukturze.

## <a name="local-function-syntax"></a>Składnia funkcji lokalnej

Funkcja lokalna jest zdefiniowana jako metoda zagnieżdżona wewnątrz elementu członkowskiego zawierającego. Jego definicja ma następującą składnię:

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

Funkcje lokalne można użyć [modyfikatorów asynchroników](../../language-reference/keywords/async.md) i [niebezpiecznych.](../../language-reference/keywords/unsafe.md)

Należy zauważyć, że wszystkie zmienne lokalne, które są zdefiniowane w element członkowski zawierający, w tym jego parametry metody, są dostępne w funkcji lokalnej.

W przeciwieństwie do definicji metody, definicja funkcji lokalnej nie może zawierać modyfikatora dostępu elementu członkowskiego. Ponieważ wszystkie funkcje lokalne są prywatne, w `private` tym modyfikator dostępu, takich jak słowo kluczowe, generuje błąd kompilatora CS0106, "Modyfikator 'private' nie jest prawidłowy dla tego elementu."

> [!NOTE]
> Przed C# 8.0 funkcje lokalne `static` nie mogą zawierać modyfikatora. W `static` tym słowo kluczowe generuje błąd kompilatora CS0106, "Modyfikator 'statyczny' nie jest prawidłowy dla tego elementu."

Ponadto atrybuty nie mogą być stosowane do funkcji lokalnej lub do jej parametrów i parametrów typu.

Poniższy przykład definiuje funkcję `AppendPathSeparator` lokalną o nazwie, `GetText`która jest prywatna dla metody o nazwie:

[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  

## <a name="local-functions-and-exceptions"></a>Funkcje lokalne i wyjątki

Jedną z przydatnych funkcji funkcji lokalnych jest to, że mogą one zezwalać na wyjątki do powierzchni natychmiast. W przypadku iteratorów metody wyjątki są wyświetlane tylko wtedy, gdy zwracana sekwencja jest wyliczona, a nie podczas pobierania iteratora. Dla metod asynchronicznych wszelkie wyjątki zgłaszane w metodzie asynchronicznego są obserwowane, gdy zwracane zadanie jest oczekiwane.

Poniższy przykład definiuje `OddSequence` metodę, która wylicza liczby nieparzyste między określonym zakresem. Ponieważ przekazuje liczbę większą niż 100 do metody `OddSequence` wyliczacza, metoda zgłasza . <xref:System.ArgumentOutOfRangeException> Jak pokazano na wyjściu z przykładu, wyjątek jest wyświetlany tylko wtedy, gdy iteracji liczb, a nie podczas pobierania wylicznika.

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]

Zamiast tego można zgłosić wyjątek podczas wykonywania sprawdzania poprawności i przed pobraniem iteratora, zwracając iterator z funkcji lokalnej, jak pokazano w poniższym przykładzie.

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

Funkcje lokalne mogą być używane w podobny sposób do obsługi wyjątków poza operacją asynchronizacyjną. Zwykle wyjątki zgłaszane w metodzie asynchronizowej wymagają zbadania <xref:System.AggregateException>wewnętrznych wyjątków . Funkcje lokalne umożliwiają kod szybko zakończyć się niepowodzeniem i zezwalaj na wyjątek zarówno zgłaszane i obserwowane synchronicznie.

W poniższym przykładzie użyto metody `GetMultipleAsync` asynchroniczne o nazwie do wstrzymania dla określonej liczby sekund i zwracanie wartości, która jest losową wielokrotnością tej liczby sekund. Maksymalne opóźnienie wynosi 5 sekund; wyniki, <xref:System.ArgumentOutOfRangeException> jeśli wartość jest większa niż 5. Jak pokazano w poniższym przykładzie, wyjątek, który jest `GetMultipleAsync` zgłaszany, gdy <xref:System.AggregateException> wartość `GetMultipleAsync` 6 jest przekazywana do metody jest zawijany w po rozpoczęciu wykonywania metody.

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]

Podobnie jak w przypadku iteratora metody, możemy refaktoryzację kodu z tego przykładu, aby wykonać sprawdzanie poprawności przed wywołaniem metody asynchroniczne. Jak pokazano na wyjściu z <xref:System.ArgumentOutOfRangeException> poniższego przykładu, nie jest zawijany w . <xref:System.AggregateException>

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]

## <a name="local-functions-vs-lambda-expressions"></a>Funkcje lokalne a wyrażenia lambda

Na pierwszy rzut oka funkcje lokalne i [wyrażenia lambda](../statements-expressions-operators/lambda-expressions.md) są bardzo podobne. W wielu przypadkach wybór między używaniem wyrażeń lambda a funkcjami lokalnymi jest kwestią stylu i osobistych preferencji. Istnieją jednak rzeczywiste różnice w tym, gdzie można użyć jednego lub drugiego, że należy pamiętać.

Przyjrzyjmy się różnice między funkcji lokalnej i implementacji wyrażenia lambda algorytmu faktorialnego. Najpierw wersja przy użyciu funkcji lokalnej:

[!code-csharp[LocalFunctionFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

Kontrast tej implementacji z wersją, która używa wyrażeń lambda:

[!code-csharp[26_LambdaFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

Funkcje lokalne mają nazwy. Wyrażenia lambda są metody anonimowe, które są `Func` przypisane do zmiennych, które są lub `Action` typy. Podczas deklarowania funkcji lokalnej typy argumentów i typ zwracany są częścią deklaracji funkcji. Zamiast być częścią treści wyrażenia lambda, typy argumentów i typ zwracany są częścią deklaracji typu zmiennego wyrażenia lambda. Te dwie różnice mogą spowodować jaśniejszy kod.

Funkcje lokalne mają różne reguły dla określonego przypisania niż wyrażenia lambda. Do deklaracji funkcji lokalnej można odwoływać się z dowolnej lokalizacji kodu, w której znajduje się w zakresie. Wyrażenie lambda musi być przypisane do zmiennej delegata, zanim będzie dostępny (lub wywoływane za pośrednictwem pełnomocnika odwołującego się do wyrażenia lambda). Należy zauważyć, że wersja przy użyciu wyrażenia lambda musi `nthFactorial` zadeklarować i zainicjować wyrażenie lambda przed zdefiniowaniem go. Nie powoduje to błąd czasu kompilacji `nthFactorial` do odwoływania się przed przypisaniem go. Różnice te oznaczają, że algorytmy cykliczne są łatwiejsze do tworzenia przy użyciu funkcji lokalnych. Można zadeklarować i zdefiniować funkcję lokalną, która wywołuje się. Wyrażenia Lambda muszą być zadeklarowane i przypisane wartość domyślną, zanim mogą być ponownie przypisane do treści, która odwołuje się do tego samego wyrażenia lambda.

Reguły określonego przypisania mają również wpływ na wszystkie zmienne, które są przechwytywane przez funkcję lokalną lub wyrażenie lambda. Zarówno funkcje lokalne, jak i reguły wyrażenia lambda wymagają, aby wszystkie przechwycone zmienne były zdecydowanie przypisywane w punkcie, gdy funkcja lokalna lub wyrażenie lambda jest konwertowane na pełnomocnika. Różnica polega na tym, że wyrażenia lambda są konwertowane na delegatów, gdy są one zadeklarowane. Funkcje lokalne są konwertowane na delegatów tylko wtedy, gdy jest używany jako pełnomocnik. Jeśli deklarujesz funkcję lokalną i odwołujesz się tylko do niej, wywołując ją jak metodę, nie zostanie ona przekonwertowana na pełnomocnika. Ta reguła umożliwia zadeklarowanie funkcji lokalnej w dowolnej dogodnej lokalizacji w jej otaczającym zakresie. Jest to typowe do deklarowania funkcji lokalnych na końcu metody nadrzędnej, po wszelkich instrukcji zwracanych.

Po trzecie kompilator może wykonywać analizę statyczną, która umożliwia funkcjom lokalnym zdecydowanie przypisać przechwycone zmienne w otaczającym zakresie. Rozważmy następujący przykład:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Kompilator można `LocalFunction` określić, `y` że zdecydowanie przypisuje, gdy wywoływane. Ponieważ `LocalFunction` jest wywoływana przed instrukcją, `return` `y` `return` jest zdecydowanie przypisany do instrukcji.

Analiza, która umożliwia analizę przykładu umożliwia czwartą różnicę. W zależności od ich użycia funkcje lokalne można uniknąć alokacji sterty, które są zawsze niezbędne dla wyrażeń lambda. Jeśli funkcja lokalna nigdy nie jest konwertowana na pełnomocnika, a żadna ze zmiennych przechwyconych przez funkcję lokalną nie jest przechwytywany przez inne funkcje lambdas lub lokalne, które są konwertowane na delegatów, kompilator może uniknąć alokacji sterty.

Rozważmy ten przykład asynchronii:

[!code-csharp[TaskLambdaExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

Zamknięcie dla tego wyrażenia lambda `index` `name` zawiera `address`, i zmienne. W przypadku funkcji lokalnych obiekt, który implementuje zamknięcie `struct` może być typem. Ten typ struktury będzie przekazywana przez odwołanie do funkcji lokalnej. Ta różnica we wdrażaniu zaoszczędziłaby na alokacji.

Wystąpienie niezbędne dla wyrażeń lambda oznacza dodatkowe alokacje pamięci, które mogą być czynnikiem wydajności w ścieżek kodu krytycznego w czasie. Funkcje lokalne nie ponoszą tego obciążenia. W powyższym przykładzie wersja funkcji lokalnych ma 2 mniej alokacji niż wersja wyrażenia lambda.

> [!NOTE]
> Lokalny odpowiednik funkcji tej metody również używa klasy do zamknięcia. Czy zamknięcie dla funkcji lokalnej jest `class` implementowana `struct` jako lub a jest szczegół implementacji. Funkcja lokalna może `struct` używać natomiast lambda zawsze `class`będzie używać .

[!code-csharp[TaskLocalFunctionExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

Jedną z zalet końcowych nie wykazane w tym przykładzie jest, że `yield return` funkcje lokalne mogą być implementowane jako iteratory, przy użyciu składni do tworzenia sekwencji wartości. Instrukcja `yield return` nie jest dozwolona w wyrażeniach lambda.

Podczas gdy funkcje lokalne mogą wydawać się zbędne do wyrażeń lambda, w rzeczywistości służą różnym celom i mają różne zastosowania. Funkcje lokalne są bardziej wydajne dla przypadku, gdy chcesz napisać funkcję, która jest wywoływana tylko z kontekstu innej metody.

## <a name="see-also"></a>Zobacz też

- [Metody](methods.md)
