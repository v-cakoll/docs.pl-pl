---
title: Rozpoczynanie pracy F# z usługą w Visual Studio Code
description: Dowiedz się, F# jak używać programu z Visual Studio Code i pakietem wtyczek Ionide.
ms.date: 12/23/2018
ms.openlocfilehash: baaa87207122cfe314972aee5dfaf8a41de2c394
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629980"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Rozpoczynanie pracy F# z usługą w Visual Studio Code

Możesz pisać F# w [Visual Studio Code](https://code.visualstudio.com) z wtyczką [Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) , aby uzyskać wspaniałe Międzyplatformowe, uproszczone zintegrowane środowisko programistyczne (IDE) z technologią IntelliSense i podstawowymi refaktoryzacjami kodu. Odwiedź stronę [Ionide.IO](http://ionide.io) , aby dowiedzieć się więcej na temat wtyczki.

Aby rozpocząć, upewnij się, że [ F# poprawnie zainstalowano wtyczkę Ionide](install-fsharp.md#install-f-with-visual-studio-code).

> [!NOTE]
> Ionide będzie generować projekty F# .NET Framework, a nie rdzeń dotnet, które mogą mieć problemy ze zgodnością między platformami. Jeśli pracujesz w systemie **Linux** lub **OSX**, prostszym sposobem na rozpoczęcie pracy jest użycie [narzędzi wiersza polecenia](get-started-command-line.md).

## <a name="creating-your-first-project-with-ionide"></a>Tworzenie pierwszego projektu przy użyciu Ionide

Aby utworzyć nowy F# projekt, otwórz Visual Studio Code w nowym folderze (można go nazwać w dowolny sposób).

Następnie Otwórz paletę poleceń (**wyświetl > palecie poleceń**) i wpisz następujące polecenie:

```
> F# new project
```

Jest to obsługiwane przez projekt [podrabiania](https://github.com/fsharp-editing/Forge) .

> [!NOTE]
> Jeśli nie widzisz opcji szablonu, spróbuj odświeżyć szablony, uruchamiając następujące polecenie w palecie poleceń `>F#: Refresh Project Templates`:.

Wybierz pozycjęF#": Nowy projekt "przez naciśnięcie **klawisza ENTER**. Spowoduje to przejście do następnego kroku, który służy do wybierania szablonu projektu.

Wybierz szablon i naciśnij klawisz **Enter.** `classlib`

Następnie wybierz katalog, w którym zostanie utworzony projekt. Jeśli pozostawisz to pole puste, zostanie użyty bieżący katalog.

Na koniec Nadaj projektowi nazwę w ostatnim kroku. F#używa [przypadku języka Pascal](http://c2.com/cgi/wiki?PascalCase) dla nazw projektów. W tym artykule `ClassLibraryDemo` jest stosowana nazwa. Po wprowadzeniu nazwy dla projektu naciśnij klawisz **Enter**.

Jeśli wykonano poprzedni krok, należy uzyskać obszar roboczy Visual Studio Code po lewej stronie, aby wyświetlić następujące elementy:

1. Sam F# projekt, poniżej `ClassLibraryDemo` folderu.
2. Poprawna struktura katalogów służąca do [`Paket`](https://fsprojects.github.io/Paket/)dodawania pakietów za pośrednictwem.
3. Międzyplatformowy skrypt kompilacji z [`FAKE`](https://fsharp.github.io/FAKE/).
4. `paket.exe` Plik wykonywalny, który może pobierać pakiety i rozwiązywać zależności.
5. Plik `.gitignore` , jeśli chcesz dodać ten projekt do kontroli źródła opartej na git.

## <a name="writing-some-code"></a>Pisanie kodu

Otwórz folder *ClassLibraryDemo* .  Powinny zostać wyświetlone następujące pliki:

1. `ClassLibraryDemo.fs`, plik F# implementacji z zdefiniowaną klasą.
2. `ClassLibraryDemo.fsproj`, plik F# projektu używany do kompilowania tego projektu.
3. `Script.fsx`, plik F# skryptu ładujący plik źródłowy.
4. `paket.references`, plik Paket, który określa zależności projektu.

Otwórz `Script.fsx`i Dodaj następujący kod na końcu:

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Ta funkcja konwertuje wyraz na formę surówki. [](https://en.wikipedia.org/wiki/Pig_Latin) Następnym krokiem jest oszacowanie go przy użyciu opcji F# Interactive (fsi).

Zaznacz całą funkcję (powinna być 11 wierszy). Gdy zostanie ono wyróżnione, przytrzymaj klawisz **Alt** i naciśnij klawisz **Enter**. Zobaczysz okno podręczne poniżej i będzie ono wyglądać następująco:

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
> Jak zauważono, wiersze w FSI są kończone z `;;`. Dzieje się tak, ponieważ FSI umożliwia wprowadzanie wielu wierszy. `;;` Na końcu FSI wie, kiedy kod został ukończony.

## <a name="explaining-the-code"></a>Objaśnienie kodu

Jeśli nie masz pewności, co robi kod w rzeczywistości, wykonaj instrukcje krok po kroku.

Jak widać, `toPigLatin` to funkcja, która przyjmuje słowo jako dane wejściowe i konwertuje ją na reprezentację w postaci tuszowej. Te reguły są następujące:

Jeśli pierwszy znak w wyrazie zaczyna się od samogłosek, Dodaj "Yay" do końca wyrazu. Jeśli nie zaczyna się od samogłosek, Przenieś ten pierwszy znak na koniec wyrazu i Dodaj do niego wartość "AY".

W FSI mogły być zauważone następujące elementy:

```fsharp
val toPigLatin : word:string -> string
```

To Stany `toPigLatin` , które są funkcją, która przyjmuje `string` jako dane wejściowe (nazywane `word`) i zwraca inną `string`. Jest to nazywane sygnaturą [typu funkcji](https://fsharpforfunandprofit.com/posts/function-signatures/), podstawową częścią F# tego klucza do poznania F# kodu. Zauważmy również, że po umieszczeniu wskaźnika myszy nad funkcją w Visual Studio Code.

W treści funkcji widoczne są dwie odrębne części:

1. Wewnętrzna funkcja, wywołana `isVowel`, która określa, czy dany znak (`c`) jest wygłosami przez sprawdzenie, czy pasuje do jednego z dostarczonych wzorców przez [dopasowanie wzorca](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md) Wyrażenie, które sprawdza, czy pierwszy znak jest samogłosek i konstruuje zwracaną wartość z znaków wejściowych w oparciu o to, czy pierwszy znak był samogłosek lub nie:

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

Przepływ `toPigLatin` jest następujący:

Sprawdź, czy pierwszy znak wyrazu wejściowego to samogłoski. Jeśli tak, Dołącz "Yay" do końca wyrazu. W przeciwnym razie Przenieś ten pierwszy znak na koniec wyrazu i Dodaj do niego wartość "AY".

Należy zwrócić uwagę na to, że nie ma żadnej bezpośredniej instrukcji zwracanej z funkcji, w przeciwieństwie do wielu innych języków. Wynika to z F# faktu, że jest oparte na wyrażeniach, a ostatnie wyrażenie w treści funkcji jest wartością zwracaną. Ponieważ `if..then..else` sama jest wyrażeniem, treść `then` bloku `else` lub treści bloku zostanie zwrócona w zależności od wartości wejściowej.

## <a name="moving-your-script-code-into-the-implementation-file"></a>Przeniesienie kodu skryptu do pliku implementacji

W poprzednich sekcjach tego artykułu przedstawiono typowy pierwszy krok podczas pisania F# kodu: pisanie początkowej funkcji i wykonywanie jej interaktywnie przy użyciu FSI. Jest to nazywane programowaniem opartym na REPL, gdzie [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) to "Read-Szacuj-Print pętl". Jest to doskonały sposób na eksperymentowanie z funkcjami do momentu, w którym będzie działać.

Następnym krokiem w programowaniu opartym na REPL polega na przeniesieniu kodu roboczego F# do pliku implementacji. Może zostać następnie skompilowany przez F# kompilator do zestawu, który może być wykonywany.

Aby rozpocząć, Otwórz `ClassLibraryDemo.fs`.  Zauważysz, że jakiś kod już istnieje. Przejdź dalej i usuń definicję klasy, ale upewnij się, że [`namespace`](../language-reference/namespaces.md) deklaracja znajduje się u góry.

Następnie utwórz nową [`module`](../language-reference/modules.md) nazwę `PigLatin` i skopiuj `toPigLatin` funkcję do niej w taki sposób:

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

Następnie ponownie Otwórz `Script.fsx` plik i Usuń całą `toPigLatin` funkcję, ale pamiętaj, aby zachować następujące dwa wiersze w pliku:

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

Zaznacz oba wiersze tekstu i naciśnij klawisze ALT + ENTER, aby wykonać te wiersze w FSI. Spowoduje to załadowanie zawartości biblioteki z wieprzowiny do procesu FSI i `open` `ClassLibraryDemo` przestrzeni nazw w celu uzyskania dostępu do funkcji.

Następnie w oknie FSI wywołaj funkcję przy użyciu `PigLatin` zdefiniowanego wcześniej modułu:

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

Prawnego! Uzyskasz te same wyniki jak poprzednio, ale teraz załadowano je z pliku F# implementacji. Istotną różnicą jest to F# , że pliki źródłowe są kompilowane do zestawów, które można wykonać w dowolnym miejscu, a nie tylko w FSI.

## <a name="summary"></a>Podsumowanie

W tym artykule przedstawiono następujące informacje:

1. Jak skonfigurować Visual Studio Code za pomocą Ionide.
2. Jak utworzyć swój pierwszy F# projekt przy użyciu Ionide.
3. Używanie F# skryptów do pisania pierwszej F# funkcji w Ionide, a następnie wykonywania jej w FSI.
4. Jak przeprowadzić migrację kodu skryptu do F# źródła, a następnie wywołać ten kod z FSI.

Teraz możesz napisać znacznie więcej F# kodu przy użyciu Visual Studio Code i Ionide.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Poniżej przedstawiono kilka sposobów rozwiązywania niektórych problemów, które mogą być wykonywane w programie:

1. Aby uzyskać funkcje edytowania kodu Ionide, należy zapisać F# pliki na dysku i w folderze, który jest otwarty w obszarze roboczym Visual Studio Code.
2. Jeśli wprowadzono zmiany w systemie lub zainstalowano wymagania wstępne Ionide z Visual Studio Code Otwórz, uruchom ponownie Visual Studio Code.
3. Sprawdź, czy można użyć F# kompilatora i F# interaktywnie z wiersza polecenia bez w pełni kwalifikowanej ścieżki. Można to zrobić `fsc` , wpisując w wierszu polecenia F# kompilatora `fsi` i lub `fsharpi` dla narzędzi wizualnych F# w systemach Windows i mono odpowiednio na komputerze Mac/Linux.
4. Jeśli w katalogach projektu znajdują się nieprawidłowe znaki, Ionide może nie zadziałał.  W takim przypadku Zmień nazwy katalogów projektu.
5. Jeśli żaden z poleceń Ionide nie działa, sprawdź powiązania klawiszy [Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) , aby sprawdzić, czy są one zastępowane przypadkowo.
6. Jeśli Ionide jest przerwany na komputerze, a żaden z powyższych elementów nie rozwiązał problemu, spróbuj usunąć `ionide-fsharp` katalog na maszynie i ponownie zainstalować pakiet wtyczek.

Ionide to projekt typu "open source" skompilowany i obsługiwany przez członków F# społeczności. Zgłoś problemy i śmiało, aby współtworzyć [Ionide-programu vscode: FSharp repozytorium](https://github.com/ionide/ionide-vscode-fsharp)GitHub.

Jeśli masz problem z raportem, postępuj zgodnie [z instrukcjami dotyczącymi pobierania dzienników do użycia podczas zgłaszania problemu](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).

Możesz również poszukać dalszej pomocy od deweloperów Ionide i F# społeczności w [kanale warunkom Ionide](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się F# więcej na temat funkcji języka, zobacz [Przewodnik F# ](../tour.md)po stronie.
