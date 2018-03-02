---
title: "Asynchroniczne przepływy pracy (F#)"
description: "Informacje o pomocy technicznej w język dla wykonywania obliczenia asynchronicznie, programowania w języku F #, które zostanie wykonane bez blokuje wykonywanie innych zadań."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ee2bb9bf-e04a-4fbe-bf58-46d07229e981
ms.openlocfilehash: e1cbdb452c8f77d97a0231a5ec75d752a98d2ed6
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="asynchronous-workflows"></a>Asynchroniczne przepływy pracy

> [!NOTE]
Łącze odwołania API spowoduje przejście do MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

W tym temacie opisano obsługę języka F # do wykonywania obliczenia asynchronicznie, oznacza to, że nie blokuje wykonywania innych zadań. Na przykład obliczeń asynchronicznych może służyć do pisania aplikacji, które mają UI, które pozostają reakcji użytkownikom aplikacji wykonuje inne zadania.

## <a name="syntax"></a>Składnia

```fsharp
async { expression }
```

## <a name="remarks"></a>Uwagi

W poprzednich składni obliczenia reprezentowany przez `expression` ustawiono uruchamiane asynchronicznie, czyli bez blokowania bieżący wątek obliczeń, gdy są wykonywane operacje asynchroniczne uśpienia, we/wy i inne operacje asynchroniczne. Asynchroniczne obliczenia często są uruchamiane w wątku tła kontynuuje wykonywanie w bieżącym wątku. Typ wyrażenia jest `Async<'T>`, gdzie `'T` jest typem zwracanym przez wyrażenie podczas `return` słowo kluczowe jest używane. Kod w takie wyrażenie jest określany jako *asynchronicznych block*, lub *asynchronicznych block*.

