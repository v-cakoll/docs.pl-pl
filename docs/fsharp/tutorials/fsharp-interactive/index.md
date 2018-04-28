---
title: Odwołanie interakcyjne F# (fsi.exe)
description: 'Dowiedz się, jak F # Interactive (fsi.exe) jest używany do interakcyjnego uruchamiania kodzie języka F # za pomocą konsoli lub wykonywanie skryptów F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: e745562e4165ce6744fcb6d07268b1a5761194aa
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="interactive-programming-with-f"></a>Programowanie w języku F # Interactive #

> [!NOTE]
W tym artykule opisano obecnie środowisko dla systemu Windows tylko.  Będzie ona ulegną.

> [!NOTE]
Łącze odwołania API spowoduje przejście do MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

F # Interactive (fsi.exe) jest używany interakcyjne uruchomianie kodzie języka F # za pomocą konsoli lub wykonywanie skryptów F #. Innymi słowy F # interactive wykonuje REPL (Odczyt, Evaluate pętli drukowania) dla języka F #.

Aby uruchomić narzędzia F # Interactive z konsoli, uruchom fsi.exe.  Dostępne są fsi.exe w "c:\Program pliki (x86) \Microsoft SDKs\F#\<wersji > \Framework\<wersji >\". Aby uzyskać informacje o dostępnych opcjach wiersza polecenia, zobacz [Opcje interakcyjne F #](../../language-reference/fsharp-interactive-options.md).

Aby uruchomić narzędzia F # Interactive za pomocą programu Visual Studio, kliknięcie przycisku odpowiednich narzędzi etykietą **F # Interactive**, lub użyj klawiszy **Ctrl + Alt + F**. W ten sposób otworzy okno interaktywne okna narzędzia, w którym działa sesja F # Interactive. Możesz też wybrać niektórych kod, który chcesz uruchomić w oknie interaktywnym i naciśnij kombinację klawiszy **ALT + ENTER**. F # Interactive rozpoczyna się w oknie narzędzia etykietą **F # Interactive**. Użycie tej kombinacji klawiszy, upewnij się, że okno edytora ma fokus.

Zarówno w przypadku korzystania z konsoli lub Visual Studio pojawi się wiersz polecenia i interpretera oczekujące na dane wejściowe. Można wprowadzić kod, tak samo jak w pliku kodu. Aby skompilować i uruchomić kod, wprowadź dwie średnikami (**;** ) zakończenie wiersza lub kilka wierszy danych wejściowych.

F # Interactive prób skompilować kod i, jeśli to się powiedzie, wykonuje kod i wyświetla podpisu typów i wartości, które go skompilować. Jeśli wystąpią błędy, interpretera wyświetla komunikaty o błędach.

Wprowadzony w tej samej sesji ma dostęp do konstrukcji, wszelkie wprowadzone uprzednio,, można je tworzyć działanie programów. Rozbudowana buforu w oknie narzędzia umożliwia skopiuj kod do pliku, jeśli to konieczne.

Po uruchomieniu programu Visual Studio, F # Interactive działa niezależnie od projektu, tak, na przykład, nie możesz użyć konstrukcji zdefiniowane w projekcie w F # Interactive, chyba że skopiuj kod dla tej funkcji do okna interaktywnego.

Jeśli masz otwarte projektu, który odwołuje się do niektórych bibliotek mogą odwoływać je w F # Interactive przez **Eksploratora rozwiązań**. Aby odwołać biblioteki w F # Interactive, rozwiń węzeł **odwołania** węzła, otwórz menu skrótów biblioteki, a następnie wybierz pozycję **wysyłać do narzędzia F # Interactive**.

Argumenty wiersza polecenia F # Interactive (Opcje) można kontrolować, dostosowując ustawienia. Na **narzędzia** menu, wybierz opcję **opcje...** , a następnie rozwiń węzeł **narzędzia F #**. Opcje narzędzia F # Interactive są dwa ustawienia, które można zmienić i **64-bitowych F # Interactive** ustawienie, które ma zastosowanie tylko wtedy, gdy używasz narzędzia F # Interactive na komputerze 64-bitowych. To ustawienie określa, czy chcesz uruchomić dedykowanych 64-bitowej wersji fsi.exe lub fsianycpu.exe, używający architektura komputera do ustalenia, czy można uruchomić jako proces 32-bitowy lub 64-bitowej.


