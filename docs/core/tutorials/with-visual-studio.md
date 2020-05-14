---
title: Tworzenie aplikacji Hello world przy użyciu platformy .NET Core w programie Visual Studio
description: Dowiedz się, jak utworzyć swoją pierwszą aplikację konsolową .NET Core za pomocą języka C# lub Visual Basic przy użyciu programu Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 738fc49a820c3c5d94fb35c1bf7a8b718ed75cb3
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394823"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a><span data-ttu-id="7a3bd-103">Samouczek: Tworzenie pierwszej aplikacji konsolowej .NET Core w programie Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="7a3bd-103">Tutorial: Create your first .NET Core console application in Visual Studio 2019</span></span>

<span data-ttu-id="7a3bd-104">Ten artykuł zawiera instrukcje krok po kroku dotyczące tworzenia i Hello world uruchamiania aplikacji konsolowej programu .NET Core w programie Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-104">This article provides a step-by-step introduction to create and run a Hello World .NET Core console application in Visual Studio 2019.</span></span> <span data-ttu-id="7a3bd-105">Aplikacja Hello world jest tradycyjnie używana do wprowadzenia początkujących do nowego języka programowania.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-105">A Hello World application is traditionally used to introduce beginners to a new programming language.</span></span> <span data-ttu-id="7a3bd-106">Ten program po prostu wyświetla frazę "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="7a3bd-106">This program simply displays the phrase "Hello World!"</span></span> <span data-ttu-id="7a3bd-107">na ekranie.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-107">on the screen.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7a3bd-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="7a3bd-108">Prerequisites</span></span>

