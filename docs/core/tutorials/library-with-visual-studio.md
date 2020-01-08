---
title: Tworzenie biblioteki klas .NET Standard w programie Visual Studio
description: Dowiedz się, jak utworzyć .NET Standardą bibliotekę klas C# zapisaną w programie lub Visual Basic przy użyciu programu Visual Studio
ms.date: 12/09/2019
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 160993a4dd40356cde541616a1f15f87712e8ae2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75343107"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="2ab91-103">Tworzenie biblioteki .NET Standard w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2ab91-103">Build a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="2ab91-104">*Biblioteka klas* definiuje typy i metody, które są wywoływane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="2ab91-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="2ab91-105">Biblioteka klas, która jest przeznaczona dla .NET Standard 2,0 umożliwia wywoływanie biblioteki przez dowolną implementację platformy .NET, która obsługuje tę wersję .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2ab91-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="2ab91-106">Po zakończeniu biblioteki klas możesz zdecydować, czy chcesz ją rozpowszechnić jako składnik innej firmy, czy chcesz ją dołączyć jako składnik pakietu z co najmniej jedną aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="2ab91-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="2ab91-107">Listę wersji .NET Standard i obsługiwanych przez nich platform można znaleźć w temacie [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="2ab91-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="2ab91-108">W tym temacie utworzysz prostą bibliotekę narzędzi, która zawiera pojedynczą metodę obsługi ciągów.</span><span class="sxs-lookup"><span data-stu-id="2ab91-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="2ab91-109">Należy zaimplementować ją jako [metodę rozszerzenia](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , aby można było wywołać ją tak, jakby była elementem członkowskim klasy <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="2ab91-109">You'll implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="create-a-visual-studio-solution"></a><span data-ttu-id="2ab91-110">Tworzenie rozwiązania programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2ab91-110">Create a Visual Studio solution</span></span>

<span data-ttu-id="2ab91-111">Zacznij od utworzenia pustego rozwiązania, aby umieścić projekt biblioteki klas w.</span><span class="sxs-lookup"><span data-stu-id="2ab91-111">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="2ab91-112">Rozwiązanie programu Visual Studio służy jako kontener dla jednego lub wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="2ab91-112">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="2ab91-113">Jeśli będziesz kontynuować pracę z serią samouczków, dodasz kolejne powiązane projekty do tego samego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="2ab91-113">You'll add additional, related projects to the same solution if you continue on with the tutorial series.</span></span>

<span data-ttu-id="2ab91-114">Aby utworzyć puste rozwiązanie:</span><span class="sxs-lookup"><span data-stu-id="2ab91-114">To create the blank solution:</span></span>

1. <span data-ttu-id="2ab91-115">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2ab91-115">Open Visual Studio.</span></span>

2. <span data-ttu-id="2ab91-116">W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="2ab91-116">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="2ab91-117">Na stronie **Tworzenie nowego projektu** wprowadź **rozwiązanie** w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="2ab91-117">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="2ab91-118">Wybierz szablon **pustego rozwiązania** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="2ab91-118">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Pusty szablon rozwiązania w programie Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="2ab91-120">Na stronie **Konfiguruj nowy projekt** wprowadź **ClassLibraryProjects** w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="2ab91-120">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="2ab91-121">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="2ab91-121">Then, choose **Create**.</span></span>

> [!TIP]
> <span data-ttu-id="2ab91-122">Możesz również pominąć ten krok i pozwolić programowi Visual Studio utworzyć rozwiązanie dla Ciebie podczas tworzenia projektu w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="2ab91-122">You can also skip this step and let Visual Studio create the solution for you when you create the project in the next step.</span></span> <span data-ttu-id="2ab91-123">Zapoznaj się z opcjami rozwiązania na stronie **Konfiguruj nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="2ab91-123">Look for the solution options on the **Configure your new project** page.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="2ab91-124">Tworzenie projektu biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="2ab91-124">Create a class library project</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[<span data-ttu-id="2ab91-125">C#</span><span class="sxs-lookup"><span data-stu-id="2ab91-125">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="2ab91-126">Dodaj nowy C# projekt biblioteki klas .NET Standard o nazwie "StringLibrary" do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="2ab91-126">Add a new C# .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="2ab91-127">Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj** > **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="2ab91-127">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="2ab91-128">Na stronie **Dodawanie nowego projektu** wprowadź **bibliotekę** w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="2ab91-128">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="2ab91-129">Wybierz **C#** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform.</span><span class="sxs-lookup"><span data-stu-id="2ab91-129">Choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="2ab91-130">Wybierz szablon **Biblioteka klas (.NET standard)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="2ab91-130">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="2ab91-131">Na stronie **Konfiguruj nowy projekt** wprowadź **StringLibrary** w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="2ab91-131">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="2ab91-132">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="2ab91-132">Then, choose **Create**.</span></span>

1. <span data-ttu-id="2ab91-133">Upewnij się, że biblioteka jest ukierunkowana na poprawną wersję .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2ab91-133">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="2ab91-134">Kliknij prawym przyciskiem myszy projekt Biblioteka w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="2ab91-134">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="2ab91-135">Pole tekstowe **platformy docelowej** pokazuje, że projekt jest docelowy .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="2ab91-135">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Właściwości projektu dla biblioteki klas](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="2ab91-137">Zastąp kod w oknie kodu następującym kodem i Zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="2ab91-137">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   <span data-ttu-id="2ab91-138">Biblioteka klas `UtilityLibraries.StringLibrary`, zawiera metodę o nazwie `StartsWithUpper`.</span><span class="sxs-lookup"><span data-stu-id="2ab91-138">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="2ab91-139">Ta metoda zwraca <xref:System.Boolean> wartość, która wskazuje, czy bieżące wystąpienie ciągu zaczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="2ab91-139">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="2ab91-140">Standard Unicode rozróżnia wielkie litery od małych liter.</span><span class="sxs-lookup"><span data-stu-id="2ab91-140">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="2ab91-141">Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> zwraca `true`, jeśli znak jest pisany wielką literą.</span><span class="sxs-lookup"><span data-stu-id="2ab91-141">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="2ab91-142">Na pasku menu wybierz kolejno opcje **kompiluj** > **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="2ab91-142">On the menu bar, select **Build** > **Build Solution**.</span></span>

# <a name="visual-basictabvb"></a>[<span data-ttu-id="2ab91-143">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2ab91-143">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="2ab91-144">Dodaj nowy projekt biblioteki klas Visual Basic .NET Standard o nazwie "StringLibrary" do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="2ab91-144">Add a new Visual Basic .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="2ab91-145">Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj** > **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="2ab91-145">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="2ab91-146">Na stronie **Dodawanie nowego projektu** wprowadź **bibliotekę** w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="2ab91-146">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="2ab91-147">Wybierz **Visual Basic** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform.</span><span class="sxs-lookup"><span data-stu-id="2ab91-147">Choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="2ab91-148">Wybierz szablon **Biblioteka klas (.NET standard)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="2ab91-148">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="2ab91-149">Na stronie **Konfiguruj nowy projekt** wprowadź **StringLibrary** w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="2ab91-149">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="2ab91-150">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="2ab91-150">Then, choose **Create**.</span></span>

1. <span data-ttu-id="2ab91-151">Upewnij się, że biblioteka jest ukierunkowana na poprawną wersję .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2ab91-151">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="2ab91-152">Kliknij prawym przyciskiem myszy projekt Biblioteka w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="2ab91-152">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="2ab91-153">Pole tekstowe **platformy docelowej** pokazuje, że projekt jest docelowy .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="2ab91-153">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Właściwości projektu dla biblioteki klas](./media/library-with-visual-studio/vb/library-project-properties.png)

1. <span data-ttu-id="2ab91-155">W oknie dialogowym **Właściwości** Wyczyść tekst w polu tekstowym **główna przestrzeń nazw** .</span><span class="sxs-lookup"><span data-stu-id="2ab91-155">In the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="2ab91-156">Dla każdego projektu Visual Basic automatycznie tworzy przestrzeń nazw, która odnosi się do nazwy projektu.</span><span class="sxs-lookup"><span data-stu-id="2ab91-156">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="2ab91-157">W tym samouczku zdefiniujesz przestrzeń nazw najwyższego poziomu za pomocą słowa kluczowego [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) w pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="2ab91-157">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="2ab91-158">Zastąp kod w oknie kodu następującym kodem i Zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="2ab91-158">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="2ab91-159">Biblioteka klas `UtilityLibraries.StringLibrary`, zawiera metodę o nazwie `StartsWithUpper`.</span><span class="sxs-lookup"><span data-stu-id="2ab91-159">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="2ab91-160">Ta metoda zwraca <xref:System.Boolean> wartość, która wskazuje, czy bieżące wystąpienie ciągu zaczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="2ab91-160">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="2ab91-161">Standard Unicode rozróżnia wielkie litery od małych liter.</span><span class="sxs-lookup"><span data-stu-id="2ab91-161">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="2ab91-162">Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> zwraca `true`, jeśli znak jest pisany wielką literą.</span><span class="sxs-lookup"><span data-stu-id="2ab91-162">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="2ab91-163">Na pasku menu wybierz kolejno opcje **kompiluj** > **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="2ab91-163">On the menu bar, select **Build** > **Build Solution**.</span></span>

---

   <span data-ttu-id="2ab91-164">Projekt powinien zostać skompilowany bez błędu.</span><span class="sxs-lookup"><span data-stu-id="2ab91-164">The project should compile without error.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2ab91-165">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="2ab91-165">Next steps</span></span>

<span data-ttu-id="2ab91-166">Biblioteka została pomyślnie skompilowana.</span><span class="sxs-lookup"><span data-stu-id="2ab91-166">You've successfully built the library.</span></span> <span data-ttu-id="2ab91-167">Ponieważ nie została wywołana żadna z jej metod, nie wiesz, czy działa ona zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="2ab91-167">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="2ab91-168">Następnym krokiem w opracowaniu biblioteki jest przetestowanie go.</span><span class="sxs-lookup"><span data-stu-id="2ab91-168">The next step in developing your library is to test it.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2ab91-169">Tworzenie projektu testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="2ab91-169">Create a unit test project</span></span>](testing-library-with-visual-studio.md)
