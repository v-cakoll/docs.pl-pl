---
title: Hello world — pierwszy program korzystający z programu Visual Studio w systemie Windows lub C# Mac — Przewodnik programowania
ms.custom: seodec18
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 0807e46d36a4cf031bc44ae0dc4efab79dd51d03
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991339"
---
# <a name="hello-world----your-first-program"></a>Hello world — pierwszy program

W tym artykule opisano tworzenie tradycyjnych "Hello world!" przy użyciu programu Visual Studio program. Program Visual Studio to profesjonalne zintegrowane środowisko programistyczne (IDE) z wieloma funkcjami przeznaczonymi do programowania na platformie .NET. Do utworzenia tego programu będziesz używać tylko kilku funkcji w programie Visual Studio. Aby dowiedzieć się więcej na temat programu Visual Studio, zobacz [wprowadzenie z wizualizacjami C# i Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a>Utwórz nową aplikację

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

Uruchom program Visual Studio. Zobaczysz następujący obraz w systemie Windows:

![Ekran powitalny programu Visual Studio w systemie Windows](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

Wybierz pozycję **Utwórz nowy projekt** w prawym dolnym rogu obrazu. Program Visual Studio Wyświetla okno dialogowe **Nowy projekt** :

![Ekran nowego projektu programu Visual Studio w systemie Windows](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> Jeśli jest to pierwsze uruchomienie programu Visual Studio, lista **ostatnio używanych szablonów projektu** jest pusta.

W oknie dialogowym Nowy projekt wybierz pozycję "Aplikacja konsolowa (.NET Core)", a następnie naciśnij przycisk **dalej**. Nadaj projektowi nazwę, na przykład "HelloWorld", a następnie naciśnij pozycję **Utwórz**.

Program Visual Studio otwiera projekt. To już podstawowy "Hello world!" przyklad. Naciśnij `Ctrl` klawisz  +  ,abyuruchomićprojekt`F5` . Program Visual Studio kompiluje projekt, konwertując kod źródłowy do pliku wykonywalnego. Następnie uruchamia okno poleceń, w którym jest uruchamiana nowa aplikacja. W oknie powinien zostać wyświetlony następujący tekst:

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

Naciśnij dowolny klawisz, aby zamknąć okno.

# <a name="macostabmacos"></a>[macOS](#tab/macos)

Rozpocznij Visual Studio dla komputerów Mac. Na komputerze Mac zobaczysz następujący obraz:

![Ekran powitalny programu Visual Studio na komputerze Mac](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> Jeśli jest to pierwsze uruchomienie Visual Studio dla komputerów Mac, lista **ostatnich projektów** jest pusta.

Wybierz pozycję **Nowy** w prawym górnym rogu obrazu. Visual Studio dla komputerów Mac wyświetla okno dialogowe **Nowy projekt** :

![Ekran nowego projektu programu Visual Studio na komputerze Mac](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

W oknie dialogowym Nowy projekt wybierz pozycję ".NET Core" i "Aplikacja konsolowa", a następnie naciśnij przycisk **dalej**. Musisz wybrać platformę docelową. Wartość domyślna to "prawidłowo", więc naciśnij przycisk Dalej. Nadaj projektowi nazwę, na przykład "HelloWorld", a następnie naciśnij pozycję **Utwórz**. Możesz użyć domyślnej lokalizacji projektu. Nie dodawaj tego projektu do kontroli źródła.

Visual Studio dla komputerów Mac otwiera projekt. To już podstawowy "Hello world!" przyklad. Naciśnij `Ctrl` klawisz  +  ,aby +  uruchomić projekt. `Fn` `F5` Visual Studio dla komputerów Mac kompiluje projekt, konwertując kod źródłowy do pliku wykonywalnego. Następnie uruchamia okno poleceń, w którym jest uruchamiana nowa aplikacja. W oknie powinien zostać wyświetlony następujący tekst:

```console
Hello World!

Press any key to close this window . . .
```

Naciśnij klawisz, aby zakończyć sesję.

---

## <a name="elements-of-a-c-program"></a>Elementy C# programu

Przeanalizujmy ważne części tego programu. Pierwszy wiersz zawiera komentarz. Znaki `//` konwertują resztę wiersza do komentarza.

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

Możesz również dodać komentarz do bloku tekstu, umieszczając go między `/*` znakami i. `*/` Pokazano to w poniższym przykładzie.

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

Aplikacja C# konsolowa musi zawierać `Main` metodę, w której kontrolka zaczyna się i skończy. Metoda `Main` ta umożliwia tworzenie obiektów i wykonywanie innych metod.

Metoda jest metodą statyczną, która znajduje się wewnątrz klasy lub struktury. [](../../language-reference/keywords/static.md) `Main` W poprzednim "Hello world!" przykład znajduje się w klasie o nazwie `Hello`. `Main` Metodę można zadeklarować w jeden z następujących sposobów:

- Może zwrócić `void`. Oznacza to, że program nie zwraca wartości.

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- Może również zwracać liczbę całkowitą. Liczba całkowita jest **kodem zakończenia** dla aplikacji.

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- Za pomocą jednego z typów zwracanych można przyjmować argumenty.

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

—lub—

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

Parametr `Main` `string` metody,, jest tablicą zawierającą argumenty wiersza polecenia używane do wywołania programu. `args`

Aby uzyskać więcej informacji o używaniu argumentów wiersza polecenia, zobacz przykłady w [Main () i argumenty wiersza polecenia](../main-and-command-args/index.md).

## <a name="input-and-output"></a>Dane wejściowe i wyjściowe

C#programy zwykle korzystają z usług wejścia/wyjścia dostarczonych przez bibliotekę wykonawczą .NET Framework. `System.Console.WriteLine("Hello World!");` Instrukcja<xref:System.Console.WriteLine%2A> używa metody. Jest to jedna z metod <xref:System.Console> wyjściowych klasy w bibliotece wykonawczej. Wyświetla jego parametr String w standardowym strumieniu wyjściowym, po którym następuje nowy wiersz. Inne <xref:System.Console> metody są dostępne dla różnych operacji wejścia i wyjścia. Jeśli dołączysz `using System;` dyrektywę na początku programu, możesz bezpośrednio <xref:System> użyć klas i metod bez ich w pełni kwalifikujących się. Na przykład można wywołać `Console.WriteLine` `System.Console.WriteLine`zamiast:

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

Aby uzyskać więcej informacji na temat metod wejścia/wyjścia <xref:System.IO>, zobacz.

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Przykłady i samouczki](../../../samples-and-tutorials/index.md)
- [Main() i argumenty wiersza polecenia](../main-and-command-args/index.md)
- [Wprowadzenie do języków Visual C# i Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
