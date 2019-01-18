---
title: Tworzenie C# biblioteki .NET Standard w programie Visual Studio 2017
description: Dowiedz się, jak utworzyć bibliotekę klas .NET Standard, napisany w języku C# za pomocą programu Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 6228cd93b275a059da63a8b8e3408032d78c5e39
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362018"
---
# <a name="build-a-net-standard-library-with-c-and-the-net-core-sdk-in-visual-studio-2017"></a><span data-ttu-id="dbb2d-103">Tworzenie biblioteki .NET Standard z C# i .NET Core SDK w programie Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="dbb2d-103">Build a .NET Standard library with C# and the .NET Core SDK in Visual Studio 2017</span></span>

<span data-ttu-id="dbb2d-104">A *biblioteki klas* Określa typy i metody, które są wywoływane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="dbb2d-105">Biblioteka klas, który jest przeznaczony dla .NET Standard 2.0 umożliwia biblioteki można wywoływać za pomocą dowolnego implementacji .NET, która obsługuje daną wersję .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-105">A class library that targets the .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of the .NET Standard.</span></span> <span data-ttu-id="dbb2d-106">Po zakończeniu biblioteki klas, można zdecydować, czy chcesz rozprowadzić go jako składników innych firm lub tego, czy chcesz dołączyć go jako składnik powiązane z jedną lub więcej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="dbb2d-107">Aby uzyskać listę wersji programu .NET Standard i platform, które obsługują, zobacz [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="dbb2d-107">For a list of the .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="dbb2d-108">W tym temacie utworzysz bibliotekę prostego narzędzia, która zawiera jedną metodę obsługi ciągów.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="dbb2d-109">Będzie implementowana jako [— metoda rozszerzenia](../../csharp/programming-guide/classes-and-structs/extension-methods.md) tak, aby można go wywołać, tak jakby był on członkiem <xref:System.String> klasy.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-109">You'll implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="creating-a-class-library-solution"></a><span data-ttu-id="dbb2d-110">Tworzenie rozwiązania biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="dbb2d-110">Creating a class library solution</span></span>

<span data-ttu-id="dbb2d-111">Rozpocznij od utworzenia rozwiązania dla Twojego projektu biblioteki klas i jej powiązane projekty.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-111">Start by creating a solution for your class library project and its related projects.</span></span> <span data-ttu-id="dbb2d-112">Rozwiązania programu Visual Studio są po prostu służy jako kontener dla jednego lub więcej projektów.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-112">A Visual Studio Solution just serves as a container for one or more projects.</span></span> <span data-ttu-id="dbb2d-113">Aby utworzyć rozwiązanie:</span><span class="sxs-lookup"><span data-stu-id="dbb2d-113">To create the solution:</span></span>

1. <span data-ttu-id="dbb2d-114">Na pasku menu programu Visual Studio, wybierz **pliku** > **New** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-114">On the Visual Studio menu bar, choose **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="dbb2d-115">W **nowy projekt** okna dialogowego, rozwiń węzeł **inne typy projektów** , a następnie wybierz węzeł **Visual Studio Solutions**.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-115">In the **New Project** dialog, expand the **Other Project Types** node, and select **Visual Studio Solutions**.</span></span> <span data-ttu-id="dbb2d-116">Nazwij rozwiązanie "ClassLibraryProjects", a następnie wybierz pozycję **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-116">Name the solution "ClassLibraryProjects" and select the **OK** button.</span></span>

   ![Okno dialogowe nowego projektu za pomocą nowe puste rozwiązanie wyróżniony](./media/library-with-visual-studio/new-project-dialog.png)

## <a name="creating-the-class-library-project"></a><span data-ttu-id="dbb2d-118">Tworzenie projektu biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="dbb2d-118">Creating the class library project</span></span>

<span data-ttu-id="dbb2d-119">Utwórz projekt biblioteki klas:</span><span class="sxs-lookup"><span data-stu-id="dbb2d-119">Create your class library project:</span></span>

