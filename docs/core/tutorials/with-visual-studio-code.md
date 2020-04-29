---
title: Wprowadzenie do języka C# i programu Visual Studio Code
description: Dowiedz się, jak utworzyć i debugować pierwszą aplikację platformy .NET Core w języku C# przy użyciu Visual Studio Code.
author: kendrahavens
ms.date: 04/23/2020
ms.openlocfilehash: 3dd7c4602fbb27e29bad977f8d3df34b6061bc23
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506909"
---
# <a name="get-started-with-c-and-visual-studio-code"></a>Wprowadzenie do języka C# i programu Visual Studio Code

Program .NET Core zapewnia szybką i modularną platformę do tworzenia aplikacji działających w systemach Windows, Linux i macOS. Użyj Visual Studio Code z rozszerzeniem języka C#, aby uzyskać zaawansowane środowisko edycji z pełną obsługą technologii IntelliSense dla języka C# (inteligentnych uzupełniania kodu) i debugowania.

## <a name="prerequisites"></a>Wymagania wstępne

1. Zainstaluj narzędzie [Visual Studio Code](https://code.visualstudio.com/).
2. Zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download).
3. Zainstaluj [rozszerzenie C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) dla Visual Studio Code. Aby uzyskać więcej informacji na temat sposobu instalowania rozszerzeń na Visual Studio Code, zobacz [vs Code rozszerzenia Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).

## <a name="hello-world"></a>Witaj, świecie

Rozpocznij pracę z prostym programem "Hello world" na platformie .NET Core:

1. Otwórz projekt:

    - Otwórz program Visual Studio Code.
    - Wybierz pozycję **plik** > **Otwórz folder** z menu głównego.
    - Utwórz folder o nazwie *HelloWorld*, a następnie kliknij pozycję **Wybierz folder**. Nazwa folderu domyślnie zmienia nazwę projektu i nazwę przestrzeni nazw. Kod zostanie dodany później w samouczku, który zakłada, że przestrzeń nazw `HelloWorld`projektu to.

1. Zainicjuj projekt C#:

    - Otwórz Terminal z Visual Studio Code, wybierając pozycję **Wyświetl** > **Terminal** z menu głównego.
    - W oknie terminalu wprowadź `dotnet new console`wartość.

      To polecenie tworzy plik *program.cs* w folderze z prostym, zapisanym już programem "Hello World", wraz z plikiem projektu C# o nazwie *HelloWorld. csproj*.

      ![Polecenie dotnet New](media/with-visual-studio-code/dotnet-new-command.png)

1. Uruchom program "Hello world":

    - W oknie terminalu wprowadź `dotnet run`wartość.

      ![Polecenie dotnet Run](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="debug"></a>Debugowanie

1. Otwórz *program.cs* , klikając go. Przy pierwszym otwarciu pliku C# w Visual Studio Code [OmniSharp](https://www.omnisharp.net/) ładuje się w edytorze.

    ![Otwórz plik Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. Visual Studio Code zostanie wyświetlony komunikat z prośbą o dodanie brakujących zasobów w celu skompilowania i debugowania aplikacji. Wybierz pozycję **tak**.

    ![Monituj o brakujące zasoby](media/with-visual-studio-code/missing-assets.png)

1. Aby otworzyć widok debugowanie, kliknij ikonę debugowania w menu po lewej stronie.

    ![Otwórz kartę debugowanie w Visual Studio Code](media/with-visual-studio-code/open-debug-tab.png)

1. Znajdź zieloną strzałkę w górnej części okienka. Upewnij się, że lista rozwijana obok niej ma wybraną wartość **.NET Core Start (Console)** .

    ![Wybieranie platformy .NET Core w Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

1. Dodaj punkt przerwania do projektu, klikając **margines edytora**, który jest odstępem po lewej stronie numerów wierszy w edytorze, obok pozycji wiersz 9 lub Przenieś kursor tekstu do wiersza 9 w edytorze i naciśnij klawisz <kbd>F9</kbd>.

    ![Ustawianie punktu przerwania](media/with-visual-studio-code/set-breakpoint-vs-code.png)

1. Aby rozpocząć debugowanie, naciśnij klawisz <kbd>F5</kbd> lub wybierz zieloną strzałkę. Debuger przerywa wykonywanie programu po osiągnięciu punktu przerwania ustawionego w poprzednim kroku.
    - Podczas debugowania można wyświetlić zmienne lokalne w lewym górnym okienku lub użyć konsoli debugowania.

1. Wybierz niebieską strzałkę u góry, aby kontynuować debugowanie, lub zaznacz czerwony kwadrat u góry, aby go zatrzymać.

    ![Uruchamianie i debugowanie w Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> Aby uzyskać więcej informacji i porady dotyczące rozwiązywania problemów dotyczących debugowania .NET Core za pomocą OmniSharp w Visual Studio Code, zobacz [instrukcje dotyczące konfigurowania debugera .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="add-a-class"></a>Dodawanie klasy

1. Aby dodać nową klasę, kliknij prawym przyciskiem myszy w Eksploratorze programu vscode poniżej *program.cs* i wybierz pozycję **nowy plik**. Spowoduje to dodanie nowego pliku do folderu, który został otwarty w programu vscode.
1. Nazwij plik *MyClass.cs*. Musisz zapisać go z `.cs` rozszerzeniem na końcu, aby można go było rozpoznać jako plik CSharp.
1. Dodaj następujący kod, aby utworzyć swoją pierwszą klasę.

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

1. Wywołaj nową klasę z `Main` metody, zastępując kod w *program.cs* następującym kodem:

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

1. Zapisz zmiany.

1. Ponownie uruchom program.

    ```dotnetcli
    dotnet run
    ```

    Zostanie wyświetlony nowy komunikat z dołączonym ciągiem.

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a>Najczęściej zadawane pytania

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a>Brakuje wymaganych zasobów do kompilowania i debugowania języka C# w Visual Studio Code. My Debugger brzmi "Brak konfiguracji".

Rozszerzenie C# Visual Studio Code może generować zasoby do kompilowania i debugowania. Visual Studio Code poprosi o wygenerowanie tych zasobów przy pierwszym otwarciu projektu C#. Jeśli zasoby nie zostały jeszcze wygenerowane, możesz uruchomić to polecenie, otwierając paletę poleceń (**wyświetl > palecie poleceń**) i wpisując "> .NET: Generate Assets for build and debug". Wybranie tej opcji spowoduje wygenerowanie plików konfiguracyjnych *. programu vscode*, *Launch. JSON*i *Tasks. JSON* , które są potrzebne.

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)
- [Debugowanie w Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)
