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
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="bef7c-103">Rozpoczynanie pracy z platformą .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="bef7c-103">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="bef7c-104">Visual Studio dla komputerów Mac udostępnia w pełni funkcjonalne rozwoju środowiska IDE (Integrated) do tworzenia aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bef7c-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="bef7c-105">Ten temat przeprowadzi Cię przez tworzenie prostej aplikacji konsolowej przy użyciu programu Visual Studio dla komputerów Mac i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bef7c-105">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="bef7c-106">Twoja opinia jest bardzo ważnych.</span><span class="sxs-lookup"><span data-stu-id="bef7c-106">Your feedback is highly valued.</span></span> <span data-ttu-id="bef7c-107">Istnieją dwa sposoby, możesz przekazywać opinie do zespołu programistycznego w programie Visual Studio dla komputerów Mac:</span><span class="sxs-lookup"><span data-stu-id="bef7c-107">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
> * <span data-ttu-id="bef7c-108">W programie Visual Studio dla komputerów Mac, wybierz **pomocy** > **Zgłoś Problem** z menu lub **Zgłoś Problem** na ekranie powitalnym, który spowoduje otwarcie okna dla Wypełniając raport o usterce.</span><span class="sxs-lookup"><span data-stu-id="bef7c-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="bef7c-109">Swoje opinie możesz śledzić w portalu [Społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="bef7c-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="bef7c-110">Aby sugestię, wybierz **pomocy** > **sugestię** z menu lub **sugestię** na ekranie powitalnym, co spowoduje przejście do [Programu visual Studio dla sieci Web społeczności deweloperów Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="bef7c-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bef7c-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="bef7c-111">Prerequisites</span></span>

<span data-ttu-id="bef7c-112">Zobacz [wymagania wstępne dla platformy .NET Core w systemie Mac](../../core/macos-prerequisites.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="bef7c-112">See the [Prerequisites for .NET Core on Mac](../../core/macos-prerequisites.md) topic.</span></span>

<span data-ttu-id="bef7c-113">Sprawdź [Obsługa platformy .NET Core](https://docs.microsoft.com/visualstudio/mac/net-core-support?view=vsmac-2019) przewodnika, aby upewnić się, używasz obsługiwanej wersji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bef7c-113">Check the [.NET Core Support](https://docs.microsoft.com/visualstudio/mac/net-core-support?view=vsmac-2019) guide to ensure you're using a supported version of .NET Core.</span></span>

## <a name="get-started"></a><span data-ttu-id="bef7c-114">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="bef7c-114">Get started</span></span>

<span data-ttu-id="bef7c-115">Po zainstalowaniu wymagań wstępnych i programu Visual Studio dla komputerów Mac, Pomiń tę sekcję i przejdź do [Tworzenie projektu](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="bef7c-115">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="bef7c-116">Wykonaj następujące kroki, aby zainstalować wstępnie wymagane składniki i programu Visual Studio dla komputerów Mac:</span><span class="sxs-lookup"><span data-stu-id="bef7c-116">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="bef7c-117">Pobierz [program Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="bef7c-117">Download the [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="bef7c-118">Uruchom Instalatora.</span><span class="sxs-lookup"><span data-stu-id="bef7c-118">Run the installer.</span></span> <span data-ttu-id="bef7c-119">Przeczytaj i zaakceptuj umowę licencyjną.</span><span class="sxs-lookup"><span data-stu-id="bef7c-119">Read and accept the license agreement.</span></span> <span data-ttu-id="bef7c-120">Podczas instalacji wybierz opcję zainstalowania platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bef7c-120">During the install, select the option to install .NET Core.</span></span> <span data-ttu-id="bef7c-121">Otrzymasz możliwość instalacji Xamarin, technologii deweloperskich aplikacji mobilnych dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="bef7c-121">You're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="bef7c-122">Instalowanie środowiska Xamarin i jego składników powiązane jest opcjonalne dla programowania .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bef7c-122">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="bef7c-123">Omówienie programu Visual Studio dla komputerów Mac, proces instalacji, zobacz [program Visual Studio for Mac dokumentacji](/visualstudio/mac/).</span><span class="sxs-lookup"><span data-stu-id="bef7c-123">For a walk-through of the Visual Studio for Mac install process, see [Visual Studio for Mac documentation](/visualstudio/mac/).</span></span> <span data-ttu-id="bef7c-124">Po zakończeniu instalacji uruchom program Visual Studio dla komputerów Mac środowiska IDE.</span><span class="sxs-lookup"><span data-stu-id="bef7c-124">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="bef7c-125">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="bef7c-125">Creating a project</span></span>

1. <span data-ttu-id="bef7c-126">Wybierz **nowe** w oknie uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="bef7c-126">Select **New** on the Start Window.</span></span>

   ![Przycisk Nowy w programie Visual Studio do ekranu startowego komputerów Mac](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. <span data-ttu-id="bef7c-128">W **nowy projekt** okno dialogowe, wybierz opcję **aplikacji** w obszarze **platformy .NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="bef7c-128">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="bef7c-129">Wybierz **aplikację Konsolową** szablonu następuje **dalej**.</span><span class="sxs-lookup"><span data-stu-id="bef7c-129">Select the **Console Application** template followed by **Next**.</span></span>

   ![Nowa lista szablonów projektu](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. <span data-ttu-id="bef7c-131">Jeśli masz więcej niż jedna wersja programu .NET Core zainstalowany, wybierz platformę docelową dla projektu.</span><span class="sxs-lookup"><span data-stu-id="bef7c-131">If you have more than one version of .NET Core installed, select the target framework for your project.</span></span>

1. <span data-ttu-id="bef7c-132">Wpisz "nazwę HelloWorld" **nazwy projektu**.</span><span class="sxs-lookup"><span data-stu-id="bef7c-132">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="bef7c-133">Wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="bef7c-133">Select **Create**.</span></span>

   ![Konfigurowanie nowego okna dialogowego aplikacji konsoli](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. <span data-ttu-id="bef7c-135">Zaczekaj, aż zostaną przywrócone zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="bef7c-135">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="bef7c-136">Projekt ma jeden C# pliku *Program.cs*, zawierającego `Program` klasy `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="bef7c-136">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="bef7c-137">`Console.WriteLine` Instrukcji zwróci "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="bef7c-137">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="bef7c-138">w konsoli, gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="bef7c-138">to the console when the app is run.</span></span>

   ![Otwórz okno główne z pliku Program.cs](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a><span data-ttu-id="bef7c-140">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="bef7c-140">Run the application</span></span>

<span data-ttu-id="bef7c-141">Uruchom aplikację w trybie debugowania przy użyciu ⌘ ↵ (polecenie + enter) lub w trybie wydania przy użyciu ⌥ ⌘ ↵ (opcja + polecenia + enter).</span><span class="sxs-lookup"><span data-stu-id="bef7c-141">Run the app in Debug mode using ⌘ ↵ (command + enter) or in Release mode using ⌥ ⌘ ↵ (option + command + enter).</span></span>

![Pokazuje, w okienku dane wyjściowe aplikacji Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a><span data-ttu-id="bef7c-143">Następny krok</span><span class="sxs-lookup"><span data-stu-id="bef7c-143">Next step</span></span>

<span data-ttu-id="bef7c-144">[Tworzenie kompletnego rozwiązania .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac](using-on-mac-vs-full-solution.md) temacie dowiesz się, jak tworzyć kompletnego rozwiązania .NET Core, który zawiera biblioteki wielokrotnego użytku i testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="bef7c-144">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
