---
title: 'Wprowadzenie do programu F # w kodzie programu Visual Studio z Ionide'
description: "Dowiedz się, jak używanie F # za pomocą programu Visual Studio Code i Ionide suite wtyczki."
keywords: visual f#, f#, functional programming, .NET, Visual Studio Code, vscode, Ionide
author: cartermp
ms.author: phcart
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 49775139-082e-442f-b5a2-dd402399b5d2
ms.openlocfilehash: 83099005074ea273eae5319edacd2e2ee0f7145f
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="getting-started-with-f-in-visual-studio-code-with-ionide"></a>Wprowadzenie do programu F # w kodzie programu Visual Studio z Ionide

Możesz pisać F # [Visual Studio Code](https://code.visualstudio.com) z [wtyczki Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp), aby uzyskać doskonałe środowisko IDE i platform, lekkie IntelliSense i refaktoryzacje podstawowego kodu.  Odwiedź stronę [Ionide.io](https://ionide.io) Aby dowiedzieć się więcej o pakiecie wtyczki.

## <a name="prerequisites"></a>Wymagania wstępne

F # 4.0 lub nowszy musi być zainstalowany na tym komputerze do użycia Ionide.

Musi mieć również [git zainstalowane](https://git-scm.com/download) i znajduje się na ŚCIEŻCE, aby użyć szablonów projektu w Ionide.  Można sprawdzić, czy jest poprawnie zainstalowany, wpisując `git` na naciśnięcie prompt.and polecenia **Enter**.

### <a name="windows"></a>Windows

Jeśli w systemie Windows, masz dwie opcje instalacji F #.

Jeśli wcześniej zainstalowanego programu Visual Studio i nie ma F #, możesz [zainstalować narzędzia Visual F # Tools](get-started-visual-studio.md#installing-f).  Spowoduje to zainstalowanie wszystkich składników niezbędnych do zapisu, kompilowania i wykonywania kodzie języka F #.

Jeśli nie chcesz zainstalować program Visual Studio, użyj poniższych instrukcji:

1. Zainstaluj [.NET Framework 4.5 lub wyższej](https://www.microsoft.com/en-US/download/details.aspx?id=30653) w przypadku systemu Windows 7.  Jeśli używasz systemu Windows 8 lub nowszym, nie trzeba w tym celu.

2. Zainstaluj zestaw Windows SDK dla Twojego systemu operacyjnego:

    * [Windows 10 SDK](https://dev.windows.com/en-US/downloads/windows-10-sdk)
    * [Windows 8.1 SDK](https://developer.microsoft.com/windows/downloads/sdk-archive)
    * [Windows 8 SDK](https://developer.microsoft.com/windows/downloads/sdk-archive)
    * [Windows 7 SDK](https://www.microsoft.com/download/details.aspx?id=8279)

3. Zainstaluj [Microsoft Build Tools 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48159).  Należy również zainstalować [Microsoft kompilacji narzędzia 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40760).

4. Zainstaluj [narzędzia Visual F #](https://www.microsoft.com/en-us/download/details.aspx?id=48179).

W 64-bitowym systemie Windows narzędzi i kompilatora znajdują się w folderze:

```
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsc.exe
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsi.exe
C:\Program Files (x86)\Microsoft SDKs\F#\4.0\Framework\v4.0\fsiAnyCpu.exe
```

W 32-bitowym systemie Windows narzędzia kompilatora znajdują się w folderze:

```
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsc.exe
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsi.exe
C:\Program Files\Microsoft SDKs\F#\4.0\Framework\v4.0\fsiAnyCpu.exe
```

Ionide automatycznie wykrywa kompilatora i narzędzi, ale jeśli z jakiegoś powodu nie (na przykład Visual F # Tools zostały zainstalowane do innego katalogu), można ręcznie dodać folderu zawierającego (`...\Microsoft SDKs\F#\4.0`) do ścieżki.

### <a name="macos"></a>macOS

Na macOS, używa Ionide [Mono](https://www.mono-project.com).  Najprostszym sposobem zainstalowania Mono na macOS odbywa się za pośrednictwem oprogramowania Homebrew.  W terminalu, po prostu wpisz następujące polecenie:

```
brew install mono
```

### <a name="linux"></a>Linux

W systemie Linux, używa również Ionide [Mono](https://www.mono-project.com).  Jeśli używasz Debian i Ubuntu, można użyć następujących czynności:

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a>Instalowanie dodatku Ionide i Visual Studio Code

Można zainstalować program Visual Studio Code z [code.visualstudio.com](https://code.visualstudio.com) witryny sieci Web.  Po wykonaniu tej istnieją dwa sposoby znajdowania Ionide wtyczki:

1. Użyj polecenia palety (Ctrl + Shift + P w systemie Windows, ⌘ + Shift + P na macOS, Ctrl + Shift + P w systemie Linux) i wpisz następujące polecenie:

    ```
    >ext install Ionide
    ```

2. Kliknij ikonę rozszerzenia i wyszukaj "Ionide":

    ![](media/getting-started-vscode/vscode-ext.png)

Tylko wtyczki, wymagana jest obsługa F # w programie Visual Studio Code [języka fsharp Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).  Jednakże można także zainstalować [SFAŁSZOWANA Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) i uzyskać [SFAŁSZOWAĆ](https://fake.build/) obsługuje i [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) uzyskanie [Paket](https://fsprojects.github.io/Paket/) obsługuje.  FAŁSZYWE i Paket są dodatkowe F # społeczności narzędzia do tworzenia projektów i zarządzanie nimi zależności, odpowiednio.

## <a name="creating-your-first-project-with-ionide"></a>Tworzenie pierwszego projektu z Ionide

Aby utworzyć nowy projekt F #, Otwórz program Visual Studio Code w nowym folderze (można określić nazwę dowolne).

![](media/getting-started-vscode/vscode-open-dir.png)

Następnie otwórz palety polecenia (Ctrl + Shift + P w systemie Windows, ⌘ + Shift + P na macOS, Ctrl + Shift + P w systemie Linux) i wpisz następujące polecenie:

```
>f#: New Project
```

Jest to obsługiwane przez [FORGE](https://github.com/fsharp-editing/Forge) projektu.  Powinny pojawić się dane podobne do poniższych:

![](media/getting-started-vscode/vscode-new-proj.png)

> [!NOTE]
Jeśli nie widzisz powyższego, spróbuj odświeżyć szablony, uruchamiając następujące polecenie w palecie polecenia: `>F#: Refresh Project Templates`.

Wybierz opcję "F #: nowego projektu" za pomocą **Enter**, która spowoduje przejście do tego kroku:

![](media/getting-started-vscode/vscode-proj-type.png)

Wybierz opcję szablon dla określonego typu projektu.  Istnieje kilka opcji, takich jak [FsLab](https://fslab.org) szablon do analizy danych lub [Suave](https://suave.io) szablon programowania sieci Web.  W tym artykule wykorzystano `classlib` szablon, więc podkreślenie i naciśnij **Enter**.  Następnie zostanie osiągnąć następny krok:

![](media/getting-started-vscode/vscode-new-dir.png)

Dzięki temu można utworzyć projektu w innym katalogu, jeśli chcesz.  Pozostaw pole puste, teraz.  Projekt zostanie utworzony w bieżącym katalogu.  Po naciśnięciu **Enter**, osiągną następujący krok:

![](media/getting-started-vscode/vscode-proj-name.png)

Dzięki temu można nazwy projektu.  F # używa [przypadku Pascal](http://c2.com/cgi/wiki?PascalCase) dla nazwy projektu.  W tym artykule wykorzystano `ClassLibraryDemo` jako nazwy.  Po wprowadzeniu nazwy dla projektu, kliknij przycisk **Enter**.

Po wykonaniu poprzednich kroków kroku, należy pobrać Visual Studio Code obszaru roboczego po lewej stronie do wyglądać mniej więcej tak:

![](media/getting-started-vscode/vscode-new-proj-explorer.png)

Ten szablon generuje kilka rzeczy, które można znaleźć przydatne:

1. F # projektu, underneath `ClassLibraryDemo` folderu.
2. Dodawanie pakietów za pomocą struktury poprawny katalog [ `Paket` ](https://fsprojects.github.io/Paket/).
3. Obsługujący wiele platform kompilacji skryptu o [ `FAKE` ](https://fake.build/).
4. `paket.exe` Plik wykonywalny, który można pobrać pakietów i rozpoznać zależności dla Ciebie.
5. A `.gitignore` plik, jeśli chcesz dodać ten projekt do kontroli źródła na podstawie Git.

## <a name="writing-some-code"></a>Pisanie kodu

Otwórz *ClassLibraryDemo* folderu.  Powinny pojawić się następujące pliki:

1. `ClassLibraryDemo.fs`, F # pliku z implementacją z klasą zdefiniowane.
2. `CassLibraryDemo.fsproj`, F # plik projektu używany do tworzenia tego projektu.
3. `Script.fsx`, F # pliku skryptu, który ładuje plik źródłowy.
4. `paket.references`, plik Paket, który określa zależności projektu.

Otwórz `Script.fsx`i Dodaj następujący kod na końcu:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Ta funkcja konwertuje wyraz do formularza z [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin).  Następnym krokiem jest do oceny przy użyciu języka F # Interactive (FSI).

Zaznacz całą funkcję (powinien być 11 wierszy).  Po jego zostanie wyróżniona, przytrzymaj **Alt** klucza i trafień **Enter**.  Można zauważyć okno wyskakujące poniżej, a powinny mieć podobny do następującego:

![](media/getting-started-vscode/vscode-fsi.png)

Czy to trzy czynności:

1. Proces FSI jego uruchomienia.
2. Wyróżniony kod go wysyłane za pośrednictwem procesu FSI.
3. Proces FSI oceniane wysyłane przez kod.

Ponieważ był wysyłany za pośrednictwem [funkcja](../language-reference/functions/index.md), można teraz wywołać tej funkcji z FSI!  W oknie interaktywnym wpisz następujące polecenie:

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

Funkcja może działać zgodnie z oczekiwaniami.  Gratulacje, po prostu zapisane pierwszej funkcji F # w programie Visual Studio Code i oceniać za jego pomocą FSI!

>[!NOTE]
Jak można zauważyć, wiersze FSI kończą się `;;`.  Jest to spowodowane FSI umożliwia wprowadzanie wielu wierszy.  `;;` Na końcu umożliwia FSI wiedzieć, po zakończeniu kod.

## <a name="explaining-the-code"></a>Wyjaśniający kodu

Jeśli nie masz pewności o kodzie faktycznie czynności, poniżej przedstawiono krok po kroku.

Jak widać, `toPigLatin` jest funkcję, która przyjmuje word jako dane wejściowe i konwertuje ją na Pig Latin reprezentację wyrazie.  Dla tej reguły są następujące:

Jeśli pierwszy znak w wyrazie rozpoczyna się od samogłosek, należy dodać "yay" do końca słowa.  Jeśli go nie zaczyna się od samogłosek, umieść ten pierwszy znak na końcu Word i "ay" Dodaj do niej.

Można zauważyć następujące opcje w FSI:

```
val toPigLatin : word:string -> string
```

Ta stwierdza, że `toPigLatin` jest funkcją, która przyjmuje `string` jako dane wejściowe (nazywane `word`) i zwraca innego `string`.  Jest to nazywane [podpis typu funkcji](https://fsharpforfunandprofit.com/posts/function-signatures/), podstawowe technologie języka F #, która jest kluczem do zrozumienia kodzie języka F #.  Należy także zauważyć, to jeśli Aktywuj funkcji w programie Visual Studio Code.

W treści funkcji można zauważyć dwa różne części:

1. Wewnętrzna funkcja wywoływana `isVowel`, która określa, czy dany znak (`c`) jest samogłoskę przez sprawdzenie, czy pasujący wzorców podana za pośrednictwem [dopasowanie wzorca](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) Wyrażenie, które sprawdza, czy pierwszy znak jest samogłoskę i konstruuje wartość zwracaną poza wprowadzanie znaków na podstawie pierwszego znaku, gdy był samogłoskę lub nie:

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

Przepływ `toPigLatin` jest w związku z tym:

Sprawdź, czy pierwszy znak wejściowy word samogłoskę.  Jeśli tak jest, Dołącz "yay" do końca słowa.  W przeciwnym razie umieść ten pierwszy znak na końcu Word i "ay" Dodaj do niej.

Brak końcowego rzecz do Zwróć uwagę na ten temat: Brak nie jawna instrukcja ma zostać zwrócony przez funkcję, w odróżnieniu od wielu innych języków tam.  To dlatego F # jest oparte na wyrażeniach oraz ostatnich wyrażenie w treści funkcji jest zwracana wartość.  Ponieważ `if..then..else` jest wyrażenie, treść `then` bloku lub treści `else` bloku zostanie zwrócony w zależności od wartości wejściowej.

## <a name="moving-your-script-code-into-the-implementation-file"></a>Przenoszenie kodu skryptu do pliku implementacji

Poprzednich sekcjach, w tym artykule przedstawiono typowe pierwszą czynnością przy tworzeniu kodzie języka F #: pisanie początkowej funkcji i jej wykonanie interakcyjnie z FSI.  Jest to nazywane REPL-driven development, gdzie oznacza REPL "Pętlę odczytu oceny-drukarek".  Jest to dobry sposób na wypróbowanie funkcji, aż do uzyskania elementu pracy.

Następny krok w REPL-driven development, jest Przenieś pracy kod do pliku implementacji F #.  Go można następnie można skompilować przez kompilator języka F # do zestawu, które mogą być wykonywane.

Aby rozpocząć, otwórz `ClassLibraryDemo.fs`.  Można zauważyć, że kod jest już istnieje.  Przejdź dalej i usunąć definicji klasy, ale pamiętaj pozostawić [ `namespace` ](../language-reference/namespaces.md) deklaracji u góry.

Następnie należy utworzyć nowy [ `module` ](../language-reference/modules.md) o nazwie `PigLatin` i skopiuj `toPigLatin` funkcji w nim sposób:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

Jest to jedna z wielu sposobów, jeśli chcesz także wywoływanie kodu z języka C# lub Visual Basic, projekty można organizować funkcje w kodzie języka F # i typowym podejściem.

Następnie otwórz folder `Script.fsx` ponownie, a następnie usuń całą `toPigLatin` działać, ale pamiętaj zachować następujące dwa wiersze w pliku:

```
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

Pierwszy wiersz jest wymagany dla skryptów do załadowania FSI `ClassLibraryDemo.fs`.  Drugi wiersz jest udogodnienie: pomijając go jest opcjonalne, ale będzie musiał podać `open ClassLibraryDemo` w oknie FSI, jeśli chcesz wyświetlić `ToPigLatin` modułu do zakresu.

Następnie w oknie FSI, wywołaj funkcję z `PigLatin` moduł, który został zdefiniowany wcześniej:

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

Powodzenie!  Pobierz wyniki przed, ale teraz załadowanego z pliku implementacji F #.  W tym miejscu główna różnica polega na tym, że pliki źródłowe języka F # są skompilowane w zestawy, które mogą być wykonywane w dowolnym miejscu, nie tylko w FSI.

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
3. Sprawdź, czy można użyć kompilator języka F # i F # interactive w wierszu polecenia bez w pełni kwalifikowaną ścieżkę.  Możesz to zrobić, wpisując `fsc` w wierszu polecenia, aby uzyskać kompilator języka F # i `fsi` lub `fsharpi` Visual F # tools w systemach Windows i Mono na system Mac/Linux, odpowiednio.
4. Jeśli masz nieprawidłowe znaki w katalogach projektu Ionide może nie działać.  Jeśli jest to możliwe, Zmień nazwy katalogów projektu.
5. Brak polecenia Ionide pracy, sprawdź Twojej [powiązań kluczy programu Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) aby zobaczyć, czy jest zastępowanie ich przypadkowo.
6. Jeśli Ionide jest dzielony na komputerze, a żadne z powyższych poprawił problemu, spróbuj usunąć `ionide-fsharp` katalogu na komputerze i ponowne zainstalowanie zestawu dodatku.

Ionide to projekt typu open source, wbudowane i obsługiwana przez członków społeczności F #.  Sprawdź zgłaszania problemów i możesz zająć się na [Ionide VSCode: repozytorium GitHub języka FSharp](https://github.com/ionide/ionide-vscode-fsharp).

Jeśli masz problem do raportu, postępuj [instrukcje dotyczące pobierania dzienników do użycia podczas raportowania problemu](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).

Możesz również poprosić Aby uzyskać dalszą pomoc od Ionide deweloperów i F # społeczności w [kanału Ionide Gitter](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej na temat języka F # i funkcji języka, zapoznaj się [samouczek programu F #](../tour.md).

## <a name="see-also"></a>Zobacz także

[Przewodnik po F#](../tour.md)

[Dokumentacja języka F#](../language-reference/index.md)

[Funkcje](../language-reference/functions/index.md)

[Moduły](../language-reference/modules.md)

[Przestrzenie nazw](../language-reference/namespaces.md)

[Ionide-VSCode: FSharp](https://github.com/ionide/ionide-vscode-fsharp)
