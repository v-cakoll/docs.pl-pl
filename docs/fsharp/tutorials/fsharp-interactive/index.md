---
title: Odwołanie interakcyjne F# (fsi.exe)
description: Dowiedz F# się, w jaki sposób interaktywny (fsi. F# exe) jest używany do interaktywnego uruchamiania kodu przy F# użyciu konsoli programu lub wykonywania skryptów.
ms.date: 05/16/2016
ms.openlocfilehash: 9f4b5c0e7527d29e375265bb31a5de2df098f8e1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419910"
---
# <a name="interactive-programming-with-f"></a>Interaktywne Programowanie przy użyciu języka F\#

> [!NOTE]
> W tym artykule opisano obecnie tylko środowisko dla systemu Windows.  Zostanie on ponownie zapisany.

> [!NOTE]
> Link odwołania do interfejsu API spowoduje przejście do witryny MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

F#Interaktywny (fsi. exe) jest używany do F# interaktywnego uruchamiania kodu przy użyciu konsoli programu lub do wykonywania F# skryptów. Inaczej mówiąc, F# interaktywnie wykonuje REPL (odczyt, oszacowanie, pętla Print) dla F# języka.

Aby uruchomić F# interaktywny z konsoli programu, uruchom program FSI. exe.  FSI. exe znajduje się w:

```console
C:\Program Files (x86)\Microsoft Visual Studio\2019\<sku>\Common7\IDE\CommonExtensions\Microsoft\FSharp
```

gdzie `sku` to `Community`, `Professional` lub `Enterprise`.

