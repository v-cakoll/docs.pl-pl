---
title: Rozpoczynanie pracy z językiem F# w programie Visual Studio Code
description: Dowiedz się, F# jak używać programu z Visual Studio Code i pakietem wtyczek Ionide.
ms.date: 12/23/2018
ms.openlocfilehash: 2802438144eb2352c3abeeccfc126b16c6a87d8f
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204912"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Rozpoczynanie pracy z językiem F# w programie Visual Studio Code

Możesz pisać F# w [Visual Studio Code](https://code.visualstudio.com) z [wtyczką Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) , aby uzyskać wspaniałe Międzyplatformowe, uproszczone zintegrowane środowisko programistyczne (IDE) korzystające z funkcji IntelliSense i refaktoryzacji kodu. Odwiedź stronę [Ionide.IO](http://ionide.io) , aby dowiedzieć się więcej na temat wtyczki.

Aby rozpocząć, upewnij się, że [ F# poprawnie zainstalowano wtyczkę Ionide](install-fsharp.md#install-f-with-visual-studio-code).

## <a name="create-your-first-project-with-ionide"></a>Tworzenie pierwszego projektu przy użyciu Ionide

Aby utworzyć nowy F# projekt, Otwórz wiersz polecenia i Utwórz nowy projekt z interfejs wiersza polecenia platformy .NET Core:

```dotnetcli
dotnet new console -lang F# -o FirstIonideProject
```

Po jego zakończeniu Zmień katalog na projekt i otwórz Visual Studio Code:

```console
cd FirstIonideProject
code .
```

Po załadowaniu projektu na Visual Studio Code powinien zostać wyświetlony okienko F# Eksplorator rozwiązań po lewej stronie otwartego okna. Oznacza to, że Ionide pomyślnie załadował projekt, który został właśnie utworzony. Możesz napisać kod w edytorze przed tym punktem w czasie, ale gdy tak się stanie, wszystko zakończyło ładowanie.

## <a name="configure-f-interactive"></a>Konfiguruj F# interaktywny

Najpierw upewnij się, że obsługa skryptów .NET Core jest domyślnym środowiskiem tworzenia skryptów:

1. Otwórz ustawienia Visual Studio Code ( **preferencje** > **kodu** > **ustawień**).
1. Wyszukaj  **F# skrypt**terminowy.
1. Kliknij pole wyboru, które mówi **FSharp: Użyj skryptów zestawu SDK**.

Jest to obecnie konieczne z powodu niektórych starszych zachowań w skryptach opartych na .NET Framework, które nie współpracują z obsługą skryptów .NET Core, a Ionide jest obecnie striving w celu zapewnienia zgodności z poprzednimi wersjami. W przyszłości skrypty środowiska .NET Core staną się domyślne.

### <a name="write-your-first-script"></a>Napisz swój pierwszy skrypt

Po skonfigurowaniu Visual Studio Code do korzystania ze skryptów .NET Core przejdź do widoku Eksplorator w Visual Studio Code i Utwórz nowy plik. Nadaj mu nazwę *MyFirstScript. FSX*.

Teraz Dodaj do niego następujący kod:

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Ta funkcja konwertuje wyraz na formę [surówki](https://en.wikipedia.org/wiki/Pig_Latin). Następnym krokiem jest oszacowanie go przy użyciu opcji F# Interactive (fsi).

Zaznacz całą funkcję (powinna być 11 wierszy). Gdy zostanie on wyróżniony, przytrzymaj wciśnięty klawisz **Alt** i naciśnij klawisz **Enter**. Zobaczysz okno terminalu w dolnej części ekranu i będzie wyglądać podobnie do tego:

![Przykład danych F# wyjściowych interaktywnych z Ionide](./media/getting-started-vscode/vscode-fsi.png)

Było to trzy rzeczy:

1. Uruchomiono proces FSI.
2. Wysłano kod wyróżniony w procesie FSI.
3. Proces FSI ocenia kod, który został wysłany.

Ponieważ wysłane przez Ciebie elementy były [funkcją](../language-reference/functions/index.md), można teraz wywołać tę funkcję za pomocą FSI! W oknie interaktywnym wpisz następujące polecenie:

```fsharp
toPigLatin "banana";;
```

Powinien zostać wyświetlony następujący wynik:

```fsharp
val it : string = "ananabay"
```

Teraz Wypróbujmy samogłosy jako pierwszą literę. Wprowadź następujące elementy:

```fsharp
toPigLatin "apple";;
```

Powinien zostać wyświetlony następujący wynik:

```fsharp
val it : string = "appleyay"
```

Funkcja wydaje się działać zgodnie z oczekiwaniami. Gratulacje, po prostu Zapisano pierwszą F# funkcję w Visual Studio Code i oceniamy ją za pomocą FSI!

> [!NOTE]
> Jak zauważono, wiersze w FSI kończą się `;;`. Dzieje się tak, ponieważ FSI umożliwia wprowadzanie wielu wierszy. `;;` na końcu umożliwia FSI, gdy kod zostanie zakończony.

## <a name="explaining-the-code"></a>Objaśnienie kodu

Jeśli nie masz pewności, co robi kod w rzeczywistości, wykonaj instrukcje krok po kroku.

Jak widać, `toPigLatin` jest funkcją, która przyjmuje słowo jako dane wejściowe i konwertuje ją na reprezentację w formacie wieprzowiny. Te reguły są następujące:

Jeśli pierwszy znak w wyrazie zaczyna się od samogłosek, Dodaj "Yay" do końca wyrazu. Jeśli nie zaczyna się od samogłosek, Przenieś ten pierwszy znak na koniec wyrazu i Dodaj do niego wartość "AY".

W FSI mogły być zauważone następujące elementy:

```fsharp
val toPigLatin : word:string -> string
```

To Stany, które `toPigLatin` to funkcja, która przyjmuje `string` jako dane wejściowe (nazywane `word`) i zwraca kolejną `string`. Jest to nazywane [sygnaturą typu funkcji](https://fsharpforfunandprofit.com/posts/function-signatures/), podstawową częścią F# tego klucza do poznania F# kodu. Zauważmy również, że po umieszczeniu wskaźnika myszy nad funkcją w Visual Studio Code.

W treści funkcji widoczne są dwie odrębne części:

1. Funkcja wewnętrzna o nazwie `isVowel`, która określa, czy dany znak (`c`) jest odgłosami przez sprawdzenie, czy pasuje do jednego z podanych wzorców przez [dopasowanie wzorca](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. Wyrażenie [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) , które sprawdza, czy pierwszy znak jest samodzielny i konstruuje zwracaną wartość z znaków wejściowych w oparciu o to, czy pierwszy znak był samogłosek lub nie:

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

Przepływ `toPigLatin` jest więc:

Sprawdź, czy pierwszy znak wyrazu wejściowego to samogłoski. Jeśli tak, Dołącz "Yay" do końca wyrazu. W przeciwnym razie Przenieś ten pierwszy znak na koniec wyrazu i Dodaj do niego wartość "AY".

Należy zwrócić uwagę na to, że nie ma żadnej bezpośredniej instrukcji zwracanej z funkcji, w przeciwieństwie do wielu innych języków. Wynika to z F# faktu, że jest oparte na wyrażeniach, a ostatnie wyrażenie w treści funkcji jest wartością zwracaną. Ponieważ `if..then..else` jest samym wyrażeniem, treść bloku `then` lub treść bloku `else` zostanie zwrócona w zależności od wartości wejściowej.

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a>Przekształcanie aplikacji konsolowej w generator łaciński

W poprzednich sekcjach tego artykułu przedstawiono typowy pierwszy krok podczas pisania F# kodu: pisanie początkowej funkcji i wykonywanie jej interaktywnie przy użyciu FSI. Jest to nazywane programowaniem opartym na REPL, gdzie [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) to "Read-Szacuj-Print pętl". Jest to doskonały sposób na eksperymentowanie z funkcjami do momentu, w którym będzie działać.

Następnym krokiem w programowaniu opartym na REPL polega na przeniesieniu kodu roboczego F# do pliku implementacji. Może zostać następnie skompilowany przez F# kompilator do zestawu, który może być wykonywany.

Aby rozpocząć, Otwórz plik *program. FS* , który został utworzony wcześniej przy użyciu interfejs wiersza polecenia platformy .NET Core. Zauważysz, że jakiś kod już istnieje.

Następnie utwórz nową [`module`](../language-reference/modules.md) o nazwie `PigLatin` i skopiuj wcześniej utworzoną funkcję `toPigLatin` w taki sposób, aby:

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

Ten moduł powinien znajdować się powyżej funkcji `main` i poniżej deklaracji `open System`. Porządek deklaracji w F#, dlatego należy zdefiniować funkcję przed wywołaniem jej w pliku.

Teraz w funkcji `main` wywołaj funkcję generatora w postaci trzody chlewnej na argumenty:

```fsharp
[<EntryPoint>]
let main argv =
    for name in argv do
        let newName = PigLatin.toPigLatin name
        printfn "%s in Pig Latin is: %s" name newName

    0
```

Teraz możesz uruchomić aplikację konsolową z poziomu wiersza polecenia:

```console
dotnet run apple banana
```

Zobaczysz, że ten sam wynik będzie taki sam jak plik skryptu, ale ten czas jest uruchomionym programem.

## <a name="troubleshooting-ionide"></a>Rozwiązywanie problemów z Ionide

Poniżej przedstawiono kilka sposobów rozwiązywania niektórych problemów, które mogą być wykonywane w programie:

1. Aby uzyskać funkcje edytowania kodu Ionide, należy zapisać F# pliki na dysku i w folderze, który jest otwarty w obszarze roboczym Visual Studio Code.
1. Jeśli wprowadzono zmiany w systemie lub zainstalowano wymagania wstępne Ionide z Visual Studio Code Otwórz, uruchom ponownie Visual Studio Code.
1. Jeśli w katalogach projektu znajdują się nieprawidłowe znaki, Ionide może nie zadziałał.  W takim przypadku Zmień nazwy katalogów projektu.
1. Jeśli żaden z poleceń Ionide nie działa, sprawdź powiązania klawiszy [Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) , aby sprawdzić, czy są one zastępowane przypadkowo.
1. Jeśli Ionide jest przerwany na komputerze, a żaden z powyższych elementów nie rozwiązał problemu, spróbuj usunąć katalog `ionide-fsharp` na maszynie i ponownie zainstalować pakiet wtyczek.
1. Jeśli nie można załadować projektu ( F# Eksplorator rozwiązań będzie on widoczny), kliknij prawym przyciskiem myszy projekt i kliknij pozycję **Wyświetl szczegóły** , aby uzyskać więcej informacji diagnostycznych.

Ionide to projekt typu "open source" skompilowany i obsługiwany przez członków F# społeczności. Zgłoś problemy i śmiało, aby współtworzyć w [repozytorium GitHub ionide-programu vscode-FSharp](https://github.com/ionide/ionide-vscode-fsharp).

Możesz również poszukać dalszej pomocy od deweloperów Ionide i F# społeczności w [kanale warunkom Ionide](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>Kolejne kroki

Aby dowiedzieć się F# więcej na temat funkcji języka, zobacz [Przewodnik F# ](../tour.md)po stronie.
