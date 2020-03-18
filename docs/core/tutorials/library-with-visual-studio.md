---
title: Tworzenie biblioteki klas standardu .NET w programie Visual Studio
description: Dowiedz się, jak utworzyć bibliotekę klas .NET Standard napisaną w języku C# lub Visual Basic przy użyciu programu Visual Studio
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 748a1499e0c3a4a41613a69b715dbcfbd585bfe3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714020"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="5ff22-103">Tworzenie biblioteki standardu .NET w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5ff22-103">Build a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="5ff22-104">*Biblioteka klas* definiuje typy i metody wywoływane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="5ff22-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="5ff22-105">Biblioteka klas przeznaczona dla programu .NET Standard 2.0 umożliwia wywoływanie biblioteki przez dowolną implementację .NET obsługującej tę wersję standardu .NET.</span><span class="sxs-lookup"><span data-stu-id="5ff22-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="5ff22-106">Po zakończeniu biblioteki klas, można zdecydować, czy chcesz rozpowszechniać go jako składnik innej firmy lub czy chcesz dołączyć go jako składnik w pakiecie z jedną lub więcej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5ff22-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="5ff22-107">Aby uzyskać listę wersji standardu .NET i obsługiwanych platform, zobacz [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="5ff22-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="5ff22-108">W tym temacie utworzysz prostą bibliotekę narzędziową zawierającą metodę obsługi pojedynczych ciągów.</span><span class="sxs-lookup"><span data-stu-id="5ff22-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="5ff22-109">Zaimplementujesz go jako [metodę rozszerzenia,](../../csharp/programming-guide/classes-and-structs/extension-methods.md) dzięki czemu można wywołać go <xref:System.String> tak, jakby był członkiem klasy.</span><span class="sxs-lookup"><span data-stu-id="5ff22-109">You'll implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="create-a-visual-studio-solution"></a><span data-ttu-id="5ff22-110">Tworzenie rozwiązania programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5ff22-110">Create a Visual Studio solution</span></span>

<span data-ttu-id="5ff22-111">Rozpocznij od utworzenia pustego rozwiązania, aby umieścić projekt biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="5ff22-111">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="5ff22-112">Rozwiązanie programu Visual Studio służy jako kontener dla jednego lub więcej projektów.</span><span class="sxs-lookup"><span data-stu-id="5ff22-112">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="5ff22-113">Dodasz dodatkowe, powiązane projekty do tego samego rozwiązania, jeśli będziesz kontynuować serię samouczków.</span><span class="sxs-lookup"><span data-stu-id="5ff22-113">You'll add additional, related projects to the same solution if you continue on with the tutorial series.</span></span>

<span data-ttu-id="5ff22-114">Aby utworzyć puste rozwiązanie:</span><span class="sxs-lookup"><span data-stu-id="5ff22-114">To create the blank solution:</span></span>

1. <span data-ttu-id="5ff22-115">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5ff22-115">Open Visual Studio.</span></span>

2. <span data-ttu-id="5ff22-116">W oknie startowym wybierz pozycję **Utwórz nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="5ff22-116">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="5ff22-117">Na stronie **Tworzenie nowego projektu** wprowadź **rozwiązanie** w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="5ff22-117">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="5ff22-118">Wybierz szablon **Puste rozwiązanie,** a następnie wybierz pozycję **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="5ff22-118">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Pusty szablon rozwiązania w programie Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="5ff22-120">Na stronie **Konfigurowanie nowego projektu** wprowadź **pozycję ClassLibraryProjects** w polu **Nazwa projektu.**</span><span class="sxs-lookup"><span data-stu-id="5ff22-120">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="5ff22-121">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="5ff22-121">Then, choose **Create**.</span></span>

> [!TIP]
> <span data-ttu-id="5ff22-122">Można również pominąć ten krok i pozwolić visual studio utworzyć rozwiązanie dla Ciebie podczas tworzenia projektu w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="5ff22-122">You can also skip this step and let Visual Studio create the solution for you when you create the project in the next step.</span></span> <span data-ttu-id="5ff22-123">Poszukaj opcji rozwiązania na stronie **Konfigurowanie nowego projektu.**</span><span class="sxs-lookup"><span data-stu-id="5ff22-123">Look for the solution options on the **Configure your new project** page.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="5ff22-124">Tworzenie projektu biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="5ff22-124">Create a class library project</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="5ff22-125">C #</span><span class="sxs-lookup"><span data-stu-id="5ff22-125">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="5ff22-126">Dodaj nowy projekt biblioteki klas Standard c# .NET o nazwie "StringLibrary" do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="5ff22-126">Add a new C# .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="5ff22-127">Kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratorze rozwiązań** i wybierz **polecenie Dodaj** > **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="5ff22-127">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="5ff22-128">Na stronie **Dodawanie nowego projektu** wprowadź **bibliotekę** w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="5ff22-128">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="5ff22-129">Wybierz **c#** z listy Język, a następnie wybierz **wszystkie platformy** z listy Platforma.</span><span class="sxs-lookup"><span data-stu-id="5ff22-129">Choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="5ff22-130">Wybierz szablon **Biblioteka klas (.NET Standard),** a następnie wybierz pozycję **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="5ff22-130">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="5ff22-131">Na stronie **Konfigurowanie nowego projektu** wprowadź **bibliotekę ciągów** w polu **Nazwa projektu.**</span><span class="sxs-lookup"><span data-stu-id="5ff22-131">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="5ff22-132">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="5ff22-132">Then, choose **Create**.</span></span>

1. <span data-ttu-id="5ff22-133">Upewnij się, że biblioteka jest przeznaczona dla poprawnej wersji programu .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="5ff22-133">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="5ff22-134">Kliknij prawym przyciskiem myszy projekt biblioteki w **Eksploratorze rozwiązań**, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="5ff22-134">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="5ff22-135">Pole tekstowe **Platforma docelowa** pokazuje, że projekt jest przeznaczony dla programu .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="5ff22-135">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Właściwości projektu dla biblioteki klas](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="5ff22-137">Zastąp kod w oknie kodu następującym kodem i zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="5ff22-137">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   <span data-ttu-id="5ff22-138">Biblioteka klas `UtilityLibraries.StringLibrary`, zawiera metodę `StartsWithUpper`o nazwie .</span><span class="sxs-lookup"><span data-stu-id="5ff22-138">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="5ff22-139">Ta metoda <xref:System.Boolean> zwraca wartość, która wskazuje, czy bieżące wystąpienie ciągu rozpoczyna się wielkimi literami.</span><span class="sxs-lookup"><span data-stu-id="5ff22-139">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="5ff22-140">Standard Unicode odróżnia wielkie litery od małych liter.</span><span class="sxs-lookup"><span data-stu-id="5ff22-140">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="5ff22-141">Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> zwraca, `true` jeśli znak jest wielkimi literami.</span><span class="sxs-lookup"><span data-stu-id="5ff22-141">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="5ff22-142">Na pasku menu wybierz pozycję **Zbuduj** > **rozwiązanie kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="5ff22-142">On the menu bar, select **Build** > **Build Solution**.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="5ff22-143">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ff22-143">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="5ff22-144">Dodaj nowy projekt biblioteki klas programu Visual Basic .NET Standard o nazwie "StringLibrary" do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="5ff22-144">Add a new Visual Basic .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="5ff22-145">Kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratorze rozwiązań** i wybierz **polecenie Dodaj** > **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="5ff22-145">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="5ff22-146">Na stronie **Dodawanie nowego projektu** wprowadź **bibliotekę** w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="5ff22-146">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="5ff22-147">Wybierz **pozycję Visual Basic** z listy Język, a następnie wybierz pozycję Wszystkie **platformy** z listy Platforma.</span><span class="sxs-lookup"><span data-stu-id="5ff22-147">Choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="5ff22-148">Wybierz szablon **Biblioteka klas (.NET Standard),** a następnie wybierz pozycję **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="5ff22-148">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="5ff22-149">Na stronie **Konfigurowanie nowego projektu** wprowadź **bibliotekę ciągów** w polu **Nazwa projektu.**</span><span class="sxs-lookup"><span data-stu-id="5ff22-149">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="5ff22-150">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="5ff22-150">Then, choose **Create**.</span></span>

1. <span data-ttu-id="5ff22-151">Upewnij się, że biblioteka jest przeznaczona dla poprawnej wersji programu .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="5ff22-151">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="5ff22-152">Kliknij prawym przyciskiem myszy projekt biblioteki w **Eksploratorze rozwiązań**, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="5ff22-152">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="5ff22-153">Pole tekstowe **Platforma docelowa** pokazuje, że projekt jest przeznaczony dla programu .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="5ff22-153">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Właściwości projektu dla biblioteki klas](./media/library-with-visual-studio/vb/library-project-properties.png)

