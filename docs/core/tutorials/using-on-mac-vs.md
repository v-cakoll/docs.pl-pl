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
# <a name="getting-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="412d8-103">Wprowadzenie do platformy .NET Core na macOS przy użyciu programu Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="412d8-103">Getting started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="412d8-104">Visual Studio for Mac zawiera kompletne programowanie środowiska IDE (Integrated) do tworzenia aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="412d8-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="412d8-105">W tym temacie przedstawiono tworzenie prostej aplikacji konsolowej przy użyciu programu Visual Studio for Mac i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="412d8-105">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="412d8-106">Twoja opinia jest bardzo ważnych.</span><span class="sxs-lookup"><span data-stu-id="412d8-106">Your feedback is highly valued.</span></span> <span data-ttu-id="412d8-107">Istnieją dwa sposoby można przekazywania informacji pozwalających na zespół deweloperów w programie Visual Studio dla komputerów Mac:</span><span class="sxs-lookup"><span data-stu-id="412d8-107">There are a two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
> * <span data-ttu-id="412d8-108">W programie Visual Studio dla komputerów Mac, wybierz **pomocy** > **zgłosić Problem** z menu lub **zgłosić Problem** na ekranie powitalnym, który zostanie otwarte okno dla składanie raport o usterce.</span><span class="sxs-lookup"><span data-stu-id="412d8-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="412d8-109">Swoje opinie możesz śledzić w portalu [Społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="412d8-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="412d8-110">Aby sugestię, wybierz **pomocy** > **Podaj sugestię** z menu lub **Podaj sugestię** na ekranie powitalnym, która spowoduje przejście do [Programu visual Studio for Mac UserVoice strony sieci Web](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).</span><span class="sxs-lookup"><span data-stu-id="412d8-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac UserVoice webpage](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="412d8-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="412d8-111">Prerequisites</span></span>

<span data-ttu-id="412d8-112">Zobacz [wymagania wstępne dotyczące .NET Core w systemie Mac](../../core/macos-prerequisites.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="412d8-112">See the [Prerequisites for .NET Core on Mac](../../core/macos-prerequisites.md) topic.</span></span>

## <a name="getting-started"></a><span data-ttu-id="412d8-113">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="412d8-113">Getting started</span></span>

<span data-ttu-id="412d8-114">Jeśli po zainstalowaniu wymagań wstępnych i Visual Studio dla komputerów Mac, Pomiń tę sekcję i przejdź do [tworzenia projektu](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="412d8-114">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="412d8-115">Wykonaj następujące kroki, aby zainstalować wstępnie wymagane składniki i Visual Studio dla komputerów Mac:</span><span class="sxs-lookup"><span data-stu-id="412d8-115">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="412d8-116">Pobierz [programu Visual Studio for Mac Instalatora](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="412d8-116">Download the [Visual Studio for Mac installer](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span> <span data-ttu-id="412d8-117">Uruchom Instalatora.</span><span class="sxs-lookup"><span data-stu-id="412d8-117">Run the installer.</span></span> <span data-ttu-id="412d8-118">Przeczytaj i zaakceptuj umowę licencyjną.</span><span class="sxs-lookup"><span data-stu-id="412d8-118">Read and accept the license agreement.</span></span> <span data-ttu-id="412d8-119">Podczas instalacji są podane możliwość Zainstaluj program Xamarin, technologii programowanie wieloplatformowych aplikacji mobilnych.</span><span class="sxs-lookup"><span data-stu-id="412d8-119">During the install, you're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="412d8-120">Instalowanie platformy Xamarin i jej powiązane składniki jest opcjonalne dla rozwoju platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="412d8-120">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="412d8-121">Omówienie programu Visual Studio for Mac proces instalacji, aby zapoznać [wprowadzenie do programu Visual Studio for Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="412d8-121">For a walk-through of the Visual Studio for Mac install process, see [Introducing Visual Studio for Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/).</span></span> <span data-ttu-id="412d8-122">Po zakończeniu instalacji uruchom program Visual Studio dla komputerów Mac IDE.</span><span class="sxs-lookup"><span data-stu-id="412d8-122">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="412d8-123">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="412d8-123">Creating a project</span></span>

1. <span data-ttu-id="412d8-124">Wybierz **nowy projekt** na ekranie powitalnym.</span><span class="sxs-lookup"><span data-stu-id="412d8-124">Select **New Project** on the Welcome screen.</span></span>

   ![Przycisk Nowy projekt w Visual Studio dla ekranu powitalnego Mac](./media/using-on-mac-vs/vsmac1.png)

1. <span data-ttu-id="412d8-126">W **nowy projekt** okno dialogowe, wybierz opcję **aplikacji** w obszarze **.NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="412d8-126">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="412d8-127">Wybierz **aplikacji konsoli** następuje szablonu **dalej**.</span><span class="sxs-lookup"><span data-stu-id="412d8-127">Select the **Console Application** template followed by **Next**.</span></span>

   ![Nowa lista szablonów projektu](./media/using-on-mac-vs/vsmac2.png)

1. <span data-ttu-id="412d8-129">Wpisz "HelloWorld" **Nazwa projektu**.</span><span class="sxs-lookup"><span data-stu-id="412d8-129">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="412d8-130">Wybierz **utworzyć**.</span><span class="sxs-lookup"><span data-stu-id="412d8-130">Select **Create**.</span></span>

   ![Konfiguruj okno dialogowe nowego aplikacji konsoli](./media/using-on-mac-vs/vsmac3.png)

1. <span data-ttu-id="412d8-132">Zaczekaj, aż zostaną przywrócone zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="412d8-132">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="412d8-133">Projekt posiada pojedynczego pliku języka C#, *Program.cs*, zawierającego `Program` klasy z `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="412d8-133">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="412d8-134">`Console.WriteLine` Instrukcji dane wyjściowe obejmują "Witaj świecie!"</span><span class="sxs-lookup"><span data-stu-id="412d8-134">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="412d8-135">w konsoli po uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="412d8-135">to the console when the app is run.</span></span>

   ![Otwórz okno główne z pliku Program.cs](./media/using-on-mac-vs/vsmac4.png)

## <a name="run-the-application"></a><span data-ttu-id="412d8-137">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="412d8-137">Run the application</span></span>

<span data-ttu-id="412d8-138">Uruchom aplikację w trybie debugowania z użyciem <kbd>F5</kbd> lub w trybie wersji z użyciem <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="412d8-138">Run the app in Debug mode using <kbd>F5</kbd> or in Release mode using <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>

![W okienku danych wyjściowych aplikacji zostaną wyświetlone Hello World!](./media/using-on-mac-vs/vsmac5.png)

## <a name="next-step"></a><span data-ttu-id="412d8-140">Następny krok</span><span class="sxs-lookup"><span data-stu-id="412d8-140">Next step</span></span>

<span data-ttu-id="412d8-141">[Tworzenia kompletnego rozwiązania .NET Core w macOS przy użyciu programu Visual Studio dla komputerów Mac](using-on-mac-vs-full-solution.md) temacie przedstawiono sposób tworzenia kompletnego rozwiązania .NET Core biblioteki do ponownego wykorzystania i testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="412d8-141">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
