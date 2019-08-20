---
title: Hello world — pierwszy Przewodnik C# programowania programu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 9a50de0bb583a1dfccfa609be1cca732868505ba
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589376"
---
# <a name="hello-world----your-first-program-c-programming-guide"></a>Hello world — pierwszy program (C# Przewodnik programowania)

Poniższa procedura tworzy C# wersję tradycyjnego "Hello World!" program. Program wyświetla ciąg`Hello World!`

Aby uzyskać więcej przykładów dotyczących wprowadzenia, zobacz [wprowadzenie z wizualizacjami C# i Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-and-run-a-console-application"></a>Aby utworzyć i uruchomić aplikację konsoli

1. Uruchom program Visual Studio.

2. Na pasku menu wybierz **pliku**, **New**, **projektu**.

     **Nowy projekt** zostanie otwarte okno dialogowe.

3. Rozwiń węzeł **zainstalowane**, rozwiń węzeł **Szablony**, rozwiń węzeł **wizualizacji C#** , a następnie wybierz pozycję **Aplikacja konsolowa**.

4. W polu **Nazwa** Określ nazwę projektu, a następnie wybierz przycisk **OK** .

     Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.

5. Jeśli Program.cs nie jest otwarty w **edytorze kodu**, otwórz menu skrótów dla **program.cs** w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Wyświetl kod**.

6. Zastąp zawartość Program.cs następującym kodem.

     [!code-csharp[csProgGuide#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#21)]

7. Wybierz klawisz F5, aby uruchomić projekt. Zostanie wyświetlone okno wiersza polecenia zawierające wiersz`Hello World!`

Następnie należy sprawdzić ważne części tego programu.

## <a name="comments"></a>Komentarze

Pierwszy wiersz zawiera komentarz. Znaki `//` konwertują resztę wiersza do komentarza.

 [!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

Możesz również dodać komentarz do bloku tekstu, umieszczając go między `/*` znakami i. `*/` Pokazano to w poniższym przykładzie.

 [!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

## <a name="main-method"></a>Metoda główna

Aplikacja C# konsolowa musi zawierać `Main` metodę, w której kontrolka zaczyna się i skończy. Metoda `Main` ta umożliwia tworzenie obiektów i wykonywanie innych metod.

Metoda jest metodą statyczną, która znajduje się wewnątrz klasy lub struktury. [](../../language-reference/keywords/static.md) `Main` W poprzednim "Hello world!" przykład znajduje się w klasie o nazwie `Hello`. `Main` Metodę można zadeklarować w jeden z następujących sposobów:

- Może zwrócić `void`.

     [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- Może również zwracać liczbę całkowitą.

     [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- Za pomocą jednego z typów zwracanych można przyjmować argumenty.

     [!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

     —lub—

     [!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

Parametr `Main` `string` metody,, jest tablicą zawierającą argumenty wiersza polecenia używane do wywołania programu. `args` W przeciwieństwie C++do programu w programie tablica nie zawiera nazwy pliku wykonywalnego (exe).

Aby uzyskać więcej informacji o sposobach używania argumentów wiersza polecenia, zobacz przykłady w [Main () i argumenty wiersza polecenia](../main-and-command-args/index.md) i [instrukcje: Tworzenie i używanie zestawów przy użyciu wiersza](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)polecenia.

Wywołanie <xref:System.Console.ReadKey%2A> na końcu `Main` metody uniemożliwia zamknięcie okna konsoli przed rozpoczęciem odczytywania danych wyjściowych podczas uruchamiania programu w trybie debugowania, naciskając klawisz F5.

## <a name="input-and-output"></a>Dane wejściowe i wyjściowe

C#programy zwykle korzystają z usług wejścia/wyjścia dostarczonych przez bibliotekę wykonawczą .NET Framework. `System.Console.WriteLine("Hello World!");` Instrukcja<xref:System.Console.WriteLine%2A> używa metody. Jest to jedna z metod <xref:System.Console> wyjściowych klasy w bibliotece wykonawczej. Wyświetla jego parametr String w standardowym strumieniu wyjściowym, po którym następuje nowy wiersz. Inne <xref:System.Console> metody są dostępne dla różnych operacji wejścia i wyjścia. Jeśli dołączysz `using System;` dyrektywę na początku programu, możesz bezpośrednio <xref:System> użyć klas i metod bez ich w pełni kwalifikujących się. Na przykład można wywołać `Console.WriteLine` `System.Console.WriteLine`zamiast:

 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

 [!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

Aby uzyskać więcej informacji na temat metod wejścia/wyjścia <xref:System.IO>, zobacz.

## <a name="command-line-compilation-and-execution"></a>Kompilacja i wykonywanie w wierszu polecenia

Można skompilować "Hello world!" program przy użyciu wiersza polecenia zamiast zintegrowanego środowiska programistycznego (IDE) programu Visual Studio.

### <a name="to-compile-and-run-from-a-command-prompt"></a>Aby skompilować i uruchomić z wiersza polecenia

1. Wklej kod z poprzedniej procedury do dowolnego edytora tekstów, a następnie Zapisz plik jako plik tekstowy. Nazwij plik `Hello.cs`. C#pliki kodu źródłowego używają rozszerzenia `.cs`.

2. Wykonaj jedną z następujących czynności, aby otworzyć okno wiersza polecenia:

    - W systemie Windows 10, w menu **Start** , Wyszukaj `Developer Command Prompt`, a następnie naciśnij lub wybierz **wiersz polecenia dla deweloperów dla programu vs 2017**.

         Zostanie wyświetlone okno wiersz polecenia dla deweloperów.

    - W systemie Windows 7 Otwórz menu **Start** , rozwiń folder dla bieżącej wersji programu Visual Studio, otwórz menu skrótów dla **Visual Studio Tools**, a następnie wybierz **wiersz polecenia dla deweloperów dla programu vs 2017**.

         Zostanie wyświetlone okno wiersz polecenia dla deweloperów.

    - Włącz kompilacje wiersza polecenia z poziomu standardowego okna wiersza polecenia.

         Zobacz [How to: Ustawianie zmiennych środowiskowych dla wiersza](../../language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)polecenia programu Visual Studio.

3. W oknie wiersza polecenia przejdź do folderu, który zawiera `Hello.cs` plik.

4. Wprowadź następujące polecenie, aby skompilować `Hello.cs`.

     `csc Hello.cs`

     Jeśli program nie ma błędów kompilacji, tworzony jest plik wykonywalny o nazwie `Hello.exe` .

5. W oknie wiersza polecenia wprowadź następujące polecenie, aby uruchomić program:

     `Hello`

 Aby uzyskać więcej informacji o C# kompilatorze i jego opcjach, zobacz [ C# opcje kompilatora](../../language-reference/compiler-options/index.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Konstrukcja programu C#](./index.md)
- [Ciągi](../strings/index.md)
- [Przykłady i samouczki](../../../samples-and-tutorials/index.md)
- [Dokumentacja języka C#](../../language-reference/index.md)
- [Main() i argumenty wiersza polecenia](../main-and-command-args/index.md)
- [Wprowadzenie do języków Visual C# i Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
