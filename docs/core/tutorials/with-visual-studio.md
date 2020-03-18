---
title: Tworzenie aplikacji Hello World z usługą .NET Core w programie Visual Studio
description: Dowiedz się, jak utworzyć pierwszą aplikację konsoli .NET Core z c# lub Visual Basic przy użyciu programu Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: ba996e4add1cfe44681154b00a6530b1f3e70b37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713996"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a><span data-ttu-id="c0bdb-103">Samouczek: Tworzenie pierwszej aplikacji konsoli .NET Core w programie Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="c0bdb-103">Tutorial: Create your first .NET Core console application in Visual Studio 2019</span></span>

<span data-ttu-id="c0bdb-104">Ten artykuł zawiera wprowadzenie krok po kroku do tworzenia i uruchamiania aplikacji konsoli Hello World .NET Core w programie Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-104">This article provides a step-by-step introduction to create and run a Hello World .NET Core console application in Visual Studio 2019.</span></span> <span data-ttu-id="c0bdb-105">Aplikacja Hello World jest tradycyjnie używana do wprowadzania początkujących do nowego języka programowania.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-105">A Hello World application is traditionally used to introduce beginners to a new programming language.</span></span> <span data-ttu-id="c0bdb-106">Ten program po prostu wyświetla wyrażenie "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="c0bdb-106">This program simply displays the phrase "Hello World!"</span></span> <span data-ttu-id="c0bdb-107">na ekranie.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-107">on the screen.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c0bdb-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c0bdb-108">Prerequisites</span></span>