## <a name="scripting-with-f"></a>Obsługa skryptów w języku F # #
Skrypty używane rozszerzenie pliku **fsx** lub **fsscript**. Zamiast kompilowanie kodu źródłowego i ponownie uruchomić w skompilowanym zestawie, możesz po prostu uruchomić **fsi.exe** i określ nazwę pliku skryptu języka F # kodu źródłowego i interakcyjne F # odczytuje kod i wykonuje go w czasie rzeczywistym.


## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a>Różnice między środowiskami interaktywne, skryptów i skompilowanych
Podczas kompilowania kodu w języku F # Interactive, czy są interakcyjnego lub uruchamianie skryptu, symbol **INTERACTIVE** jest zdefiniowany. Gdy kompilacja kodu w kompilatorze, symbol **COMPILED** jest zdefiniowany. W związku z tym kod musi być różna w trybach skompilowany i interaktywne, można użyć dyrektywy preprocesora dla kompilacji warunkowej ustalenie, który ma zostać użyty.

Niektóre dyrektywy są dostępne, gdy są wykonywanie skryptów w F # Interactive nie są dostępne, gdy są wykonywane przez kompilator. Poniższa tabela zawiera podsumowanie dyrektywy, które są dostępne w przypadku korzystania z narzędzia F # Interactive.

|Dyrektywy|Opis|
|---------|-----------|
|**#help**|Wyświetla informacje o dostępnych dyrektywy.|
|**#I**|Określa ścieżkę wyszukiwania zestawu w znaki cudzysłowu.|
|**#load**|Odczytuje plik źródłowy, kompiluje go i uruchamia go.|
|**#quit**|Kończy sesję F # Interactive.|
|**#r**|Odwołuje się do zestawu.|
|**#time ["na"&#124;"off"]**|Samodzielnie **#time** przełącza, czy mają być wyświetlane informacje o wydajności. Gdy jest włączone, F # Interactive mierzy czasu rzeczywistego, czas procesora CPU i pamięci zbierają informacje dla każdej sekcji kodu, który jest interpretowany i wykonywane.|

Po określeniu pliki lub ścieżki w F # Interactive, oczekiwano literału ciągu. W związku z tym pliki i ścieżki musi być w cudzysłowie, a następnie zastosować znaki specjalne zwykle. Ponadto można użyć znaku spowodować F # Interactive zinterpretować ciąg, który zawiera ścieżkę jako ciągu dosłownego wyrażenia @. Powoduje to F # Interactive zignorować wszelkie znaki specjalne.

Jednym z różnic między trybem skompilowany i interaktywne jest sposób uzyskać dostępu do argumentów wiersza polecenia. W trybie skompilowanych za pomocą **System.Environment.GetCommandLineArgs**. W skryptach, użyj **elementu fsi.CommandLineArgs**.

Poniższy kod ilustruje sposób tworzenia funkcję, która odczytuje argumenty wiersza polecenia skryptu i również pokazano, jak odwołać się do innego zestawu ze skryptu. Pierwszy plik kodu **MyAssembly.fs**, to kod dla zestawu, do którego nastąpiło odwołanie. Kompiluj tego pliku w wierszu polecenia: **nadzoru - MyAssembly.fs** , a następnie wykonaj drugi plik jako skrypt przy użyciu wiersza polecenia: **fsi - exec file1.fsx** testu

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
60
```

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----|-----------|
|[Opcje F# Interactive](../../language-reference/fsharp-interactive-options.md)|Zawiera opis składni wiersza polecenia i opcje dotyczące programu F # Interactive, fsi.exe.|
|[Odwołanie do biblioteki interakcyjnej F #](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-interactive-library-reference)|Opisuje funkcje biblioteki są dostępne podczas wykonywania kodu w języku F # interactive.|
