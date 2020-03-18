---
title: Wprowadzenie do języka C# i programu Visual Studio Code
description: Dowiedz się, jak utworzyć i debugować pierwszą aplikację .NET Core w języku C# przy użyciu kodu programu Visual Studio.
author: kendrahavens
ms.date: 12/05/2018
ms.openlocfilehash: 8eaf1ba2314dcab96db615a8691afed82c5011a7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398882"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>Wprowadzenie do języka C# i programu Visual Studio Code

.NET Core zapewnia szybką i modułową platformę do tworzenia aplikacji działających w systemach Windows, Linux i macOS. Użyj kodu programu Visual Studio z rozszerzeniem Języka C#, aby uzyskać zaawansowane środowisko edycji z pełną obsługą języka C# IntelliSense (inteligentnego uzupełniania kodu) i debugowania.

## <a name="prerequisites"></a>Wymagania wstępne

1. Zainstaluj narzędzie [Visual Studio Code](https://code.visualstudio.com/).
2. Zainstaluj zestaw [SDK .NET Core](https://dotnet.microsoft.com/download).
3. Zainstaluj [rozszerzenie C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) dla kodu programu Visual Studio. Aby uzyskać więcej informacji na temat instalowania rozszerzeń w kodzie programu Visual Studio, zobacz [Vs Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).

## <a name="hello-world"></a>Witaj, świecie

Zacznijmy od prostego programu "Hello World" w programie .NET Core:

1. Otwórz projekt:

    - Otwórz program Visual Studio Code.
    - Kliknij ikonę Eksploratora w menu po lewej stronie, a następnie kliknij pozycję **Otwórz folder**.
    - Wybierz **pozycję Otwórz folder pliku** > **Open Folder** z menu głównego, aby otworzyć folder, w którym ma znajdować się projekt języka C#, i kliknij pozycję **Wybierz folder**. W naszym przykładzie tworzymy folder dla naszego projektu o nazwie *HelloWorld*.

      ![Otwarty folder kodu programu Visual Studio](media/with-visual-studio-code/vs-code-open-folder.png)

2. Inicjuj projekt języka C#:

    - Otwórz zintegrowany terminal z kodu Visual Studio, wybierając z menu głównego **opcję Wyświetl** > **zintegrowany terminal.**
    - W oknie terminalu `dotnet new console`wpisz .
    - To polecenie tworzy *plik Program.cs* w folderze z prostym programem "Hello World" już napisanym, wraz z plikiem projektu C# o nazwie *HelloWorld.csproj*.

      ![Nowe polecenie dotnet](media/with-visual-studio-code/dotnet-new-command.png)

3. Rozwiąż zasoby kompilacji:

    - Dla **.NET Core 1.x**, wpisz `dotnet restore`. Uruchamianie `dotnet restore` zapewnia dostęp do wymaganych pakietów .NET Core, które są potrzebne do tworzenia projektu.

      ![Polecenie przywracania dotnetu](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. Uruchom program "Hello World":

    - Wpisz polecenie `dotnet run`.

      ![Polecenie uruchamiania dotnet](media/with-visual-studio-code/dotnet-run-command.png)

Możesz również obejrzeć krótki film instruktażowy, aby uzyskać dalszą pomoc w konfiguracji w [systemie Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS)lub [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

## <a name="debug"></a>Debugowanie

1. Otwórz *Program.cs,* klikając na niego. Przy pierwszym otwarciu pliku C# w kodzie programu Visual Studio [omniSharp](https://www.omnisharp.net/) ładuje się w edytorze.

    ![Otwieranie pliku Program.cs](media/with-visual-studio-code/open-program-cs.png)

2. Kod programu Visual Studio powinien monitować o dodanie brakujących zasobów do tworzenia i debugowania aplikacji. Wybierz **pozycję Tak**.

    ![Monituj o brakujące zasoby](media/with-visual-studio-code/missing-assets.png)

3. Aby otworzyć widok Debugowania, kliknij ikonę Debugowanie w menu po lewej stronie.

    ![Otwieranie karty Debugowanie w kodzie programu Visual Studio](media/with-visual-studio-code/open-debug-tab.png)

4. Zlokalizuj zieloną strzałkę w górnej części okienka. Upewnij się, że w menu rozwijanym obok jest zaznaczona opcja **.NET Core Launch (konsola).**

    ![Wybieranie programu .NET Core w kodzie programu Visual Studio](media/with-visual-studio-code/select-net-core.png)

5. Dodaj punkt przerwania do projektu, klikając **margines edytora**, który jest miejscem po lewej stronie numerów wierszy w edytorze, obok wiersza 9, lub przenieś kursor tekstu na wiersz 9 w edytorze i naciśnij <kbd>klawisz F9</kbd>.

    ![Ustawianie punktu przerwania](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. Aby rozpocząć debugowanie, naciśnij <kbd>klawisz F5</kbd> lub wybierz zieloną strzałkę. Debuger zatrzymuje wykonywanie programu po osiągnięciu punktu przerwania ustawionego w poprzednim kroku.
    - Podczas debugowania można wyświetlać zmienne lokalne w lewym górnym okienku lub korzystać z konsoli debugowania.

7. Wybierz niebieską strzałkę u góry, aby kontynuować debugowanie, lub wybierz czerwony kwadrat u góry, aby zatrzymać.

    ![Uruchamianie i debugowanie w kodzie programu Visual Studio](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> Aby uzyskać więcej informacji i wskazówki dotyczące rozwiązywania problemów dotyczące debugowania .NET Core za pomocą narzędzia OmniSharp w kodzie programu Visual Studio, zobacz [Instrukcje dotyczące konfigurowania debugera .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="add-a-class"></a>Dodawanie klasy

1. Aby dodać nową klasę, kliknij prawym przyciskiem myszy eksploratorvscode i wybierz polecenie **Nowy plik**. Spowoduje to dodanie nowego pliku do folderu otwartego w VSCode.
2. Nazwij plik *MyClass.cs*. Należy zapisać go `.cs` z rozszerzeniem na końcu, aby został rozpoznany jako plik csharp.
3. Dodaj poniższy kod, aby utworzyć pierwszą klasę. Upewnij się, że zawiera poprawny obszar nazw, dzięki czemu można odwoływać się do niego z pliku *Program.cs:*

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

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Brakuje wymaganych zasobów do tworzenia i debugowania języka C# w kodzie programu Visual Studio. Mój debuger mówi "Brak konfiguracji".

Rozszerzenie Kodu C# programu Visual Studio może generować zasoby do tworzenia i debugowania dla Ciebie. Kod programu Visual Studio monituje o wygenerowanie tych zasobów po pierwszym otwarciu projektu C#. Jeśli nie wygenerowałeś zasobów, nadal można uruchomić to polecenie, otwierając paletę poleceń **(Widok > paletę poleceń)** i wpisując ">.NET: Generuj zasoby dla kompilacji i debugowania". Wybranie tej opcji generuje pliki konfiguracyjne *.vscode*, *launch.json*i *tasks.json.*

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie kodu programu Visual Studio](https://code.visualstudio.com/docs/setup/setup-overview)
- [Debugowanie w kodzie programu Visual Studio](https://code.visualstudio.com/Docs/editor/debugging)
