---
title: Wprowadzenie do platformy .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac
description: Ten temat przeprowadzi Cię przez tworzenie prostej aplikacji konsolowej przy użyciu programu Visual Studio dla komputerów Mac i .NET Core.
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.openlocfilehash: f751e7532e9627de3d3733476f7214654089e468
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50170734"
---
# <a name="getting-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Wprowadzenie do platformy .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac udostępnia w pełni funkcjonalne rozwoju środowiska IDE (Integrated) do tworzenia aplikacji platformy .NET Core. Ten temat przeprowadzi Cię przez tworzenie prostej aplikacji konsolowej przy użyciu programu Visual Studio dla komputerów Mac i .NET Core.

> [!NOTE]
> Twoja opinia jest bardzo ważnych. Istnieją dwa sposoby, możesz przekazywać opinie do zespołu programistycznego w programie Visual Studio dla komputerów Mac:
> * W programie Visual Studio dla komputerów Mac, wybierz **pomocy** > **Zgłoś Problem** z menu lub **Zgłoś Problem** na ekranie powitalnym, który spowoduje otwarcie okna dla Wypełniając raport o usterce. Swoje opinie możesz śledzić w portalu [Społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/8/index.html).
> * Aby sugestię, wybierz **pomocy** > **sugestię** z menu lub **sugestię** na ekranie powitalnym, co spowoduje przejście do [Programu visual Studio dla sieci Web społeczności deweloperów Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Wymagania wstępne

Zobacz [wymagania wstępne dla platformy .NET Core w systemie Mac](../../core/macos-prerequisites.md) tematu.

## <a name="getting-started"></a>Wprowadzenie

Po zainstalowaniu wymagań wstępnych i programu Visual Studio dla komputerów Mac, Pomiń tę sekcję i przejdź do [Tworzenie projektu](#creating-a-project). Wykonaj następujące kroki, aby zainstalować wstępnie wymagane składniki i programu Visual Studio dla komputerów Mac:

Pobierz [program Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/visual-studio-mac/). Uruchom Instalatora. Przeczytaj i zaakceptuj umowę licencyjną. Podczas instalacji otrzymasz możliwość instalacji Xamarin, technologii deweloperskich aplikacji mobilnych dla wielu platform. Instalowanie środowiska Xamarin i jego składników powiązane jest opcjonalne dla programowania .NET Core. Omówienie programu Visual Studio dla komputerów Mac, proces instalacji, zobacz [wprowadzenie do programu Visual Studio dla komputerów Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/). Po zakończeniu instalacji uruchom program Visual Studio dla komputerów Mac środowiska IDE.

## <a name="creating-a-project"></a>Tworzenie projektu

1. Wybierz **nowy projekt** na ekranie powitalnym.

   ![Przycisk Nowy projekt w programie Visual Studio dla komputerów Mac startowa](./media/using-on-mac-vs/vsmac1.png)

1. W **nowy projekt** okno dialogowe, wybierz opcję **aplikacji** w obszarze **platformy .NET Core** węzła. Wybierz **aplikację Konsolową** szablonu następuje **dalej**.

   ![Nowa lista szablonów projektu](./media/using-on-mac-vs/vsmac2.png)

1. Wpisz "nazwę HelloWorld" **nazwy projektu**. Wybierz **tworzenie**.

   ![Konfigurowanie nowego okna dialogowego aplikacji konsoli](./media/using-on-mac-vs/vsmac3.png)

1. Zaczekaj, aż zostaną przywrócone zależności projektu. Projekt ma jeden C# pliku *Program.cs*, zawierającego `Program` klasy `Main` metody. `Console.WriteLine` Instrukcji zwróci "Hello World!" w konsoli, gdy aplikacja jest uruchomiona.

   ![Otwórz okno główne z pliku Program.cs](./media/using-on-mac-vs/vsmac4.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

Uruchom aplikację w trybie debugowania za pomocą <kbd>F5</kbd> lub w trybie wydania przy użyciu <kbd>CTRL</kbd>+<kbd>F5</kbd>.

![Pokazuje, w okienku dane wyjściowe aplikacji Hello World!](./media/using-on-mac-vs/vsmac5.png)

## <a name="next-step"></a>Następny krok

[Tworzenie kompletnego rozwiązania .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac](using-on-mac-vs-full-solution.md) temacie dowiesz się, jak tworzyć kompletnego rozwiązania .NET Core, który zawiera biblioteki wielokrotnego użytku i testy jednostkowe.
