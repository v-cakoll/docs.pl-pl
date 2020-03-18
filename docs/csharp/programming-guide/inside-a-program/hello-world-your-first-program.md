---
title: Hello World - Twój pierwszy program za pomocą programu Visual Studio w systemie Windows lub Mac - Przewodnik po programowaniu C#
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 910fa4af1b4e45ce627b589a06910dc168490047
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712146"
---
# <a name="hello-world----your-first-program"></a>Hello World - Twój pierwszy program

W tym artykule użyjesz programu Visual Studio do utworzenia tradycyjnego "Hello World!" Program. Visual Studio to profesjonalne zintegrowane środowisko programistyczne (IDE) z wieloma funkcjami przeznaczonymi do tworzenia .NET. Do utworzenia tego programu użyjesz tylko kilku funkcji w programie Visual Studio. Aby dowiedzieć się więcej o programie Visual Studio, zobacz [Wprowadzenie do języka Visual C#](/visualstudio/ide/quickstart-csharp-console).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a>Tworzenie nowej aplikacji

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

Uruchom program Visual Studio. W systemie Windows zostanie wyświetlony następujący obraz:

![Ekran powitalny programu Visual Studio w systemie Windows](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

Wybierz **pozycję Utwórz nowy projekt** w prawym dolnym rogu obrazu. Program Visual Studio wyświetla okno dialogowe **Nowy projekt:**

![Nowy ekran projektu programu Visual Studio w systemie Windows](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> Jeśli jest to pierwszy raz, gdy uruchomiono program Visual Studio, lista **Ostatnie szablony projektów** jest pusta.

W nowym oknie dialogowym projektu wybierz "Aplikacja konsoli (.NET Core)", a następnie naciśnij klawisz **Dalej**. Nadaj projektowi nazwę, na przykład "HelloWorld", a następnie naciśnij klawisz **Create**.

Visual Studio otwiera projekt. To już podstawowy "Hello World!" Przykład. Naciśnij, `Ctrl`  +  `F5` aby uruchomić projekt. Visual Studio tworzy projekt, konwertując kod źródłowy do pliku wykonywalnego. Następnie uruchamia okno polecenia, które uruchamia nową aplikację. W oknie powinien zostać wyświetlony następujący tekst:

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

Naciśnij klawisz, aby zamknąć okno.

# <a name="macos"></a>[Macos](#tab/macos)

Uruchom program Visual Studio dla komputerów Mac. Na komputerze Mac zostanie wyświetlony następujący obraz:

![Ekran powitalny programu Visual Studio na komputerze Mac](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> Jeśli jest to pierwszy raz, gdy program Visual Studio dla komputerów Mac został uruchomiony, lista **Ostatnie projekty** jest pusta.

Wybierz **pozycję Nowy** w prawym górnym rogu obrazu. Program Visual Studio dla komputerów Mac wyświetla okno dialogowe **Nowy projekt:**

![Visual Studio nowy ekran projektu na komputerze Mac](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

W nowym oknie dialogowym projektu wybierz ".NET Core" i "Aplikacja konsoli", a następnie naciśnij klawisz **Dalej**. Należy wybrać platformę docelową. Domyślnie jest w porządku, więc naciśnij dalej. Nadaj projektowi nazwę, na przykład "HelloWorld", a następnie naciśnij klawisz **Create**. Można użyć domyślnej lokalizacji projektu. Nie dodawaj tego projektu do kontroli źródła.

Visual Studio dla komputerów Mac otwiera projekt. To już podstawowy "Hello World!" Przykład. `Ctrl`  +  `Fn` Naciśnij,  +  `F5` aby uruchomić projekt. Visual Studio dla komputerów Mac tworzy projekt, konwertując kod źródłowy do pliku wykonywalnego. Następnie uruchamia okno polecenia, które uruchamia nową aplikację. W oknie powinien zostać wyświetlony następujący tekst:

```console
Hello World!

Press any key to close this window . . .
```

Naciśnij klawisz, aby zakończyć sesję.

---

## <a name="elements-of-a-c-program"></a>Elementy programu C#

Przeanalizujmy ważne części tego programu. Pierwszy wiersz zawiera komentarz. Znaki `//` konwertują resztę wiersza na komentarz.

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

Możesz również skomentować blok tekstu, załączając go między `/*` znakami. `*/` Jest to pokazane w poniższym przykładzie.

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

Aplikacja konsoli Języka C# `Main` musi zawierać metodę, w której formant rozpoczyna się i kończy. Metoda `Main` jest, gdzie można tworzyć obiekty i wykonywać inne metody.

Metoda `Main` jest metodą [statyczną,](../../language-reference/keywords/static.md) która znajduje się wewnątrz klasy lub struktury. W poprzednim "Hello World!" na przykład znajduje się w `Hello`klasie o nazwie . Metodę można `Main` zadeklarować w jeden z następujących sposobów:

- Może powrócić `void`. Oznacza to, że program nie zwraca wartości.

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- Może również zwrócić liczby całkowitej. Liczba całkowita jest **kodem zakończenia** dla aplikacji.

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- Z jednego z typów zwracanych może przyjmować argumenty.

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

— lub —

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

Parametr `Main` metody , `args`jest tablicą zawierającą `string` argumenty wiersza polecenia używane do wywoływania programu.

Aby uzyskać więcej informacji na temat używania argumentów wiersza polecenia, zobacz przykłady w [argumentach Main() i Command-Line](../main-and-command-args/index.md).

## <a name="input-and-output"></a>Dane wejściowe i wyjściowe

Programy C# zazwyczaj używają usług wejścia/wyjścia dostarczanych przez bibliotekę wykonywania programu .NET Framework. Instrukcja `System.Console.WriteLine("Hello World!");` używa <xref:System.Console.WriteLine%2A> metody. Jest to jedna z metod <xref:System.Console> wyjściowych klasy w bibliotece czasu wykonywania. Wyświetla jego parametr ciągu w standardowym strumieniu wyjściowym, po którym następuje nowy wiersz. Inne <xref:System.Console> metody są dostępne dla różnych operacji wejścia i wyjścia. Jeśli uwzględnisz dyrektywę `using System;` na początku programu, można <xref:System> bezpośrednio użyć klas i metod bez ich pełnego kwalifikowania. Na przykład można `Console.WriteLine` wywołać `System.Console.WriteLine`zamiast :

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

Aby uzyskać więcej informacji na temat <xref:System.IO>metod wejścia/wyjścia, zobacz .

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Przykłady i samouczki](../../../samples-and-tutorials/index.md)
- [Main() i argumenty wiersza polecenia](../main-and-command-args/index.md)
- [Wprowadzenie do programu Visual C #](/visualstudio/ide/quickstart-csharp-console)
