---
title: Rozpoczynanie pracy z platformą .NET Core przy użyciu programu Visual Studio dla komputerów Mac
description: W tym temacie przedstawiono tworzenie prostej aplikacji konsoli przy użyciu programu Visual Studio dla komputerów Mac i programu .NET Core.
ms.date: 12/19/2019
ms.openlocfilehash: 4cd7e311411bce62698e291e763227496877ea39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740490"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Rozpoczynanie pracy z platformą .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac udostępnia w pełni funkcjonalne zintegrowane środowisko programistyczne (IDE) do tworzenia aplikacji .NET Core. W tym artykule przedstawiono tworzenie prostej aplikacji konsoli przy użyciu programu Visual Studio dla komputerów Mac i programu .NET Core.

> [!NOTE]
> Twoja opinia jest wysoko ceniona. Istnieją dwa sposoby przekazywania informacji zwrotnych do zespołu programistów w programie Visual Studio dla komputerów Mac:
>
> * W programie Visual Studio dla komputerów Mac wybierz pozycję > **Zgłoś problem** z menu lub **Zgłoś problem** na ekranie powitalnym, który otworzy okno do zgłoszenia raportu o błędzie. **Help** Swoje opinie możesz śledzić w portalu [Społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/8/index.html).
> * Aby przedstawić sugestię, wybierz **pozycję Pomóż** > **udostępnij sugestię** z menu lub **Podaj sugestię** z ekranu powitalnego, który zostanie przeniesiony do [strony społeczności programistów programu Visual Studio dla komputerów Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Wymagania wstępne

Zobacz [.NET Core zależności i wymagania](../install/dependencies.md?pivots=os-macos) artykułu.

Sprawdź artykuł [pomocy technicznej programu .NET Core,](/visualstudio/mac/net-core-support) aby upewnić się, że używasz obsługiwanej wersji programu .NET Core.

## <a name="get-started"></a>Rozpoczęcie pracy

Jeśli masz już zainstalowane wymagania wstępne i visual studio dla komputerów Mac, pomiń tę sekcję i przejdź do [tworzenie projektu](#creating-a-project). Wykonaj następujące kroki, aby zainstalować wymagania wstępne i program Visual Studio dla komputerów Mac:

Pobierz [instalator programu Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Uruchom instalatora. Przeczytaj i zaakceptuj umowę licencyjną. Podczas instalacji wybierz opcję zainstalowania programu .NET Core. Masz możliwość zainstalowania xamarin, wieloplatformowej technologii tworzenia aplikacji mobilnych. Instalowanie usługi Xamarin i powiązanych z nią składników jest opcjonalne dla rozwoju programu .NET Core. Aby zapoznać się z procesem instalacji programu Visual Studio dla komputerów Mac, zobacz [Dokumentacja programu Visual Studio dla komputerów Mac](/visualstudio/mac/). Po zakończeniu instalacji uruchom program Visual Studio dla komputerów Mac IDE.

## <a name="creating-a-project"></a>Tworzenie projektu

1. Wybierz **pozycję Nowy** w oknie początkowym.

   ![Nowy przycisk na ekranie startowym programu Visual Studio dla komputerów Mac](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. W oknie dialogowym **Nowy projekt** wybierz **pozycję Aplikacja** w węźle **.NET Core** . Wybierz szablon **Aplikacji konsoli,** po którym następuje **następny**.

   ![Nowa lista szablonów projektów](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. Jeśli zainstalowano więcej niż jedną wersję programu .NET Core, wybierz platformę docelową dla projektu.

1. Wpisz "HelloWorld" dla **nazwy projektu**. Wybierz **pozycję Utwórz**.

   ![Konfigurowanie nowego okna dialogowego Aplikacja konsoli](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. Poczekaj, aż zależności projektu zostaną przywrócone. Projekt ma pojedynczy plik C# *Program.cs* `Program` , zawierający `Main` klasę z metodą. Oświadczenie `Console.WriteLine` będzie wyprowadzać "Hello World!" do konsoli po uruchomieniu aplikacji.

   ![Okno główne z otwartym plikiem Program.cs](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

Uruchom aplikację w trybie debugowania za pomocą  ( polecenie + enter) lub w trybie zwalniania za pomocą   (opcja + polecenie + enter).

![Okienko Wyjście aplikacji pokazuje Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a>Następny krok

[Tworzenie kompletnego rozwiązania .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac](using-on-mac-vs-full-solution.md) zawiera sposób tworzenia kompletnego rozwiązania .NET Core, które zawiera bibliotekę wielokrotnego użytku i testowanie jednostek.
