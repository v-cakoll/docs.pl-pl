---
title: Rozpoczynanie pracy z platformą .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac
description: W tym temacie omówiono tworzenie prostej aplikacji konsolowej przy użyciu Visual Studio dla komputerów Mac i .NET Core.
author: mairaw
ms.date: 07/11/2019
ms.custom: seodec18
ms.openlocfilehash: ff508bbe8d72a88ea32adfbed984d4e9e8b8e7ca
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925828"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="1d63c-103">Rozpoczynanie pracy z platformą .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="1d63c-103">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="1d63c-104">Visual Studio dla komputerów Mac udostępnia w pełni funkcjonalne zintegrowane środowisko programistyczne (IDE) do tworzenia aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1d63c-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="1d63c-105">W tym temacie omówiono tworzenie prostej aplikacji konsolowej przy użyciu Visual Studio dla komputerów Mac i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1d63c-105">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="1d63c-106">Opinie są wysoce wyceniane.</span><span class="sxs-lookup"><span data-stu-id="1d63c-106">Your feedback is highly valued.</span></span> <span data-ttu-id="1d63c-107">Istnieją dwa sposoby przekazywania opinii zespołowi programistycznemu na Visual Studio dla komputerów Mac:</span><span class="sxs-lookup"><span data-stu-id="1d63c-107">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> * <span data-ttu-id="1d63c-108">W Visual Studio dla komputerów Mac wybierz pozycję **Pomoc** > **Zgłoś problem** z menu lub **Zgłoś problem** na ekranie powitalnym, co spowoduje otwarcie okna do zgłoszenia usterki.</span><span class="sxs-lookup"><span data-stu-id="1d63c-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="1d63c-109">Swoje opinie możesz śledzić w portalu [Społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="1d63c-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="1d63c-110">Aby skorzystać z sugestii, wybierz pozycję **Pomoc** > **Podaj sugestię** z menu lub **Podaj sugestię** na ekranie powitalnym, co spowoduje przejście do [strony internetowej społeczność deweloperów Visual Studio dla komputerów Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="1d63c-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1d63c-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="1d63c-111">Prerequisites</span></span>

<span data-ttu-id="1d63c-112">Zapoznaj się z tematem [wymagania wstępne dotyczące programu .NET Core w systemie Mac](../macos-prerequisites.md) .</span><span class="sxs-lookup"><span data-stu-id="1d63c-112">See the [Prerequisites for .NET Core on Mac](../macos-prerequisites.md) topic.</span></span>

<span data-ttu-id="1d63c-113">Sprawdź Przewodnik [obsługi .NET Core](https://docs.microsoft.com/visualstudio/mac/net-core-support?view=vsmac-2019) , aby upewnić się, że używasz obsługiwanej wersji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1d63c-113">Check the [.NET Core Support](https://docs.microsoft.com/visualstudio/mac/net-core-support?view=vsmac-2019) guide to ensure you're using a supported version of .NET Core.</span></span>

## <a name="get-started"></a><span data-ttu-id="1d63c-114">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="1d63c-114">Get started</span></span>

<span data-ttu-id="1d63c-115">Jeśli zainstalowano już wymagania wstępne i Visual Studio dla komputerów Mac, Pomiń tę sekcję i Kontynuuj, aby [utworzyć projekt](#creating-a-project).</span><span class="sxs-lookup"><span data-stu-id="1d63c-115">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="1d63c-116">Wykonaj następujące kroki, aby zainstalować wymagania wstępne i Visual Studio dla komputerów Mac:</span><span class="sxs-lookup"><span data-stu-id="1d63c-116">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="1d63c-117">Pobierz [instalatora Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="1d63c-117">Download the [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="1d63c-118">Uruchom Instalatora.</span><span class="sxs-lookup"><span data-stu-id="1d63c-118">Run the installer.</span></span> <span data-ttu-id="1d63c-119">Przeczytaj i zaakceptuj umowę licencyjną.</span><span class="sxs-lookup"><span data-stu-id="1d63c-119">Read and accept the license agreement.</span></span> <span data-ttu-id="1d63c-120">Podczas instalacji wybierz opcję zainstalowania platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1d63c-120">During the install, select the option to install .NET Core.</span></span> <span data-ttu-id="1d63c-121">Masz możliwość zainstalowania platformy Xamarin, wieloplatformowej technologii tworzenia aplikacji mobilnych.</span><span class="sxs-lookup"><span data-stu-id="1d63c-121">You're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="1d63c-122">Instalowanie programu Xamarin i powiązanych z nim składników jest opcjonalne w przypadku programowania w środowisku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1d63c-122">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="1d63c-123">Aby zapoznać się z procesem instalacji Visual Studio dla komputerów Mac, zobacz [dokumentację usługi Visual Studio dla komputerów Mac](/visualstudio/mac/).</span><span class="sxs-lookup"><span data-stu-id="1d63c-123">For a walk-through of the Visual Studio for Mac install process, see [Visual Studio for Mac documentation](/visualstudio/mac/).</span></span> <span data-ttu-id="1d63c-124">Po zakończeniu instalacji uruchom Visual Studio dla komputerów Mac IDE.</span><span class="sxs-lookup"><span data-stu-id="1d63c-124">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="1d63c-125">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="1d63c-125">Creating a project</span></span>

1. <span data-ttu-id="1d63c-126">W oknie uruchamiania wybierz pozycję **Nowy** .</span><span class="sxs-lookup"><span data-stu-id="1d63c-126">Select **New** on the Start Window.</span></span>

   ![Przycisk Nowy na ekranie startowym Visual Studio dla komputerów Mac](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. <span data-ttu-id="1d63c-128">W oknie dialogowym **Nowy projekt** wybierz pozycję **aplikacja** w węźle **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="1d63c-128">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="1d63c-129">Wybierz szablon **aplikacji konsolowej** , a następnie przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="1d63c-129">Select the **Console Application** template followed by **Next**.</span></span>

   ![Lista nowych szablonów projektu](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. <span data-ttu-id="1d63c-131">Jeśli masz zainstalowaną więcej niż jedną wersję programu .NET Core, Wybierz platformę docelową dla projektu.</span><span class="sxs-lookup"><span data-stu-id="1d63c-131">If you have more than one version of .NET Core installed, select the target framework for your project.</span></span>

1. <span data-ttu-id="1d63c-132">Wpisz "HelloWorld" dla **nazwy projektu**.</span><span class="sxs-lookup"><span data-stu-id="1d63c-132">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="1d63c-133">Wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="1d63c-133">Select **Create**.</span></span>

   ![Okno dialogowe Konfigurowanie nowej aplikacji konsolowej](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. <span data-ttu-id="1d63c-135">Zaczekaj na przywrócenie zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="1d63c-135">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="1d63c-136">Projekt ma C# jeden plik, *program.cs* `Program` , zawierający klasę z `Main` metodą.</span><span class="sxs-lookup"><span data-stu-id="1d63c-136">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="1d63c-137">`Console.WriteLine` Instrukcja zwróci wartość "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="1d63c-137">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="1d63c-138">do konsoli programu, gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="1d63c-138">to the console when the app is run.</span></span>

   ![Okno główne z otwartym plikiem Program.cs](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a><span data-ttu-id="1d63c-140">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="1d63c-140">Run the application</span></span>

<span data-ttu-id="1d63c-141">Uruchom aplikację w trybie debugowania za pomocą polecenia ⌘ ↵ (Command + Enter) lub w trybie wydania przy użyciu ⌥ ⌘ ↵ (Option + Command + Enter).</span><span class="sxs-lookup"><span data-stu-id="1d63c-141">Run the app in Debug mode using ⌘ ↵ (command + enter) or in Release mode using ⌥ ⌘ ↵ (option + command + enter).</span></span>

![W okienku danych wyjściowych aplikacji zostanie wyświetlona Hello world!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a><span data-ttu-id="1d63c-143">Następny krok</span><span class="sxs-lookup"><span data-stu-id="1d63c-143">Next step</span></span>

<span data-ttu-id="1d63c-144">[Tworzenie kompletnego rozwiązania .NET Core w systemie macOS za pomocą Visual Studio dla komputerów Mac](using-on-mac-vs-full-solution.md) tematu pokazuje, jak utworzyć kompletne rozwiązanie .NET Core, które obejmuje bibliotekę wielokrotnego użytku i testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="1d63c-144">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
