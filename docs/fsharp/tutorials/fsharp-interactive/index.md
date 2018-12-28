---
title: Odwołanie interakcyjne F# (fsi.exe)
description: Dowiedz się, jak F# Interactive (fsi.exe) jest używany do uruchamiania F# kodu interaktywnego w konsoli lub wykonać F# skryptów.
ms.date: 05/16/2016
ms.openlocfilehash: 0fccc818f0a4b3d6d09a69e91da1f5c337c53a44
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611064"
---
# <a name="interactive-programming-with-f"></a>Interaktywny, programowanie za pomocąF# #

> [!NOTE]
> W tym artykule opisano aktualnie środowisko Windows tylko.  Będzie inaczej.

> [!NOTE]
> Łącze odwołania API spowoduje przejście do MSDN.  Dokumentacja interfejsu API w witrynie docs.microsoft.com nie została ukończona.

F#Interactive (fsi.exe) jest używany do uruchamiania F# kodu interaktywnego w konsoli, lub wykonać F# skryptów. Innymi słowy F# interaktywne wykonuje REPL (Odczyt, oszacowanie, drukowania Loop) dla F# języka.

Aby uruchomić F# interakcyjne z poziomu konsoli, uruchom fsi.exe.  Znajdziesz fsi.exe w:

```console
C:\Program Files (x86)\Microsoft Visual Studio\2017\<sku>\Common7\IDE\CommonExtensions\Microsoft\FSharp
```

gdzie `sku` jest `Community`, `Professional`, lub `Enterprise`.