Istnieją różne sposoby programowania asynchronicznego i [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7) klasa dostarcza metody, które obsługują kilka scenariuszy. Ogólne podejście jest utworzenie `Async` obiektów, które reprezentują obliczeń lub obliczenia, które mają być uruchamiane asynchronicznie, a następnie uruchom te obliczenia przy użyciu jednej z funkcji wyzwalania. Różne funkcje wyzwalająca zapewniają różne sposoby uruchamiania obliczeń asynchronicznych i używanego jeden zależy od tego, czy ma być używany bieżący wątek, wątku w tle lub obiekt zadania .NET Framework i czy istnieją kontynuacji Funkcje, które powinny być uruchamiane po zakończeniu obliczenia. Na przykład aby uruchomić obliczeń asynchronicznych w bieżącym wątku, można użyć [ `Async.StartImmediate` ](https://msdn.microsoft.com/library/2f71d1cc-187f-48cf-ac66-e7fda41c46e3). Po uruchomieniu obliczeń asynchronicznych z wątku interfejsu użytkownika nie blokują pętli głównego zdarzeń, która przetwarza akcje użytkownika, takie jak naciśnięć klawiszy i działanie myszy tak reaguje aplikacji.

## <a name="asynchronous-binding-by-using-let"></a>Asynchroniczne powiązania za pomocą let!

W przepływie pracy asynchroniczne niektóre wyrażeń i operacje są synchroniczne, a niektóre są dłuższe obliczenia, które są przeznaczone do zwrócenia wyniku asynchronicznie. Podczas wywołania metody asynchronicznie, zamiast zwykłego `let` powiązanie, użyj `let!`. Efekt `let!` umożliwia wykonanie kontynuowanie na innych obliczenia lub wątków i obliczenia jest wykonywana. Po prawej stronie `let!` zwraca powiązanie wykonywania wznawia reszty asynchroniczne przepływu pracy.

Poniższy kod przedstawia różnice między `let` i `let!`. Wiersz kodu, który używa `let` po prostu tworzy obliczeń asynchronicznych jako obiekt, który można uruchomić później za pomocą, na przykład `Async.StartImmediate` lub [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b). Wiersz kodu, który używa `let!` uruchamia obliczenia, a następnie wątek został wstrzymany, dopóki wynik nie będzie dostępne, w których wykonywanie punktu będzie kontynuowane.

```fsharp
// let just stores the result as an asynchronous operation.
let (result1 : Async<byte[]>) = stream.AsyncRead(bufferSize)
// let! completes the asynchronous operation and returns the data.
let! (result2 : byte[])  = stream.AsyncRead(bufferSize)
```

Oprócz `let!`, można użyć `use!` do wykonywania asynchronicznych powiązania. Różnica między `let!` i `use!` jest taka sama jak różnica między `let` i `use`. Aby uzyskać `use!`, obiekt jest usunięty z na koniec bieżącego zakresu. Należy pamiętać, że w bieżącej wersji języka F # `use!` nie zezwala na wartość zainicjowana na wartość null, nawet jeśli `use` jest.

## <a name="asynchronous-primitives"></a>Asynchroniczne podstawowych

Wywoływana jest metoda, która wykonuje pojedyncze zadanie asynchroniczne i zwraca wynik *asynchroniczne pierwotnych*, a te zostały zaprojektowane specjalnie dla `let!`. Kilka podstawowych asynchroniczne są definiowane w biblioteki podstawowej F #. Dwie metody takich aplikacji sieci Web są zdefiniowane w module [ `Microsoft.FSharp.Control.WebExtensions` ](https://msdn.microsoft.com/library/95ef17bc-ee3f-44ba-8a11-c90fcf4cf003): [ `WebRequest.AsyncGetResponse` ](https://msdn.microsoft.com/library/09a60c31-e6e2-4b5c-ad23-92a86e50060c) i [ `WebClient.AsyncDownloadString` ](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a). Oba elementy podstawowe pobierania danych ze strony sieci Web danego adresu URL. `AsyncGetResponse` Tworzy `System.Net.WebResponse` obiektu, a `AsyncDownloadString` generuje ciąg reprezentujący HTML dla strony sieci Web.

Kilka podstawowych dla asynchronicznych operacji We/Wy są uwzględnione w [ `Microsoft.FSharp.Control.CommonExtensions` ](https://msdn.microsoft.com/library/2edb67cb-6814-4a30-849f-b6dbdd042396) modułu. Te metody rozszerzenia `System.IO.Stream` klasy są [ `Stream.AsyncRead` ](https://msdn.microsoft.com/library/85698aaa-bdda-47e6-abed-3730f59fda5e) i [ `Stream.AsyncWrite` ](https://msdn.microsoft.com/library/1b0a2751-e42a-47e1-bd27-020224adc618).

Dostępne są dodatkowe podstawowych asynchronicznego [F # PowerTools](https://fsprojects.github.io/VisualFSharpPowerTools/). Można również napisać własny podstawowych asynchronicznego, definiując funkcji, których pełną treść jest ujęta w bloku async.

Aby używać metod asynchronicznych w programie .NET Framework, które są przeznaczone dla innymi modelami asynchronicznymi z F # asynchroniczne modelu programowania, Utwórz funkcję, która zwraca F # `Async` obiektu. Biblioteki języka F # ma funkcje, które łatwo to zrobić.

Jednym z przykładów przy użyciu Asynchroniczne przepływy pracy dotyczy tutaj; istnieje wiele innych użytkowników w dokumentacji metody [klasy Async](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).

Ten przykład przedstawia sposób użycia Asynchroniczne przepływy pracy do wykonania obliczenia równolegle.

W poniższym przykładzie kodu, funkcja `fetchAsync` pobiera tekst HTML zwrócona z żądania sieci Web. `fetchAsync` Funkcja zawiera asynchroniczne bloku kodu. Powiązanie nawiązaniem do wyniku asynchronicznego pierwotny, w tym przypadku [ `AsyncDownloadString` ](https://msdn.microsoft.com/library/8a85a9b7-f712-4cac-a0ce-0a797f8ea32a), let! zamiast let jest używana.

Użyj funkcji [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) do wykonywania operacji asynchronicznej i poczekaj na jego wynik. Na przykład można uruchamiać wielu operacji asynchronicznych równolegle przy użyciu [ `Async.Parallel` ](https://msdn.microsoft.com/library/aa9b0355-2d55-4858-b943-cbe428de9dc4) działają razem z `Async.RunSynchronously` funkcji. `Async.Parallel` Funkcja przyjmuje listę `Async` obiektów, ustawia kod dla każdego `Async` obiektu zadania do uruchomienia równoległego i zwraca `Async` obiekt, który reprezentuje równoległej obliczeń. Podobnie jak w przypadku jednej operacji, należy wywołać `Async.RunSynchronously` rozpocząć wykonywania.

`runAll` Funkcji uruchamia trzy Asynchroniczne przepływy pracy równolegle i czeka, aż wszystkie ukończenia.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet8003.fs)]

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka F#](index.md)

[Wyrażenia obliczeń](computation-expressions.md)

[Control.Async — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.async-class-%5bfsharp%5d)
