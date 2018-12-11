---
title: Wprowadzenie do platformy .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac
description: Ten temat przeprowadzi Cię przez tworzenie prostej aplikacji konsolowej przy użyciu programu Visual Studio dla komputerów Mac i .NET Core.
author: guardrex
ms.date: 06/12/2017
ms.custom: seodec18
ms.openlocfilehash: 471bdfdaa10b2d66c19177ae36b8bd18ce19e468
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169576"
---
# <a name="getting-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="12b42-103">Wprowadzenie do platformy .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="12b42-103">Getting started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="12b42-104">Visual Studio dla komputerów Mac udostępnia w pełni funkcjonalne rozwoju środowiska IDE (Integrated) do tworzenia aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="12b42-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="12b42-105">Ten temat przeprowadzi Cię przez tworzenie prostej aplikacji konsolowej przy użyciu programu Visual Studio dla komputerów Mac i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="12b42-105">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="12b42-106">Twoja opinia jest bardzo ważnych.</span><span class="sxs-lookup"><span data-stu-id="12b42-106">Your feedback is highly valued.</span></span> <span data-ttu-id="12b42-107">Istnieją dwa sposoby, możesz przekazywać opinie do zespołu programistycznego w programie Visual Studio dla komputerów Mac:</span><span class="sxs-lookup"><span data-stu-id="12b42-107">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
> * <span data-ttu-id="12b42-108">W programie Visual Studio dla komputerów Mac, wybierz **pomocy** > **Zgłoś Problem** z menu lub **Zgłoś Problem** na ekranie powitalnym, który spowoduje otwarcie okna dla Wypełniając raport o usterce.</span><span class="sxs-lookup"><span data-stu-id="12b42-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="12b42-109">Swoje opinie możesz śledzić w portalu [Społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="12b42-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="12b42-110">Aby sugestię, wybierz **pomocy** > **sugestię** z menu lub **sugestię** na ekranie powitalnym, co spowoduje przejście do [Programu visual Studio dla sieci Web społeczności deweloperów Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="12b42-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="12b42-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="12b42-111">Prerequisites</span></span>

<span data-ttu-id="12b42-112">Zobacz [wymagania wstępne dla platformy .NET Core w systemie Mac](../../core/macos-prerequisites.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="12b42-112">See the [Prerequisites for .NET Core on Mac](../../core/macos-prerequisites.md) topic.</span></span>

## <a name="getting-started"></a><span data-ttu-id="12b42-113">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="12b42-113">Getting started</span></span>

<span data-ttu-id="12b42-114">Po zainstalowaniu wymagań wstępnych i programu Visual Studio dla komputerów Mac, Pomiń tę sekcję i przejdź do [Tworzenie projektu](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="12b42-114">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="12b42-115">Wykonaj następujące kroki, aby zainstalować wstępnie wymagane składniki i programu Visual Studio dla komputerów Mac:</span><span class="sxs-lookup"><span data-stu-id="12b42-115">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="12b42-116">Pobierz [program Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="12b42-116">Download the [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span></span> <span data-ttu-id="12b42-117">Uruchom Instalatora.</span><span class="sxs-lookup"><span data-stu-id="12b42-117">Run the installer.</span></span> <span data-ttu-id="12b42-118">Przeczytaj i zaakceptuj umowę licencyjną.</span><span class="sxs-lookup"><span data-stu-id="12b42-118">Read and accept the license agreement.</span></span> <span data-ttu-id="12b42-119">Podczas instalacji otrzymasz możliwość instalacji Xamarin, technologii deweloperskich aplikacji mobilnych dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="12b42-119">During the install, you're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="12b42-120">Instalowanie środowiska Xamarin i jego składników powiązane jest opcjonalne dla programowania .NET Core.</span><span class="sxs-lookup"><span data-stu-id="12b42-120">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="12b42-121">Omówienie programu Visual Studio dla komputerów Mac, proces instalacji, zobacz [wprowadzenie do programu Visual Studio dla komputerów Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="12b42-121">For a walk-through of the Visual Studio for Mac install process, see [Introducing Visual Studio for Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/).</span></span> <span data-ttu-id="12b42-122">Po zakończeniu instalacji uruchom program Visual Studio dla komputerów Mac środowiska IDE.</span><span class="sxs-lookup"><span data-stu-id="12b42-122">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="12b42-123">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="12b42-123">Creating a project</span></span>

1. <span data-ttu-id="12b42-124">Wybierz **nowy projekt** na ekranie powitalnym.</span><span class="sxs-lookup"><span data-stu-id="12b42-124">Select **New Project** on the Welcome screen.</span></span>

   ![Przycisk Nowy projekt w programie Visual Studio dla komputerów Mac startowa](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. <span data-ttu-id="12b42-126">W **nowy projekt** okno dialogowe, wybierz opcję **aplikacji** w obszarze **platformy .NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="12b42-126">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="12b42-127">Wybierz **aplikację Konsolową** szablonu następuje **dalej**.</span><span class="sxs-lookup"><span data-stu-id="12b42-127">Select the **Console Application** template followed by **Next**.</span></span>

   ![Nowa lista szablonów projektu](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. <span data-ttu-id="12b42-129">Wpisz "nazwę HelloWorld" **nazwy projektu**.</span><span class="sxs-lookup"><span data-stu-id="12b42-129">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="12b42-130">Wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="12b42-130">Select **Create**.</span></span>

   ![Konfigurowanie nowego okna dialogowego aplikacji konsoli](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. <span data-ttu-id="12b42-132">Zaczekaj, aż zostaną przywrócone zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="12b42-132">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="12b42-133">Projekt ma jeden C# pliku *Program.cs*, zawierającego `Program` klasy `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="12b42-133">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="12b42-134">`Console.WriteLine` Instrukcji zwróci "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="12b42-134">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="12b42-135">w konsoli, gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="12b42-135">to the console when the app is run.</span></span>

   ![Otwórz okno główne z pliku Program.cs](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a><span data-ttu-id="12b42-137">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="12b42-137">Run the application</span></span>

<span data-ttu-id="12b42-138">Uruchom aplikację w trybie debugowania za pomocą <kbd>F5</kbd> lub w trybie wydania przy użyciu <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="12b42-138">Run the app in Debug mode using <kbd>F5</kbd> or in Release mode using <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>

![Pokazuje, w okienku dane wyjściowe aplikacji Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a><span data-ttu-id="12b42-140">Następny krok</span><span class="sxs-lookup"><span data-stu-id="12b42-140">Next step</span></span>

<span data-ttu-id="12b42-141">[Tworzenie kompletnego rozwiązania .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac](using-on-mac-vs-full-solution.md) temacie dowiesz się, jak tworzyć kompletnego rozwiązania .NET Core, który zawiera biblioteki wielokrotnego użytku i testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="12b42-141">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
