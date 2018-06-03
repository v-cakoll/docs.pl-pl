---
title: 'Rozpoczynanie pracy z F # w kodzie programu Visual Studio'
description: 'Dowiedz się, jak używanie F # za pomocą programu Visual Studio Code i Ionide suite wtyczki.'
ms.date: 05/28/2018
ms.openlocfilehash: e56274caf36be231338876ded5a6d7c7968906b0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728631"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Rozpoczynanie pracy z F # w kodzie programu Visual Studio

Możesz pisać F # [Visual Studio Code](https://code.visualstudio.com) z [wtyczki Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)w celu uzyskania maksymalnego komfortu obsługi zintegrowane środowisko rozwoju (IDE) i platform, lekkie IntelliSense i podstawowe kodu refaktoryzacje. Odwiedź stronę [Ionide.io](http://ionide.io) Aby dowiedzieć się więcej o pakiecie wtyczki.

## <a name="prerequisites"></a>Wymagania wstępne

Musi mieć [git zainstalowane](https://git-scm.com/download) i znajduje się na ŚCIEŻCE, aby użyć szablonów projektu w Ionide. Można sprawdzić, czy jest poprawnie zainstalowany, wpisując `git --version` w wierszu polecenia i naciskając klawisz **Enter**.

### <a name="macostabmacos"></a>[macOS](#tab/macos)

Używa Ionide [Mono](http://www.mono-project.com). Najprostszym sposobem zainstalowania Mono na macOS odbywa się za pośrednictwem oprogramowania Homebrew. W terminalu, po prostu wpisz następujące polecenie:

```
brew install mono
```

Należy również zainstalować [.NET Core SDK](https://www.microsoft.com/net/download).

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

W systemie Linux, używa również Ionide [Mono](https://www.mono-project.com). Jeśli używasz Debian i Ubuntu, można użyć następujących czynności:

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

Należy również zainstalować [.NET Core SDK](https://www.microsoft.com/net/download).

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

Jeśli w systemie Windows, należy najpierw [zainstalować program Visual Studio z obsługą F #](get-started-visual-studio.md#installing-f). Spowoduje to zainstalowanie wszystkich składników niezbędnych do zapisu, kompilowania i wykonywania kodzie języka F #.

Należy również zainstalować [.NET Core SDK](https://www.microsoft.com/net/download/).

---

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a>Instalowanie dodatku Ionide i Visual Studio Code

Można zainstalować program Visual Studio Code z [code.visualstudio.com](https://code.visualstudio.com) witryny sieci Web.

Następnie kliknij ikonę rozszerzenia i wyszukaj "Ionide":

Tylko wtyczki, wymagana jest obsługa F # w programie Visual Studio Code [języka fsharp Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Jednakże można także zainstalować [SFAŁSZOWANA Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) uzyskanie [SFAŁSZOWAĆ](https://fsharp.github.io/FAKE/) obsługuje i [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) można pobrać [Paket](https://fsprojects.github.io/Paket/) obsługuje. FAŁSZYWE i Paket są dodatkowe narzędzia społeczności F # do tworzenia projektów i zarządzanie zależności, odpowiednio.

## <a name="creating-your-first-project-with-ionide"></a>Tworzenie pierwszego projektu z Ionide

Aby utworzyć nowy projekt F #, Otwórz program Visual Studio Code w nowym folderze (można określić nazwę dowolne).

Następnie otwórz folder pallette polecenia (**Widok > Pallette polecenia**) i wpisz następujące polecenie:

```
> F# new project
```

Jest to obsługiwane przez [FORGE](https://github.com/fsharp-editing/Forge) projektu.

> [!NOTE]
Jeśli nie widzisz opcji szablonu, spróbuj odświeżyć szablony, uruchamiając następujące polecenie w palecie polecenia: `>F#: Refresh Project Templates`.

Wybierz opcję "F #: nowego projektu" za pomocą **Enter**. Powoduje to przejście do następnego kroku, czyli wybierania szablonu projektu.

Wybierz `classlib` szablonu i naciśnij klawisz **Enter**.

Następnie wybierz katalog do tworzenia projektu w. Jeśli pole pozostanie puste, używa bieżącego katalogu.

Na koniec nazwy projektu w ostatnim kroku. F # używa [przypadku Pascal](http://c2.com/cgi/wiki?PascalCase) dla nazwy projektu. W tym artykule wykorzystano `ClassLibraryDemo` jako nazwy. Po wprowadzeniu nazwy dla projektu, kliknij przycisk **Enter**.

Po wykonaniu poprzedniego kroku, należy pobrać Visual Studio kod obszaru roboczego po lewej stronie się z następujących czynności:

1. F # projektu, underneath `ClassLibraryDemo` folderu.
2. Dodawanie pakietów za pomocą struktury poprawny katalog [ `Paket` ](https://fsprojects.github.io/Paket/).
3. Obsługujący wiele platform kompilacji skryptu o [ `FAKE` ](https://fsharp.github.io/FAKE/).
4. `paket.exe` Pliku wykonywalnego, który można pobrać pakietów i rozpoznać zależności dla Ciebie.
5. A `.gitignore` plik, jeśli chcesz dodać ten projekt do kontroli źródła na podstawie Git.

## <a name="writing-some-code"></a>Pisanie kodu

Otwórz *ClassLibraryDemo* folderu.  Powinny pojawić się następujące pliki:

1. `ClassLibraryDemo.fs`, F # pliku z implementacją z klasą zdefiniowane.
2. `ClassLibraryDemo.fsproj`, F # plik projektu używany do tworzenia tego projektu.
3. `Script.fsx`, F # plik skryptu, który ładuje plik źródłowy.
4. `paket.references`, plik Paket, który określa zależności projektu.

Otwórz `Script.fsx`i Dodaj następujący kod na końcu:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Ta funkcja konwertuje wyraz do formularza z [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin). Następnym krokiem jest do oceny przy użyciu języka F # Interactive (FSI).

Zaznacz całą funkcję (powinien być 11 wierszy). Po jego zostanie wyróżniona, przytrzymaj **Alt** klucza i trafień **Enter**. Można zauważyć okno wyskakujące poniżej, a powinny mieć podobny do następującego:

![Przykład F # Interactive danych wyjściowych z Ionide](media/getting-started-vscode/vscode-fsi.png)

Czy to trzy czynności:

1. Proces FSI jego uruchomienia.
2. Wyróżniony kod go wysyłane za pośrednictwem procesu FSI.
3. Proces FSI oceniane wysyłane przez kod.

Ponieważ był wysyłany za pośrednictwem [funkcja](../language-reference/functions/index.md), można teraz wywołać tej funkcji z FSI! W oknie interaktywnym wpisz następujące polecenie:

```fsharp
toPigLatin "banana";;
```

Powinny być widoczne następujące wyniki:

```fsharp
val it : string = "ananabay"
```

Teraz spróbujmy się od samogłosek jako pierwszą literę. Wprowadź następujące informacje:

```fsharp
toPigLatin "apple";;
```

Powinny być widoczne następujące wyniki:

```fsharp
val it : string = "appleyay"
```

Funkcja może działać zgodnie z oczekiwaniami. Gratulacje, po prostu zapisane pierwszej funkcji F # w programie Visual Studio Code i oceniać za jego pomocą FSI!

>[!NOTE]
Jak można zauważyć, wiersze FSI kończą się `;;`. Jest to spowodowane FSI umożliwia wprowadzanie wielu wierszy. `;;` Na końcu umożliwia FSI wiedzieć, po zakończeniu kod.

## <a name="explaining-the-code"></a>Wyjaśniający kodu

Jeśli nie masz pewności o kodzie faktycznie czynności, poniżej przedstawiono krok po kroku.

Jak widać, `toPigLatin` jest funkcją, która przyjmuje word jako dane wejściowe i konwertuje ją na Pig Latin reprezentację wyrazie. Dla tej reguły są następujące:

Jeśli pierwszy znak w wyrazie rozpoczyna się od samogłosek, należy dodać "yay" do końca słowa. Jeśli go nie zaczyna się od samogłosek, umieść ten pierwszy znak na końcu Word i "ay" Dodaj do niej.

Można zauważyć następujące opcje w FSI:

```fsharp
val toPigLatin : word:string -> string
```

Stanowi to, że `toPigLatin` to funkcja, która przyjmuje `string` jako dane wejściowe (nazywane `word`) i zwraca innego `string`. Jest to nazywane [podpis typu funkcji](https://fsharpforfunandprofit.com/posts/function-signatures/), podstawowe technologie języka F #, która jest kluczem do zrozumienia kodzie języka F #. Należy także zauważyć, to jeśli Aktywuj funkcji w programie Visual Studio Code.

W treści funkcji można zauważyć dwa różne części:

1. Wewnętrzna funkcja wywoływana `isVowel`, określający, jeśli dany znak (`c`) jest samogłoskę przez sprawdzenie, czy pasujący wzorców podana za pośrednictwem [dopasowanie wzorca](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) Wyrażenie, która sprawdza, czy pierwszy znak samogłoskę, a konstrukcje zwracanym wartość poza wprowadzanie znaków oparte na jeśli pierwszym znakiem jest samogłoskę lub nie:

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

Przepływ `toPigLatin` jest w związku z tym:

Sprawdź, czy pierwszy znak wejściowy word samogłoskę. Jeśli tak jest, Dołącz "yay" do końca słowa. W przeciwnym razie umieść ten pierwszy znak na końcu Word i "ay" Dodaj do niej.

Brak końcowego rzecz do Zwróć uwagę na ten temat: Brak nie jawna instrukcja ma zostać zwrócony przez funkcję, w odróżnieniu od wielu innych języków tam. To dlatego F # jest oparte na wyrażeniach oraz ostatnich wyrażenie w treści funkcji jest zwracana wartość. Ponieważ `if..then..else` jest wyrażenie, treść `then` bloku lub treści `else` bloku zostanie zwrócony w zależności od wartości wejściowej.

## <a name="moving-your-script-code-into-the-implementation-file"></a>Przenoszenie kodu skryptu do pliku implementacji

Poprzednich sekcjach, w tym artykule przedstawiono typowe pierwszą czynnością przy tworzeniu kodzie języka F #: pisanie początkowej funkcji i jej wykonanie interakcyjnie z FSI. Jest to nazywane REPL-driven development, gdzie [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) oznacza "Pętlę odczytu oceny-drukarek". Jest to dobry sposób na wypróbowanie funkcji, aż do uzyskania elementu pracy.

Następny krok w REPL-driven development, jest Przenieś pracy kod do pliku implementacji F #. Go można następnie zbierane przez kompilator języka F # w zespół, który może zostać wykonany.

Aby rozpocząć, otwórz `ClassLibraryDemo.fs`.  Można zauważyć, że kod jest już istnieje. Przejdź dalej i usunąć definicji klasy, ale pamiętaj pozostawić [ `namespace` ](../language-reference/namespaces.md) deklaracji u góry.

Następnie należy utworzyć nowy [ `module` ](../language-reference/modules.md) o nazwie `PigLatin` i skopiuj `toPigLatin` funkcji w nim sposób:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

Następnie otwórz folder `Script.fsx` ponownie, a następnie usuń całą `toPigLatin` działać, ale pamiętaj zachować następujące dwa wiersze w pliku:

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

Pierwszy wiersz jest wymagany dla skryptów do załadowania FSI `ClassLibraryDemo.fs`. Drugi wiersz jest udogodnienie: pomijając go jest opcjonalne, ale będzie musiał podać `open ClassLibraryDemo` w oknie FSI, jeśli chcesz wyświetlić `ToPigLatin` modułu do zakresu.

Następnie w oknie FSI, wywołaj funkcję z `PigLatin` moduł, który został zdefiniowany wcześniej:

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

Powodzenie! Pobierz wyniki przed, ale teraz załadowanego z pliku implementacji F #. Główną różnicą jest kompilowane pliki źródłowe języka F # w zestawy, które mogą być wykonywane w dowolnym miejscu, nie tylko w FSI.

## <a name="summary"></a>Podsumowanie

W tym artykule kiedy znasz już:

1. Jak skonfigurować program Visual Studio Code z Ionide.
2. Jak utworzyć pierwszy projekt F # z Ionide.
3. Jak używać F # skryptów do zapisywania pierwszej funkcji F # w Ionide i wykonaj go w FSI.
4. Jak przeprowadzić migrację skryptu kodu źródłowego języka F #, a następnie wywołać kodu z FSI.

Teraz jest wyposażona w kodzie znacznie więcej F # za pomocą programu Visual Studio Code i Ionide.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Poniżej przedstawiono kilka sposobów, można rozwiązać niektóre problemy, które mogą być uruchamiane na:

1. Aby uzyskać funkcji Ionide edycji kodu, plikach języka F # trzeba zapisać na dysku i wewnątrz folderu, który jest otwarty w obszarze roboczym Visual Studio Code.
2. Jeśli zostały wprowadzone zmiany w systemie lub zainstalowane wymagania wstępne Ionide z programu Visual Studio Code Otwórz, uruchom ponownie program Visual Studio Code.
3. Sprawdź, czy można użyć kompilator języka F # i F # interactive w wierszu polecenia bez w pełni kwalifikowaną ścieżkę. Możesz to zrobić, wpisując `fsc` w wierszu polecenia, aby uzyskać kompilator języka F # i `fsi` lub `fsharpi` Visual F # tools w systemach Windows i Mono na system Mac/Linux, odpowiednio.
4. Jeśli masz nieprawidłowe znaki w katalogach projektu Ionide może nie działać.  Jeśli jest to możliwe, Zmień nazwy katalogów projektu.
5. Brak polecenia Ionide pracy, sprawdź Twojej [powiązań kluczy programu Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) aby zobaczyć, czy jest zastępowanie ich przypadkowo.
6. Jeśli Ionide jest dzielony na komputerze, a żadne z powyższych poprawił problemu, spróbuj usunąć `ionide-fsharp` katalogu na komputerze i ponowne zainstalowanie zestawu dodatku.

Ionide to projekt typu open source, wbudowane i obsługiwana przez członków społeczności F #. Sprawdź zgłaszania problemów i możesz zająć się na [Ionide VSCode: repozytorium GitHub języka FSharp](https://github.com/ionide/ionide-vscode-fsharp).

Jeśli masz problem do raportu, postępuj [instrukcje dotyczące pobierania dzienników do użycia podczas raportowania problemu](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).

Możesz również poprosić Aby uzyskać dalszą pomoc od Ionide deweloperów i F # społeczności w [kanału Ionide Gitter](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej na temat języka F # i funkcji języka, zapoznaj się [samouczek programu F #](../tour.md).
