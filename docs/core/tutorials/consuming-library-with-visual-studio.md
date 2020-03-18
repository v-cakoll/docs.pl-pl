---
title: Korzystanie z biblioteki .NET Standard w programie Visual Studio
description: Skompiluj aplikację .NET Core, która wywołuje członków innej biblioteki klas za pomocą programu Visual Studio 2019.
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4eb75f23359334ea483cba1498f1804c4b24c80c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920454"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="e9843-103">Korzystanie z biblioteki .NET Standard w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e9843-103">Consume a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="e9843-104">Po utworzeniu biblioteki klas .NET Standard przetestowano ją i skonstruowano wersję biblioteki, następnym krokiem jest udostępnienie jej obiektom wywołującym.</span><span class="sxs-lookup"><span data-stu-id="e9843-104">Once you've created a .NET Standard class library, tested it, and built a release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="e9843-105">Możesz to zrobić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="e9843-105">You can do this in two ways:</span></span>

- <span data-ttu-id="e9843-106">Jeśli biblioteka będzie używana przez pojedyncze rozwiązanie (na przykład, jeśli jest składnikiem w jednej dużej aplikacji), można dołączyć go jako projekt w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="e9843-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>
- <span data-ttu-id="e9843-107">Jeśli biblioteka będzie publicznie dostępna, można rozpowszechniać go jako pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="e9843-107">If the library will be publicly available, you can distribute it as a NuGet package.</span></span>

<span data-ttu-id="e9843-108">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="e9843-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="e9843-109">Dodaj aplikację konsoli do rozwiązania, które odwołuje się do projektu biblioteki standardu .NET.</span><span class="sxs-lookup"><span data-stu-id="e9843-109">Add a console app to your solution that references a .NET Standard library project.</span></span>
> - <span data-ttu-id="e9843-110">Utwórz pakiet NuGet zawierający projekt biblioteki standardów .NET.</span><span class="sxs-lookup"><span data-stu-id="e9843-110">Create a NuGet package that contains a .NET Standard library project.</span></span>

## <a name="add-a-console-app-to-your-solution"></a><span data-ttu-id="e9843-111">Dodawanie aplikacji konsoli do rozwiązania</span><span class="sxs-lookup"><span data-stu-id="e9843-111">Add a console app to your solution</span></span>

<span data-ttu-id="e9843-112">Podobnie jak w tym samym rozwiązaniu, co biblioteka klas, w [testowej bibliotece standardu .NET w programie Visual Studio,](testing-library-with-visual-studio.md)aplikacja może być dołączona jako część tego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="e9843-112">Just as you included unit tests in the same solution as your class library in [Test a .NET Standard library in Visual Studio](testing-library-with-visual-studio.md), you can include your application as part of that solution.</span></span> <span data-ttu-id="e9843-113">Na przykład można użyć biblioteki klas w aplikacji konsoli, która monituje użytkownika, aby wprowadzić ciąg i raporty, czy jego pierwszy znak jest wielkimi literami:</span><span class="sxs-lookup"><span data-stu-id="e9843-113">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

1. <span data-ttu-id="e9843-114">Otwórz `ClassLibraryProjects` rozwiązanie utworzone w artykule [Tworzenie biblioteki standardu .NET w](library-with-visual-studio.md) programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e9843-114">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="e9843-115">Dodaj do rozwiązania nową aplikację konsoli .NET Core o nazwie "ShowCase".</span><span class="sxs-lookup"><span data-stu-id="e9843-115">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="e9843-116">Kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratorze rozwiązań** i wybierz **polecenie Dodaj** > **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="e9843-116">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="e9843-117">Na stronie **Dodawanie nowego projektu** wprowadź **konsolę** w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="e9843-117">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="e9843-118">Wybierz **c#** lub **Visual Basic** z listy Język, a następnie wybierz pozycję Wszystkie **platformy** z listy Platforma.</span><span class="sxs-lookup"><span data-stu-id="e9843-118">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="e9843-119">Wybierz szablon **aplikacji konsoli (.NET Core),** a następnie wybierz pozycję **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="e9843-119">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="e9843-120">Na stronie **Konfigurowanie nowego projektu** wprowadź **pokaż sprawę** w polu **Nazwa projektu.**</span><span class="sxs-lookup"><span data-stu-id="e9843-120">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="e9843-121">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="e9843-121">Then, choose **Create**.</span></span>

