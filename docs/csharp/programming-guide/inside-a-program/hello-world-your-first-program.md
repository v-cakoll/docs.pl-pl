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
ms.openlocfilehash: edab64bf02a2b60cce21af536d2da98193dea9a1
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73196216"
---
# <a name="hello-world----your-first-program"></a>Hello world — pierwszy program

W tym artykule opisano tworzenie tradycyjnych "Hello world!" przy użyciu programu Visual Studio Program. Program Visual Studio to profesjonalne zintegrowane środowisko programistyczne (IDE) z wieloma funkcjami przeznaczonymi do programowania na platformie .NET. Do utworzenia tego programu będziesz używać tylko kilku funkcji w programie Visual Studio. Aby dowiedzieć się więcej na temat programu Visual Studio, zobacz [wprowadzenie with Visual C# ](/visualstudio/ide/quickstart-csharp-console).

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

Program Visual Studio otwiera projekt. To już podstawowy "Hello world!" przyklad. Naciśnij `Ctrl` + `F5`, aby uruchomić projekt. Program Visual Studio kompiluje projekt, konwertując kod źródłowy do pliku wykonywalnego. Następnie uruchamia okno poleceń, w którym jest uruchamiana nowa aplikacja. W oknie powinien zostać wyświetlony następujący tekst:

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

Naciśnij klawisz, aby zamknąć okno.

# <a name="macostabmacos"></a>[macOS](#tab/macos)

Rozpocznij Visual Studio dla komputerów Mac. Na komputerze Mac zobaczysz następujący obraz:

![Ekran powitalny programu Visual Studio na komputerze Mac](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> Jeśli jest to pierwsze uruchomienie Visual Studio dla komputerów Mac, lista **ostatnich projektów** jest pusta.

Wybierz pozycję **Nowy** w prawym górnym rogu obrazu. Visual Studio dla komputerów Mac wyświetla okno dialogowe **Nowy projekt** :

![Ekran nowego projektu programu Visual Studio na komputerze Mac](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

W oknie dialogowym Nowy projekt wybierz pozycję ".NET Core" i "Aplikacja konsolowa", a następnie naciśnij przycisk **dalej**. Musisz wybrać platformę docelową. Wartość domyślna to "prawidłowo", więc naciśnij przycisk Dalej. Nadaj projektowi nazwę, na przykład "HelloWorld", a następnie naciśnij pozycję **Utwórz**. Możesz użyć domyślnej lokalizacji projektu. Nie dodawaj tego projektu do kontroli źródła.

Visual Studio dla komputerów Mac otwiera projekt. To już podstawowy "Hello world!" przyklad. Naciśnij `Ctrl` + `Fn` + `F5`, aby uruchomić projekt. Visual Studio dla komputerów Mac kompiluje projekt, konwertując kod źródłowy do pliku wykonywalnego. Następnie uruchamia okno poleceń, w którym jest uruchamiana nowa aplikacja. W oknie powinien zostać wyświetlony następujący tekst:

```console
Hello World!

Press any key to close this window . . .
```

Naciśnij klawisz, aby zakończyć sesję.

---

## <a name="elements-of-a-c-program"></a>Elementy C# programu

Przeanalizujmy ważne części tego programu. Pierwszy wiersz zawiera komentarz. Znaki `//` konwertują resztę wiersza do komentarza.

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

Możesz również dodać komentarz do bloku tekstu, umieszczając go między `/*` i `*/` znaków. Pokazano to w poniższym przykładzie.

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

Aplikacja C# konsolowa musi zawierać metodę `Main`, w której kontrolka zaczyna się i skończy. Metoda `Main` służy do tworzenia obiektów i wykonywania innych metod.

Metoda `Main` jest metodą [statyczną](../../language-reference/keywords/static.md) , która znajduje się wewnątrz klasy lub struktury. W poprzednim "Hello world!" przykład znajduje się w klasie o nazwie `Hello`. Metodę `Main` można zadeklarować w jeden z następujących sposobów:

- Może zwrócić `void`. Oznacza to, że program nie zwraca wartości.

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- Może również zwracać liczbę całkowitą. Liczba całkowita jest **kodem zakończenia** dla aplikacji.

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- Za pomocą jednego z typów zwracanych można przyjmować argumenty.

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

—lub—

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

Parametr metody `Main`, `args`, jest tablicą `string` zawierającą argumenty wiersza polecenia używane do wywoływania programu.

Aby uzyskać więcej informacji o używaniu argumentów wiersza polecenia, zobacz przykłady w [Main () i argumenty wiersza polecenia](../main-and-command-args/index.md).

## <a name="input-and-output"></a>Dane wejściowe i wyjściowe

C#programy zwykle korzystają z usług wejścia/wyjścia dostarczonych przez bibliotekę wykonawczą .NET Framework. `System.Console.WriteLine("Hello World!");` instrukcji używa metody <xref:System.Console.WriteLine%2A>. Jest to jedna z metod wyjściowych klasy <xref:System.Console> w bibliotece wykonawczej. Wyświetla jego parametr String w standardowym strumieniu wyjściowym, po którym następuje nowy wiersz. Inne metody <xref:System.Console> są dostępne dla różnych operacji wejścia i wyjścia. Jeśli dołączysz dyrektywę `using System;` na początku programu, możesz bezpośrednio użyć klas <xref:System> i metod bez ich w pełni kwalifikujących się. Na przykład można wywołać `Console.WriteLine` zamiast `System.Console.WriteLine`:

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

Aby uzyskać więcej informacji na temat metod wejścia/wyjścia, zobacz <xref:System.IO>.

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Przykłady i samouczki](../../../samples-and-tutorials/index.md)
- [Main() i argumenty wiersza polecenia](../main-and-command-args/index.md)
- [Wprowadzenie z wizualizacjąC#](/visualstudio/ide/quickstart-csharp-console)