1. <span data-ttu-id="5ff22-155">W oknie dialogowym **Właściwości** wyczyść tekst w polu tekstowym **Główny obszar nazw.**</span><span class="sxs-lookup"><span data-stu-id="5ff22-155">In the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="5ff22-156">Dla każdego projektu program Visual Basic automatycznie tworzy obszar nazw odpowiadający nazwie projektu.</span><span class="sxs-lookup"><span data-stu-id="5ff22-156">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="5ff22-157">W tym samouczku można zdefiniować obszar nazw [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) najwyższego poziomu przy użyciu słowa kluczowego w pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="5ff22-157">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="5ff22-158">Zastąp kod w oknie kodu następującym kodem i zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="5ff22-158">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="5ff22-159">Biblioteka klas `UtilityLibraries.StringLibrary`, zawiera metodę `StartsWithUpper`o nazwie .</span><span class="sxs-lookup"><span data-stu-id="5ff22-159">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="5ff22-160">Ta metoda <xref:System.Boolean> zwraca wartość, która wskazuje, czy bieżące wystąpienie ciągu rozpoczyna się wielkimi literami.</span><span class="sxs-lookup"><span data-stu-id="5ff22-160">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="5ff22-161">Standard Unicode odróżnia wielkie litery od małych liter.</span><span class="sxs-lookup"><span data-stu-id="5ff22-161">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="5ff22-162">Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> zwraca, `true` jeśli znak jest wielkimi literami.</span><span class="sxs-lookup"><span data-stu-id="5ff22-162">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="5ff22-163">Na pasku menu wybierz pozycję **Zbuduj** > **rozwiązanie kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="5ff22-163">On the menu bar, select **Build** > **Build Solution**.</span></span>

---

   <span data-ttu-id="5ff22-164">Projekt należy skompilować bez błędów.</span><span class="sxs-lookup"><span data-stu-id="5ff22-164">The project should compile without error.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5ff22-165">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="5ff22-165">Next steps</span></span>

<span data-ttu-id="5ff22-166">Biblioteka została pomyślnie utworzona.</span><span class="sxs-lookup"><span data-stu-id="5ff22-166">You've successfully built the library.</span></span> <span data-ttu-id="5ff22-167">Ponieważ nie zostały wywołane żadnej z jego metod, nie wiesz, czy to działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="5ff22-167">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="5ff22-168">Następnym krokiem w tworzeniu biblioteki jest przetestowanie jej.</span><span class="sxs-lookup"><span data-stu-id="5ff22-168">The next step in developing your library is to test it.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5ff22-169">Tworzenie projektu testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="5ff22-169">Create a unit test project</span></span>](testing-library-with-visual-studio.md)