- <span data-ttu-id="7a3bd-109">[Program Visual Studio 2019 w wersji 16,4 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym **wieloplatformowym obciążeniem programistycznym dla platformy .NET Core** .</span><span class="sxs-lookup"><span data-stu-id="7a3bd-109">[Visual Studio 2019 version 16.4 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="7a3bd-110">Zestaw .NET Core 3,1 SDK jest instalowany automatycznie po wybraniu tego obciążenia.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-110">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

<span data-ttu-id="7a3bd-111">Aby uzyskać więcej informacji, zobacz sekcję [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) w artykule [Instalowanie zestaw .NET Core SDK](../install/sdk.md?pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="7a3bd-111">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="7a3bd-112">Tworzymy aplikację.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-112">Create the app</span></span>

<span data-ttu-id="7a3bd-113">Poniższe instrukcje tworzą prostą aplikację konsolową Hello world:</span><span class="sxs-lookup"><span data-stu-id="7a3bd-113">The following instructions create a simple Hello World console application:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="7a3bd-114">C#</span><span class="sxs-lookup"><span data-stu-id="7a3bd-114">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="7a3bd-115">Otwórz program Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-115">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="7a3bd-116">Utwórz nowy projekt aplikacji konsolowej C# .NET Core o nazwie "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="7a3bd-116">Create a new C# .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="7a3bd-117">W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-117">On the start window, choose **Create a new project**.</span></span>

      ![Przycisk Utwórz nowy projekt wybrany w oknie uruchamiania programu Visual Studio](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="7a3bd-119">Na stronie **Tworzenie nowego projektu** wprowadź w polu wyszukiwania **konsolę** .</span><span class="sxs-lookup"><span data-stu-id="7a3bd-119">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="7a3bd-120">Następnie wybierz pozycję **C#** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-120">Next, choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="7a3bd-121">Wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-121">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Utwórz nowe okno projektu z wybranymi filtrami](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="7a3bd-123">Jeśli nie widzisz szablonów .NET Core, prawdopodobnie brakuje wymaganego obciążenia.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-123">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="7a3bd-124">W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** .</span><span class="sxs-lookup"><span data-stu-id="7a3bd-124">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="7a3bd-125">Zostanie otwarty Instalator programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-125">The Visual Studio Installer opens.</span></span> <span data-ttu-id="7a3bd-126">Upewnij się, że masz zainstalowaną **Międzyplatformowe obciążenie programistyczne dla platformy .NET Core** .</span><span class="sxs-lookup"><span data-stu-id="7a3bd-126">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="7a3bd-127">Na stronie **Konfiguruj nowy projekt** wprowadź **HelloWorld** w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="7a3bd-127">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="7a3bd-128">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-128">Then, choose **Create**.</span></span>

      ![Skonfiguruj okno nowego projektu z nazwą projektu, lokalizacją i polami nazw rozwiązań](./media/with-visual-studio/configure-new-project.png)

   <span data-ttu-id="7a3bd-130">Szablon aplikacji konsolowej w języku C# dla platformy .NET Core automatycznie definiuje klasę, `Program` przy użyciu pojedynczej metody, `Main` która przyjmuje <xref:System.String> tablicę jako argument.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-130">The C# Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="7a3bd-131">`Main`jest punktem wejścia aplikacji, metoda, która jest wywoływana automatycznie przez środowisko uruchomieniowe podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-131">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="7a3bd-132">Wszystkie argumenty wiersza polecenia dostarczone podczas uruchamiania aplikacji są dostępne w tablicy *args* .</span><span class="sxs-lookup"><span data-stu-id="7a3bd-132">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Program Visual Studio i nowy projekt HelloWorld](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basic"></a>[<span data-ttu-id="7a3bd-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a3bd-134">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="7a3bd-135">Otwórz program Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-135">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="7a3bd-136">Utwórz Visual Basic nowy projekt aplikacji konsoli programu .NET Core o nazwie "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="7a3bd-136">Create a new Visual Basic .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="7a3bd-137">W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-137">On the start window, choose **Create a new project**.</span></span>

      ![Przycisk Utwórz nowy projekt wybrany w oknie uruchamiania programu Visual Studio](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="7a3bd-139">Na stronie **Tworzenie nowego projektu** wprowadź w polu wyszukiwania **konsolę** .</span><span class="sxs-lookup"><span data-stu-id="7a3bd-139">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="7a3bd-140">Następnie wybierz **Visual Basic** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-140">Next, choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="7a3bd-141">Wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-141">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Wybierz szablon Visual Basic dla aplikacji konsolowej (.NET Framework)](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="7a3bd-143">Jeśli nie widzisz szablonów .NET Core, prawdopodobnie brakuje wymaganego obciążenia.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-143">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="7a3bd-144">W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** .</span><span class="sxs-lookup"><span data-stu-id="7a3bd-144">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="7a3bd-145">Zostanie otwarty Instalator programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-145">The Visual Studio Installer opens.</span></span> <span data-ttu-id="7a3bd-146">Upewnij się, że masz zainstalowaną **Międzyplatformowe obciążenie programistyczne dla platformy .NET Core** .</span><span class="sxs-lookup"><span data-stu-id="7a3bd-146">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="7a3bd-147">Na stronie **Konfiguruj nowy projekt** wprowadź **HelloWorld** w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="7a3bd-147">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="7a3bd-148">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-148">Then, choose **Create**.</span></span>

   <span data-ttu-id="7a3bd-149">Szablon aplikacji konsoli dla platformy .NET Core automatycznie definiuje klasę, `Program` przy użyciu pojedynczej metody, `Main` która przyjmuje <xref:System.String> tablicę jako argument.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-149">The console app template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="7a3bd-150">`Main`jest punktem wejścia aplikacji, metoda, która jest wywoływana automatycznie przez środowisko uruchomieniowe podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-150">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="7a3bd-151">Wszystkie argumenty wiersza polecenia dostarczone podczas uruchamiania aplikacji są dostępne w `args` parametrze.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-151">Any command-line arguments supplied when the application is launched are available in the `args` parameter.</span></span>

   ![Program Visual Studio i nowy projekt HelloWorld](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   <span data-ttu-id="7a3bd-153">Szablon tworzy prostą aplikację "Hello world".</span><span class="sxs-lookup"><span data-stu-id="7a3bd-153">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="7a3bd-154">Wywołuje <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodę w celu wyświetlenia ciągu literału "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="7a3bd-154">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="7a3bd-155">w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-155">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="7a3bd-156">Uruchomienie aplikacji</span><span class="sxs-lookup"><span data-stu-id="7a3bd-156">Run the app</span></span>

1. <span data-ttu-id="7a3bd-157">Aby uruchomić program, wybierz opcję **HelloWorld** na pasku narzędzi lub naciśnij klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-157">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

   ![Pasek narzędzi programu Visual Studio z wybranym przyciskiem Uruchom jako HelloWorld](./media/with-visual-studio/run-program.png)

   <span data-ttu-id="7a3bd-159">Zostanie otwarte okno konsoli z tekstem "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="7a3bd-159">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="7a3bd-160">Wydrukowano na ekranie i niektóre informacje debugowania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-160">printed on the screen and some Visual Studio debug information.</span></span>

   ![Okno konsoli z pokazanymi Hello world naciśnij dowolny klawisz, aby kontynuować](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="7a3bd-162">Naciśnij dowolny klawisz, aby zamknąć okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-162">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="7a3bd-163">Ulepszanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="7a3bd-163">Enhance the app</span></span>

<span data-ttu-id="7a3bd-164">Zwiększ swoją aplikację, aby monitować użytkownika o ich nazwę i wyświetlać ją wraz z datą i godziną.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-164">Enhance your application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="7a3bd-165">Poniższe instrukcje modyfikują i uruchamiają aplikację ponownie:</span><span class="sxs-lookup"><span data-stu-id="7a3bd-165">The following instructions modify and run the app again:</span></span>

# <a name="c"></a>[<span data-ttu-id="7a3bd-166">C#</span><span class="sxs-lookup"><span data-stu-id="7a3bd-166">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="7a3bd-167">Zastąp zawartość `Main` metody, która jest aktualnie tylko wierszem, który wywołuje `Console.WriteLine` , przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="7a3bd-167">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/HelloWorld.cs#1)]

   <span data-ttu-id="7a3bd-168">Ten kod wyświetla "co to jest Twoja nazwa?"</span><span class="sxs-lookup"><span data-stu-id="7a3bd-168">This code displays "What is your name?"</span></span> <span data-ttu-id="7a3bd-169">w oknie konsoli i czeka, aż użytkownik wprowadzi ciąg, a następnie klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-169">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="7a3bd-170">Ten ciąg jest przechowywany w zmiennej o nazwie `name` .</span><span class="sxs-lookup"><span data-stu-id="7a3bd-170">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="7a3bd-171">Pobiera również wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości, która zawiera bieżący czas lokalny i przypisuje go do zmiennej o nazwie `date` .</span><span class="sxs-lookup"><span data-stu-id="7a3bd-171">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="7a3bd-172">Na koniec używa [ciągu interpolowanego](../../csharp/language-reference/tokens/interpolated.md) , aby wyświetlić te wartości w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-172">Finally, it uses an [interpolated string](../../csharp/language-reference/tokens/interpolated.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="7a3bd-173">Skompiluj program, **wybierając opcję Kompiluj**  >  **kompilację rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-173">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="7a3bd-174">Aby uruchomić program, wybierz opcję **HelloWorld** na pasku narzędzi lub naciśnij klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-174">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="7a3bd-175">Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz **Enter** .</span><span class="sxs-lookup"><span data-stu-id="7a3bd-175">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Okno konsoli ze zmodyfikowanym wyjściem programu](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="7a3bd-177">Naciśnij dowolny klawisz, aby zamknąć okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-177">Press any key to close the console window.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="7a3bd-178">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a3bd-178">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="7a3bd-179">Zastąp zawartość `Main` metody, która jest aktualnie tylko wierszem, który wywołuje `Console.WriteLine` , przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="7a3bd-179">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/Program.vb#1)]

   <span data-ttu-id="7a3bd-180">Ten kod wyświetla "co to jest Twoja nazwa?"</span><span class="sxs-lookup"><span data-stu-id="7a3bd-180">This code displays "What is your name?"</span></span> <span data-ttu-id="7a3bd-181">w oknie konsoli i czeka, aż użytkownik wprowadzi ciąg, a następnie klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-181">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="7a3bd-182">Ten ciąg jest przechowywany w zmiennej o nazwie `name` .</span><span class="sxs-lookup"><span data-stu-id="7a3bd-182">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="7a3bd-183">Pobiera również wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości, która zawiera bieżący czas lokalny i przypisuje go do zmiennej o nazwie `date` .</span><span class="sxs-lookup"><span data-stu-id="7a3bd-183">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="7a3bd-184">Na koniec używa [ciągu interpolowanego](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) , aby wyświetlić te wartości w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-184">Finally, it uses an [interpolated string](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="7a3bd-185">Skompiluj program, **wybierając opcję Kompiluj**  >  **kompilację rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-185">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="7a3bd-186">Aby uruchomić program, wybierz opcję **HelloWorld** na pasku narzędzi lub naciśnij klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-186">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="7a3bd-187">Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz **Enter** .</span><span class="sxs-lookup"><span data-stu-id="7a3bd-187">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Okno konsoli ze zmodyfikowanym wyjściem programu](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="7a3bd-189">Naciśnij dowolny klawisz, aby zamknąć okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-189">Press any key to close the console window.</span></span>

---

## <a name="next-steps"></a><span data-ttu-id="7a3bd-190">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="7a3bd-190">Next steps</span></span>

<span data-ttu-id="7a3bd-191">W tym artykule opisano tworzenie i uruchamianie pierwszej aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-191">In this article, you've created and run your first .NET Core application.</span></span> <span data-ttu-id="7a3bd-192">W następnym kroku debugujesz aplikację.</span><span class="sxs-lookup"><span data-stu-id="7a3bd-192">In the next step, you debug your app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7a3bd-193">Debugowanie aplikacji Hello world .NET Core w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7a3bd-193">Debug a .NET Core Hello World application in Visual Studio</span></span>](debugging-with-visual-studio.md)
