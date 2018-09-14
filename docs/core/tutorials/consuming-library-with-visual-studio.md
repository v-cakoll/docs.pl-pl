---
title: Korzystanie z biblioteki .NET Standard w programie Visual Studio 2017
description: Dowiedz się, jak wywołać składowe w bibliotece klas w programie Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 06/05/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 52ec46c23bb928b49f034270ed1d510d1acf992e
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45518168"
---
# <a name="consuming-a-net-standard-library-in-visual-studio-2017"></a><span data-ttu-id="d3de6-103">Korzystanie z biblioteki .NET Standard w programie Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d3de6-103">Consuming a .NET Standard library in Visual Studio 2017</span></span>

<span data-ttu-id="d3de6-104">Po utworzeniu biblioteki klas .NET Standard, wykonując kroki opisane w [tworzenia biblioteki klas C# za pomocą programu .NET Core w programie Visual Studio 2017](./library-with-visual-studio.md) lub [Tworzenie biblioteki klas w języku Visual Basic z platformą .NET Core w programie Visual Studio 2017 ](vb-library-with-visual-studio.md), przetestowane w [testowanie biblioteki klas w języku .NET Core w programie Visual Studio 2017](testing-library-with-visual-studio.md), a wbudowane wersji biblioteki, następnym krokiem jest być udostępniana dla kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="d3de6-104">Once you've created a .NET Standard class library by following the steps in [Building a C# class library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) or [Building a Visual Basic class library with .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md), tested it in [Testing a class library with .NET Core in Visual Studio 2017](testing-library-with-visual-studio.md), and built a Release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="d3de6-105">Można to zrobić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="d3de6-105">You can do this in two ways:</span></span>

* <span data-ttu-id="d3de6-106">Jeśli biblioteka będzie używany przez jedno rozwiązanie (na przykład, jeśli jest on składnikiem w jednej aplikacji duże), możesz dołączyć go jako projekt w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="d3de6-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>

* <span data-ttu-id="d3de6-107">Jeśli biblioteka będzie ogólnie dostępna, można rozprowadzić ją jako pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="d3de6-107">If the library will be generally accessible, you can distribute it as a NuGet package.</span></span>

## <a name="including-a-library-as-a-project-in-a-solution"></a><span data-ttu-id="d3de6-108">W tym bibliotekę jako projekt w rozwiązaniu</span><span class="sxs-lookup"><span data-stu-id="d3de6-108">Including a library as a project in a solution</span></span>

<span data-ttu-id="d3de6-109">Tak, jak testy jednostkowe są zawarte w tym samym rozwiązaniu jako biblioteki klas, można umieścić aplikację w ramach tego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d3de6-109">Just as you included unit tests in the same solution as your class library, you can include your application as part of that solution.</span></span> <span data-ttu-id="d3de6-110">Na przykład można użyć biblioteki klas w aplikacji konsoli, który monituje użytkownika o podanie ciągu i raporty, czy jego pierwszy znak jest wielką literą:</span><span class="sxs-lookup"><span data-stu-id="d3de6-110">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="d3de6-111">C#</span><span class="sxs-lookup"><span data-stu-id="d3de6-111">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="d3de6-112">Otwórz `ClassLibraryProjects` rozwiązanie utworzone w [tworzenia biblioteki klas C# za pomocą programu .NET Core w programie Visual Studio 2017](./library-with-visual-studio.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="d3de6-112">Open the `ClassLibraryProjects` solution you created in the [Building a C# Class Library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="d3de6-113">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ClassLibraryProjects** rozwiązań i wybierz pozycję **Dodaj** > **nowy projekt** z menu kontekstowe.</span><span class="sxs-lookup"><span data-stu-id="d3de6-113">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="d3de6-114">W **Dodaj nowy projekt** okna dialogowego, rozwiń węzeł **Visual C#** a następnie wybierz węzeł **platformy .NET Core** węzła następuje **Aplikacja konsoli (.NET Core)** szablon projektu.</span><span class="sxs-lookup"><span data-stu-id="d3de6-114">In the **Add New Project** dialog, expand the **Visual C#** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="d3de6-115">W **nazwa** pole tekstowe, wpisz "Pokaz", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d3de6-115">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Dodaj okno dialogowe Nowy projekt](./media/consuming-library-with-visual-studio/addnewproject.png)

1. <span data-ttu-id="d3de6-117">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **pokaz** projektu, a następnie wybierz **Ustaw jako projekt startowy** w menu kontekstowym.</span><span class="sxs-lookup"><span data-stu-id="d3de6-117">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span> 

   ![Menu kontekstowe pokaz](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. <span data-ttu-id="d3de6-119">Początkowo projektu nie ma dostępu do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="d3de6-119">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="d3de6-120">Aby umożliwić go do wywoływania metody w bibliotece klasy, należy utworzyć odwołanie do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="d3de6-120">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="d3de6-121">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `ShowCase` projektu **zależności** a następnie wybierz węzeł **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="d3de6-121">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Menu kontekstowe zależności pokaz](./media/consuming-library-with-visual-studio/addreference.png)

