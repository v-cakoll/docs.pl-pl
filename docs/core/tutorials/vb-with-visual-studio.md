---
title: Tworzenie aplikacji Hello World przy użyciu platformy .NET Core i Visual Basic w programie Visual Studio 2017
description: Dowiedz się, jak utworzyć prostą aplikację konsoli .NET Core za pomocą Visual Basic w programie Visual Studio 2017.
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: d6b58e491b2857f83fe9b2e55ed35630c42b79ed
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45596533"
---
# <a name="build-a-visual-basic-hello-world-application-with-net-core-in-visual-studio-2017"></a><span data-ttu-id="5ca8a-103">Tworzenie aplikacji Visual Basic Hello World z platformą .NET Core w programie Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="5ca8a-103">Build a Visual Basic Hello World application with .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="5ca8a-104">Ten temat zawiera instrukcje krok po kroku wprowadzenie do tworzenia, debugowania i publikowania prostego aplikacji konsolowej .NET Core w języku Visual Basic w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-104">This topic provides a step-by-step introduction to building, debugging, and publishing a simple .NET Core console application using Visual Basic in Visual Studio 2017.</span></span> <span data-ttu-id="5ca8a-105">Program Visual Studio 2017 zapewnia środowisko projektowe w pełni funkcjonalne służące do tworzenia aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-105">Visual Studio 2017 provides a full-featured development environment for building .NET Core applications.</span></span> <span data-ttu-id="5ca8a-106">Tak długo, jak aplikacja nie ma zależności specyficzne dla platformy, aplikację można uruchomić na dowolnej platformie przeznaczonego platformy .NET Core i w każdym systemie, który ma zainstalowany .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-106">As long as the application doesn't have platform-specific dependencies, the application can run on any platform that .NET Core targets and on any system that has .NET Core installed.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5ca8a-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5ca8a-107">Prerequisites</span></span>

