---
title: Tworzenie biblioteki klas .NET Standard w programie Visual Studio
description: Dowiedz się, jak utworzyć .NET Standard bibliotekę klas przy użyciu programu Visual Studio.
ms.date: 05/21/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 2afe11ad75fc36a67efed48d56dbafb11bceaf2a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005276"
---
# <a name="tutorial-create-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="876f5-103">Samouczek: Tworzenie biblioteki .NET Standard w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="876f5-103">Tutorial: Create a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="876f5-104">*Biblioteka klas* definiuje typy i metody, które są wywoływane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="876f5-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="876f5-105">Biblioteka klas, która jest przeznaczona dla .NET Standard 2,0 umożliwia wywoływanie biblioteki przez dowolną implementację platformy .NET, która obsługuje tę wersję .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="876f5-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="876f5-106">Po zakończeniu biblioteki klas możesz zdecydować, czy chcesz ją rozpowszechnić jako składnik innej firmy, czy chcesz ją dołączyć jako składnik pakietu z co najmniej jedną aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="876f5-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="876f5-107">Listę wersji .NET Standard i obsługiwanych przez nich platform można znaleźć w temacie [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="876f5-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="876f5-108">W tym samouczku utworzysz prostą bibliotekę narzędzi, która zawiera pojedynczą metodę obsługi ciągów.</span><span class="sxs-lookup"><span data-stu-id="876f5-108">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="876f5-109">Implementuje ją jako [metodę rozszerzenia](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , aby można było wywołać ją tak, jakby była elementem członkowskim <xref:System.String> klasy.</span><span class="sxs-lookup"><span data-stu-id="876f5-109">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="876f5-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="876f5-110">Prerequisites</span></span>

