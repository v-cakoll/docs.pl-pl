---
title: 'Zarządzanie zasobami: Słowo kluczowe use'
description: Dowiedz się F# więcej o słowie kluczowym "use" i funkcji "Using", która może kontrolować inicjalizację i wydawanie zasobów.
ms.date: 05/16/2016
ms.openlocfilehash: 5e0838401bee02050343b2f6dcc646a8dc8b4dc0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627257"
---
# <a name="resource-management-the-use-keyword"></a>Zarządzanie zasobami: Słowo kluczowe use

W tym temacie opisano słowo `use` kluczowe `using` i funkcję, które mogą kontrolować inicjalizację i wydawanie zasobów.

## <a name="resources"></a>Zasoby

Termin *zasób* jest używany w więcej niż jeden sposób. Tak, zasoby mogą być danymi, które są używane przez aplikację, takich jak ciągi, grafika i podobne, ale w tym kontekście *zasoby* odnoszą się do zasobów oprogramowania lub systemu operacyjnego, takich jak konteksty urządzeń graficznych, dojścia do plików, Sieć i baza danych. połączenia, obiekty współbieżności, takie jak uchwyty oczekiwania i tak dalej. Użycie tych zasobów przez aplikacje obejmuje Nabycie zasobu od systemu operacyjnego lub innego dostawcy zasobów, a następnie późniejsze wydanie zasobu do puli, dzięki czemu można je dostarczyć innym aplikacjom. Problemy występują, gdy aplikacje nie zwalniają zasobów z powrotem do wspólnej puli.

## <a name="managing-resources"></a>Zarządzanie zasobami

Aby efektywnie i odpowiedzialnie zarządzać zasobami w aplikacji, musisz natychmiast zwolnić zasoby i w sposób przewidywalny. .NET Framework pomaga to zrobić, dostarczając `System.IDisposable` interfejs. Typ, który implementuje `System.IDisposable` , `System.IDisposable.Dispose` ma metodę, która poprawnie zwalnia zasoby. Dobrze napisano aplikacje gwarantujące, że jest wywoływana natychmiast, `System.IDisposable.Dispose` gdy dowolny obiekt, który przechowuje ograniczony zasób, nie jest już wymagany. Na szczęście większość języków .NET zapewnia pomoc techniczną i F# nie ma wyjątku. Istnieją dwa przydatne konstrukcje języka, które obsługują wzorzec Dispose: `use` powiązanie `using` i funkcję.

## <a name="use-binding"></a>Użyj powiązania

Słowo kluczowe ma postać podobną `let` do powiązania: `use`

Użyj*wyrażenia* *wartości* = 

Zapewnia takie same funkcje jak `let` powiązanie, ale dodaje wywołanie do `Dispose` wartości, gdy wartość wykracza poza zakres. Należy zauważyć, że kompilator wstawia sprawdzanie wartości null na wartość, więc jeśli wartość jest `null`, `Dispose` wywołanie nie jest podejmowane.

Poniższy przykład pokazuje, `use` jak zamknąć plik automatycznie przy użyciu słowa kluczowego.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

> [!NOTE]
> Można używać `use` w wyrażeniach obliczeniowych, w których przypadku używana jest dostosowana `use` wersja wyrażenia. Aby uzyskać więcej informacji, [](sequences.md)Zobacz sekwencje, [asynchroniczne przepływy pracy](asynchronous-workflows.md)i [wyrażenia obliczeń](computation-expressions.md).

## <a name="using-function"></a>Funkcja using

`using` Funkcja ma następującą postać:

`using`(*wyrażenie1*) *Function-lub-lambda*

W wyrażeniu wyrażenie1 tworzy obiekt, który musi zostać usunięty. `using` Wynik *wyrażenie1* (obiekt, który musi zostać usunięty), jest argumentem, *wartością*, do *funkcji-lub-lambda*, która jest funkcją, która oczekuje jednego pozostałego argumentu typu, który pasuje do wartości wygenerowanej przez  *wyrażenie1*lub wyrażenie lambda, które oczekuje argumentu tego typu. Po zakończeniu wykonywania funkcji środowisko uruchomieniowe wywołuje `Dispose` i zwalnia zasoby (chyba że jest `null`to wartość, w takim przypadku nie jest podejmowana próba wywołania metody Dispose).

Poniższy przykład ilustruje `using` wyrażenie z wyrażeniem lambda.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

W następnym przykładzie pokazano `using` wyrażenie z funkcją.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

Należy zauważyć, że funkcja może być funkcją, która ma już zastosowane argumenty. Poniższy przykład kodu demonstruje ten sposób. Tworzy plik, który zawiera ciąg `XYZ`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

`using` Funkcja`use` i powiązanie są niemal równoważnymi sposobami wykonywania tego samego celu. Słowo `using` kluczowe zapewnia większą kontrolę nad tym `Dispose` , kiedy jest wywoływana. Gdy używasz `Dispose` `use` , jest wywoływana na końcu funkcji lub wyrażenia lambda; w przypadku użycia słowa kluczowego `Dispose` jest wywoływana na końcu bloku zawierającego kod. `using` Ogólnie rzecz biorąc należy używać `use` zamiast `using` funkcji.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
