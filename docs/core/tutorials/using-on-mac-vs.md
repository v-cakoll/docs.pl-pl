---
title: Wprowadzenie do platformy .NET Core na macOS przy użyciu programu Visual Studio dla komputerów Mac
description: W tym temacie przedstawiono tworzenie prostej aplikacji konsolowej przy użyciu programu Visual Studio for Mac i .NET Core.
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.openlocfilehash: 82cd7c09dd595a8273eb88a4caaf34782fa10ac4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214546"
---
# <a name="getting-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Wprowadzenie do platformy .NET Core na macOS przy użyciu programu Visual Studio dla komputerów Mac

Visual Studio for Mac zawiera kompletne programowanie środowiska IDE (Integrated) do tworzenia aplikacji platformy .NET Core. W tym temacie przedstawiono tworzenie prostej aplikacji konsolowej przy użyciu programu Visual Studio for Mac i .NET Core.

> [!NOTE]
> Twoja opinia jest bardzo ważnych. Istnieją dwa sposoby można przekazywania informacji pozwalających na zespół deweloperów w programie Visual Studio dla komputerów Mac:
> * W programie Visual Studio dla komputerów Mac, wybierz **pomocy** > **zgłosić Problem** z menu lub **zgłosić Problem** na ekranie powitalnym, który zostanie otwarte okno dla składanie raport o usterce. Swoje opinie możesz śledzić w portalu [Społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/8/index.html).
> * Aby sugestię, wybierz **pomocy** > **Podaj sugestię** z menu lub **Podaj sugestię** na ekranie powitalnym, która spowoduje przejście do [Programu visual Studio for Mac UserVoice strony sieci Web](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).

## <a name="prerequisites"></a>Wymagania wstępne

Zobacz [wymagania wstępne dotyczące .NET Core w systemie Mac](../../core/macos-prerequisites.md) tematu.

## <a name="getting-started"></a>Wprowadzenie

Jeśli po zainstalowaniu wymagań wstępnych i Visual Studio dla komputerów Mac, Pomiń tę sekcję i przejdź do [tworzenia projektu](#creating-a-project). Wykonaj następujące kroki, aby zainstalować wstępnie wymagane składniki i Visual Studio dla komputerów Mac:

Pobierz [programu Visual Studio for Mac Instalatora](https://www.visualstudio.com/vs/visual-studio-mac/). Uruchom Instalatora. Przeczytaj i zaakceptuj umowę licencyjną. Podczas instalacji są podane możliwość Zainstaluj program Xamarin, technologii programowanie wieloplatformowych aplikacji mobilnych. Instalowanie platformy Xamarin i jej powiązane składniki jest opcjonalne dla rozwoju platformy .NET Core. Omówienie programu Visual Studio for Mac proces instalacji, aby zapoznać [wprowadzenie do programu Visual Studio for Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/). Po zakończeniu instalacji uruchom program Visual Studio dla komputerów Mac IDE.

## <a name="creating-a-project"></a>Tworzenie projektu

1. Wybierz **nowy projekt** na ekranie powitalnym.

   ![Przycisk Nowy projekt w Visual Studio dla ekranu powitalnego Mac](./media/using-on-mac-vs/vsmac1.png)

1. W **nowy projekt** okno dialogowe, wybierz opcję **aplikacji** w obszarze **.NET Core** węzła. Wybierz **aplikacji konsoli** następuje szablonu **dalej**.

   ![Nowa lista szablonów projektu](./media/using-on-mac-vs/vsmac2.png)

1. Wpisz "HelloWorld" **Nazwa projektu**. Wybierz **utworzyć**.

   ![Konfiguruj okno dialogowe nowego aplikacji konsoli](./media/using-on-mac-vs/vsmac3.png)

1. Zaczekaj, aż zostaną przywrócone zależności projektu. Projekt posiada pojedynczego pliku języka C#, *Program.cs*, zawierającego `Program` klasy z `Main` metody. `Console.WriteLine` Instrukcji dane wyjściowe obejmują "Witaj świecie!" w konsoli po uruchomieniu aplikacji.

   ![Otwórz okno główne z pliku Program.cs](./media/using-on-mac-vs/vsmac4.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

Uruchom aplikację w trybie debugowania z użyciem <kbd>F5</kbd> lub w trybie wersji z użyciem <kbd>CTRL</kbd>+<kbd>F5</kbd>.

![W okienku danych wyjściowych aplikacji zostaną wyświetlone Hello World!](./media/using-on-mac-vs/vsmac5.png)

## <a name="next-step"></a>Następny krok

[Tworzenia kompletnego rozwiązania .NET Core w macOS przy użyciu programu Visual Studio dla komputerów Mac](using-on-mac-vs-full-solution.md) temacie przedstawiono sposób tworzenia kompletnego rozwiązania .NET Core biblioteki do ponownego wykorzystania i testowania jednostek.