- <span data-ttu-id="876f5-111">[Program Visual Studio 2019 w wersji 16,6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym **wieloplatformowym obciążeniem programistycznym dla platformy .NET Core** .</span><span class="sxs-lookup"><span data-stu-id="876f5-111">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="876f5-112">Zestaw .NET Core 3,1 SDK jest instalowany automatycznie po wybraniu tego obciążenia.</span><span class="sxs-lookup"><span data-stu-id="876f5-112">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="876f5-113">Aby uzyskać więcej informacji, zobacz sekcję [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) w artykule [Instalowanie zestaw .NET Core SDK](../install/sdk.md?pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="876f5-113">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-a-visual-studio-solution"></a><span data-ttu-id="876f5-114">Tworzenie rozwiązania programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="876f5-114">Create a Visual Studio solution</span></span>

<span data-ttu-id="876f5-115">Zacznij od utworzenia pustego rozwiązania, aby umieścić projekt biblioteki klas w.</span><span class="sxs-lookup"><span data-stu-id="876f5-115">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="876f5-116">Rozwiązanie programu Visual Studio służy jako kontener dla jednego lub wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="876f5-116">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="876f5-117">Dodasz kolejne powiązane projekty do tego samego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="876f5-117">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="876f5-118">Aby utworzyć puste rozwiązanie:</span><span class="sxs-lookup"><span data-stu-id="876f5-118">To create the blank solution:</span></span>

1. <span data-ttu-id="876f5-119">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="876f5-119">Open Visual Studio.</span></span>

2. <span data-ttu-id="876f5-120">W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="876f5-120">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="876f5-121">Na stronie **Tworzenie nowego projektu** wprowadź **rozwiązanie** w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="876f5-121">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="876f5-122">Wybierz szablon **pustego rozwiązania** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="876f5-122">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Pusty szablon rozwiązania w programie Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="876f5-124">Na stronie **Konfiguruj nowy projekt** wprowadź **ClassLibraryProjects** w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="876f5-124">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="876f5-125">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="876f5-125">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="876f5-126">Tworzenie projektu biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="876f5-126">Create a class library project</span></span>

1. <span data-ttu-id="876f5-127">Dodaj nowy projekt biblioteki klas .NET Standard o nazwie "StringLibrary" do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="876f5-127">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="876f5-128">Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="876f5-128">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="876f5-129">Na stronie **Dodawanie nowego projektu** wprowadź **bibliotekę** w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="876f5-129">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="876f5-130">Wybierz pozycję **C#** lub **Visual Basic** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform.</span><span class="sxs-lookup"><span data-stu-id="876f5-130">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="876f5-131">Wybierz szablon **Biblioteka klas (.NET standard)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="876f5-131">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="876f5-132">Na stronie **Konfiguruj nowy projekt** wprowadź **StringLibrary** w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="876f5-132">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="876f5-133">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="876f5-133">Then, choose **Create**.</span></span>

1. <span data-ttu-id="876f5-134">Upewnij się, że biblioteka jest ukierunkowana na poprawną wersję .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="876f5-134">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="876f5-135">Kliknij prawym przyciskiem myszy projekt Biblioteka w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="876f5-135">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="876f5-136">Pole tekstowe **platformy docelowej** pokazuje, że projekt jest docelowy .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="876f5-136">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Właściwości projektu dla biblioteki klas](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="876f5-138">Jeśli używasz Visual Basic, wyczyść tekst w polu tekstowym **główna przestrzeń nazw** .</span><span class="sxs-lookup"><span data-stu-id="876f5-138">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   ![Właściwości projektu dla biblioteki klas](./media/library-with-visual-studio/vb/library-project-properties.png)

   <span data-ttu-id="876f5-140">Dla każdego projektu Visual Basic automatycznie tworzy przestrzeń nazw, która odnosi się do nazwy projektu.</span><span class="sxs-lookup"><span data-stu-id="876f5-140">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="876f5-141">W tym samouczku zdefiniujesz przestrzeń nazw najwyższego poziomu za pomocą [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) słowa kluczowego w pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="876f5-141">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="876f5-142">Zastąp kod w oknie kodu dla *Class1.cs* lub *Class1. vb* następującym kodem i Zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="876f5-142">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="876f5-143">Jeśli język, którego chcesz użyć, nie jest wyświetlany, Zmień selektor języka w górnej części strony.</span><span class="sxs-lookup"><span data-stu-id="876f5-143">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   [!code-csharp[](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]
   [!code-vb[](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="876f5-144">Biblioteka klas, `UtilityLibraries.StringLibrary` ,,, zawiera metodę o nazwie `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="876f5-144">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="876f5-145">Ta metoda zwraca <xref:System.Boolean> wartość wskazującą, czy bieżące wystąpienie ciągu zaczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="876f5-145">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="876f5-146">Standard Unicode rozróżnia wielkie litery od małych liter.</span><span class="sxs-lookup"><span data-stu-id="876f5-146">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="876f5-147"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType>Metoda zwraca `true` czy znak jest pisany wielką literą.</span><span class="sxs-lookup"><span data-stu-id="876f5-147">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="876f5-148">Na pasku menu wybierz opcję **Kompiluj**  >  **rozwiązanie kompilacji** , aby sprawdzić, czy projekt kompiluje się bez błędu.</span><span class="sxs-lookup"><span data-stu-id="876f5-148">On the menu bar, select **Build** > **Build Solution** to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="876f5-149">Dodawanie aplikacji konsolowej do rozwiązania</span><span class="sxs-lookup"><span data-stu-id="876f5-149">Add a console app to the solution</span></span>

<span data-ttu-id="876f5-150">Użyj biblioteki klas w aplikacji konsolowej, która wyświetla użytkownikowi komunikat, aby wprowadzić ciąg i określić, czy ciąg rozpoczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="876f5-150">Use the class library in a console application that prompts the user to enter a string and reports whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="876f5-151">Dodaj nową aplikację konsolową .NET Core do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="876f5-151">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="876f5-152">Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="876f5-152">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="876f5-153">Na stronie **Dodawanie nowego projektu** wprowadź w polu wyszukiwania **konsolę** .</span><span class="sxs-lookup"><span data-stu-id="876f5-153">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="876f5-154">Wybierz pozycję **C#** lub **Visual Basic** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform.</span><span class="sxs-lookup"><span data-stu-id="876f5-154">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="876f5-155">Wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="876f5-155">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="876f5-156">Na stronie **Konfiguruj nowy projekt** wprowadź wartość **Prezentacja** w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="876f5-156">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="876f5-157">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="876f5-157">Then choose **Create**.</span></span>

1. <span data-ttu-id="876f5-158">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **pokazu** i wybierz polecenie **Ustaw jako projekt startowy** w menu kontekstowym.</span><span class="sxs-lookup"><span data-stu-id="876f5-158">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Menu kontekstowe projektu programu Visual Studio, aby ustawić projekt startowy](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="876f5-160">Początkowo nowy projekt aplikacji konsolowej nie ma dostępu do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="876f5-160">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="876f5-161">Aby zezwolić na wywoływanie metod w bibliotece klas, Utwórz odwołanie do projektu do projektu biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="876f5-161">To allow it to call methods in the class library, create a project reference to the class library project.</span></span> <span data-ttu-id="876f5-162">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy `ShowCase` węzeł **zależności** projektu i wybierz polecenie **Dodaj odwołanie do projektu**.</span><span class="sxs-lookup"><span data-stu-id="876f5-162">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   ![Dodaj menu kontekstowe odwołania w programie Visual Studio](media/library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="876f5-164">W oknie dialogowym **Menedżer odwołań** wybierz projekt **StringLibrary** , a następnie wybierz **przycisk OK**.</span><span class="sxs-lookup"><span data-stu-id="876f5-164">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   ![Okno dialogowe programu Reference Manager z wybraną pozycją StringLibrary](media/library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="876f5-166">W oknie kodu dla pliku *program.cs* lub *program. vb* Zastąp cały kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="876f5-166">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="876f5-167">Kod używa `row` zmiennej do obsługi liczby wierszy danych zapisywana w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="876f5-167">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="876f5-168">Za każdym razem, gdy jest większy lub równy 25, kod czyści okno konsoli i wyświetla komunikat dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="876f5-168">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="876f5-169">Program poprosi użytkownika o wprowadzenie ciągu.</span><span class="sxs-lookup"><span data-stu-id="876f5-169">The program prompts the user to enter a string.</span></span> <span data-ttu-id="876f5-170">Wskazuje, czy ciąg rozpoczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="876f5-170">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="876f5-171">Jeśli użytkownik naciśnie klawisz ENTER bez wprowadzania ciągu, aplikacja zostanie zakończona, a okno konsoli zostanie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="876f5-171">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="876f5-172">W razie potrzeby zmień pasek narzędzi w celu skompilowania wersji **debugowania** `ShowCase` projektu.</span><span class="sxs-lookup"><span data-stu-id="876f5-172">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="876f5-173">Skompiluj i uruchom program, wybierając zieloną strzałkę na przycisku **Pokaz** .</span><span class="sxs-lookup"><span data-stu-id="876f5-173">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Pasek narzędzi projektu programu Visual Studio z widocznym przyciskiem Debuguj](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. <span data-ttu-id="876f5-175">Wypróbuj program, wprowadzając ciągi i naciskając klawisz **Enter**, a następnie naciśnij klawisz **Enter** , aby wyjść.</span><span class="sxs-lookup"><span data-stu-id="876f5-175">Try out the program by entering strings and pressing **Enter**, then press **Enter** to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Okno konsoli z uruchomionym pokazem":::

## <a name="next-steps"></a><span data-ttu-id="876f5-177">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="876f5-177">Next steps</span></span>

<span data-ttu-id="876f5-178">W tym samouczku utworzono rozwiązanie, dodano projekt biblioteki i dodano projekt aplikacji konsolowej, który używa biblioteki.</span><span class="sxs-lookup"><span data-stu-id="876f5-178">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="876f5-179">W następnym samouczku dodasz projekt testu jednostkowego do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="876f5-179">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="876f5-180">Testowanie biblioteki .NET Standard przy użyciu platformy .NET Core w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="876f5-180">Test a .NET Standard library with .NET Core in Visual Studio</span></span>](testing-library-with-visual-studio.md)
