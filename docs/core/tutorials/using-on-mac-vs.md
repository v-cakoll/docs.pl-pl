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
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="03793-103">Rozpoczynanie pracy z platformą .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="03793-103">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="03793-104">Visual Studio dla komputerów Mac udostępnia w pełni funkcjonalne zintegrowane środowisko programistyczne (IDE) do tworzenia aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="03793-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="03793-105">W tym artykule przedstawiono tworzenie prostej aplikacji konsoli przy użyciu programu Visual Studio dla komputerów Mac i programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="03793-105">This article walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="03793-106">Twoja opinia jest wysoko ceniona.</span><span class="sxs-lookup"><span data-stu-id="03793-106">Your feedback is highly valued.</span></span> <span data-ttu-id="03793-107">Istnieją dwa sposoby przekazywania informacji zwrotnych do zespołu programistów w programie Visual Studio dla komputerów Mac:</span><span class="sxs-lookup"><span data-stu-id="03793-107">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> * <span data-ttu-id="03793-108">W programie Visual Studio dla komputerów Mac wybierz pozycję > **Zgłoś problem** z menu lub **Zgłoś problem** na ekranie powitalnym, który otworzy okno do zgłoszenia raportu o błędzie. **Help**</span><span class="sxs-lookup"><span data-stu-id="03793-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="03793-109">Swoje opinie możesz śledzić w portalu [Społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="03793-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="03793-110">Aby przedstawić sugestię, wybierz **pozycję Pomóż** > **udostępnij sugestię** z menu lub **Podaj sugestię** z ekranu powitalnego, który zostanie przeniesiony do [strony społeczności programistów programu Visual Studio dla komputerów Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="03793-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="03793-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="03793-111">Prerequisites</span></span>

<span data-ttu-id="03793-112">Zobacz [.NET Core zależności i wymagania](../install/dependencies.md?pivots=os-macos) artykułu.</span><span class="sxs-lookup"><span data-stu-id="03793-112">See the [.NET Core dependencies and requirements](../install/dependencies.md?pivots=os-macos) article.</span></span>

<span data-ttu-id="03793-113">Sprawdź artykuł [pomocy technicznej programu .NET Core,](/visualstudio/mac/net-core-support) aby upewnić się, że używasz obsługiwanej wersji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="03793-113">Check the [.NET Core Support](/visualstudio/mac/net-core-support) article to ensure you're using a supported version of .NET Core.</span></span>

## <a name="get-started"></a><span data-ttu-id="03793-114">Rozpoczęcie pracy</span><span class="sxs-lookup"><span data-stu-id="03793-114">Get started</span></span>

<span data-ttu-id="03793-115">Jeśli masz już zainstalowane wymagania wstępne i visual studio dla komputerów Mac, pomiń tę sekcję i przejdź do [tworzenie projektu](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="03793-115">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="03793-116">Wykonaj następujące kroki, aby zainstalować wymagania wstępne i program Visual Studio dla komputerów Mac:</span><span class="sxs-lookup"><span data-stu-id="03793-116">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="03793-117">Pobierz [instalator programu Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="03793-117">Download the [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="03793-118">Uruchom instalatora.</span><span class="sxs-lookup"><span data-stu-id="03793-118">Run the installer.</span></span> <span data-ttu-id="03793-119">Przeczytaj i zaakceptuj umowę licencyjną.</span><span class="sxs-lookup"><span data-stu-id="03793-119">Read and accept the license agreement.</span></span> <span data-ttu-id="03793-120">Podczas instalacji wybierz opcję zainstalowania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="03793-120">During the install, select the option to install .NET Core.</span></span> <span data-ttu-id="03793-121">Masz możliwość zainstalowania xamarin, wieloplatformowej technologii tworzenia aplikacji mobilnych.</span><span class="sxs-lookup"><span data-stu-id="03793-121">You're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="03793-122">Instalowanie usługi Xamarin i powiązanych z nią składników jest opcjonalne dla rozwoju programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="03793-122">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="03793-123">Aby zapoznać się z procesem instalacji programu Visual Studio dla komputerów Mac, zobacz [Dokumentacja programu Visual Studio dla komputerów Mac](/visualstudio/mac/).</span><span class="sxs-lookup"><span data-stu-id="03793-123">For a walk-through of the Visual Studio for Mac install process, see [Visual Studio for Mac documentation](/visualstudio/mac/).</span></span> <span data-ttu-id="03793-124">Po zakończeniu instalacji uruchom program Visual Studio dla komputerów Mac IDE.</span><span class="sxs-lookup"><span data-stu-id="03793-124">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="03793-125">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="03793-125">Creating a project</span></span>

1. <span data-ttu-id="03793-126">Wybierz **pozycję Nowy** w oknie początkowym.</span><span class="sxs-lookup"><span data-stu-id="03793-126">Select **New** on the start window.</span></span>

   ![Nowy przycisk na ekranie startowym programu Visual Studio dla komputerów Mac](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. <span data-ttu-id="03793-128">W oknie dialogowym **Nowy projekt** wybierz **pozycję Aplikacja** w węźle **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="03793-128">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="03793-129">Wybierz szablon **Aplikacji konsoli,** po którym następuje **następny**.</span><span class="sxs-lookup"><span data-stu-id="03793-129">Select the **Console Application** template followed by **Next**.</span></span>

   ![Nowa lista szablonów projektów](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. <span data-ttu-id="03793-131">Jeśli zainstalowano więcej niż jedną wersję programu .NET Core, wybierz platformę docelową dla projektu.</span><span class="sxs-lookup"><span data-stu-id="03793-131">If you have more than one version of .NET Core installed, select the target framework for your project.</span></span>

1. <span data-ttu-id="03793-132">Wpisz "HelloWorld" dla **nazwy projektu**.</span><span class="sxs-lookup"><span data-stu-id="03793-132">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="03793-133">Wybierz **pozycję Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="03793-133">Select **Create**.</span></span>

   ![Konfigurowanie nowego okna dialogowego Aplikacja konsoli](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. <span data-ttu-id="03793-135">Poczekaj, aż zależności projektu zostaną przywrócone.</span><span class="sxs-lookup"><span data-stu-id="03793-135">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="03793-136">Projekt ma pojedynczy plik C# *Program.cs* `Program` , zawierający `Main` klasę z metodą.</span><span class="sxs-lookup"><span data-stu-id="03793-136">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="03793-137">Oświadczenie `Console.WriteLine` będzie wyprowadzać "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="03793-137">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="03793-138">do konsoli po uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="03793-138">to the console when the app is run.</span></span>

   ![Okno główne z otwartym plikiem Program.cs](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a><span data-ttu-id="03793-140">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="03793-140">Run the application</span></span>

<span data-ttu-id="03793-141">Uruchom aplikację w trybie debugowania za pomocą  ( polecenie + enter) lub w trybie zwalniania za pomocą   (opcja + polecenie + enter).</span><span class="sxs-lookup"><span data-stu-id="03793-141">Run the app in Debug mode using ⌘ ↵ (command + enter) or in Release mode using ⌥ ⌘ ↵ (option + command + enter).</span></span>

![Okienko Wyjście aplikacji pokazuje Hello World!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a><span data-ttu-id="03793-143">Następny krok</span><span class="sxs-lookup"><span data-stu-id="03793-143">Next step</span></span>

<span data-ttu-id="03793-144">[Tworzenie kompletnego rozwiązania .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac](using-on-mac-vs-full-solution.md) zawiera sposób tworzenia kompletnego rozwiązania .NET Core, które zawiera bibliotekę wielokrotnego użytku i testowanie jednostek.</span><span class="sxs-lookup"><span data-stu-id="03793-144">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
