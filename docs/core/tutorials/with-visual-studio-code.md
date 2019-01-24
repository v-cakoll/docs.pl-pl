---
title: Wprowadzenie do języka C# i Visual Studio Code
description: Informacje o sposobie tworzenia i debugowania pierwszej aplikacji platformy .NET Core w języku C# za pomocą programu Visual Studio Code.
author: kendrahavens
ms.date: 12/05/2018
ms.custom: seodec18
ms.openlocfilehash: ea8b93128e4acd435ad95fc42257df6ab22812fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620555"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>Wprowadzenie do języka C# i Visual Studio Code

.NET core udostępnia szybka, modularna platforma do tworzenia aplikacji działających w Windows, Linux i macOS. Użyj programu Visual Studio Code z rozszerzeniem języka C#, aby uzyskać Zaawansowane edytowanie z pełnym wsparciem dla języka C# IntelliSense (uzupełnianie kodu inteligentnych) i debugowania.

## <a name="prerequisites"></a>Wymagania wstępne

1. Zainstaluj [programu Visual Studio Code](https://code.visualstudio.com/).
2. Zainstaluj [platformy .NET Core SDK](https://www.microsoft.com/net/download/core).
3. Zainstaluj [rozszerzenie języka C#](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) dla programu Visual Studio Code. Aby uzyskać więcej informacji na temat instalowania rozszerzeń w programie Visual Studio Code, zobacz [Portal Marketplace z rozszerzeniami kodu programu VS](https://code.visualstudio.com/docs/editor/extension-gallery).

## <a name="hello-world"></a>Witaj Świecie

Zacznijmy od prostego programu "Hello World" na platformie .NET Core:

1. Otwórz projekt:

    * Open Visual Studio Code.
    * Kliknij ikonę Explorer z menu po lewej stronie, a następnie kliknij przycisk **Otwórz Folder**.
    * Wybierz **pliku** > **Otwórz Folder** z menu głównego, aby otworzyć folder dla której projekt C# w, a następnie kliknij przycisk **wybierz Folder**. W tym przykładzie tworzymy folderem naszego projektu o nazwie *HelloWorld*.

      ![Visual Studio Code Otwórz folder.](media/with-visual-studio-code/vs-code-open-folder.png)

2. Inicjowanie projektu C#:
    * Otworzyć zintegrowany Terminal programu z Visual Studio Code, wybierając **widoku** > **zintegrowany Terminal** z menu głównego.
    * W oknie terminalu wpisz `dotnet new console`.
    * To polecenie umożliwia utworzenie `Program.cs` plik w folderze przy użyciu programu proste "Hello World", została ona już zapisana, wraz z plikiem projektu C# o nazwie `HelloWorld.csproj`.

      ![Nowe polecenie dotnet](media/with-visual-studio-code/dotnet-new-command.png)

3. Aby usunąć zasoby kompilacji:

    * Aby uzyskać **platformy .NET Core 1.x**, typ `dotnet restore`. Uruchamianie `dotnet restore` zapewnia dostęp do wymaganych pakietów .NET Core, które są wymagane do kompilowania projektu.

      ![Polecenie restore dotnet](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. Uruchom program "Hello World":

    * Typ `dotnet run`.

      ![Polecenia dotnet, uruchom polecenie](media/with-visual-studio-code/dotnet-run-command.png)

Możesz też obejrzeć krótki samouczek wideo, aby uzyskać dalszą pomoc Instalatora na [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), lub [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

## <a name="debug"></a>Debugowanie

1. Otwórz *Program.cs* , klikając ją. Przy pierwszym otwarciu pliku C# w programie Visual Studio Code [technologię OmniSharp](https://www.omnisharp.net/) ładuje w edytorze.

    ![Otwórz plik Program.cs](media/with-visual-studio-code/open-program-cs.png)

2. Visual Studio Code powinien zostać wyświetlony monit można dodać brakujące zasoby do tworzenia i debugowania aplikacji. Wybierz **tak**.

    ![Monituj o brakujących zasobów](media/with-visual-studio-code/missing-assets.png)

3. Aby otworzyć widok debugowania, kliknij ikonę debugowanie z menu po lewej stronie.

    ![Otwórz kartę debugowania w programie Visual Studio Codee](media/with-visual-studio-code/open-debug-tab.png)

4. Znajdź zieloną strzałkę w górnej części okienka. Upewnij się, ma listę rozwijaną obok niego `.NET Core Launch (console)` wybrane.

    ![Wybieranie platformy .NET Core w programie Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

5. Dodaj punkt przerwania do projektu, klikając **marginesu edytora**, która jest miejsce po lewej stronie numery wierszy w edytorze, obok wiersza 9, lub Przesuń kursor tekst w wierszu 9 w edytorze i naciśnij klawisz <kbd>F9</kbd>.

    ![Ustawienie punktu przerwania](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. Aby rozpocząć debugowanie, wybierz <kbd>F5</kbd> lub zieloną strzałkę. Debuger zatrzymuje wykonanie programu, po osiągnięciu punktu przerwania ustawione w poprzednim kroku.
    * Podczas debugowania, można wyświetlać swoje zmienne lokalne w górnym okienku po lewej stronie, lub za pomocą konsoli debugowania.

7. Wybierz niebieską strzałką u góry, aby kontynuować debugowanie lub wybrać czerwony kwadrat u góry, aby zatrzymać.

    ![Uruchamianie i debugowanie w programie Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> Aby uzyskać więcej informacji i rozwiązywanie problemów z porad na temat platformy .NET Core debugowania przy użyciu technologię OmniSharp w programie Visual Studio Code, zobacz [instrukcje dotyczące konfigurowania debugera platformy .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="add-a-class"></a>Dodaj klasę

1. Aby dodać nowe kliknij prawym przyciskiem myszy klasy w Eksploratorze programu VSCode i wybierz **nowy plik**. Spowoduje to dodanie nowego pliku do folderu otwartych w VSCode.
2. Nadaj plikowi nazwę `Class1.cs`. Musisz zapisać ją z `.cs` rozszerzenia na końcu, aby mogła zostać rozpoznany jako plik csharp.
3. Dodaj poniższy kod, aby tworzenie swojej pierwszej klasy. Upewnij się, że zawiera poprawną przestrzeń nazw, więc możesz odwoływać się do niej z usługi `Program.cs` pliku.
``` csharp
using System;

namespace HelloWorld
{
    public class Class1
    {
        public string ReturnMessage()
        {
            return "Happy coding!";
        }
    }
}
```

4. Wywoływanie nowej klasie z głównej metody w `Program.cs` , dodając poniższy kod.

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Class1 c1 = new Class1();
            Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
        }
    }
}
```

5. Zapisz zmiany, a następnie ponownie uruchom program. Nowa wiadomość powinna zostać wyświetlona z dołączonym ciągiem.
```console
> dotnet run
Hello World! Happy coding!
```

## <a name="faq"></a>Najczęściej zadawane pytania

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Brakiem wymagane zasoby do tworzenia i debugowania języka C# w programie Visual Studio Code. Moje debugera jest wyświetlany komunikat "Brak konfiguracji".

Rozszerzenia programu Visual Studio kodu C# można wygenerować zasoby do tworzenia i debugowania dla Ciebie. Visual Studio Code jest wyświetlany monit o generowanie tych zasobów, przy pierwszym otwarciu projektu C#. Jeśli nie Generuj elementy zawartości, to nadal można uruchomić tego polecenia, otwierając paletę poleceń (**Widok > paletę poleceń**) i wprowadzając polecenie "> .NET: Wygenerować zasoby kompilacji i debugowania". Wybranie tej generuje .vscode pliku launch.json i tasks.json pliki konfiguracji, które należy.

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie programu Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)
- [Debugowanie w programie Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)
