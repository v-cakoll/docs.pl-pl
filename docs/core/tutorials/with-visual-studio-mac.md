---
title: Tworzenie aplikacji konsolowej platformy .NET Core przy użyciu Visual Studio dla komputerów Mac
description: Dowiedz się, jak utworzyć aplikację konsolową .NET Core przy użyciu Visual Studio dla komputerów Mac.
ms.date: 06/02/2020
ms.openlocfilehash: 57f16e510270b7256b285493b1f978101fc11804
ms.sourcegitcommit: f6350c2c542e6edd52d7e9d6667b96d85d810e67
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2020
ms.locfileid: "84717526"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-for-mac"></a>Samouczek: Tworzenie aplikacji konsolowej platformy .NET Core przy użyciu Visual Studio dla komputerów Mac

W tym samouczku pokazano, jak utworzyć i uruchomić aplikację konsolową .NET Core przy użyciu Visual Studio dla komputerów Mac.

> [!NOTE]
> Opinie są wysoce wyceniane. Istnieją dwa sposoby przekazywania opinii zespołowi programistycznemu na Visual Studio dla komputerów Mac:
>
> * W Visual Studio dla komputerów Mac wybierz pozycję **Pomoc**  >  **Zgłoś problem** z menu lub **Zgłoś problem** na ekranie powitalnym, co spowoduje otwarcie okna do zgłoszenia usterki. Swoje opinie możesz śledzić w portalu [Społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/8/index.html).
> * Aby skorzystać z sugestii, wybierz pozycję **Pomoc**  >  **Podaj sugestię** z menu lub **Podaj sugestię** na ekranie powitalnym, co spowoduje przejście do [strony internetowej społeczność deweloperów Visual Studio dla komputerów Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Wymagania wstępne

* [Visual Studio dla komputerów Mac w wersji 8,6 lub nowszej](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Wybierz opcję zainstalowania platformy .NET Core. Instalowanie platformy Xamarin jest opcjonalne w przypadku programowania .NET Core. Więcej informacji zawierają następujące zasoby:

  * [Samouczek: instalowanie Visual Studio dla komputerów Mac](/visualstudio/mac/installation).
  * [Obsługiwane wersje macOS](../install/dependencies.md?pivots=os-macos).
  * [Wersje programu .NET Core obsługiwane przez Visual Studio dla komputerów Mac](/visualstudio/mac/net-core-support).

## <a name="create-the-app"></a>Tworzymy aplikację.

Utwórz projekt aplikacji konsolowej .NET Core o nazwie "HelloWorld".

1. Rozpocznij Visual Studio dla komputerów Mac.

1. W oknie uruchamiania wybierz pozycję **Nowy** .

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Przycisk Nowy na ekranie startowym Visual Studio dla komputerów Mac":::

1. W oknie dialogowym **Nowy projekt** wybierz pozycję **aplikacja** w węźle **Sieć Web i konsola** . Wybierz szablon **aplikacja konsoli** , a następnie wybierz przycisk **dalej**.

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-dialog.png" alt-text="Lista nowych szablonów projektu":::

1. Na liście rozwijanej **platforma docelowa** okna dialogowego **Konfigurowanie nowej aplikacji konsoli** wybierz pozycję **.NET Core 3,1**, a następnie wybierz przycisk **dalej**.

   :::image type="content" source="media/with-visual-studio-mac/target-framework.png" alt-text="Wybierz platformę docelową":::

1. Wpisz "HelloWorld" jako **nazwę projektu**, a następnie wybierz pozycję **Utwórz**.

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-options.png" alt-text="Okno dialogowe Konfigurowanie nowej aplikacji konsolowej":::

Szablon tworzy prostą aplikację "Hello world". Wywołuje metodę, <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> Aby wyświetlić "Hello World!" w oknie terminalu.

Kod szablonu definiuje klasę, `Program` przy użyciu pojedynczej metody, `Main` która przyjmuje <xref:System.String> tablicę jako argument:

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

`Main`jest punktem wejścia aplikacji, metoda, która jest wywoływana automatycznie przez środowisko uruchomieniowe podczas uruchamiania aplikacji. Wszystkie argumenty wiersza polecenia dostarczone podczas uruchamiania aplikacji są dostępne w `args` tablicy.

## <a name="run-the-app"></a>Uruchomienie aplikacji

1. Naciśnij pozycję <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Option</kbd> + <kbd>Command</kbd> + <kbd>Enter</kbd>), aby uruchomić aplikację bez debugowania.

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-output.png" alt-text="Terminal zawiera Hello world!":::

1. Zamknij okno **terminalu** .

## <a name="enhance-the-app"></a>Ulepszanie aplikacji

Podnieś poziom aplikacji, aby monitować użytkownika o jego nazwę i wyświetlić go wraz z datą i godziną.

1. W *program.cs*Zastąp zawartość `Main` metody, która jest wierszem, który wywołuje `Console.WriteLine` , przy użyciu następującego kodu:

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="1":::

   Ten kod wyświetla "co to jest Twoja nazwa?" w oknie konsoli i czeka, aż użytkownik wprowadzi ciąg, a następnie klawisz <kbd>Enter</kbd> . Ten ciąg jest przechowywany w zmiennej o nazwie `name` . Pobiera również wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości, która zawiera bieżący czas lokalny i przypisuje go do zmiennej o nazwie `date` . Na koniec wyświetla te wartości w oknie konsoli.

   `\n`Reprezentuje znak nowego wiersza.

   Znak dolara ( `$` ) przed ciągiem umożliwia umieszczenie wyrażeń takich jak nazwy zmiennych w nawiasach klamrowych w ciągu. Wartość wyrażenia jest wstawiana do ciągu zamiast wyrażenia. Ta składnia jest określana mianem [ciągów interpolowanych](../../csharp/language-reference/tokens/interpolated.md).

1. Naciśnij pozycję <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>Option</kbd> + <kbd>Command</kbd> + <kbd>Enter</kbd>), aby uruchomić aplikację.

1. Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz <kbd>Enter</kbd>.

   :::image type="content" source="media/with-visual-studio-mac/hello-world-update.png" alt-text="Terminal pokazuje zmodyfikowane dane wyjściowe programu":::

1. Zamknij Terminal.

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzono aplikację konsolową .NET Core. W następnym samouczku debugujesz aplikację.

> [!div class="nextstepaction"]
> [Debugowanie aplikacji konsolowej .NET Core w programie Visual Studio](debugging-with-visual-studio-mac.md)
