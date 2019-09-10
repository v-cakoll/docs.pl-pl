---
title: Wprowadzenie do języka C# i programu Visual Studio Code
description: Dowiedz się, jak utworzyć i debugować pierwszą aplikację platformy .NET C# Core w programie przy użyciu Visual Studio Code.
author: kendrahavens
ms.date: 12/05/2018
ms.custom: seodec18
ms.openlocfilehash: 03a2edcbb3414cfd63006603424a3ca1eade528f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849456"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>Wprowadzenie do języka C# i programu Visual Studio Code

Program .NET Core zapewnia szybką i modularną platformę do tworzenia aplikacji działających w systemach Windows, Linux i macOS. Użyj Visual Studio Code z rozszerzeniem C# , aby uzyskać zaawansowane środowisko edycji z pełną obsługą C# technologii IntelliSense (inteligentnych uzupełniania kodu) i debugowania.

## <a name="prerequisites"></a>Wymagania wstępne

1. Zainstaluj [Visual Studio Code](https://code.visualstudio.com/).
2. Zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download).
3. Zainstaluj [ C# rozszerzenie](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) dla Visual Studio Code. Aby uzyskać więcej informacji na temat sposobu instalowania rozszerzeń na Visual Studio Code, zobacz [vs Code rozszerzenia Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).

## <a name="hello-world"></a>Witaj Świecie

Zacznijmy od prostego programu "Hello world" na platformie .NET Core:

1. Otwórz projekt:

    - Otwórz Visual Studio Code.
    - Kliknij ikonę Eksploratora w menu po lewej stronie, a następnie kliknij polecenie **Otwórz folder**.
    - Wybierz pozycję **plik** > **Otwórz folder** z menu głównego, aby otworzyć folder, w którym C# ma się znajdować projekt, a następnie kliknij pozycję **Wybierz folder**. W naszym przykładzie tworzymy folder dla naszego projektu o nazwie *HelloWorld*.

      ![Visual Studio Code Otwórz folder](media/with-visual-studio-code/vs-code-open-folder.png)

2. Zainicjuj C# projekt:
    - Otwórz zintegrowany terminal z Visual Studio Code, wybierając opcję **Wyświetl** > **zintegrowany terminal** z menu głównego.
    - W oknie terminalu wpisz `dotnet new console`polecenie.
    - To polecenie tworzy `Program.cs` plik w folderze z prostym, już zapisanym programem "Hello World", wraz z plikiem C# projektu o nazwie `HelloWorld.csproj`.

      ![Polecenie dotnet New](media/with-visual-studio-code/dotnet-new-command.png)

3. Rozpoznaj zasoby kompilacji:

    - W przypadku **platformy .NET Core 1. x**wpisz `dotnet restore`polecenie. Uruchomienie `dotnet restore` zapewnia dostęp do wymaganych pakietów .NET Core, które są potrzebne do skompilowania projektu.

      ![dotnet restore polecenie](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. Uruchom program "Hello world":

    - Typ `dotnet run`.

      ![Polecenie dotnet Run](media/with-visual-studio-code/dotnet-run-command.png)

Możesz również obejrzeć krótki samouczek wideo dotyczący dalszej instalacji [systemu Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS)lub [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

## <a name="debug"></a>Debugowanie

1. Otwórz *program.cs* , klikając go. Przy pierwszym otwarciu C# pliku w Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) ładuje się w edytorze.

    ![Otwórz plik Program.cs](media/with-visual-studio-code/open-program-cs.png)

2. Visual Studio Code powinien monitować o dodanie brakujących zasobów do kompilowania i debugowania aplikacji. Wybierz pozycję **tak**.

    ![Monituj o brakujące zasoby](media/with-visual-studio-code/missing-assets.png)

3. Aby otworzyć widok debugowanie, kliknij ikonę debugowania w menu po lewej stronie.

    ![Otwórz kartę debugowanie w Visual Studio Code](media/with-visual-studio-code/open-debug-tab.png)

4. Znajdź zieloną strzałkę w górnej części okienka. Upewnij się, że lista rozwijana obok niej została `.NET Core Launch (console)` wybrana.

    ![Wybieranie platformy .NET Core w Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

5. Dodaj punkt przerwania do projektu, klikając **margines edytora**, który jest odstępem po lewej stronie numerów wierszy w edytorze, obok pozycji wiersz 9 lub Przenieś kursor tekstu do wiersza 9 w edytorze i naciśnij klawisz <kbd>F9</kbd>.

    ![Ustawianie punktu przerwania](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. Aby rozpocząć debugowanie, wybierz <kbd>F5</kbd> lub zieloną strzałkę. Debuger przerywa wykonywanie programu po osiągnięciu punktu przerwania ustawionego w poprzednim kroku.
    - Podczas debugowania można wyświetlić zmienne lokalne w lewym górnym okienku lub użyć konsoli debugowania.

7. Wybierz niebieską strzałkę u góry, aby kontynuować debugowanie, lub zaznacz czerwony kwadrat u góry, aby go zatrzymać.

    ![Uruchamianie i debugowanie w Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> Aby uzyskać więcej informacji i porady dotyczące rozwiązywania problemów dotyczących debugowania .NET Core za pomocą OmniSharp w Visual Studio Code, zobacz [instrukcje dotyczące konfigurowania debugera .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="add-a-class"></a>Dodawanie klasy

1. Aby dodać nową klasę, kliknij prawym przyciskiem myszy w Eksploratorze programu vscode i wybierz polecenie **nowy plik**. Spowoduje to dodanie nowego pliku do folderu, który został otwarty w programu vscode.
2. Nazwij plik `MyClass.cs`. Musisz zapisać go z `.cs` rozszerzeniem na końcu, aby można go było rozpoznać jako plik CSharp.
3. Dodaj poniższy kod, aby utworzyć swoją pierwszą klasę. Upewnij się, że dołączysz poprawną przestrzeń nazw, aby można było `Program.cs` odwołać się do niej z pliku.

    ``` csharp
    using System;

    namespace HelloWorld
    {
        public class MyClass
        {
            public string ReturnMessage()
            {
                return "Happy coding!";
            }
        }
    }
    ```

4. Wywołaj nową klasę z metody Main w programie `Program.cs` , dodając Poniższy kod.

    ```csharp
    using System;
    
    namespace HelloWorld
    {
        class Program
        {
            static void Main(string[] args)
            {
                MyClass c1 = new MyClass();
                Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
            }
        }
    }
    ```

5. Zapisz zmiany i ponownie uruchom program. Nowy komunikat powinien pojawić się z dołączonym ciągiem.

    ```console
    > dotnet run
    Hello World! Happy coding!
    ```

## <a name="faq"></a>Najczęściej zadawane pytania

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Nie mam wymaganych zasobów do kompilowania i debugowania C# w Visual Studio Code. My Debugger brzmi "Brak konfiguracji".

Rozszerzenie Visual Studio Code C# może generować zasoby do kompilowania i debugowania. Visual Studio Code poprosi o wygenerowanie tych zasobów przy pierwszym otwarciu C# projektu. Jeśli zasoby nie zostały jeszcze wygenerowane, możesz uruchomić to polecenie, otwierając paletę poleceń (**wyświetl > palecie poleceń**) i wpisując "> .NET: Generuj zasoby dla kompilacji i debugowania. Wybranie tej opcji spowoduje wygenerowanie plików konfiguracyjnych. programu vscode, Launch. JSON i Tasks. JSON, które są potrzebne.

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)
- [Debugowanie w Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)
