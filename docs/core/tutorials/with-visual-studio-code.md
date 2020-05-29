---
title: Tworzenie aplikacji konsolowej z platformą .NET Core przy użyciu Visual Studio Code
description: Dowiedz się, jak utworzyć aplikację konsolową .NET Core przy użyciu Visual Studio Code i interfejs wiersza polecenia platformy .NET Core.
ms.date: 05/22/2020
ms.openlocfilehash: 673c4a639a2cab26261b7cdafd5d8e20acfafb94
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201703"
---
# <a name="tutorial-create-a-console-application-with-net-core-using-visual-studio-code"></a>Samouczek: Tworzenie aplikacji konsolowej z platformą .NET Core przy użyciu Visual Studio Code

W tym samouczku pokazano, jak utworzyć i uruchomić aplikację konsolową .NET Core przy użyciu Visual Studio Code i interfejs wiersza polecenia platformy .NET Core. Zadania projektu, takie jak tworzenie, kompilowanie i uruchamianie projektu, są wykonywane za pomocą interfejsu wiersza polecenia, więc można wykonać kroki tego samouczka z innym edytorem kodu i uruchamiać polecenia w terminalu, jeśli wolisz.

## <a name="prerequisites"></a>Wymagania wstępne

1. [Visual Studio Code](https://code.visualstudio.com/) z zainstalowanym [rozszerzeniem języka C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) . Aby uzyskać informacje na temat sposobu instalowania rozszerzeń na Visual Studio Code, zobacz [vs Code rozszerzenia Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).
2. [Zestaw SDK platformy .NET Core 3,1 lub nowszy](https://dotnet.microsoft.com/download)

## <a name="create-the-app"></a>Tworzymy aplikację.

1. Otwórz program Visual Studio Code.

1. Utwórz projekt.

   1. Wybierz pozycję **plik**  >  **Otwórz folder** / **Otwórz...** z menu głównego, Utwórz folder *HelloWorld* , a następnie kliknij pozycję **Wybierz folder** / **Otwórz**.

      Nazwa folderu domyślnie zmienia nazwę projektu i nazwę przestrzeni nazw. Kod zostanie dodany później w samouczku, który zakłada, że przestrzeń nazw projektu to `HelloWorld` .

   1. Otwórz **Terminal** w Visual Studio Code, wybierając pozycję **Wyświetl**  >  **Terminal** z menu głównego.

      Zostanie otwarty **Terminal** z wierszem polecenia w folderze *HelloWorld* .

   1. W **terminalu**wprowadź następujące polecenie:

      ```dotnetcli
      dotnet new console
      ```

Szablon aplikacji konsoli dla platformy .NET Core definiuje klasę, `Program` przy użyciu pojedynczej metody, `Main` która pobiera <xref:System.String> tablicę jako argument. Plik *program.cs* ma następujący kod:

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

`Main`jest punktem wejścia aplikacji, metoda, która jest wywoływana automatycznie przez środowisko uruchomieniowe podczas uruchamiania aplikacji. Wszystkie argumenty wiersza polecenia dostarczone podczas uruchamiania aplikacji są dostępne w tablicy *args* .

Szablon tworzy prostą aplikację, która wywołuje <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodę, aby wyświetlić "Hello World!" w oknie konsoli.

## <a name="run-the-app"></a>Uruchomienie aplikacji

Uruchom następujące polecenie w **terminalu**:

```dotnetcli
dotnet run
```

Program wyświetla "Hello world!" i zakończenia.

![Polecenie dotnet Run](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a>Ulepszanie aplikacji

Podnieś poziom aplikacji, aby monitować użytkownika o jego nazwę i wyświetlić go wraz z datą i godziną.

1. Otwórz *program.cs* , klikając go.

   Przy pierwszym otwarciu pliku C# w Visual Studio Code [OmniSharp](https://www.omnisharp.net/) ładuje się w edytorze.

   ![Otwórz plik Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. Wybierz opcję **tak** , gdy Visual Studio Code zostanie wyświetlony komunikat z prośbą o dodanie brakujących zasobów do kompilowania i debugowania aplikacji.

   ![Monituj o brakujące zasoby](media/with-visual-studio-code/missing-assets.png)

1. Zastąp zawartość `Main` metody w *program.cs*, która jest obecnie tylko wierszem, który wywołuje `Console.WriteLine` , przy użyciu następującego kodu:

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="Snippet1":::

   Ten kod wyświetla "co to jest Twoja nazwa?" w oknie konsoli i czeka, aż użytkownik wprowadzi ciąg, a następnie klawisz **Enter** . Ten ciąg jest przechowywany w zmiennej o nazwie `name` . Pobiera również wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości, która zawiera bieżący czas lokalny i przypisuje go do zmiennej o nazwie `date` . Na koniec wyświetla te wartości w oknie konsoli.

   `\n`Reprezentuje znak nowego wiersza.

   Znak dolara ( `$` ) przed ciągiem umożliwia umieszczenie wyrażeń takich jak nazwy zmiennych w nawiasach klamrowych w ciągu. Wartość wyrażenia jest wstawiana do ciągu zamiast wyrażenia. Ta składnia jest określana mianem [ciągów interpolowanych](../../csharp/language-reference/tokens/interpolated.md).

1. Zapisz zmiany.

   > [!IMPORTANT]
   > W Visual Studio Code należy jawnie zapisać zmiany. W przeciwieństwie do programu Visual Studio zmiany plików nie są automatycznie zapisywane podczas kompilowania i uruchamiania aplikacji.

1. Ponownie uruchom program:

   ```dotnetcli
   dotnet run
   ```

1. Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz **Enter** .

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="Okno terminalu ze zmodyfikowanym wyjściem programu":::

1. Naciśnij dowolny klawisz, aby wyjść z programu.

## <a name="additional-resources"></a>Zasoby dodatkowe

- [Konfigurowanie Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzono aplikację .NET Core. W następnym samouczku debugujesz aplikację.

> [!div class="nextstepaction"]
> [Debugowanie aplikacji konsolowej .NET Core przy użyciu Visual Studio Code](debugging-with-visual-studio-code.md)
