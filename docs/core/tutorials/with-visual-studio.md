---
title: Tworzenie aplikacji Hello world przy użyciu platformy .NET Core w programie Visual Studio
description: Dowiedz się, jak utworzyć swoją pierwszą aplikację konsolową C# .NET Core z użyciem programu Visual Studio lub Visual Basic.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: ba996e4add1cfe44681154b00a6530b1f3e70b37
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713996"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a><span data-ttu-id="10c5f-103">Samouczek: Tworzenie pierwszej aplikacji konsolowej .NET Core w programie Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="10c5f-103">Tutorial: Create your first .NET Core console application in Visual Studio 2019</span></span>

<span data-ttu-id="10c5f-104">Ten artykuł zawiera instrukcje krok po kroku dotyczące tworzenia i Hello world uruchamiania aplikacji konsolowej programu .NET Core w programie Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="10c5f-104">This article provides a step-by-step introduction to create and run a Hello World .NET Core console application in Visual Studio 2019.</span></span> <span data-ttu-id="10c5f-105">Aplikacja Hello world jest tradycyjnie używana do wprowadzenia początkujących do nowego języka programowania.</span><span class="sxs-lookup"><span data-stu-id="10c5f-105">A Hello World application is traditionally used to introduce beginners to a new programming language.</span></span> <span data-ttu-id="10c5f-106">Ten program po prostu wyświetla frazę "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="10c5f-106">This program simply displays the phrase "Hello World!"</span></span> <span data-ttu-id="10c5f-107">na ekranie.</span><span class="sxs-lookup"><span data-stu-id="10c5f-107">on the screen.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="10c5f-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="10c5f-108">Prerequisites</span></span>