1. <span data-ttu-id="d3de6-123">W **Menadżer odwołań** okno dialogowe, wybierz opcję **StringLibrary**, projekt biblioteki klas, a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d3de6-123">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Menadżer odwołań](./media/consuming-library-with-visual-studio/referencemanager.png)

1. <span data-ttu-id="d3de6-125">W oknie kodu *Program.cs* pliku, Zastąp cały kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="d3de6-125">In the code window for the *Program.cs* file, replace all of the code with the following code:</span></span>

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   <span data-ttu-id="d3de6-126">Kod używa `row` zmiennej do utrzymywania licznika liczby wierszy danych zapisanych w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="d3de6-126">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="d3de6-127">Zawsze, gdy jest mniejsza niż 25, kod Czyści okno konsoli i zostanie wyświetlony komunikat dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d3de6-127">Whenever it is greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="d3de6-128">Monituje użytkownika o podanie ciągu.</span><span class="sxs-lookup"><span data-stu-id="d3de6-128">The program prompts the user to enter a string.</span></span> <span data-ttu-id="d3de6-129">Oznacza to, czy ciąg rozpoczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="d3de6-129">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="d3de6-130">Gdy użytkownik naciśnie klawisz Enter, bez konieczności wprowadzania ciągu, kończy działanie aplikacji i zamyka okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="d3de6-130">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="d3de6-131">W razie potrzeby zmień narzędzi do kompilowania **debugowania** wersji `ShowCase` projektu.</span><span class="sxs-lookup"><span data-stu-id="d3de6-131">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="d3de6-132">Skompilować i uruchomić program, wybierając zieloną strzałkę na **pokaz** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d3de6-132">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Obraz](./media/consuming-library-with-visual-studio/toolbar.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="d3de6-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3de6-134">Visual Basic</span></span>](#tab/visual-basic)
1. <span data-ttu-id="d3de6-135">Otwórz `ClassLibraryProjects` rozwiązanie utworzone w [tworzenia klasy biblioteki w języku Visual Basic i .NET Core w programie Visual Studio 2017](vb-library-with-visual-studio.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="d3de6-135">Open the `ClassLibraryProjects` solution you created in the [Building a class Library with Visual Basic and .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="d3de6-136">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ClassLibraryProjects** rozwiązań i wybierz pozycję **Dodaj** > **nowy projekt** z menu kontekstowe.</span><span class="sxs-lookup"><span data-stu-id="d3de6-136">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="d3de6-137">W **Dodaj nowy projekt** okna dialogowego, rozwiń węzeł **języka Visual Basic** a następnie wybierz węzeł **platformy .NET Core** węzła następuje **Aplikacja konsoli (.NET Core)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="d3de6-137">In the **Add New Project** dialog, expand the **Visual Basic** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="d3de6-138">W **nazwa** pole tekstowe, wpisz "Pokaz", a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d3de6-138">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Dodaj okno dialogowe Nowy projekt](./media/consuming-library-with-visual-studio/vb-addnewproject.png)

1. <span data-ttu-id="d3de6-140">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **pokaz** projektu, a następnie wybierz **Ustaw jako projekt startowy** w menu kontekstowym.</span><span class="sxs-lookup"><span data-stu-id="d3de6-140">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span> 

   ![Menu kontekstowe pokaz](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. <span data-ttu-id="d3de6-142">Początkowo projektu nie ma dostępu do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="d3de6-142">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="d3de6-143">Aby umożliwić go do wywoływania metody w bibliotece klasy, należy utworzyć odwołanie do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="d3de6-143">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="d3de6-144">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `ShowCase` projektu **zależności** a następnie wybierz węzeł **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="d3de6-144">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Menu kontekstowe zależności pokaz](./media/consuming-library-with-visual-studio/addreference.png)

1. <span data-ttu-id="d3de6-146">W **Menadżer odwołań** okno dialogowe, wybierz opcję **StringLibrary**, projekt biblioteki klas, a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d3de6-146">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Menadżer odwołań](./media/consuming-library-with-visual-studio/referencemanager.png)

1. <span data-ttu-id="d3de6-148">W oknie kodu *Program.vb* pliku, Zastąp cały kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="d3de6-148">In the code window for the *Program.vb* file, replace all of the code with the following code:</span></span>

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="d3de6-149">Kod używa `row` zmiennej do utrzymywania licznika liczby wierszy danych zapisanych w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="d3de6-149">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="d3de6-150">Zawsze, gdy jest mniejsza niż 25, kod Czyści okno konsoli i zostanie wyświetlony komunikat dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d3de6-150">Whenever it is greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="d3de6-151">Monituje użytkownika o podanie ciągu.</span><span class="sxs-lookup"><span data-stu-id="d3de6-151">The program prompts the user to enter a string.</span></span> <span data-ttu-id="d3de6-152">Oznacza to, czy ciąg rozpoczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="d3de6-152">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="d3de6-153">Gdy użytkownik naciśnie klawisz Enter, bez konieczności wprowadzania ciągu, kończy działanie aplikacji i zamyka okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="d3de6-153">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="d3de6-154">W razie potrzeby zmień narzędzi do kompilowania **debugowania** wersji `ShowCase` projektu.</span><span class="sxs-lookup"><span data-stu-id="d3de6-154">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="d3de6-155">Skompilować i uruchomić program, wybierając zieloną strzałkę na **pokaz** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d3de6-155">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Obraz](./media/consuming-library-with-visual-studio/toolbar.png)
---

<span data-ttu-id="d3de6-157">Możesz debugować i publikować aplikacji, która korzysta z tej biblioteki, wykonując kroki opisane w [debugowanie aplikacji Hello World w programie Visual Studio 2017](debugging-with-visual-studio.md) i [publikowanie aplikacji Hello World z programem Visual Studio 2017](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="d3de6-157">You can debug and publish the application that uses this library by following the steps in [Debugging your Hello World application with Visual Studio 2017](debugging-with-visual-studio.md) and [Publishing your Hello World Application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

## <a name="distributing-the-library-in-a-nuget-package"></a><span data-ttu-id="d3de6-158">Dystrybucja biblioteki w pakiecie NuGet</span><span class="sxs-lookup"><span data-stu-id="d3de6-158">Distributing the library in a NuGet package</span></span>

<span data-ttu-id="d3de6-159">Można udostępnić biblioteki klas powszechnie przez opublikowanie go jako pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="d3de6-159">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="d3de6-160">Program Visual Studio nie obsługuje tworzenia pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="d3de6-160">Visual Studio does not support the creation of NuGet packages.</span></span> <span data-ttu-id="d3de6-161">Aby utworzyć, należy użyć [ `dotnet` narzędzia wiersza polecenia](../../core/tools/dotnet.md):</span><span class="sxs-lookup"><span data-stu-id="d3de6-161">To create one, you use the [`dotnet` command line utility](../../core/tools/dotnet.md):</span></span>

1. <span data-ttu-id="d3de6-162">Otwórz okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="d3de6-162">Open a console window.</span></span> <span data-ttu-id="d3de6-163">Na przykład w **Zadaj mi dowolne pytanie** tekstu pola na pasku zadań Windows, należy wprowadzić `Command Prompt` (lub `cmd` w skrócie) i Otwórz okno konsoli wybierając **wiersza polecenia** aplikacji klasycznej lub jeśli została wybrana w wynikach wyszukiwania, naciskając klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="d3de6-163">For example in the **Ask me anything** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="d3de6-164">Przejdź do katalogu projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="d3de6-164">Navigate to your library's project directory.</span></span> <span data-ttu-id="d3de6-165">O ile nie został ponownie skonfigurowany lokalizacji pliku typowe, jest on *2017\Projects\ClassLibraryProjects\StringLibrary Documents\Visual Studio* katalogu.</span><span class="sxs-lookup"><span data-stu-id="d3de6-165">Unless you've reconfigured the typical file location, it's in the *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* directory.</span></span> <span data-ttu-id="d3de6-166">Katalog zawiera kod źródłowy i plik projektu *StringLibrary.csproj*.</span><span class="sxs-lookup"><span data-stu-id="d3de6-166">The directory contains your source code and a project file, *StringLibrary.csproj*.</span></span>

1. <span data-ttu-id="d3de6-167">Należy wydać polecenie `dotnet pack --no-build`.</span><span class="sxs-lookup"><span data-stu-id="d3de6-167">Issue the command `dotnet pack --no-build`.</span></span> <span data-ttu-id="d3de6-168">`dotnet` Narzędzie generuje pakiet z *.nupkg* rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="d3de6-168">The `dotnet` utility generates a package with a *.nupkg* extension.</span></span>

   > [!TIP]
   > <span data-ttu-id="d3de6-169">Jeśli katalog, który zawiera *dotnet.exe* jest nie w ŚCIEŻCE, można znaleźć lokalizacji, wprowadzając `where dotnet.exe` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="d3de6-169">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="d3de6-170">Aby uzyskać więcej informacji na temat tworzenia pakietów NuGet, zobacz [jak utworzyć pakiet NuGet za pomocą wielu narzędzi platformy](../../core/deploying/creating-nuget-packages.md).</span><span class="sxs-lookup"><span data-stu-id="d3de6-170">For more information on creating NuGet packages, see [How to Create a NuGet Package with Cross Platform Tools](../../core/deploying/creating-nuget-packages.md).</span></span>
