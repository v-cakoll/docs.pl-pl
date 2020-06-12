---
title: Tworzenie biblioteki klas .NET Standard przy użyciu programu Visual Studio
description: Dowiedz się, jak utworzyć .NET Standard bibliotekę klas przy użyciu programu Visual Studio.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: ef9c62b0378e1064d8cfd90a8c59aed74ea312b2
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2020
ms.locfileid: "84701568"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio"></a><span data-ttu-id="9acb1-103">Samouczek: Tworzenie biblioteki .NET Standard przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9acb1-103">Tutorial: Create a .NET Standard library using Visual Studio</span></span>

<span data-ttu-id="9acb1-104">W tym samouczku utworzysz prostą bibliotekę narzędzi, która zawiera pojedynczą metodę obsługi ciągów.</span><span class="sxs-lookup"><span data-stu-id="9acb1-104">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="9acb1-105">Implementuje ją jako [metodę rozszerzenia](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , aby można było wywołać ją tak, jakby była elementem członkowskim <xref:System.String> klasy.</span><span class="sxs-lookup"><span data-stu-id="9acb1-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="9acb1-106">*Biblioteka klas* definiuje typy i metody, które są wywoływane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="9acb1-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="9acb1-107">Biblioteka klas, która jest przeznaczona dla .NET Standard 2,0 umożliwia wywoływanie biblioteki przez dowolną implementację platformy .NET, która obsługuje tę wersję .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="9acb1-107">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="9acb1-108">Po zakończeniu biblioteki klas można ją rozpowszechnić jako składnik innej firmy lub jako składnik pakietu z jedną lub wieloma aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="9acb1-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9acb1-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="9acb1-109">Prerequisites</span></span>

- <span data-ttu-id="9acb1-110">[Program Visual Studio 2019 w wersji 16,6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym **wieloplatformowym obciążeniem programistycznym dla platformy .NET Core** .</span><span class="sxs-lookup"><span data-stu-id="9acb1-110">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="9acb1-111">Zestaw .NET Core 3,1 SDK jest instalowany automatycznie po wybraniu tego obciążenia.</span><span class="sxs-lookup"><span data-stu-id="9acb1-111">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="9acb1-112">Aby uzyskać więcej informacji, zobacz sekcję [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) w artykule [Instalowanie zestaw .NET Core SDK](../install/sdk.md?pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="9acb1-112">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="9acb1-113">Tworzenie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="9acb1-113">Create a solution</span></span>

<span data-ttu-id="9acb1-114">Zacznij od utworzenia pustego rozwiązania, aby umieścić projekt biblioteki klas w.</span><span class="sxs-lookup"><span data-stu-id="9acb1-114">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="9acb1-115">Rozwiązanie programu Visual Studio służy jako kontener dla jednego lub wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="9acb1-115">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="9acb1-116">Dodasz kolejne powiązane projekty do tego samego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9acb1-116">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="9acb1-117">Aby utworzyć puste rozwiązanie:</span><span class="sxs-lookup"><span data-stu-id="9acb1-117">To create the blank solution:</span></span>

1. <span data-ttu-id="9acb1-118">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9acb1-118">Start Visual Studio.</span></span>

2. <span data-ttu-id="9acb1-119">W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="9acb1-119">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="9acb1-120">Na stronie **Tworzenie nowego projektu** wprowadź **rozwiązanie** w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="9acb1-120">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="9acb1-121">Wybierz szablon **pustego rozwiązania** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="9acb1-121">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Pusty szablon rozwiązania w programie Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="9acb1-123">Na stronie **Konfiguruj nowy projekt** wprowadź **ClassLibraryProjects** w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="9acb1-123">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="9acb1-124">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="9acb1-124">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="9acb1-125">Tworzenie projektu biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="9acb1-125">Create a class library project</span></span>

1. <span data-ttu-id="9acb1-126">Dodaj nowy projekt biblioteki klas .NET Standard o nazwie "StringLibrary" do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9acb1-126">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="9acb1-127">Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="9acb1-127">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="9acb1-128">Na stronie **Dodawanie nowego projektu** wprowadź **bibliotekę** w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="9acb1-128">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="9acb1-129">Wybierz pozycję **C#** lub **Visual Basic** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform.</span><span class="sxs-lookup"><span data-stu-id="9acb1-129">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="9acb1-130">Wybierz szablon **Biblioteka klas (.NET standard)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="9acb1-130">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="9acb1-131">Na stronie **Konfiguruj nowy projekt** wprowadź **StringLibrary** w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="9acb1-131">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="9acb1-132">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="9acb1-132">Then, choose **Create**.</span></span>

1. <span data-ttu-id="9acb1-133">Upewnij się, że biblioteka jest ukierunkowana na poprawną wersję .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="9acb1-133">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="9acb1-134">Kliknij prawym przyciskiem myszy projekt Biblioteka w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9acb1-134">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="9acb1-135">Pole tekstowe **platformy docelowej** pokazuje, że projekt jest docelowy .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="9acb1-135">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Właściwości projektu dla biblioteki klas](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="9acb1-137">Jeśli używasz Visual Basic, wyczyść tekst w polu tekstowym **główna przestrzeń nazw** .</span><span class="sxs-lookup"><span data-stu-id="9acb1-137">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   ![Właściwości projektu dla biblioteki klas](./media/library-with-visual-studio/vb/library-project-properties.png)

   <span data-ttu-id="9acb1-139">Dla każdego projektu Visual Basic automatycznie tworzy przestrzeń nazw, która odnosi się do nazwy projektu.</span><span class="sxs-lookup"><span data-stu-id="9acb1-139">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="9acb1-140">W tym samouczku zdefiniujesz przestrzeń nazw najwyższego poziomu za pomocą [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) słowa kluczowego w pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="9acb1-140">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="9acb1-141">Zastąp kod w oknie kodu dla *Class1.cs* lub *Class1. vb* następującym kodem i Zapisz plik.</span><span class="sxs-lookup"><span data-stu-id="9acb1-141">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="9acb1-142">Jeśli język, którego chcesz użyć, nie jest wyświetlany, Zmień selektor języka w górnej części strony.</span><span class="sxs-lookup"><span data-stu-id="9acb1-142">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   <span data-ttu-id="9acb1-143">Biblioteka klas, `UtilityLibraries.StringLibrary` ,,, zawiera metodę o nazwie `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="9acb1-143">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="9acb1-144">Ta metoda zwraca <xref:System.Boolean> wartość wskazującą, czy bieżące wystąpienie ciągu zaczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="9acb1-144">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="9acb1-145">Standard Unicode rozróżnia wielkie litery od małych liter.</span><span class="sxs-lookup"><span data-stu-id="9acb1-145">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="9acb1-146"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType>Metoda zwraca `true` czy znak jest pisany wielką literą.</span><span class="sxs-lookup"><span data-stu-id="9acb1-146">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="9acb1-147">Na pasku menu wybierz opcję **Kompiluj**  >  **rozwiązanie kompilacji** , aby sprawdzić, czy projekt kompiluje się bez błędu.</span><span class="sxs-lookup"><span data-stu-id="9acb1-147">On the menu bar, select **Build** > **Build Solution** to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="9acb1-148">Dodawanie aplikacji konsolowej do rozwiązania</span><span class="sxs-lookup"><span data-stu-id="9acb1-148">Add a console app to the solution</span></span>

<span data-ttu-id="9acb1-149">Dodaj aplikację konsolową, która używa biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="9acb1-149">Add a console application that uses the class library.</span></span> <span data-ttu-id="9acb1-150">Aplikacja wyświetli monit o wprowadzenie ciągu i zgłoszenie, czy ciąg rozpoczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="9acb1-150">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="9acb1-151">Dodaj nową aplikację konsolową .NET Core do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9acb1-151">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="9acb1-152">Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="9acb1-152">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="9acb1-153">Na stronie **Dodawanie nowego projektu** wprowadź w polu wyszukiwania **konsolę** .</span><span class="sxs-lookup"><span data-stu-id="9acb1-153">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="9acb1-154">Wybierz pozycję **C#** lub **Visual Basic** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform.</span><span class="sxs-lookup"><span data-stu-id="9acb1-154">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="9acb1-155">Wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="9acb1-155">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="9acb1-156">Na stronie **Konfiguruj nowy projekt** wprowadź wartość **Prezentacja** w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="9acb1-156">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="9acb1-157">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="9acb1-157">Then choose **Create**.</span></span>

1. <span data-ttu-id="9acb1-158">W oknie kodu dla pliku *program.cs* lub *program. vb* Zastąp cały kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="9acb1-158">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   <span data-ttu-id="9acb1-159">Kod używa `row` zmiennej do obsługi liczby wierszy danych zapisywana w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="9acb1-159">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="9acb1-160">Za każdym razem, gdy jest większy lub równy 25, kod czyści okno konsoli i wyświetla komunikat dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9acb1-160">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="9acb1-161">Program poprosi użytkownika o wprowadzenie ciągu.</span><span class="sxs-lookup"><span data-stu-id="9acb1-161">The program prompts the user to enter a string.</span></span> <span data-ttu-id="9acb1-162">Wskazuje, czy ciąg rozpoczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="9acb1-162">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="9acb1-163">Jeśli użytkownik naciśnie klawisz <kbd>Enter</kbd> bez wprowadzania ciągu, aplikacja zostanie zakończona, a okno konsoli zostanie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="9acb1-163">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="9acb1-164">Dodaj odwołanie do projektu</span><span class="sxs-lookup"><span data-stu-id="9acb1-164">Add a project reference</span></span>

<span data-ttu-id="9acb1-165">Początkowo nowy projekt aplikacji konsolowej nie ma dostępu do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="9acb1-165">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="9acb1-166">Aby zezwolić na wywoływanie metod w bibliotece klas, Utwórz odwołanie do projektu do projektu biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="9acb1-166">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="9acb1-167">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy `ShowCase` węzeł **zależności** projektu i wybierz polecenie **Dodaj odwołanie do projektu**.</span><span class="sxs-lookup"><span data-stu-id="9acb1-167">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   ![Dodaj menu kontekstowe odwołania w programie Visual Studio](media/library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="9acb1-169">W oknie dialogowym **Menedżer odwołań** wybierz projekt **StringLibrary** , a następnie wybierz **przycisk OK**.</span><span class="sxs-lookup"><span data-stu-id="9acb1-169">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   ![Okno dialogowe programu Reference Manager z wybraną pozycją StringLibrary](media/library-with-visual-studio/manage-project-references.png)

## <a name="run-the-app"></a><span data-ttu-id="9acb1-171">Uruchomienie aplikacji</span><span class="sxs-lookup"><span data-stu-id="9acb1-171">Run the app</span></span>

1. <span data-ttu-id="9acb1-172">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **pokazu** i wybierz polecenie **Ustaw jako projekt startowy** w menu kontekstowym.</span><span class="sxs-lookup"><span data-stu-id="9acb1-172">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Menu kontekstowe projektu programu Visual Studio, aby ustawić projekt startowy](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="9acb1-174">Naciśnij klawisz <kbd>SHIFT</kbd> + <kbd>F5</kbd> , aby skompilować i uruchomić program bez debugowania.</span><span class="sxs-lookup"><span data-stu-id="9acb1-174">Press <kbd>Shift</kbd>+<kbd>F5</kbd> to compile and run the program without debugging.</span></span>

   ![Pasek narzędzi projektu programu Visual Studio z widocznym przyciskiem Debuguj](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. <span data-ttu-id="9acb1-176">Wypróbuj program, wprowadzając ciągi i naciskając klawisz <kbd>Enter</kbd>, a następnie naciśnij klawisz <kbd>Enter</kbd> , aby wyjść.</span><span class="sxs-lookup"><span data-stu-id="9acb1-176">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Okno konsoli z uruchomionym pokazem":::

## <a name="additional-resources"></a><span data-ttu-id="9acb1-178">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="9acb1-178">Additional resources</span></span>

* [<span data-ttu-id="9acb1-179">Tworzenie bibliotek przy użyciu interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="9acb1-179">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="9acb1-180">[Wersje .NET Standard i obsługiwane przez nich platformy](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="9acb1-180">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9acb1-181">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="9acb1-181">Next steps</span></span>

<span data-ttu-id="9acb1-182">W tym samouczku utworzono rozwiązanie, dodano projekt biblioteki i dodano projekt aplikacji konsolowej, który używa biblioteki.</span><span class="sxs-lookup"><span data-stu-id="9acb1-182">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="9acb1-183">W następnym samouczku dodasz projekt testu jednostkowego do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9acb1-183">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9acb1-184">Testowanie biblioteki .NET Standard za pomocą platformy .NET Core przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9acb1-184">Test a .NET Standard library with .NET Core using Visual Studio</span></span>](testing-library-with-visual-studio.md)