- <span data-ttu-id="c0bdb-109">[Visual Studio 2019 w wersji 16.4 lub nowszej wersji](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem **programistycznym .NET Core.**</span><span class="sxs-lookup"><span data-stu-id="c0bdb-109">[Visual Studio 2019 version 16.4 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="c0bdb-110">Zestaw SDK .NET Core 3.1 jest instalowany automatycznie po wybraniu tego obciążenia.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-110">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

<span data-ttu-id="c0bdb-111">Aby uzyskać więcej informacji, zobacz [sekcję Instalowanie w programie Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) w artykule [Instalowanie sdk .NET Core SDK.](../install/sdk.md?pivots=os-windows)</span><span class="sxs-lookup"><span data-stu-id="c0bdb-111">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="c0bdb-112">Tworzymy aplikację.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-112">Create the app</span></span>

<span data-ttu-id="c0bdb-113">Poniższe instrukcje tworzą prostą aplikację konsoli Hello World:</span><span class="sxs-lookup"><span data-stu-id="c0bdb-113">The following instructions create a simple Hello World console application:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="c0bdb-114">C #</span><span class="sxs-lookup"><span data-stu-id="c0bdb-114">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="c0bdb-115">Otwórz Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-115">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="c0bdb-116">Utwórz nowy projekt aplikacji konsoli C# .NET Core o nazwie "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="c0bdb-116">Create a new C# .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="c0bdb-117">W oknie startowym wybierz pozycję **Utwórz nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-117">On the start window, choose **Create a new project**.</span></span>

      ![Tworzenie nowego przycisku projektu wybranego w oknie startowym programu Visual Studio](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="c0bdb-119">Na stronie **Tworzenie nowego projektu** wprowadź **konsolę** w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-119">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="c0bdb-120">Następnie wybierz **c#** z listy Język, a następnie wybierz **pozycję Wszystkie platformy** z listy Platforma.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-120">Next, choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="c0bdb-121">Wybierz szablon **aplikacji konsoli (.NET Core),** a następnie wybierz pozycję **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-121">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Tworzenie nowego okna projektu z zaznaczonymi filtrami](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="c0bdb-123">Jeśli nie widzisz szablonów .NET Core, prawdopodobnie brakuje wymaganego obciążenia zainstalowanego.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-123">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="c0bdb-124">W **Install more tools and features** **obszarze Nie znajdując tego, czego szukasz?**</span><span class="sxs-lookup"><span data-stu-id="c0bdb-124">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="c0bdb-125">Zostanie otwarty Instalator programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-125">The Visual Studio Installer opens.</span></span> <span data-ttu-id="c0bdb-126">Upewnij się, że masz zainstalowane obciążenie **programistyczne dla wielu platform .NET Core.**</span><span class="sxs-lookup"><span data-stu-id="c0bdb-126">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="c0bdb-127">Na stronie **Konfigurowanie nowego projektu** wprowadź **helloworld** w polu **Nazwa projektu.**</span><span class="sxs-lookup"><span data-stu-id="c0bdb-127">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="c0bdb-128">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-128">Then, choose **Create**.</span></span>

      ![Konfigurowanie nowego okna projektu za pomocą pól nazwa projektu, lokalizacja i nazwa rozwiązania](./media/with-visual-studio/configure-new-project.png)

   <span data-ttu-id="c0bdb-130">Szablon aplikacji konsoli C# dla .NET Core automatycznie `Program`definiuje klasę, `Main`z jedną <xref:System.String> metodą, przyjmuje tablicę jako argument.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-130">The C# Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="c0bdb-131">`Main`jest punktem wejścia aplikacji, metodą, która jest wywoływana automatycznie przez czas wykonywania po uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-131">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="c0bdb-132">Wszystkie argumenty wiersza polecenia podane po uruchomieniu aplikacji są dostępne w *tablicy args.*</span><span class="sxs-lookup"><span data-stu-id="c0bdb-132">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Visual Studio i nowy projekt HelloWorld](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basic"></a>[<span data-ttu-id="c0bdb-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c0bdb-134">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="c0bdb-135">Otwórz Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-135">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="c0bdb-136">Utwórz nowy projekt aplikacji konsoli programu Visual Basic .NET Core o nazwie "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="c0bdb-136">Create a new Visual Basic .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="c0bdb-137">W oknie startowym wybierz pozycję **Utwórz nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-137">On the start window, choose **Create a new project**.</span></span>

      ![Tworzenie nowego przycisku projektu wybranego w oknie startowym programu Visual Studio](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="c0bdb-139">Na stronie **Tworzenie nowego projektu** wprowadź **konsolę** w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-139">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="c0bdb-140">Następnie wybierz **visual basic** z listy Język, a następnie wybierz pozycję Wszystkie **platformy** z listy Platforma.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-140">Next, choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="c0bdb-141">Wybierz szablon **aplikacji konsoli (.NET Core),** a następnie wybierz pozycję **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-141">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Wybierz szablon języka Visual Basic dla aplikacji konsoli (.NET Framework)](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="c0bdb-143">Jeśli nie widzisz szablonów .NET Core, prawdopodobnie brakuje wymaganego obciążenia zainstalowanego.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-143">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="c0bdb-144">W **Install more tools and features** **obszarze Nie znajdując tego, czego szukasz?**</span><span class="sxs-lookup"><span data-stu-id="c0bdb-144">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="c0bdb-145">Zostanie otwarty Instalator programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-145">The Visual Studio Installer opens.</span></span> <span data-ttu-id="c0bdb-146">Upewnij się, że masz zainstalowane obciążenie **programistyczne dla wielu platform .NET Core.**</span><span class="sxs-lookup"><span data-stu-id="c0bdb-146">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="c0bdb-147">Na stronie **Konfigurowanie nowego projektu** wprowadź **helloworld** w polu **Nazwa projektu.**</span><span class="sxs-lookup"><span data-stu-id="c0bdb-147">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="c0bdb-148">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-148">Then, choose **Create**.</span></span>

   <span data-ttu-id="c0bdb-149">Szablon aplikacji konsoli dla programu .NET Core `Program`automatycznie definiuje klasę `Main`, z <xref:System.String> jedną metodą, która przyjmuje tablicę jako argument.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-149">The console app template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="c0bdb-150">`Main`jest punktem wejścia aplikacji, metodą, która jest wywoływana automatycznie przez czas wykonywania po uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-150">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="c0bdb-151">Wszystkie argumenty wiersza polecenia podane po uruchomieniu `args` aplikacji są dostępne w parametrze.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-151">Any command-line arguments supplied when the application is launched are available in the `args` parameter.</span></span>

   ![Visual Studio i nowy projekt HelloWorld](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   <span data-ttu-id="c0bdb-153">Szablon tworzy prostą aplikację "Hello World".</span><span class="sxs-lookup"><span data-stu-id="c0bdb-153">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="c0bdb-154">Wywołuje metodę, <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> aby wyświetlić ciąg literału "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="c0bdb-154">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="c0bdb-155">w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-155">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="c0bdb-156">Uruchomienie aplikacji</span><span class="sxs-lookup"><span data-stu-id="c0bdb-156">Run the app</span></span>

1. <span data-ttu-id="c0bdb-157">Aby uruchomić program, wybierz **helloworld** na pasku narzędzi lub naciśnij **klawisz F5**.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-157">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

   ![Pasek narzędzi programu Visual Studio z zaznaczonym przyciskiem uruchamiania HelloWorld](./media/with-visual-studio/run-program.png)

   <span data-ttu-id="c0bdb-159">Zostanie otwarte okno konsoli z tekstem "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="c0bdb-159">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="c0bdb-160">wydrukowane na ekranie i niektóre informacje debugowania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-160">printed on the screen and some Visual Studio debug information.</span></span>

   ![Okno konsoli z wyświetlonym klawiszem Hello World Naciśnij dowolny klawisz, aby kontynuować](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="c0bdb-162">Naciśnij dowolny klawisz, aby zamknąć okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-162">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="c0bdb-163">Ulepszanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="c0bdb-163">Enhance the app</span></span>

<span data-ttu-id="c0bdb-164">Popraw aplikację, aby monitować użytkownika o jego nazwę i wyświetlić ją wraz z datą i godziną.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-164">Enhance your application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="c0bdb-165">Poniższe instrukcje modyfikują i ponownie uruchamiają aplikację:</span><span class="sxs-lookup"><span data-stu-id="c0bdb-165">The following instructions modify and run the app again:</span></span>

# <a name="c"></a>[<span data-ttu-id="c0bdb-166">C #</span><span class="sxs-lookup"><span data-stu-id="c0bdb-166">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="c0bdb-167">Zamień zawartość `Main` metody, która jest obecnie tylko `Console.WriteLine`wiersz, który wywołuje , z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="c0bdb-167">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   <span data-ttu-id="c0bdb-168">Ten kod wyświetla "Jak się nazywasz?"</span><span class="sxs-lookup"><span data-stu-id="c0bdb-168">This code displays "What is your name?"</span></span> <span data-ttu-id="c0bdb-169">w oknie konsoli i czeka, aż użytkownik wejdzie ciąg, a następnie klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-169">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="c0bdb-170">Przechowuje ten ciąg w `name`zmiennej o nazwie .</span><span class="sxs-lookup"><span data-stu-id="c0bdb-170">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="c0bdb-171">Pobiera również wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości, która zawiera bieżący czas lokalny i przypisuje ją `date`do zmiennej o nazwie .</span><span class="sxs-lookup"><span data-stu-id="c0bdb-171">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="c0bdb-172">Na koniec używa [interpolowany ciąg](../../csharp/language-reference/tokens/interpolated.md) do wyświetlania tych wartości w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-172">Finally, it uses an [interpolated string](../../csharp/language-reference/tokens/interpolated.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="c0bdb-173">Skompiluj program, wybierając **rozwiązanie kompilacji .** > **Build Solution**</span><span class="sxs-lookup"><span data-stu-id="c0bdb-173">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="c0bdb-174">Aby uruchomić program, wybierz **helloworld** na pasku narzędzi lub naciśnij **klawisz F5**.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-174">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="c0bdb-175">Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz **Enter.**</span><span class="sxs-lookup"><span data-stu-id="c0bdb-175">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Okno konsoli ze zmodyfikowanym wyjściem programu](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="c0bdb-177">Naciśnij dowolny klawisz, aby zamknąć okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-177">Press any key to close the console window.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="c0bdb-178">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c0bdb-178">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="c0bdb-179">Zamień zawartość `Main` metody, która jest obecnie tylko `Console.WriteLine`wiersz, który wywołuje , z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="c0bdb-179">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   <span data-ttu-id="c0bdb-180">Ten kod wyświetla "Jak się nazywasz?"</span><span class="sxs-lookup"><span data-stu-id="c0bdb-180">This code displays "What is your name?"</span></span> <span data-ttu-id="c0bdb-181">w oknie konsoli i czeka, aż użytkownik wejdzie ciąg, a następnie klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-181">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="c0bdb-182">Przechowuje ten ciąg w `name`zmiennej o nazwie .</span><span class="sxs-lookup"><span data-stu-id="c0bdb-182">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="c0bdb-183">Pobiera również wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości, która zawiera bieżący czas lokalny i przypisuje ją `date`do zmiennej o nazwie .</span><span class="sxs-lookup"><span data-stu-id="c0bdb-183">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="c0bdb-184">Na koniec używa [interpolowany ciąg](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) do wyświetlania tych wartości w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-184">Finally, it uses an [interpolated string](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="c0bdb-185">Skompiluj program, wybierając **rozwiązanie kompilacji .** > **Build Solution**</span><span class="sxs-lookup"><span data-stu-id="c0bdb-185">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="c0bdb-186">Aby uruchomić program, wybierz **helloworld** na pasku narzędzi lub naciśnij **klawisz F5**.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-186">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="c0bdb-187">Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz **Enter.**</span><span class="sxs-lookup"><span data-stu-id="c0bdb-187">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Okno konsoli ze zmodyfikowanym wyjściem programu](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="c0bdb-189">Naciśnij dowolny klawisz, aby zamknąć okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-189">Press any key to close the console window.</span></span>

---

## <a name="next-steps"></a><span data-ttu-id="c0bdb-190">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="c0bdb-190">Next steps</span></span>

<span data-ttu-id="c0bdb-191">W tym artykule utworzono i uruchom i uruchom pierwszą aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-191">In this article, you've created and run your first .NET Core application.</span></span> <span data-ttu-id="c0bdb-192">W następnym kroku debugujesz aplikację.</span><span class="sxs-lookup"><span data-stu-id="c0bdb-192">In the next step, you debug your app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c0bdb-193">Debugowanie aplikacji .NET Core Hello World w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c0bdb-193">Debug a .NET Core Hello World application in Visual Studio</span></span>](debugging-with-visual-studio.md)