Aby uzyskać informacje o dostępnych opcjach wiersza polecenia, zobacz [ F# opcje interaktywne](../../language-reference/fsharp-interactive-options.md).

Aby uruchomić F# interaktywnie za pomocą programu Visual Studio, można kliknąć odpowiedni przycisk paska narzędzi z etykietą  **F# Interactive**lub użyć klawiszy **Ctrl + Alt + F**. Spowoduje to otwarcie okna interaktywnego, okna narzędzia z uruchomioną sesją F# interaktywną. Możesz również wybrać kod, który ma być uruchamiany w oknie interaktywnym i nacisnąć kombinację klawiszy **ALT + ENTER**. F#Interaktywny Start jest uruchamiany w oknie narzędzi z etykietą  **F# Interactive**. W przypadku korzystania z tej kombinacji klawiszy upewnij się, że okno edytora ma fokus.

Niezależnie od tego, czy używasz konsoli programu, czy programu Visual Studio, zostanie wyświetlony wiersz polecenia, a interpreter czeka na dane wejściowe. Możesz wprowadzić kod tak samo jak w pliku kodu. Aby skompilować i wykonać kod, wprowadź dwa średnika ( **;;** ), aby zakończyć wiersz lub kilka wierszy danych wejściowych.

F#Interaktywna Próba skompilowania kodu i, jeśli to się powiedzie, wykonuje kod i drukuje sygnaturę typów i wartości, które zostały skompilowane. Jeśli wystąpią błędy, interpreter wyświetla komunikaty o błędach.

Kod wprowadzony w tej samej sesji ma dostęp do dowolnych wcześniej wprowadzonych konstrukcji, dzięki czemu można kompilować programy. Obszerny bufor w oknie narzędzi umożliwia skopiowanie kodu do pliku w razie potrzeby.

W przypadku uruchamiania w programie Visual F# Studio interaktywne uruchomienia niezależnie od projektu, więc na przykład nie można używać konstrukcji zdefiniowanych w projekcie w F# trybie interaktywnym, chyba że skopiujesz kod funkcji do okna interaktywnego.

Jeśli masz otwarty projekt, który odwołuje się do niektórych bibliotek, możesz odwoływać F# się do nich w trybie interaktywnym przez **Eksplorator rozwiązań**. Aby odwołać się do F# biblioteki w programie Interactive, rozwiń węzeł **odwołania** , otwórz menu skrótów dla biblioteki i wybierz polecenie **Wyślij do F# interaktywne**.

Można kontrolować F# interaktywne argumenty wiersza polecenia (Opcje) przez dostosowanie ustawień. W menu **Narzędzia** wybierz pozycję **Opcje...** , a następnie rozwiń węzeł  **F# narzędzia**. Dwa ustawienia, które można zmienić, to opcje F# interaktywne i **64-bitowe F# ustawienia interaktywne** , które są istotne tylko wtedy, gdy uruchamiasz F# interaktywnie na komputerze 64-bitowym. To ustawienie określa, czy chcesz uruchomić dedykowaną 64-bitową wersję programu FSI. exe lub fsianycpu. exe, która korzysta z architektury komputera, aby określić, czy uruchomić program jako proces 32-bitowy czy 64-bitowy.

## <a name="scripting-with-f"></a>Wykonywanie skryptów przy użyciu języka F\#

Skrypty używają rozszerzenia pliku **. FSX** lub **. FSSCRIPT**. Zamiast kompilowania kodu źródłowego, a następnie uruchamiania skompilowanego zestawu, można po prostu uruchomić **FSI. exe** i określić nazwę pliku skryptu kodu F# źródłowego, a F# interaktywnie odczytuje kod i wykonuje go w czasie rzeczywistym.

## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a>Różnice między interaktywnym, skryptowym i skompilowanym środowiskiem

W przypadku kompilowania kodu w F# trybie interaktywnym, niezależnie od tego, czy uruchamiasz interaktywnie, czy uruchamiasz skrypt, jest definiowany symbol **interaktywny** . Podczas kompilowania kodu w kompilatorze jest zdefiniowany symbol **skompilowany** . W tym przypadku, jeśli kod musi być inny w skompilowanych i interaktywnych trybach, można użyć dyrektyw preprocesora dla kompilacji warunkowej, aby określić, która z nich ma być używana.

Niektóre dyrektywy są dostępne w przypadku wykonywania skryptów w F# trybie interaktywnym, które nie są dostępne podczas wykonywania kompilatora. Poniższa tabela zawiera podsumowanie dyrektyw, które są dostępne w przypadku korzystania F# z programu Interactive.

|Dyrektywę|Opis|
|---------|-----------|
|**#help**|Wyświetla informacje dotyczące dostępnych dyrektyw.|
|**#I**|Określa ścieżkę wyszukiwania zestawu w cudzysłowie.|
|**#load**|Odczytuje plik źródłowy, kompiluje go i uruchamia.|
|**#quit**|Kończy sesję F# interaktywną.|
|**#r**|Odwołuje się do zestawu.|
|**#time ["on"&#124;"off"]**|Niezależnie od tego **#time** włącza, czy mają być wyświetlane informacje o wydajności. Gdy jest włączona, F# interaktywne miary czasu rzeczywistego, czasu procesora oraz informacje o wyrzucaniu elementów bezużytecznych dla każdej sekcji kodu, który jest interpretowany i wykonywany.|

Po określeniu plików lub ścieżek w F# interaktywnym, oczekiwany jest literał ciągu. W związku z tym pliki i ścieżki muszą być ujęte w znaki cudzysłowu, a normalne znaki ucieczki mają zastosowanie. Ponadto można użyć @ znaku, aby spowodować F# , że interaktywny interpretuje ciąg, który zawiera ścieżkę jako ciąg Verbatim. Powoduje F# to, że interaktywny ignoruje wszystkie znaki ucieczki.

Jedną z różnic między skompilowanym i interaktywnym trybem jest sposób dostępu do argumentów wiersza polecenia. W trybie skompilowanym Użyj **System. Environment. GetCommandLineArgs**. W skryptach Użyj **FSI. CommandLineArgs —** .

Poniższy kod ilustruje sposób tworzenia funkcji, która odczytuje argumenty wiersza polecenia w skrypcie, a także pokazuje, jak odwoływać się do innego zestawu ze skryptu. Pierwszy plik kodu, **. FS**, jest kodem, do którego odwołuje się zestaw. Skompiluj ten plik przy użyciu wiersza polecenia: **Urząd nadzoru systemu.** , a następnie wykonaj drugi plik jako skrypt z wierszem polecenia: **FSI--exec plik1. FSX** test

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

Dane wyjściowe są następujące:

```console
Command line arguments:
file1.fsx
test
90
```

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----|-----------|
|[Opcje F# Interactive](../../language-reference/fsharp-interactive-options.md)|Opisuje składnię wiersza polecenia i opcje dla F# Interactive, FSI. exe.|
|[F#Dokumentacja biblioteki interaktywnej](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-interactive-library-reference)|Opisuje funkcje biblioteki dostępne podczas wykonywania kodu w F# trybie interaktywnym.|
