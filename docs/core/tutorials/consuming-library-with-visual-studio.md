---
title: Korzystanie z biblioteki .NET Standard w programie Visual Studio 2017
description: Tworzenie aplikacji .NET Core, która wywołuje elementy członkowskie innej biblioteki klas z programem Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 06/05/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 31a9183f541afa5365862b1e89704354cf7bd527
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969294"
---
# <a name="consume-a-net-standard-library-in-visual-studio-2017"></a><span data-ttu-id="5bbde-103">Korzystanie z biblioteki .NET Standard w programie Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="5bbde-103">Consume a .NET Standard library in Visual Studio 2017</span></span>

<span data-ttu-id="5bbde-104">Po utworzeniu biblioteki klas .NET Standard, wykonując kroki opisane w sekcji [Kompilowanie C# biblioteki klas przy użyciu platformy .NET Core w programie Visual Studio 2017](./library-with-visual-studio.md) lub [Kompilowanie biblioteki klas Visual Basic przy użyciu platformy .net core w programie Visual Studio 2017](vb-library-with-visual-studio.md), przetestowano ją w [ Testowanie biblioteki klas przy użyciu platformy .NET Core w programie Visual Studio 2017](testing-library-with-visual-studio.md)i skompilowanej wersji biblioteki, następnym krokiem jest udostępnienie jej dla obiektów wywołujących.</span><span class="sxs-lookup"><span data-stu-id="5bbde-104">Once you've created a .NET Standard class library by following the steps in [Building a C# class library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) or [Building a Visual Basic class library with .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md), tested it in [Testing a class library with .NET Core in Visual Studio 2017](testing-library-with-visual-studio.md), and built a Release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="5bbde-105">Można to zrobić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="5bbde-105">You can do this in two ways:</span></span>

* <span data-ttu-id="5bbde-106">Jeśli biblioteka będzie używana przez pojedyncze rozwiązanie (na przykład w przypadku składnika w pojedynczej dużej aplikacji), można dołączyć go jako projekt w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="5bbde-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>

* <span data-ttu-id="5bbde-107">Jeśli biblioteka będzie ogólnie dostępna, możesz ją rozpowszechnić jako pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="5bbde-107">If the library will be generally accessible, you can distribute it as a NuGet package.</span></span>

## <a name="including-a-library-as-a-project-in-a-solution"></a><span data-ttu-id="5bbde-108">Dołączanie biblioteki jako projektu w rozwiązaniu</span><span class="sxs-lookup"><span data-stu-id="5bbde-108">Including a library as a project in a solution</span></span>

<span data-ttu-id="5bbde-109">Podobnie jak w przypadku testów jednostkowych w tym samym rozwiązaniu co Biblioteka klas, możesz dołączyć aplikację jako część tego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="5bbde-109">Just as you included unit tests in the same solution as your class library, you can include your application as part of that solution.</span></span> <span data-ttu-id="5bbde-110">Można na przykład użyć biblioteki klas w aplikacji konsolowej, która wyświetla użytkownikowi komunikat, aby wprowadzić ciąg i określić, czy jego pierwszy znak jest pisany wielkimi literami:</span><span class="sxs-lookup"><span data-stu-id="5bbde-110">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[<span data-ttu-id="5bbde-111">C#</span><span class="sxs-lookup"><span data-stu-id="5bbde-111">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="5bbde-112">Otwórz rozwiązanie utworzone w sekcji [Kompilowanie biblioteki C# klas przy użyciu programu .NET Core w programie Visual Studio 2017.](./library-with-visual-studio.md) `ClassLibraryProjects`</span><span class="sxs-lookup"><span data-stu-id="5bbde-112">Open the `ClassLibraryProjects` solution you created in the [Building a C# Class Library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="5bbde-113">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie **ClassLibraryProjects** i wybierz polecenie **Dodaj** > **Nowy projekt** z menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="5bbde-113">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="5bbde-114">W oknie dialogowym **Dodaj nowy projekt** rozwiń węzeł **wizualizacji C#**  i wybierz węzeł **.NET Core** , a następnie szablon projektu **aplikacja konsoli (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="5bbde-114">In the **Add New Project** dialog, expand the **Visual C#** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="5bbde-115">W polu tekstowym **Nazwa** wpisz "pokaz" i wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="5bbde-115">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Okno dialogowe Dodawanie nowego projektu w programie Visual Studio —C#](./media/consuming-library-with-visual-studio/add-new-project-dialog.png)

1. <span data-ttu-id="5bbde-117">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **pokazu** i wybierz polecenie **Ustaw jako projekt startowy** w menu kontekstowym.</span><span class="sxs-lookup"><span data-stu-id="5bbde-117">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Menu kontekstowe projektu programu Visual Studio do ustawiania projektu startowego —C#](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="5bbde-119">Początkowo projekt nie ma dostępu do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="5bbde-119">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="5bbde-120">Aby zezwolić na wywoływanie metod w bibliotece klas, należy utworzyć odwołanie do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="5bbde-120">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="5bbde-121">W **Eksplorator rozwiązań**kliknij prawym przyciskiem `ShowCase` myszy węzeł **zależności** projektu i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="5bbde-121">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Menu kontekstowe dodawania odwołania w projekcie programu Visual Studio —C#](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="5bbde-123">W oknie dialogowym **Menedżer odwołań** wybierz pozycję **StringLibrary**, projekt biblioteki klas, a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="5bbde-123">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Okno dialogowe zarządzania odwołaniami w programie Visual Studio —C#](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="5bbde-125">W oknie kod dla pliku *program.cs* Zastąp cały kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="5bbde-125">In the code window for the *Program.cs* file, replace all of the code with the following code:</span></span>

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   <span data-ttu-id="5bbde-126">Kod używa `row` zmiennej do obsługi liczby wierszy danych zapisywana w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="5bbde-126">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="5bbde-127">Za każdym razem, gdy jest większy lub równy 25, kod czyści okno konsoli i wyświetla komunikat dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5bbde-127">Whenever it is greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="5bbde-128">Program poprosi użytkownika o wprowadzenie ciągu.</span><span class="sxs-lookup"><span data-stu-id="5bbde-128">The program prompts the user to enter a string.</span></span> <span data-ttu-id="5bbde-129">Wskazuje, czy ciąg rozpoczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="5bbde-129">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="5bbde-130">Jeśli użytkownik naciśnie klawisz ENTER bez wpisywania ciągu, aplikacja zostanie przerwana, a okno konsoli zostanie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="5bbde-130">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="5bbde-131">W razie potrzeby zmień pasek narzędzi w celu skompilowania wersji `ShowCase` **debugowania** projektu.</span><span class="sxs-lookup"><span data-stu-id="5bbde-131">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="5bbde-132">Skompiluj i uruchom program, wybierając zieloną strzałkę na przycisku **Pokaz** .</span><span class="sxs-lookup"><span data-stu-id="5bbde-132">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Pasek narzędzi projektu programu Visual Studio z widocznym przyciskiem DebugujC#](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

# <a name="visual-basictabvb"></a>[<span data-ttu-id="5bbde-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5bbde-134">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="5bbde-135">Otwórz rozwiązanie utworzone w sekcji [Tworzenie biblioteki klas z Visual Basic i .NET Core w programie Visual Studio 2017.](vb-library-with-visual-studio.md) `ClassLibraryProjects`</span><span class="sxs-lookup"><span data-stu-id="5bbde-135">Open the `ClassLibraryProjects` solution you created in the [Building a class Library with Visual Basic and .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="5bbde-136">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie **ClassLibraryProjects** i wybierz polecenie **Dodaj** > **Nowy projekt** z menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="5bbde-136">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="5bbde-137">W oknie dialogowym **Dodaj nowy projekt** rozwiń węzeł **Visual Basic** i wybierz węzeł **.NET Core** , a następnie szablon projektu **aplikacja konsoli (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="5bbde-137">In the **Add New Project** dialog, expand the **Visual Basic** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="5bbde-138">W polu tekstowym **Nazwa** wpisz "pokaz" i wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="5bbde-138">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Okno dialogowe Dodawanie nowego projektu w programie Visual Studio — Visual Basic](./media/consuming-library-with-visual-studio/add-new-vb-project-dialog.png)

1. <span data-ttu-id="5bbde-140">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **pokazu** i wybierz polecenie **Ustaw jako projekt startowy** w menu kontekstowym.</span><span class="sxs-lookup"><span data-stu-id="5bbde-140">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span> 

   ![Menu kontekstowe projektu programu Visual Studio, aby ustawić projekt startowy — Visual Basic](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="5bbde-142">Początkowo projekt nie ma dostępu do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="5bbde-142">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="5bbde-143">Aby zezwolić na wywoływanie metod w bibliotece klas, należy utworzyć odwołanie do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="5bbde-143">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="5bbde-144">W **Eksplorator rozwiązań**kliknij prawym przyciskiem `ShowCase` myszy węzeł **zależności** projektu i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="5bbde-144">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Menu kontekstowe dodawania odwołania do projektu programu Visual Studio — Visual Basic](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="5bbde-146">W oknie dialogowym **Menedżer odwołań** wybierz pozycję **StringLibrary**, projekt biblioteki klas, a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="5bbde-146">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Okno dialogowe Zarządzanie odwołaniami w programie Visual Studio — Visual Basic](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="5bbde-148">W oknie kod dla pliku *program. vb* Zastąp cały kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="5bbde-148">In the code window for the *Program.vb* file, replace all of the code with the following code:</span></span>

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="5bbde-149">Kod używa `row` zmiennej do obsługi liczby wierszy danych zapisywana w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="5bbde-149">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="5bbde-150">Za każdym razem, gdy jest większy lub równy 25, kod czyści okno konsoli i wyświetla komunikat dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5bbde-150">Whenever it is greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="5bbde-151">Program poprosi użytkownika o wprowadzenie ciągu.</span><span class="sxs-lookup"><span data-stu-id="5bbde-151">The program prompts the user to enter a string.</span></span> <span data-ttu-id="5bbde-152">Wskazuje, czy ciąg rozpoczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="5bbde-152">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="5bbde-153">Jeśli użytkownik naciśnie klawisz ENTER bez wpisywania ciągu, aplikacja zostanie przerwana, a okno konsoli zostanie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="5bbde-153">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="5bbde-154">W razie potrzeby zmień pasek narzędzi w celu skompilowania wersji `ShowCase` **debugowania** projektu.</span><span class="sxs-lookup"><span data-stu-id="5bbde-154">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="5bbde-155">Skompiluj i uruchom program, wybierając zieloną strzałkę na przycisku **Pokaz** .</span><span class="sxs-lookup"><span data-stu-id="5bbde-155">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Debuguj na pasku narzędzi-Visual Basic](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

---

<span data-ttu-id="5bbde-157">Można debugować i publikować aplikację, która korzysta z tej biblioteki, wykonując czynności opisane w sekcji [debugowanie aplikacji Hello World za pomocą programu Visual studio 2017](debugging-with-visual-studio.md) i [publikowanie aplikacji Hello World przy użyciu programu Visual Studio 2017](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="5bbde-157">You can debug and publish the application that uses this library by following the steps in [Debugging your Hello World application with Visual Studio 2017](debugging-with-visual-studio.md) and [Publishing your Hello World Application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

## <a name="distributing-the-library-in-a-nuget-package"></a><span data-ttu-id="5bbde-158">Dystrybuowanie biblioteki w pakiecie NuGet</span><span class="sxs-lookup"><span data-stu-id="5bbde-158">Distributing the library in a NuGet package</span></span>

<span data-ttu-id="5bbde-159">Bibliotekę klas można udostępnić publicznie, publikując ją jako pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="5bbde-159">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="5bbde-160">Program Visual Studio nie obsługuje tworzenia pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="5bbde-160">Visual Studio does not support the creation of NuGet packages.</span></span> <span data-ttu-id="5bbde-161">Aby go utworzyć, użyj [ `dotnet` narzędzia wiersza polecenia](../tools/dotnet.md):</span><span class="sxs-lookup"><span data-stu-id="5bbde-161">To create one, you use the [`dotnet` command line utility](../tools/dotnet.md):</span></span>

1. <span data-ttu-id="5bbde-162">Otwórz okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="5bbde-162">Open a console window.</span></span> <span data-ttu-id="5bbde-163">Na przykład w polu tekstowym **pytaj mnie coś** na pasku zadań systemu Windows wpisz `Command Prompt` (lub `cmd` for Short), a następnie otwórz okno konsoli, wybierając **polecenie Wiersz polecenia** aplikacji klasycznej lub naciskając klawisz ENTER, jeśli jest zaznaczone w polu wyszukiwania. uzyskane.</span><span class="sxs-lookup"><span data-stu-id="5bbde-163">For example in the **Ask me anything** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="5bbde-164">Przejdź do katalogu projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="5bbde-164">Navigate to your library's project directory.</span></span> <span data-ttu-id="5bbde-165">O ile nie skonfigurowano ponownie typowej lokalizacji pliku, znajduje się ona w katalogu *Documents\Visual Studio 2017 \ Projects\ClassLibraryProjects\StringLibrary* .</span><span class="sxs-lookup"><span data-stu-id="5bbde-165">Unless you've reconfigured the typical file location, it's in the *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* directory.</span></span> <span data-ttu-id="5bbde-166">Katalog zawiera kod źródłowy i plik projektu, *StringLibrary. csproj*.</span><span class="sxs-lookup"><span data-stu-id="5bbde-166">The directory contains your source code and a project file, *StringLibrary.csproj*.</span></span>

1. <span data-ttu-id="5bbde-167">Wydaj polecenie `dotnet pack --no-build`.</span><span class="sxs-lookup"><span data-stu-id="5bbde-167">Issue the command `dotnet pack --no-build`.</span></span> <span data-ttu-id="5bbde-168">Narzędzie generuje pakiet z rozszerzeniem *. nupkg.* `dotnet`</span><span class="sxs-lookup"><span data-stu-id="5bbde-168">The `dotnet` utility generates a package with a *.nupkg* extension.</span></span>

   > [!TIP]
   > <span data-ttu-id="5bbde-169">Jeśli katalog zawierający program *dotnet. exe* nie znajduje się w ścieżce, można znaleźć jego lokalizację, wprowadzając `where dotnet.exe` ją w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="5bbde-169">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="5bbde-170">Aby uzyskać więcej informacji na temat tworzenia pakietów NuGet, zobacz [jak utworzyć pakiet NuGet za pomocą narzędzi międzyplatformowych](../deploying/creating-nuget-packages.md).</span><span class="sxs-lookup"><span data-stu-id="5bbde-170">For more information on creating NuGet packages, see [How to Create a NuGet Package with Cross Platform Tools](../deploying/creating-nuget-packages.md).</span></span>
