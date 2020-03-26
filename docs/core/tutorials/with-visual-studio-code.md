---
title: Wprowadzenie do języka C# i programu Visual Studio Code
description: Dowiedz się, jak utworzyć i debugować pierwszą aplikację .NET Core w języku C# przy użyciu programu Visual Studio Code.
author: kendrahavens
ms.date: 12/05/2018
ms.openlocfilehash: 49a1271f2bf74224e189e70bebf0d22c49408e5d
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111065"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>Wprowadzenie do języka C# i programu Visual Studio Code

Program .NET Core zapewnia szybką i modułową platformę do tworzenia aplikacji uruchomionych w systemach Windows, Linux i macOS. Użyj programu Visual Studio Code z rozszerzeniem C#, aby uzyskać zaawansowane środowisko edycji z pełną obsługą języka C# IntelliSense (ukończenie inteligentnego kodu) i debugowanie.

## <a name="prerequisites"></a>Wymagania wstępne

1. Zainstaluj narzędzie [Visual Studio Code](https://code.visualstudio.com/).
2. Zainstaluj pakiet [.NET Core SDK](https://dotnet.microsoft.com/download).
3. Zainstaluj [rozszerzenie C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) dla programu Visual Studio Code. Aby uzyskać więcej informacji na temat instalowania rozszerzeń w programie Visual Studio Code, zobacz [vs.](https://code.visualstudio.com/docs/editor/extension-gallery)

## <a name="hello-world"></a>Witaj, świecie

Zacznijmy od prostego programu "Hello World" w serwisie .NET Core:

1. Otwórz projekt:

    - Otwórz program Visual Studio Code.
    - Kliknij ikonę Eksploratora w menu po lewej stronie, a następnie kliknij pozycję **Otwórz folder**.
    - Wybierz **polecenie Folder** > **otwierania pliku** z menu głównego, aby otworzyć folder, w który ma znajdować się projekt języka C#, a następnie kliknij pozycję Wybierz **folder**. Na przykład tworzymy folder dla naszego projektu o nazwie *HelloWorld*.

      ![Folder otwarty kodu programu Visual Studio](media/with-visual-studio-code/vs-code-open-folder.png)

2. Zainicjowanie projektu języka C#:

    - Otwórz zintegrowany terminal z programu Visual Studio Code, wybierając **widok** > **zintegrowanego terminala** z menu głównego.
    - W oknie terminala `dotnet new console`wpisz .
    - To polecenie tworzy *plik Program.cs* w folderze z prostym programem "Hello World" już napisanym, wraz z plikiem projektu C# o nazwie *HelloWorld.csproj*.

      ![Nowe polecenie dotnet](media/with-visual-studio-code/dotnet-new-command.png)

3. Rozwiąż zasoby kompilacji:

    - W przypadku **.NET Core 1.x**wpisz `dotnet restore`. Uruchamianie `dotnet restore` daje dostęp do wymaganych pakietów .NET Core, które są potrzebne do tworzenia projektu.

      ![Polecenie przywracania dotnetu](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. Uruchom program "Hello World":

    - Wpisz polecenie `dotnet run`.

      ![Polecenie dotnet run](media/with-visual-studio-code/dotnet-run-command.png)

Można również obejrzeć krótki film instruktażowy dla dalszej pomocy konfiguracji w [systemie Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS)lub [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

## <a name="debug"></a>Debugowanie

1. Otwórz *Program.cs* klikając na niego. Przy pierwszym otwarciu pliku języka C# w programie Visual Studio [Code, OmniSharp](https://www.omnisharp.net/) ładuje się w edytorze.

    ![Otwieranie pliku Program.cs](media/with-visual-studio-code/open-program-cs.png)

2. Visual Studio Kod powinien monitować o dodanie brakujących zasobów do tworzenia i debugowania aplikacji. Wybierz **pozycję Tak**.

    ![Monitowanie o brakujące zasoby](media/with-visual-studio-code/missing-assets.png)

3. Aby otworzyć widok debugowania, kliknij ikonę debugowania w menu po lewej stronie.

    ![Otwieranie karty Debugowanie w programie Visual Studio Code](media/with-visual-studio-code/open-debug-tab.png)

4. Znajdź zieloną strzałkę w górnej części okienka. Upewnij się, że obok listy rozwijanej jest zaznaczona opcja **.NET Core Launch (konsola).**

    ![Wybieranie programu .NET Core w programie Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

5. Dodaj punkt przerwania do projektu, klikając **na margines edytora**, który jest spacją po lewej stronie numerów wierszy w edytorze, obok wiersza 9, lub przenieś kursor tekstowy na linię 9 w edytorze i naciśnij <kbd>klawisz F9</kbd>.

    ![Ustawianie punktu przerwania](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. Aby rozpocząć debugowanie, naciśnij <kbd>klawisz F5</kbd> lub wybierz zieloną strzałkę. Debuger zatrzymuje wykonywanie programu, gdy osiągnie punkt przerwania ustawiony w poprzednim kroku.
    - Podczas debugowania można wyświetlić zmienne lokalne w lewym górnym okienku lub użyć konsoli debugowania.

7. Wybierz niebieską strzałkę u góry, aby kontynuować debugowanie, lub wybierz czerwony kwadrat u góry, aby zatrzymać.

    ![Uruchamianie i debugowanie w programie Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> Aby uzyskać więcej informacji i wskazówek dotyczących rozwiązywania problemów z debugowaniem rdzenia .NET za pomocą programu OmniSharp w programie Visual Studio Code, zobacz [Instrukcje konfigurowania debugera .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="add-a-class"></a>Dodawanie klasy

1. Aby dodać nową klasę, kliknij prawym przyciskiem myszy w Eksploratorze VSCode i wybierz polecenie **Nowy plik**. Spowoduje to dodanie nowego pliku do folderu otwartego w programie VSCode.
2. Nadaj nazwę *pliku MyClass.cs*. Musisz zapisać go `.cs` z rozszerzeniem na końcu, aby został rozpoznany jako plik csharp.
3. Dodaj poniższy kod, aby utworzyć pierwszą klasę. Upewnij się, że zawieraszdytny obszar nazw, aby można było odwoływać się do niego z pliku *Program.cs:*

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

4. Zadzwoń do nowej klasy z głównej metody w *Program.cs,* dodając poniższy kod:

    ```csharp
    using System;

    namespace HelloWorld
    {
        class Program
        {
            static void Main(string[] args)
            {
                var c1 = new MyClass();
                Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
            }
        }
    }
    ```

5. Zapisz zmiany i uruchom program ponownie. Nowa wiadomość powinna pojawić się z dołączonym ciągiem.

    ```dotnetcli
    dotnet run
    ```

    Dane wyjściowe są następujące:

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a>Często zadawane pytania

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Brakuje mi wymaganych zasobów do tworzenia i debugowania języka C# w programie Visual Studio Code. Mój debuger mówi "Brak konfiguracji".

Rozszerzenie kodu programu Visual Studio C# może generować zasoby do tworzenia i debugowania dla Ciebie. Visual Studio Code monituje o wygenerowanie tych zasobów przy pierwszym otwarciu projektu języka C#. Jeśli nie wygenerowałeś zasobów, to nadal można uruchomić to polecenie, otwierając paletę poleceń **(Wyświetl > paletę poleceń)** i wpisując ">.NET: Generuj zasoby dla kompilacji i debugowania". Wybranie tej opcji powoduje wygenerowanie potrzebnych plików konfiguracyjnych *.vscode*, *launch.json*i *tasks.json.*

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie kodu programu Visual Studio](https://code.visualstudio.com/docs/setup/setup-overview)
- [Debugowanie w programie Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)