- <span data-ttu-id="10c5f-109">[Program Visual Studio 2019 w wersji 16,4 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym **wieloplatformowym obciążeniem programistycznym dla platformy .NET Core** .</span><span class="sxs-lookup"><span data-stu-id="10c5f-109">[Visual Studio 2019 version 16.4 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="10c5f-110">Zestaw .NET Core 3,1 SDK jest instalowany automatycznie po wybraniu tego obciążenia.</span><span class="sxs-lookup"><span data-stu-id="10c5f-110">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

<span data-ttu-id="10c5f-111">Aby uzyskać więcej informacji, zobacz sekcję [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) w artykule [Instalowanie zestaw .NET Core SDK](../install/sdk.md?pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="10c5f-111">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="10c5f-112">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="10c5f-112">Create the app</span></span>

<span data-ttu-id="10c5f-113">Poniższe instrukcje tworzą prostą aplikację konsolową Hello world:</span><span class="sxs-lookup"><span data-stu-id="10c5f-113">The following instructions create a simple Hello World console application:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[<span data-ttu-id="10c5f-114">C#</span><span class="sxs-lookup"><span data-stu-id="10c5f-114">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="10c5f-115">Open Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="10c5f-115">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="10c5f-116">Utwórz nowy C# projekt aplikacji konsoli .NET Core o nazwie "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="10c5f-116">Create a new C# .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="10c5f-117">W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="10c5f-117">On the start window, choose **Create a new project**.</span></span>

      ![Przycisk Utwórz nowy projekt wybrany w oknie uruchamiania programu Visual Studio](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="10c5f-119">Na stronie **Tworzenie nowego projektu** wprowadź w polu wyszukiwania **konsolę** .</span><span class="sxs-lookup"><span data-stu-id="10c5f-119">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="10c5f-120">Następnie wybierz **C#** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform.</span><span class="sxs-lookup"><span data-stu-id="10c5f-120">Next, choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="10c5f-121">Wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="10c5f-121">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Utwórz nowe okno projektu z wybranymi filtrami](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="10c5f-123">Jeśli nie widzisz szablonów .NET Core, prawdopodobnie brakuje wymaganego obciążenia.</span><span class="sxs-lookup"><span data-stu-id="10c5f-123">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="10c5f-124">W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** .</span><span class="sxs-lookup"><span data-stu-id="10c5f-124">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="10c5f-125">Zostanie otwarty Instalator programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="10c5f-125">The Visual Studio Installer opens.</span></span> <span data-ttu-id="10c5f-126">Upewnij się, że masz zainstalowaną **Międzyplatformowe obciążenie programistyczne dla platformy .NET Core** .</span><span class="sxs-lookup"><span data-stu-id="10c5f-126">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="10c5f-127">Na stronie **Konfiguruj nowy projekt** wprowadź **HelloWorld** w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="10c5f-127">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="10c5f-128">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="10c5f-128">Then, choose **Create**.</span></span>

      ![Skonfiguruj okno nowego projektu z nazwą projektu, lokalizacją i polami nazw rozwiązań](./media/with-visual-studio/configure-new-project.png)

   <span data-ttu-id="10c5f-130">Szablon C# aplikacji konsoli dla platformy .NET Core automatycznie definiuje klasę, `Program`przy użyciu pojedynczej metody `Main`, która przyjmuje tablicę <xref:System.String> jako argument.</span><span class="sxs-lookup"><span data-stu-id="10c5f-130">The C# Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="10c5f-131">`Main` jest punktem wejścia aplikacji, metoda, która jest wywoływana automatycznie przez środowisko uruchomieniowe podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="10c5f-131">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="10c5f-132">Wszystkie argumenty wiersza polecenia dostarczone podczas uruchamiania aplikacji są dostępne w tablicy *args* .</span><span class="sxs-lookup"><span data-stu-id="10c5f-132">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Program Visual Studio i nowy projekt HelloWorld](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basictabvb"></a>[<span data-ttu-id="10c5f-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10c5f-134">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="10c5f-135">Open Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="10c5f-135">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="10c5f-136">Utwórz Visual Basic nowy projekt aplikacji konsoli programu .NET Core o nazwie "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="10c5f-136">Create a new Visual Basic .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="10c5f-137">W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="10c5f-137">On the start window, choose **Create a new project**.</span></span>

      ![Przycisk Utwórz nowy projekt wybrany w oknie uruchamiania programu Visual Studio](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="10c5f-139">Na stronie **Tworzenie nowego projektu** wprowadź w polu wyszukiwania **konsolę** .</span><span class="sxs-lookup"><span data-stu-id="10c5f-139">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="10c5f-140">Następnie wybierz **Visual Basic** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform.</span><span class="sxs-lookup"><span data-stu-id="10c5f-140">Next, choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="10c5f-141">Wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="10c5f-141">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Wybierz szablon Visual Basic dla aplikacji konsolowej (.NET Framework)](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="10c5f-143">Jeśli nie widzisz szablonów .NET Core, prawdopodobnie brakuje wymaganego obciążenia.</span><span class="sxs-lookup"><span data-stu-id="10c5f-143">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="10c5f-144">W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** .</span><span class="sxs-lookup"><span data-stu-id="10c5f-144">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="10c5f-145">Zostanie otwarty Instalator programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="10c5f-145">The Visual Studio Installer opens.</span></span> <span data-ttu-id="10c5f-146">Upewnij się, że masz zainstalowaną **Międzyplatformowe obciążenie programistyczne dla platformy .NET Core** .</span><span class="sxs-lookup"><span data-stu-id="10c5f-146">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="10c5f-147">Na stronie **Konfiguruj nowy projekt** wprowadź **HelloWorld** w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="10c5f-147">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="10c5f-148">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="10c5f-148">Then, choose **Create**.</span></span>

   <span data-ttu-id="10c5f-149">Szablon aplikacji konsoli dla platformy .NET Core automatycznie definiuje klasę, `Program`przy użyciu pojedynczej metody `Main`, która przyjmuje tablicę <xref:System.String> jako argument.</span><span class="sxs-lookup"><span data-stu-id="10c5f-149">The console app template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="10c5f-150">`Main` jest punktem wejścia aplikacji, metoda, która jest wywoływana automatycznie przez środowisko uruchomieniowe podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="10c5f-150">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="10c5f-151">Wszystkie argumenty wiersza polecenia dostarczone podczas uruchamiania aplikacji są dostępne w parametrze `args`.</span><span class="sxs-lookup"><span data-stu-id="10c5f-151">Any command-line arguments supplied when the application is launched are available in the `args` parameter.</span></span>

   ![Program Visual Studio i nowy projekt HelloWorld](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   <span data-ttu-id="10c5f-153">Szablon tworzy prostą aplikację "Hello world".</span><span class="sxs-lookup"><span data-stu-id="10c5f-153">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="10c5f-154">Wywołuje metodę <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>, aby wyświetlić ciąg literału "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="10c5f-154">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="10c5f-155">w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="10c5f-155">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="10c5f-156">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="10c5f-156">Run the app</span></span>

1. <span data-ttu-id="10c5f-157">Aby uruchomić program, wybierz opcję **HelloWorld** na pasku narzędzi lub naciśnij klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="10c5f-157">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

   ![Pasek narzędzi programu Visual Studio z wybranym przyciskiem Uruchom jako HelloWorld](./media/with-visual-studio/run-program.png)

   <span data-ttu-id="10c5f-159">Zostanie otwarte okno konsoli z tekstem "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="10c5f-159">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="10c5f-160">Wydrukowano na ekranie i niektóre informacje debugowania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="10c5f-160">printed on the screen and some Visual Studio debug information.</span></span>

   ![Okno konsoli z pokazanymi Hello world naciśnij dowolny klawisz, aby kontynuować](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="10c5f-162">Naciśnij dowolny klawisz, aby zamknąć okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="10c5f-162">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="10c5f-163">Ulepszanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="10c5f-163">Enhance the app</span></span>

<span data-ttu-id="10c5f-164">Zwiększ swoją aplikację, aby monitować użytkownika o ich nazwę i wyświetlać ją wraz z datą i godziną.</span><span class="sxs-lookup"><span data-stu-id="10c5f-164">Enhance your application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="10c5f-165">Poniższe instrukcje modyfikują i uruchamiają aplikację ponownie:</span><span class="sxs-lookup"><span data-stu-id="10c5f-165">The following instructions modify and run the app again:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="10c5f-166">C#</span><span class="sxs-lookup"><span data-stu-id="10c5f-166">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="10c5f-167">Zastąp zawartość metody `Main`, która jest obecnie tylko linią, która wywołuje `Console.WriteLine`, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="10c5f-167">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   <span data-ttu-id="10c5f-168">Ten kod wyświetla "co to jest Twoja nazwa?"</span><span class="sxs-lookup"><span data-stu-id="10c5f-168">This code displays "What is your name?"</span></span> <span data-ttu-id="10c5f-169">w oknie konsoli i czeka, aż użytkownik wprowadzi ciąg, a następnie klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="10c5f-169">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="10c5f-170">Ten ciąg jest przechowywany w zmiennej o nazwie `name`.</span><span class="sxs-lookup"><span data-stu-id="10c5f-170">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="10c5f-171">Pobiera również wartość właściwości <xref:System.DateTime.Now?displayProperty=nameWithType>, która zawiera bieżący czas lokalny i przypisuje go do zmiennej o nazwie `date`.</span><span class="sxs-lookup"><span data-stu-id="10c5f-171">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="10c5f-172">Na koniec używa [ciągu interpolowanego](../../csharp/language-reference/tokens/interpolated.md) , aby wyświetlić te wartości w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="10c5f-172">Finally, it uses an [interpolated string](../../csharp/language-reference/tokens/interpolated.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="10c5f-173">Skompiluj program, wybierając opcję **kompiluj** > **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="10c5f-173">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="10c5f-174">Aby uruchomić program, wybierz opcję **HelloWorld** na pasku narzędzi lub naciśnij klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="10c5f-174">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="10c5f-175">Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz **Enter** .</span><span class="sxs-lookup"><span data-stu-id="10c5f-175">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Okno konsoli ze zmodyfikowanym wyjściem programu](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="10c5f-177">Naciśnij dowolny klawisz, aby zamknąć okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="10c5f-177">Press any key to close the console window.</span></span>

# <a name="visual-basictabvb"></a>[<span data-ttu-id="10c5f-178">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10c5f-178">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="10c5f-179">Zastąp zawartość metody `Main`, która jest obecnie tylko linią, która wywołuje `Console.WriteLine`, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="10c5f-179">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   <span data-ttu-id="10c5f-180">Ten kod wyświetla "co to jest Twoja nazwa?"</span><span class="sxs-lookup"><span data-stu-id="10c5f-180">This code displays "What is your name?"</span></span> <span data-ttu-id="10c5f-181">w oknie konsoli i czeka, aż użytkownik wprowadzi ciąg, a następnie klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="10c5f-181">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="10c5f-182">Ten ciąg jest przechowywany w zmiennej o nazwie `name`.</span><span class="sxs-lookup"><span data-stu-id="10c5f-182">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="10c5f-183">Pobiera również wartość właściwości <xref:System.DateTime.Now?displayProperty=nameWithType>, która zawiera bieżący czas lokalny i przypisuje go do zmiennej o nazwie `date`.</span><span class="sxs-lookup"><span data-stu-id="10c5f-183">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="10c5f-184">Na koniec używa [ciągu interpolowanego](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) , aby wyświetlić te wartości w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="10c5f-184">Finally, it uses an [interpolated string](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="10c5f-185">Skompiluj program, wybierając opcję **kompiluj** > **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="10c5f-185">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="10c5f-186">Aby uruchomić program, wybierz opcję **HelloWorld** na pasku narzędzi lub naciśnij klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="10c5f-186">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="10c5f-187">Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz **Enter** .</span><span class="sxs-lookup"><span data-stu-id="10c5f-187">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Okno konsoli ze zmodyfikowanym wyjściem programu](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="10c5f-189">Naciśnij dowolny klawisz, aby zamknąć okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="10c5f-189">Press any key to close the console window.</span></span>

---

## <a name="next-steps"></a><span data-ttu-id="10c5f-190">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="10c5f-190">Next steps</span></span>

<span data-ttu-id="10c5f-191">W tym artykule opisano tworzenie i uruchamianie pierwszej aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10c5f-191">In this article, you've created and run your first .NET Core application.</span></span> <span data-ttu-id="10c5f-192">W następnym kroku debugujesz aplikację.</span><span class="sxs-lookup"><span data-stu-id="10c5f-192">In the next step, you debug your app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="10c5f-193">Debugowanie aplikacji Hello world .NET Core w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="10c5f-193">Debug a .NET Core Hello World application in Visual Studio</span></span>](debugging-with-visual-studio.md)