1. <span data-ttu-id="e9843-122">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **ShowCase** i w menu kontekstowym wybierz polecenie **Ustaw jako projekt startup.**</span><span class="sxs-lookup"><span data-stu-id="e9843-122">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Menu kontekstowe projektu programu Visual Studio do ustawiania projektu startowego](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="e9843-124">Początkowo projekt nie ma dostępu do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="e9843-124">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="e9843-125">Aby zezwolić na wywoływanie metod w bibliotece klas, należy utworzyć odwołanie do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="e9843-125">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="e9843-126">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł `ShowCase` **Zależności** projektu i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="e9843-126">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Dodawanie menu kontekstowego odwołania w programie Visual Studio](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="e9843-128">W oknie dialogowym **Menedżer odwołań** wybierz pozycję **StringLibrary**, projekt biblioteki klas i wybierz przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="e9843-128">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Okno dialogowe Menedżera odwołań z zaznaczoną biblioteką ciągów](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="e9843-130">W oknie kodu pliku *Program.cs* lub *Program.vb* zastąp cały kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="e9843-130">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code:</span></span>

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="e9843-131">Kod używa `row` zmiennej do obsługi liczby wierszy danych zapisanych w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="e9843-131">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="e9843-132">Zawsze, gdy jest większa lub równa 25, kod czyści okno konsoli i wyświetla komunikat do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e9843-132">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="e9843-133">Program monituje użytkownika o wprowadzenie ciągu.</span><span class="sxs-lookup"><span data-stu-id="e9843-133">The program prompts the user to enter a string.</span></span> <span data-ttu-id="e9843-134">Wskazuje, czy ciąg zaczyna się od znaku wielkich liter.</span><span class="sxs-lookup"><span data-stu-id="e9843-134">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="e9843-135">Jeśli użytkownik naciśnie klawisz Enter bez wprowadzania ciągu, aplikacja się kończy, a okno konsoli zostanie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="e9843-135">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="e9843-136">W razie potrzeby zmień pasek narzędzi, aby skompilować wersję **debugowania** `ShowCase` projektu.</span><span class="sxs-lookup"><span data-stu-id="e9843-136">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="e9843-137">Skompiluj i uruchom program, wybierając zieloną strzałkę na przycisku **ShowCase.**</span><span class="sxs-lookup"><span data-stu-id="e9843-137">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Pasek narzędzi projektu programu Visual Studio z przyciskiem Debugowania](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

<span data-ttu-id="e9843-139">Można debugować i publikować aplikację korzystającą z tej biblioteki, wykonując kroki opisane w [debugowania aplikacji C# lub Visual Basic .NET Core Hello World przy użyciu programu Visual Studio](debugging-with-visual-studio.md) i [publikowania aplikacji .NET Core Hello World za pomocą programu Visual Studio](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="e9843-139">You can debug and publish the application that uses this library by following the steps in [Debug your C# or Visual Basic .NET Core Hello World application using Visual Studio](debugging-with-visual-studio.md) and [Publish your .NET Core Hello World application with Visual Studio](publishing-with-visual-studio.md).</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="e9843-140">Tworzenie pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="e9843-140">Create a NuGet package</span></span>

<span data-ttu-id="e9843-141">Można udostępnić biblioteki klas powszechnie dostępne przez opublikowanie go jako pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="e9843-141">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="e9843-142">Program Visual Studio nie obsługuje tworzenia pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="e9843-142">Visual Studio doesn't support the creation of NuGet packages.</span></span> <span data-ttu-id="e9843-143">Aby go utworzyć, należy użyć poleceń cli .NET Core:</span><span class="sxs-lookup"><span data-stu-id="e9843-143">To create one, you need to use the .NET Core CLI commands:</span></span>

1. <span data-ttu-id="e9843-144">Otwórz okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="e9843-144">Open a console window.</span></span>

   <span data-ttu-id="e9843-145">Na przykład wprowadź **wiersz polecenia** w polu wyszukiwania na pasku zadań systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e9843-145">For example, enter **Command Prompt** in the search box on the Windows task bar.</span></span> <span data-ttu-id="e9843-146">Wybierz aplikację **klasyczną Wiersz polecenia** lub naciśnij klawisz **Enter,** jeśli jest już zaznaczona w wynikach wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="e9843-146">Select the **Command Prompt** desktop app or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="e9843-147">Przejdź do katalogu projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="e9843-147">Navigate to your library's project directory.</span></span> <span data-ttu-id="e9843-148">Katalog zawiera kod źródłowy i plik projektu, *StringLibrary.csproj* lub *StringLibrary.vbproj*.</span><span class="sxs-lookup"><span data-stu-id="e9843-148">The directory contains your source code and a project file, *StringLibrary.csproj* or *StringLibrary.vbproj*.</span></span>

1. <span data-ttu-id="e9843-149">Uruchom polecenie [dotnet pack,](../tools/dotnet-pack.md) aby wygenerować pakiet z rozszerzeniem *.nupkg:*</span><span class="sxs-lookup"><span data-stu-id="e9843-149">Run the [dotnet pack](../tools/dotnet-pack.md) command to generate a package with a *.nupkg* extension:</span></span>

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > <span data-ttu-id="e9843-150">Jeśli katalog zawierający *program dotnet.exe* nie znajduje się w ścieżce, można znaleźć jego lokalizację, wprowadzając `where dotnet.exe` ją w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="e9843-150">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="e9843-151">Aby uzyskać więcej informacji na temat tworzenia pakietów NuGet, zobacz [Jak utworzyć pakiet NuGet za pomocą .NET Core CLI](../deploying/creating-nuget-packages.md).</span><span class="sxs-lookup"><span data-stu-id="e9843-151">For more information on creating NuGet packages, see [How to create a NuGet package with the .NET Core CLI](../deploying/creating-nuget-packages.md).</span></span>