Aby uzyskać informacje o dostępnych opcjach wiersza polecenia, zobacz [ F# interaktywnych opcji](../../language-reference/fsharp-interactive-options.md).

Aby uruchomić F# Interactive za pomocą programu Visual Studio, możesz kliknąć przycisk odpowiednich narzędzi, oznaczone  **F# Interactive**, lub użyj klawiszy **Ctrl + Alt + F**. W ten sposób spowoduje otwarcie okna interaktywnego okna narzędzi, uruchamianie F# interaktywnej sesji. Możesz również wybrać kodu, który chcesz uruchomić w oknie interaktywnym i naciśnij kombinację klawiszy **klawisze ALT + ENTER**. F#Interaktywne rozpoczyna się w oknie narzędzi etykietą  **F# interaktywne**. Gdy używasz tej kombinacji klawiszy, upewnij się, że okno edytora ma fokus.

Czy używasz konsoli lub Visual Studio, zostanie wyświetlony wiersz polecenia, a następnie interpreter czeka na dane wejściowe. Można wprowadzić kod, tak samo jak w pliku kodu. Aby skompilować i wykonywania kodu, wprowadź dwie średnikami (**;** ) do zakończenia wiersza lub kilka wierszy danych wejściowych.

F#Interakcyjne próbuje skompilować kod i, jeśli to się powiedzie, wykonuje kod i drukuje podpis typy i wartości jego skompilowany. Jeśli wystąpią błędy, interpreter wypisuje komunikaty o błędach.

Wprowadzono w tej samej sesji kod ma dostęp do konstrukcji, wszystkie wprowadzone wcześniej, można je tworzyć programy grupy. Rozbudowane buforu, w oknie narzędzia pozwala skopiować kod do pliku, jeśli to konieczne.

Podczas uruchamiania w programie Visual Studio, F# interaktywne działa niezależnie od projektu, dlatego na przykład nie można użyć konstrukcji zdefiniowana w projekcie w F# interaktywne, chyba że skopiuj kod funkcji w oknie interaktywnym.

W przypadku otwarciu projektu, który odwołuje się do niektórych bibliotek możesz odwoływać się do tych F# Interactive za pośrednictwem **Eksploratora rozwiązań**. Aby odwoływać się do biblioteki w F# Interactive, rozwiń węzeł **odwołania** węzła, otwórz menu skrótów dla biblioteki, a następnie wybierz **wysyłać F# Interactive**.

Możesz kontrolować F# argumenty interaktywne wiersza polecenia (Opcje), dostosowując ustawienia. Na **narzędzia** menu, wybierz opcję **opcje...** , a następnie rozwiń węzeł  **F# narzędzia**. Są dwa ustawienia, które mogą być zmieniane F# Opcje interakcyjne i **64-bitowych F# Interactive** ustawienie, które ma zastosowanie tylko wtedy, gdy są uruchomione F# Interactive na komputerze 64-bitowym. To ustawienie określa, czy chcesz uruchomić dedykowanych 64-bitowej wersji fsi.exe lub fsianycpu.exe, która korzysta z architektury maszyny w celu ustalenia, czy można uruchomić jako proces 32-bitową lub 64-bitowych.


## <a name="scripting-with-f"></a>Obsługa skryptów w programieF# #
Skrypty za pomocą rozszerzenia pliku **.fsx** lub **.fsscript**. Zamiast kompilowanie kodu źródłowego, a następnie uruchamiając skompilowanego zestawu, można po prostu uruchomisz **fsi.exe** i określ nazwę pliku skryptu na F# kod źródłowy, a F# interaktywne odczytuje kod i wykonuje rzeczywistą czas.


## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a>Różnice między środowiskami interaktywne, skryptów i skompilowany
Gdy kompilujesz kod w F# Interactive, czy są interakcyjnego lub uruchamiając skrypt, symbol **INTERACTIVE** jest zdefiniowana. Gdy kompilujesz kod w kompilatorze symbol **COMPILED** jest zdefiniowana. W związku z tym kod musi różnić się w trybie skompilowane i interaktywnych, można użyć dyrektywy preprocesora dla kompilacji warunkowej do określenia, które do użycia.

Niektóre dyrektywy są dostępne w przypadku, gdy są wykonywanie skryptów w F# Interactive, które nie są dostępne, gdy są wykonywane kompilator. Poniższa tabela zawiera podsumowanie dyrektyw, które są dostępne podczas korzystania z F# interakcyjne.

|— Dyrektywa|Opis|
|---------|-----------|
|**#help**|Wyświetla informacje o dostępnych dyrektywy.|
|**#I**|Określa ścieżkę wyszukiwania zestawu w znaki cudzysłowu.|
|**#load**|Odczytuje plik źródłowy, kompiluje go i uruchamia go.|
|**#quit**|Kończy F# interaktywnej sesji.|
|**#r**|Odwołuje się do zestawu.|
|**#time ["włączone"&#124;"wyłączone"]**|Przez siebie **#time** przełącza, czy mają być wyświetlane informacje o wydajności. Po jej włączeniu F# Interactive mierzy czasu rzeczywistego, czas procesora CPU i informacje o kolekcji wyrzucania elementów dla każdej sekcji kodu, który jest interpretowany i wykonywane.|

Po określeniu pliki lub ścieżki w F# Interactive, oczekiwano literału ciągu. W związku z tym pliki i ścieżki muszą być ujęte w znaki cudzysłowu i znaków ucieczki zwykle zastosowania. Ponadto, możesz użyć znaku, aby spowodować @ F# Interactive zinterpretować ciąg, który zawiera ścieżkę jako ciąg verbatim. Powoduje to, że F# Interactive, aby ignorować wszystkie znaki ucieczki.

Jedną z różnic między trybem skompilowane i interaktywne to sposób, możesz uzyskać dostęp do argumentów wiersza polecenia. W trybie skompilowanych za pomocą **System.Environment.GetCommandLineArgs**. W skryptach, należy użyć **fsi.CommandLineArgs**.

Poniższy kod ilustruje sposób tworzenia funkcji, która odczytuje argumenty wiersza polecenia w skrypcie, a także pokazuje, jak odwołać się do innego zestawu pochodzące ze skryptu. Pierwszy plik kodu **MyAssembly.fs**, to kod dla zestawu, do którego nastąpiło odwołanie. Skompiluj ten plik przy użyciu wiersza polecenia: **nadzoru — MyAssembly.fs** , a następnie wykonaj drugiego pliku jako skrypt przy użyciu wiersza polecenia: **fsi — exec file1.fsx** testu

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

```fsharp
// file1.fsx
#r "MyAssembly.dll"

printfn "Command line arguments: "

for arg in fsi.CommandLineArgs do
    printfn "%s" arg

printfn "%A" (MyAssembly.myFunction 10 40)
```

Wynik jest następujący:

```
Command line arguments: 
file1.fsx
test
90
```

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----|-----------|
|[Opcje F# Interactive](../../language-reference/fsharp-interactive-options.md)|W tym artykule opisano składnia wiersza polecenia i opcje dla F# Interactive, fsi.exe.|
|[F#Odwołanie do biblioteki interakcyjnej](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-interactive-library-reference)|Zawiera opis funkcji biblioteki, które są dostępne podczas wykonywania kodu w F# interaktywne.|