1. <span data-ttu-id="dbb2d-120">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ClassLibraryProjects** rozwiązania pliku, a następnie z menu kontekstowego wybierz pozycję **Dodaj** > **New Projekt**.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-120">In **Solution Explorer**, right-click on the **ClassLibraryProjects** solution file and from the context menu, select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="dbb2d-121">W **Dodaj nowy projekt** okna dialogowego, rozwiń węzeł **Visual C#** węzła, następnie wybierz pozycję **.NET Standard** węzła następuje **biblioteki klas (.NET Standard)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-121">In the **Add New Project** dialog, expand the **Visual C#** node, then select the **.NET Standard** node followed by the **Class Library (.NET Standard)** project template.</span></span> <span data-ttu-id="dbb2d-122">W **nazwa** tekstu wprowadź "StringLibrary" jako nazwę projektu.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-122">In the **Name** text box, enter "StringLibrary" as the name of the project.</span></span> <span data-ttu-id="dbb2d-123">Wybierz **OK** Aby utworzyć projekt biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-123">Select **OK** to create the class library project.</span></span>

   ![Dodawanie okna dialogowego Nowy projekt biblioteki](./media/library-with-visual-studio/add-new-library-project.png)

   <span data-ttu-id="dbb2d-125">W oknie kodu, a następnie zostanie otwarta w środowisku programowania Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-125">The code window then opens in the Visual Studio development environment.</span></span>

   ![Visual Studio okna aplikacji, przedstawiający kod szablonu domyślnego klasy biblioteki](./media/library-with-visual-studio/string-library-project.png)

1. <span data-ttu-id="dbb2d-127">Sprawdź, czy nasza biblioteka jest przeznaczony dla prawidłowej wersji programu .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-127">Check to make sure that our library targets the correct version of the .NET Standard.</span></span> <span data-ttu-id="dbb2d-128">Kliknij prawym przyciskiem myszy na projekt biblioteki w **Eksploratora rozwiązań** systemu windows, następnie wybierz pozycję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-128">Right-click on the library project in the **Solution Explorer** windows, then select **Properties**.</span></span> <span data-ttu-id="dbb2d-129">**Platformę docelową** pole tekstowe pokazuje, że firma Microsoft objęci .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-129">The **Target Framework** text box shows that we're targeting .NET Standard 2.0.</span></span>

   ![Właściwości projektu biblioteki klas](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="dbb2d-131">Zastąp kod w oknie Kod następującym kodem, a następnie zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="dbb2d-131">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   <span data-ttu-id="dbb2d-132">Biblioteka klas `UtilityLibraries.StringLibrary`, zawiera metodę o nazwie `StartsWithUpper`, co powoduje zwrócenie <xref:System.Boolean> wartość, która wskazuje, czy bieżące wystąpienie ciągu rozpoczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-132">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`, which returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="dbb2d-133">Unicode standard rozróżnia wielkie litery z małych liter.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-133">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="dbb2d-134"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> Metoda zwraca `true` Jeśli znak jest wielką literą.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-134">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="dbb2d-135">Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-135">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="dbb2d-136">Projekt powinien być skompilowana bez błędów.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-136">The project should compile without error.</span></span>

   ![Okienko danych wyjściowych, pokazujący, że kompilacja zakończyła się pomyślnie](./media/library-with-visual-studio/output-pane-successful-build.png)

## <a name="next-step"></a><span data-ttu-id="dbb2d-138">Następny krok</span><span class="sxs-lookup"><span data-stu-id="dbb2d-138">Next step</span></span>

<span data-ttu-id="dbb2d-139">Został pomyślnie skompilowany biblioteki.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-139">You've successfully built the library.</span></span> <span data-ttu-id="dbb2d-140">Ponieważ jeszcze nie wywołać dowolną z jego metod, nie wiadomo, czy działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="dbb2d-140">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="dbb2d-141">Następnym krokiem w tworzeniu biblioteki jest przetestowanie go za pomocą [projektu testu jednostkowego](testing-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="dbb2d-141">The next step in developing your library is to test it by using a [Unit Test Project](testing-library-with-visual-studio.md).</span></span>