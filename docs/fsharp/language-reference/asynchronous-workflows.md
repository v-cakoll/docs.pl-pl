---
title: Asynchroniczne przepływy pracy
description: Dowiedz się więcej o obsłudze w F# języka programowania dla wykonywania obliczeń w sposób asynchroniczny, którego wykonane bez blokowania wykonywania innych zadań.
ms.date: 05/16/2016
ms.openlocfilehash: 87d4c927be89bbb404a087091eed8c4cae167f0f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645519"
---
# <a name="asynchronous-workflows"></a>Asynchroniczne przepływy pracy

> [!NOTE]
> Łącze odwołania API spowoduje przejście do MSDN.  Dokumentacja interfejsu API w witrynie docs.microsoft.com nie została ukończona.

W tym temacie opisano obsługę F# do wykonywania obliczeń asynchronicznie, bez blokowania wykonywania innych pracy. Na przykład asynchronicznych obliczeń może służyć do pisania aplikacji, które mają interfejsów użytkownika, które ciągle reagować na użytkowników, jak aplikacja wykonuje inne prace.

## <a name="syntax"></a>Składnia

```fsharp
async { expression }
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni obliczenia jest reprezentowane przez `expression` jest skonfigurowany do uruchamiane asynchronicznie, oznacza to, że nie blokuje bieżący wątek obliczeń, gdy wykonywane są operacje asynchroniczne uśpienia, operacji We/Wy i innych operacji asynchronicznych. Asynchroniczne obliczenia często są uruchamiane w wątku w tle, gdy wykonywanie jest kontynuowane w bieżącym wątku. Typ wyrażenia jest `Async<'T>`, gdzie `'T` jest typem zwracanym przez wyrażenie po `return` słowo kluczowe jest używane. Kod w wyrażeniu jest nazywa się *asynchronicznego bloku*, lub *bloku async*.

Istnieją różne sposoby programowania asynchronicznego, a [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7) klasa dostarcza metody, które obsługują kilka scenariuszy. Ogólne podejście jest utworzenie `Async` obiektów, które reprezentują obliczeń lub obliczeń, które mają być uruchamiane asynchronicznie, a następnie uruchom te obliczenia przy użyciu jednej z funkcji wyzwalania. Różne funkcje wyzwalająca zapewniają różne sposoby uruchomionych obliczeń asynchronicznych i, w którym używane jest zależna od tego, czy chcesz użyć, bieżący wątek, wątek w tle lub obiekt zadania .NET Framework i tego, czy istnieją kontynuacji Funkcje, które powinny być uruchamiane po zakończeniu obliczeń. Na przykład, aby rozpocząć asynchroniczne obliczenie w bieżącym wątku, można użyć [ `Async.StartImmediate` ](https://msdn.microsoft.com/library/2f71d1cc-187f-48cf-ac66-e7fda41c46e3). Po uruchomieniu asynchronicznych obliczeń z wątku interfejsu użytkownika nie blokują pętlę głównego zdarzeń, która przetwarza akcje użytkownika, takie jak naciśnięcia klawiszy i myszy działanie, dzięki czemu aplikacja reaguje.

## <a name="asynchronous-binding-by-using-let"></a>Asynchroniczne wiązanie przy użyciu let!

W asynchronicznego przepływu pracy niektóre wyrażenia i operacje są synchroniczne, a niektóre są dłuższe obliczeń, opracowane w celu zwrócenia wyniku asynchronicznego. Gdy zostanie wywołana metoda asynchronicznie, zamiast zwykłej `let` powiązania, możesz użyć `let!`. Efekt `let!` jest umożliwienie wykonywania kontynuować na innych obliczeń lub wątków, ponieważ obliczenie jest wykonywane. Po prawej stronie `let!` zwraca powiązania, pozostała część asynchronicznego przepływu pracy wznawia działanie.

Poniższy kod przedstawia różnicę między `let` i `let!`. Wiersz kodu, który używa `let` po prostu tworzy asynchroniczne obliczenie, jako obiekt, który można uruchomić później za pomocą, na przykład `Async.StartImmediate` lub [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b). Wiersz kodu, który używa `let!` rozpoczyna obliczenia, a następnie wątek jest zawieszony, dopóki wynik nie będzie dostępna, w której punkt wykonywanie jest kontynuowane.

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

Oprócz `let!`, możesz użyć `use!` do wykonania asynchronicznej powiązania. Różnica między `let!` i `use!` jest taka sama jak różnica między `let` i `use`. Aby uzyskać `use!`, obiekt jest usunięty na zakończenie bieżącego zakresu. Należy pamiętać, że w bieżącej wersji funkcji F# języka, `use!` nie zezwala na wartość, aby być inicjowane na wartość null, nawet jeśli `use` jest.

## <a name="asynchronous-primitives"></a>Asynchroniczne w nim elementów podstawowych

Wywoływana jest metoda, która wykonuje jedno zadanie asynchroniczne i zwraca wynik *asynchronicznego podstawowego*, i są one przeznaczone specjalnie do użytku z `let!`. Kilka podstawowych asynchronicznych są zdefiniowane w F# podstawowej biblioteki. Dwie metody takie aplikacje sieci Web są zdefiniowane w module [ `Microsoft.FSharp.Control.WebExtensions` ](https://msdn.microsoft.com/library/95ef17bc-ee3f-44ba-8a11-c90fcf4cf003): [ `WebRequest.AsyncGetResponse` ](https://msdn.microsoft.com/library/09a60c31-e6e2-4b5c-ad23-92a86e50060c) i [ `WebClient.AsyncDownloadString` ](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a). Oba elementy podstawowe pobrać dane ze strony sieci Web danego adresu URL. `AsyncGetResponse` Tworzy `System.Net.WebResponse` obiektu, a `AsyncDownloadString` daje ciąg, który reprezentuje kod HTML dla strony sieci Web.

Kilka podstawowych dla asynchronicznych operacji We/Wy są objęte [ `Microsoft.FSharp.Control.CommonExtensions` ](https://msdn.microsoft.com/library/2edb67cb-6814-4a30-849f-b6dbdd042396) modułu. Te metody rozszerzenia `System.IO.Stream` klasy są [ `Stream.AsyncRead` ](https://msdn.microsoft.com/library/85698aaa-bdda-47e6-abed-3730f59fda5e) i [ `Stream.AsyncWrite` ](https://msdn.microsoft.com/library/1b0a2751-e42a-47e1-bd27-020224adc618).

Można także napisać własny podstawowych asynchronicznych, definiując funkcji, w których pełną treść jest ujęty w bloku async.

Używać metod asynchronicznych na platformie .NET Framework, które są przeznaczone dla innymi modelami asynchronicznymi z F# modelu programowania asynchronicznego, utworzyć funkcję, która zwraca F# `Async` obiektu. F# Biblioteka ma funkcje, które ułatwiają to zrobić.

Przykładem przy użyciu asynchronicznych przepływów pracy jest uwzględniony w tym miejscu; istnieje wiele innych w dokumentacji metody [Async — klasa](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).

W tym przykładzie pokazano, jak używać Asynchroniczne przepływy pracy do wykonywania obliczeń równoległych.

W poniższym przykładzie kodu funkcji `fetchAsync` pobiera tekst HTML zwracanego z żądania sieci Web. `fetchAsync` Funkcja zawiera asynchroniczne bloku kodu. Powiązanie nawiązaniem do wyniku asynchronicznego pierwotny, w tym przypadku [ `AsyncDownloadString` ](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a), let! zamiast umożliwiają jest używana.

W przypadku użycia funkcji [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) do wykonywania operacji asynchronicznej i czeka na wynik. Na przykład można wykonać wiele operacji asynchronicznych w sposób równoległy, za pomocą [ `Async.Parallel` ](https://msdn.microsoft.com/library/aa9b0355-2d55-4858-b943-cbe428de9dc4) działać razem z `Async.RunSynchronously` funkcji. `Async.Parallel` Funkcja przyjmuje listę `Async` obiektów, konfiguruje kodu dla każdego `Async` obiektu zadania do uruchomienia równoległego i zwraca `Async` obiekt, który reprezentuje obliczeń równoległych. Podobnie jak w przypadku jednej operacji, należy wywołać `Async.RunSynchronously` Aby uruchomić wykonywanie.

`runAll` Funkcji uruchamia trzy Asynchroniczne przepływy pracy równolegle i czeka, aż wszystkie zakończył.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Wyrażenia obliczeń](computation-expressions.md)
- [Control.Async — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)
