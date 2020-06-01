---
title: Hello world — pierwszy program korzystający z programu Visual Studio w systemie Windows lub Mac — Przewodnik programowania w języku C#
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 6d78ec83fec72b30f5cee398af1816d0cac35886
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241867"
---
# <a name="hello-world----your-first-program"></a>Hello world — pierwszy program

W tym artykule opisano tworzenie tradycyjnych "Hello world!" przy użyciu programu Visual Studio Program. Program Visual Studio to profesjonalne zintegrowane środowisko programistyczne (IDE) z wieloma funkcjami przeznaczonymi do programowania na platformie .NET. Do utworzenia tego programu będziesz używać tylko kilku funkcji w programie Visual Studio. Aby dowiedzieć się więcej na temat programu Visual Studio, zobacz [wprowadzenie with Visual C#](/visualstudio/ide/quickstart-csharp-console).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a>Tworzenie nowej aplikacji

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

Uruchom program Visual Studio. Zobaczysz następujący obraz w systemie Windows:

![Ekran powitalny programu Visual Studio w systemie Windows](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

Wybierz pozycję **Utwórz nowy projekt** w prawym dolnym rogu obrazu. Program Visual Studio Wyświetla okno dialogowe **Nowy projekt** :

![Ekran nowego projektu programu Visual Studio w systemie Windows](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> Jeśli jest to pierwsze uruchomienie programu Visual Studio, lista **ostatnio używanych szablonów projektu** jest pusta.

W oknie dialogowym Nowy projekt wybierz pozycję "Aplikacja konsolowa (.NET Core)", a następnie naciśnij przycisk **dalej**. Nadaj projektowi nazwę, na przykład "HelloWorld", a następnie naciśnij pozycję **Utwórz**.

Program Visual Studio otwiera projekt. To już podstawowy "Hello world!" przyklad. Naciśnij klawisz `Ctrl`  +  `F5` , aby uruchomić projekt. Program Visual Studio kompiluje projekt, konwertując kod źródłowy do pliku wykonywalnego. Następnie uruchamia okno poleceń, w którym jest uruchamiana nowa aplikacja. W oknie powinien zostać wyświetlony następujący tekst:

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

Naciśnij klawisz, aby zamknąć okno.

# <a name="macos"></a>[macOS](#tab/macos)

Rozpocznij Visual Studio dla komputerów Mac. Na komputerze Mac zobaczysz następujący obraz:

![Ekran powitalny programu Visual Studio na komputerze Mac](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> Jeśli jest to pierwsze uruchomienie Visual Studio dla komputerów Mac, lista **ostatnich projektów** jest pusta.

Wybierz pozycję **Nowy** w prawym górnym rogu obrazu. Visual Studio dla komputerów Mac wyświetla okno dialogowe **Nowy projekt** :

![Ekran nowego projektu programu Visual Studio na komputerze Mac](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

W oknie dialogowym Nowy projekt wybierz pozycję ".NET Core" i "Aplikacja konsolowa", a następnie naciśnij przycisk **dalej**. Musisz wybrać platformę docelową. Wartość domyślna to "prawidłowo", więc naciśnij przycisk Dalej. Nadaj projektowi nazwę, na przykład "HelloWorld", a następnie naciśnij pozycję **Utwórz**. Możesz użyć domyślnej lokalizacji projektu. Nie dodawaj tego projektu do kontroli źródła.

Visual Studio dla komputerów Mac otwiera projekt. To już podstawowy "Hello world!" przyklad. Naciśnij klawisz `Ctrl`  +  `Fn`  +  `F5` , aby uruchomić projekt. Visual Studio dla komputerów Mac kompiluje projekt, konwertując kod źródłowy do pliku wykonywalnego. Następnie uruchamia okno poleceń, w którym jest uruchamiana nowa aplikacja. W oknie powinien zostać wyświetlony następujący tekst:

```console
Hello World!

Press any key to close this window . . .
```

Naciśnij klawisz, aby zakończyć sesję.

---

## <a name="elements-of-a-c-program"></a>Elementy programu C#

Przeanalizujmy ważne części tego programu. Pierwszy wiersz zawiera komentarz. Znaki `//` konwertują resztę wiersza do komentarza.

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

Możesz również dodać komentarz do bloku tekstu, umieszczając go między `/*` `*/` znakami i. Pokazano to w poniższym przykładzie.

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

Aplikacja konsolowa w języku C# musi zawierać `Main` metodę, w której kontrolka zaczyna się i skończy. `Main`Metoda ta umożliwia tworzenie obiektów i wykonywanie innych metod.

`Main`Metoda jest metodą [statyczną](../../language-reference/keywords/static.md) , która znajduje się wewnątrz klasy lub struktury. W poprzednim "Hello world!" przykład znajduje się w klasie o nazwie `Hello` . Metodę można zadeklarować `Main` w jeden z następujących sposobów:

- Może zwrócić `void` . Oznacza to, że program nie zwraca wartości.

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- Może również zwracać liczbę całkowitą. Liczba całkowita jest **kodem zakończenia** dla aplikacji.

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- Za pomocą jednego z typów zwracanych można przyjmować argumenty.

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

-lub-

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

Parametr `Main` metody, `args` , jest `string` tablicą zawierającą argumenty wiersza polecenia używane do wywołania programu.

Aby uzyskać więcej informacji o używaniu argumentów wiersza polecenia, zobacz przykłady w [Main () i argumenty wiersza polecenia](../main-and-command-args/index.md).

## <a name="input-and-output"></a>Dane wejściowe i wyjściowe

Programy języka C# zwykle używają usług wejścia/wyjścia dostarczonych przez bibliotekę wykonawczą platformy .NET. Instrukcja `System.Console.WriteLine("Hello World!");` używa <xref:System.Console.WriteLine%2A> metody. Jest to jedna z metod wyjściowych <xref:System.Console> klasy w bibliotece wykonawczej. Wyświetla jego parametr String w standardowym strumieniu wyjściowym, po którym następuje nowy wiersz. Inne <xref:System.Console> metody są dostępne dla różnych operacji wejścia i wyjścia. Jeśli dołączysz `using System;` dyrektywę na początku programu, możesz bezpośrednio użyć <xref:System> klas i metod bez ich w pełni kwalifikujących się. Na przykład można wywołać `Console.WriteLine` zamiast `System.Console.WriteLine` :

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

Aby uzyskać więcej informacji na temat metod wejścia/wyjścia, zobacz <xref:System.IO> .

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Przykłady i samouczki](../../../samples-and-tutorials/index.md)
- [Main () i argumenty wiersza polecenia](../main-and-command-args/index.md)
- [Wprowadzenie z Visual C #](/visualstudio/ide/quickstart-csharp-console)
