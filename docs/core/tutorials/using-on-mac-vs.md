---
title: Rozpoczynanie pracy z platformą .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac
description: Ten temat przeprowadzi Cię przez tworzenie prostej aplikacji konsolowej przy użyciu programu Visual Studio dla komputerów Mac i .NET Core.
author: mairaw
ms.date: 07/11/2019
ms.custom: seodec18
ms.openlocfilehash: a6d58d2a54ce9742542a3f7e5c9378be89b8f89a
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2019
ms.locfileid: "67870544"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Rozpoczynanie pracy z platformą .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac udostępnia w pełni funkcjonalne rozwoju środowiska IDE (Integrated) do tworzenia aplikacji platformy .NET Core. Ten temat przeprowadzi Cię przez tworzenie prostej aplikacji konsolowej przy użyciu programu Visual Studio dla komputerów Mac i .NET Core.

> [!NOTE]
> Twoja opinia jest bardzo ważnych. Istnieją dwa sposoby, możesz przekazywać opinie do zespołu programistycznego w programie Visual Studio dla komputerów Mac:
> * W programie Visual Studio dla komputerów Mac, wybierz **pomocy** > **Zgłoś Problem** z menu lub **Zgłoś Problem** na ekranie powitalnym, który spowoduje otwarcie okna dla Wypełniając raport o usterce. Swoje opinie możesz śledzić w portalu [Społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/8/index.html).
> * Aby sugestię, wybierz **pomocy** > **sugestię** z menu lub **sugestię** na ekranie powitalnym, co spowoduje przejście do [Programu visual Studio dla sieci Web społeczności deweloperów Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Wymagania wstępne

Zobacz [wymagania wstępne dla platformy .NET Core w systemie Mac](../../core/macos-prerequisites.md) tematu.

Sprawdź [Obsługa platformy .NET Core](https://docs.microsoft.com/visualstudio/mac/net-core-support?view=vsmac-2019) przewodnika, aby upewnić się, używasz obsługiwanej wersji programu .NET Core.

## <a name="get-started"></a>Wprowadzenie

Po zainstalowaniu wymagań wstępnych i programu Visual Studio dla komputerów Mac, Pomiń tę sekcję i przejdź do [Tworzenie projektu](#creating-a-project). Wykonaj następujące kroki, aby zainstalować wstępnie wymagane składniki i programu Visual Studio dla komputerów Mac:

Pobierz [program Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Uruchom Instalatora. Przeczytaj i zaakceptuj umowę licencyjną. Podczas instalacji wybierz opcję zainstalowania platformy .NET Core. Otrzymasz możliwość instalacji Xamarin, technologii deweloperskich aplikacji mobilnych dla wielu platform. Instalowanie środowiska Xamarin i jego składników powiązane jest opcjonalne dla programowania .NET Core. Omówienie programu Visual Studio dla komputerów Mac, proces instalacji, zobacz [program Visual Studio for Mac dokumentacji](/visualstudio/mac/). Po zakończeniu instalacji uruchom program Visual Studio dla komputerów Mac środowiska IDE.

## <a name="creating-a-project"></a>Tworzenie projektu

1. Wybierz **nowe** w oknie uruchamiania.

   ![Przycisk Nowy w programie Visual Studio do ekranu startowego komputerów Mac](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. W **nowy projekt** okno dialogowe, wybierz opcję **aplikacji** w obszarze **platformy .NET Core** węzła. Wybierz **aplikację Konsolową** szablonu następuje **dalej**.

   ![Nowa lista szablonów projektu](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. Jeśli masz więcej niż jedna wersja programu .NET Core zainstalowany, wybierz platformę docelową dla projektu.

1. Wpisz "nazwę HelloWorld" **nazwy projektu**. Wybierz pozycję **Utwórz**.

   ![Konfigurowanie nowego okna dialogowego aplikacji konsoli](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. Zaczekaj, aż zostaną przywrócone zależności projektu. Projekt ma jeden C# pliku *Program.cs*, zawierającego `Program` klasy `Main` metody. `Console.WriteLine` Instrukcji zwróci "Hello World!" w konsoli, gdy aplikacja jest uruchomiona.

   ![Otwórz okno główne z pliku Program.cs](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

Uruchom aplikację w trybie debugowania przy użyciu ⌘ ↵ (polecenie + enter) lub w trybie wydania przy użyciu ⌥ ⌘ ↵ (opcja + polecenia + enter).

![Pokazuje, w okienku dane wyjściowe aplikacji Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a>Następny krok

[Tworzenie kompletnego rozwiązania .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac](using-on-mac-vs-full-solution.md) temacie dowiesz się, jak tworzyć kompletnego rozwiązania .NET Core, który zawiera biblioteki wielokrotnego użytku i testy jednostkowe.