<span data-ttu-id="5ca8a-108">[Program Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core".</span><span class="sxs-lookup"><span data-stu-id="5ca8a-108">[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) with the ".NET Core cross-platform development" workload installed.</span></span> <span data-ttu-id="5ca8a-109">Można opracować aplikację przy użyciu platformy .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-109">You can develop your app with .NET Core 2.0.</span></span>

<span data-ttu-id="5ca8a-110">Aby uzyskać więcej informacji, zobacz [wymagania wstępne dla platformy .NET Core w Windows](../../core/windows-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="5ca8a-110">For more information, see [Prerequisites for .NET Core on Windows](../../core/windows-prerequisites.md).</span></span>

## <a name="a-simple-hello-world-application"></a><span data-ttu-id="5ca8a-111">Prostą aplikację typu Hello World</span><span class="sxs-lookup"><span data-stu-id="5ca8a-111">A simple Hello World application</span></span>

<span data-ttu-id="5ca8a-112">Rozpocznij od utworzenia prostej aplikacji konsoli "Hello World".</span><span class="sxs-lookup"><span data-stu-id="5ca8a-112">Begin by creating a simple "Hello World" console application.</span></span> <span data-ttu-id="5ca8a-113">Wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="5ca8a-113">Follow these steps:</span></span>

1. <span data-ttu-id="5ca8a-114">Uruchom program Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-114">Launch Visual Studio 2017.</span></span> <span data-ttu-id="5ca8a-115">Wybierz **pliku** > **New** > **projektu** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-115">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="5ca8a-116">W *nowy projekt*\* okno dialogowe, wybierz opcję **języka Visual Basic** węzła następuje **platformy .NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-116">In the *New Project*\* dialog, select the **Visual Basic** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="5ca8a-117">Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-117">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="5ca8a-118">W **nazwa** tekstu wpisz "nazwę HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="5ca8a-118">In the **Name** text box, type "HelloWorld".</span></span> <span data-ttu-id="5ca8a-119">Wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-119">Select the **OK** button.</span></span>

   ![Okno dialogowe nowego projektu za pomocą aplikacji Konsolowej wybrane](./media/vb-with-visual-studio/new-project.png)
   
1. <span data-ttu-id="5ca8a-121">Program Visual Studio używa tego szablonu do utworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-121">Visual Studio uses the template to create your project.</span></span> <span data-ttu-id="5ca8a-122">Szablon aplikacji konsoli Visual Basic dla platformy .NET Core automatycznie definiuje klasę, `Program`, z jednej metody `Main`, która przyjmuje <xref:System.String> tablic jako argumentu.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-122">The Visual Basic Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="5ca8a-123">`Main` jest punkt wejścia aplikacji, metody, która jest wywoływana automatycznie w czasie wykonywania po jej uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-123">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="5ca8a-124">Argumenty wiersza polecenia, dostarczana, gdy aplikacja zostanie uruchomiona, są dostępne w *args* tablicy.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-124">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Program Visual Studio i nowego projektu HelloWorld](./media/vb-with-visual-studio/devenv.png)

   <span data-ttu-id="5ca8a-126">Ten szablon tworzy prostą aplikację "Hello World".</span><span class="sxs-lookup"><span data-stu-id="5ca8a-126">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="5ca8a-127">Wywołuje <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodę w celu wyświetlenia literału ciągu "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="5ca8a-127">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="5ca8a-128">w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-128">in the console window.</span></span> <span data-ttu-id="5ca8a-129">Wybierając **HelloWorld** przycisk z zieloną strzałkę na pasku narzędzi, można uruchomić program w trybie debugowania.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-129">By selecting the **HelloWorld** button with the green arrow on the toolbar, you can run the program in Debug mode.</span></span> <span data-ttu-id="5ca8a-130">Jeśli to zrobisz, okno konsoli jest widoczna na interwał krótki czas przed jej zamknięciem.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-130">If you do, the console window is visible for only a brief time interval before it closes.</span></span> <span data-ttu-id="5ca8a-131">Dzieje się tak dlatego `Main` metoda kończy działanie i aplikacja kończy się najszybciej, jak pojedynczą instrukcję w `Main` metoda jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-131">This occurs because the `Main` method terminates and the application ends as soon as the single statement in the `Main` method executes.</span></span>

1. <span data-ttu-id="5ca8a-132">Aby spowodować, że aplikacja wstrzymać przed jej zamknięciem okna konsoli, Dodaj następujący kod bezpośrednio po wywołaniu <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metody:</span><span class="sxs-lookup"><span data-stu-id="5ca8a-132">To cause the application to pause before it closes the console window, add the following code immediately after the call to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method:</span></span>

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```
   <span data-ttu-id="5ca8a-133">Ten kod monituje użytkownika o naciśnij dowolny klawisz, a następnie zatrzymuje program, dopóki nie zostanie naciśnięty klawisz.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-133">This code prompts the user to press any key and then pauses the program until a key is pressed.</span></span>

1. <span data-ttu-id="5ca8a-134">Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-134">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="5ca8a-135">Program to kompilowany na język pośredni (IL), który jest konwertowany na kod binarny przez kompilator just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="5ca8a-135">This compiles your program into an intermediate language (IL) that's converted into binary code by a just-in-time (JIT) compiler.</span></span>

1. <span data-ttu-id="5ca8a-136">Uruchom program, wybierając **HelloWorld** przycisk z zieloną strzałkę na pasku narzędzi.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-136">Run the program by selecting the **HelloWorld** button with the green arrow on the toolbar.</span></span>

   ![Okno konsoli przedstawiający Hello World naciśnij dowolny klawisz, aby kontynuować](./media/with-visual-studio/helloworld1.png)

1. <span data-ttu-id="5ca8a-138">Naciśnij dowolny klawisz, aby zamknąć okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-138">Press any key to close the console window.</span></span>

## <a name="enhancing-the-hello-world-application"></a><span data-ttu-id="5ca8a-139">Udoskonalanie aplikacji Hello World</span><span class="sxs-lookup"><span data-stu-id="5ca8a-139">Enhancing the Hello World application</span></span>

<span data-ttu-id="5ca8a-140">Rozszerz aplikację, aby monitować użytkownika o jej nazwę i wyświetlić go wraz z daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-140">Enhance your application to prompt the user for his or her name and to display it along with the date and time.</span></span> <span data-ttu-id="5ca8a-141">Aby zmodyfikować i przetestować program, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5ca8a-141">To modify and test the program, do the following:</span></span>

1. <span data-ttu-id="5ca8a-142">Wprowadź następujący kod w języku Visual Basic w oknie kodu bezpośrednio po otwierającym, który następuje po `Sub Main(args As String())` wierszu i przed pierwszym nawiasem zamykającym:</span><span class="sxs-lookup"><span data-stu-id="5ca8a-142">Enter the following Visual Basic code in the code window immediately after the opening bracket that follows the `Sub Main(args As String())` line and before the first closing bracket:</span></span>

   [!code-vb[GettingStarted#1](../../../samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   <span data-ttu-id="5ca8a-143">Ten kod zastępuje istniejące <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, i <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-143">This code replaces the existing <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, and <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> statements.</span></span>

   ![Plik Visual Studio Program przy użyciu zaktualizowanych metody Main](./media/vb-with-visual-studio/codewindow.png)

   <span data-ttu-id="5ca8a-145">Ten kod wyświetla "Jak ma nazwę"?</span><span class="sxs-lookup"><span data-stu-id="5ca8a-145">This code displays "What is your name?"</span></span> <span data-ttu-id="5ca8a-146">w oknie konsoli i czeka, aż użytkownik wprowadza się ciąg, a następnie klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-146">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="5ca8a-147">Ten ciąg jest przechowywana w zmiennej o nazwie `name`.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-147">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="5ca8a-148">Pobiera również wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwość, która zawiera bieżący czas lokalny, a następnie przypisuje go do zmiennej o nazwie `currentDate`.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-148">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `currentDate`.</span></span> <span data-ttu-id="5ca8a-149">Na koniec używa [ciągiem interpolowanym](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) można wyświetlać te wartości w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-149">Finally, it uses an [interpolated string](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="5ca8a-150">Skompilować program, wybierając **kompilacji** > **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-150">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="5ca8a-151">Uruchom program w trybie debugowania w programie Visual Studio, wybierając zieloną strzałkę na pasku narzędzi, naciskając klawisz F5 lub wybierając pozycję **debugowania** > **Rozpocznij debugowanie** elementu menu.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-151">Run the program in Debug mode in Visual Studio by selecting the green arrow on the toolbar, pressing F5, or choosing the **Debug** > **Start Debugging** menu item.</span></span> <span data-ttu-id="5ca8a-152">Odpowiedzieć na monit podawania nazwy i naciskając klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-152">Respond to the prompt by entering a name and pressing the Enter key.</span></span>

   ![Okno konsoli z danych wyjściowych zmodyfikowane programu](./media/with-visual-studio/helloworld2.png)

1. <span data-ttu-id="5ca8a-154">Naciśnij dowolny klawisz, aby zamknąć okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-154">Press any key to close the console window.</span></span>

<span data-ttu-id="5ca8a-155">Został utworzony i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="5ca8a-155">You've created and run your application.</span></span> <span data-ttu-id="5ca8a-156">Tworzenie profesjonalnych aplikacji, należy wykonać dodatkowe kroki w celu przygotowania aplikacji do wersji:</span><span class="sxs-lookup"><span data-stu-id="5ca8a-156">To develop a professional application, take some additional steps to make your application ready for release:</span></span>

- <span data-ttu-id="5ca8a-157">Aby uzyskać informacje na temat debugowania aplikacji, zobacz [debugowania języka C# aplikacji Hello World w programie Visual Studio 2017](debugging-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="5ca8a-157">For information on debugging your application, see [Debugging your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md).</span></span>

- <span data-ttu-id="5ca8a-158">Aby uzyskać informacje na temat tworzenia i publikowania dystrybucyjny wersji aplikacji, zobacz [publikowania C# aplikacji Hello World w programie Visual Studio 2017](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="5ca8a-158">For information on developing and publishing a distributable version of your application, see [Publishing your C# Hello World application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

<!--
## Related topics

Instead of a console application, you can also build a class library with .NET Core and Visual Studio 2017. For a step-by-step introduction, see [Building a class library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md).

You can also develop a .NET Core console app on Mac, Linux, and Windows by using [Visual Studio Code](https://code.visualstudio.com/), a downloadable code editor. For a step-by-step tutorial, see [Getting Started with Visual Studio Code](with-visual-studio-code.md). -->
