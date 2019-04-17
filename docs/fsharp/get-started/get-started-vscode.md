---
title: Rozpoczynanie pracy z usługą F# w programie Visual Studio Code
description: Dowiedz się, jak używać F# za pomocą programu Visual Studio Code i Ionide zestawu wtyczki.
ms.date: 12/23/2018
ms.openlocfilehash: 7c2ecab14b3351d441249e7fc7cb3188a4ee7eba
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612891"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Rozpoczynanie pracy z usługą F# w programie Visual Studio Code

Można napisać F# w [programu Visual Studio Code](https://code.visualstudio.com) z [wtyczki Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) uzyskać dla wielu platform, proste tworzenie środowiska IDE (Integrated) spełni za pomocą funkcji IntelliSense i podstawowego kodu operacje refaktoryzacji. Odwiedź stronę [Ionide.io](http://ionide.io) Aby dowiedzieć się więcej na temat dodatku plug-in.

Aby rozpocząć, upewnij się, że [ F# i poprawnie zainstalowaną wtyczką Ionide](install-fsharp.md#install-f-with-visual-studio-code).

> [!NOTE]
> Ionide wygeneruje .NET Framework F# projektów, nie dotnet rdzeń procesora, który może mieć problemy ze zgodnością między platformami. Jeśli są uruchomione na **Linux** lub **OSX**, prostszy sposób na rozpoczęcie pracy jest użycie [narzędzi wiersza polecenia](https://docs.microsoft.com/en-us/dotnet/fsharp/get-started/get-started-command-line).

## <a name="creating-your-first-project-with-ionide"></a>Tworzenie pierwszego projektu za pomocą Ionide

Aby utworzyć nowy F# projektu, Otwórz program Visual Studio Code w nowym folderze (można określić nazwę wedle uznania).

Następnie otwórz paletę poleceń (**Widok > paletę poleceń**) i wpisz następujące polecenie:

```
> F# new project
```

Jest to obsługiwane przez [FORGE](https://github.com/fsharp-editing/Forge) projektu.

> [!NOTE]
> Jeśli nie widzisz opcji szablonów, Odśwież szablony, uruchamiając następujące polecenie w palecie poleceń: `>F#: Refresh Project Templates`.

Wybierz pozycję "F#: Nowy projekt", naciskając **Enter**. Spowoduje to przejście do następnego kroku, która jest przez wybranie szablonu projektu.

Wybierz `classlib` szablonu, a następnie wybierz pozycję **Enter**.

Następnie wybierz katalog, aby utworzyć projekt w programie. Jeśli pole pozostanie puste, zostanie użyta bieżącego katalogu.

Na koniec nazwę projektu w ostatnim kroku. F#używa [pisanymi wielkimi literami](http://c2.com/cgi/wiki?PascalCase) dotyczące nazw projektów. W tym artykule wykorzystano `ClassLibraryDemo` jako nazwę. Po wprowadzeniu nazwę dla projektu trafień **Enter**.

Jeśli wykonano poprzedniego kroku, należy uzyskać Visual Studio Code obszaru roboczego po lewej stronie do pojawiają się z następujących czynności:

1. F# Sam projekt poniżej `ClassLibraryDemo` folderu.
2. Trwa dodawanie pakietów przy użyciu struktury katalogu poprawny [ `Paket` ](https://fsprojects.github.io/Paket/).
3. Dla wielu platform, tworzenie skript [ `FAKE` ](https://fsharp.github.io/FAKE/).
4. `paket.exe` Plik wykonywalny, który można pobrać pakiety i rozwiązywanie zależności.
5. A `.gitignore` plik, jeśli chcesz dodać ten projekt do kontroli źródła opartych o Git.

## <a name="writing-some-code"></a>Pisanie kodu

Otwórz *ClassLibraryDemo* folderu.  Powinny zostać wyświetlone następujące pliki:

1. `ClassLibraryDemo.fs`, F# pliku implementacji przy użyciu klasy zdefiniowane.
2. `ClassLibraryDemo.fsproj`, F# pliku projektu, używany do tworzenia tego projektu.
3. `Script.fsx`, F# pliku skryptu, który ładuje plik źródłowy.
4. `paket.references`, plik Paket, który określa zależności projektu.

Otwórz `Script.fsx`i Dodaj następujący kod na końcu:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

Ta funkcja konwertuje słowo na formę [Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin). Następnym krokiem jest ocena za pomocą F# interakcyjne (FSI).

Zaznacz całą funkcję (powinno wskazywać 11 wierszy). Gdy jest wyróżniona, przytrzymaj **Alt** kluczy i kliknij przycisk **Enter**. Można zauważyć okno wyskakujące okienko poniżej, a powinna ona zostać wyświetlona mniej więcej tak:

![Przykład F# Interactive dane wyjściowe z Ionide](media/getting-started-vscode/vscode-fsi.png)

To wykonanie trzech czynności:

1. Proces FSI jego uruchomienia.
2. Kod, który zostanie wyróżniony go przesyłane za pośrednictwem procesu FSI.
3. Proces FSI oceniane kod, który wysyłane za pośrednictwem.

Ponieważ był wysyłany za pośrednictwem [funkcja](../language-reference/functions/index.md), teraz można wywołać tę funkcję za pomocą FSI! W oknie interaktywnym wpisz następujące polecenie:

```fsharp
toPigLatin "banana";;
```

Powinny zostać wyświetlone następujące wyniki:

```fsharp
val it : string = "ananabay"
```

Teraz Wypróbujmy się od samogłosek jako pierwszą literę. Wprowadź następujące informacje:

```fsharp
toPigLatin "apple";;
```

Powinny zostać wyświetlone następujące wyniki:

```fsharp
val it : string = "appleyay"
```

Funkcja wydaje się działać zgodnie z oczekiwaniami. Gratulacje, napisany właśnie pierwszej F# funkcji w programie Visual Studio Code i oceniać je za pomocą FSI!

> [!NOTE]
> Jak być może zauważono, wiersze FSI kończą się za pomocą `;;`. Jest to spowodowane FSI pozwala wprowadzić wiele wierszy. `;;` Na końcu umożliwia FSI dowiedzieć się, gdy kod jest zostało zakończone.

## <a name="explaining-the-code"></a>Wyjaśniające, kod

Jeśli nie masz pewności, o jakie rzeczywiście jest zastosowanie danego kodu, poniżej przedstawiono instrukcje krok po kroku.

Jak widać, `toPigLatin` jest funkcją, która przyjmuje word jako dane wejściowe i konwertuje ją na reprezentację w postaci Pig Latin tego wyrazu. Dostępne są następujące reguły, w tym:

Jeśli pierwszy znak w wyraz rozpoczyna się od samogłosek, należy dodać "yay" do końca słowa. Jeśli go nie zaczyna się od samogłosek, Przenieś pierwszym znaku do końca słowa i "ay" Dodaj do niej.

Być może zauważono FSI następujące czynności:

```fsharp
val toPigLatin : word:string -> string
```

Stanowi to, że `toPigLatin` jest funkcją, która przyjmuje `string` jako dane wejściowe (o nazwie `word`) i zwraca innego `string`. Jest to nazywane [sygnatura typu funkcji](https://fsharpforfunandprofit.com/posts/function-signatures/), podstawowe fragment F# jest kluczem do zrozumienia F# kodu. Należy także zauważyć, to po umieszczeniu wskaźnika myszy nad funkcji w programie Visual Studio Code.

W treści funkcji można zauważyć dwa oddzielne części:

1. Wewnętrzna funkcja wywoływana `isVowel`, która określa, czy dany znak (`c`) jest samogłosek, sprawdzając, jeśli jest on zgodny z jednym z wzorców podanych za pośrednictwem [dopasowywania do wzorca](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md) Wyrażenie, które sprawdza, czy pierwszym znakiem jest samogłosek i konstrukcji, wartość zwracana z wprowadzonych znaków na podstawie jeśli pierwszym znakiem jest samogłosek, lub nie:

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

Przepływ `toPigLatin` jest w ten sposób:

Sprawdź, czy pierwszy znak wyrazu danych wejściowych jest samogłosek. Jeśli tak jest, należy dołączyć "yay" do końca słowa. W przeciwnym razie przenieść pierwszym znaku do końca słowa i "ay" Dodaj do niej.

Istnieje jedno końcowe należy zwrócić uwagę na ten temat: jest nie jawnego instrukcji, zostać zwrócony przez funkcję, w przeciwieństwie do wielu innych języków tam. Jest to spowodowane F# jest oparte na wyrażeniach i ostatniego wyrażenia w treści funkcji jest wartością zwracaną. Ponieważ `if..then..else` sama jest wyrażenie treści `then` bloku lub treści `else` blok zostanie zwrócona, w zależności od wartości wejściowej.

## <a name="moving-your-script-code-into-the-implementation-file"></a>Przenoszenie kodu skryptu w pliku implementacji

Poprzednie sekcje w tym artykule przedstawiono typowe, pierwszym krokiem na piśmie F# kodu: pisanie funkcję początkową i wykonywania w interaktywnie przy użyciu FSI. Jest to nazywane projektowania opartego na REPL, gdzie [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) oznacza "Odczytu oceny — Drukuj pętlę". Jest to doskonały sposób na wypróbowanie funkcji, aż do uzyskania elementu pracy.

Następnym krokiem projektowania opartego na REPL jest przeniesienie działającego kodu do F# pliku implementacji. Następnie może być kompilowane przez F# kompilatora do zestawu, który może zostać wykonany.

Aby rozpocząć, otwórz `ClassLibraryDemo.fs`.  Można zauważyć, że jakiś kod jest już istnieje. Przejdź dalej i usuń definicję klasy, ale pamiętaj pozostawić [ `namespace` ](../language-reference/namespaces.md) deklaracji u góry.

Następnie utwórz nową [ `module` ](../language-reference/modules.md) o nazwie `PigLatin` i skopiuj `toPigLatin` funkcji do niego w związku z tym:

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

Następnie otwórz `Script.fsx` ponownie plik, a następnie usuń całą `toPigLatin` działać, ale pamiętaj zapewnić następujące dwa wiersze w pliku:

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

Wybierz obie linie tekstu, a następnie naciśnij klawisze Alt + Enter, aby wykonać te wiersze w FSI. Te załaduje zawartość biblioteki Pig Latin procesem FSI i `open` `ClassLibraryDemo` przestrzeni nazw, aby mieć dostęp do funkcji.

Następnie w oknie FSI Wywołaj funkcję z `PigLatin` moduł, który wcześniej zdefiniowaną:

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

SUKCES! Pobierz te same wyniki jak wcześniej, ale teraz ładowane z F# pliku implementacji. Główną różnicą jest to, że F# pliki źródłowe są kompilowane do zestawów, które mogą być wykonywane w dowolnym miejscu, nie tylko w FSI.

## <a name="summary"></a>Podsumowanie

W tym artykule wyjaśniono:

1. Jak skonfigurować program Visual Studio Code za pomocą Ionide.
2. Tworzenie pierwszej F# projektu za pomocą Ionide.
3. Jak używać F# skryptów do zapisania pierwszej F# działać w Ionide, a następnie uruchomić go w FSI.
4. Jak przeprowadzić migrację kodu skryptu do F# źródła, a następnie wywołać kod z FSI.

Teraz masz umożliwiającymi zapisu m.in F# kodowanie przy użyciu programu Visual Studio Code i Ionide.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Oto kilka sposobów, które można rozwiązać niektóre problemy, które możesz napotkać:

1. Aby uzyskać funkcji Ionide, edycji kodu usługi F# pliki muszą zostać zapisane na dysku i wewnątrz folderu, która jest otwarta w obszarze roboczym programu Visual Studio Code.
2. Jeśli zostały wprowadzone zmiany do systemu lub zainstalować wstępnie wymagane składniki Ionide za pomocą programu Visual Studio Code Otwórz, uruchom ponownie program Visual Studio Code.
3. Upewnij się, że można użyć F# kompilatora i F# interakcyjne z wiersza polecenia bez w pełni kwalifikowaną ścieżkę. Możesz to zrobić, wpisując `fsc` w wierszu polecenia, aby uzyskać F# kompilator i `fsi` lub `fsharpi` wizualizacji F# narzędzi Windows i platformy Mono na Mac/Linux, odpowiednio.
4. Jeśli masz nieprawidłowe znaki w katalogach projektu Ionide mogą nie działać.  Jeśli jest to możliwe, należy zmienić nazwy katalogów projektu.
5. Brak polecenia Ionide pracy, sprawdź swoje [powiązania klawiszy programu Visual Studio Code](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) aby zobaczyć, jeśli masz zastępowania ich przypadkowo.
6. Jeśli Ionide jest dzielony na komputerze, a żadne z powyższych poprawił problemu, spróbuj usunąć `ionide-fsharp` katalogu na komputerze i ponowne zainstalowanie pakietu wtyczki.

Ionide to projekt typu open source utworzone i przechowywane przez członków F# społeczności. Należy zgłaszać problemy i możesz współtworzyć na [Ionide VSCode: Repozytorium FSharp GitHub](https://github.com/ionide/ionide-vscode-fsharp).

Jeśli masz problem do raportu, wykonaj [instrukcje dotyczące pobierania dzienników do użycia podczas zgłoszenia problemu dotyczącego](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting).

Możesz również poprosić, aby uzyskać dalszą pomoc, od deweloperów Ionide i F# społeczności [kanału Ionide dotyczącym oprogramowania Gitter](https://gitter.im/ionide/ionide-project).

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej na temat F# i z funkcji języka, zapoznaj się z [Przewodnik po przykładzie F# ](../tour.md).
