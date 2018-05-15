---
title: Tworzenie .NET Standard biblioteki klas C# i .NET Core w Visual Studio 2017 r.
description: Informacje o sposobie tworzenia biblioteki klas .NET Standard napisane w języku C# za pomocą programu Visual Studio 2017 r.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.openlocfilehash: fa265dc5e1101c54ae8d65ad9a3232cd6bd4e52a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="building-a-class-library-with-c-and-net-core-in-visual-studio-2017"></a><span data-ttu-id="afc2b-103">Kompilowanie biblioteki klas C# i .NET Core w Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="afc2b-103">Building a class library with C# and .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="afc2b-104">A *biblioteki klas* definiuje typy i metody, które są wywoływane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="afc2b-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="afc2b-105">Biblioteka klas, przeznaczonego dla programu .NET 2.0 standardowe umożliwia biblioteki ma być wywoływana przez wszystkie implementacja .NET obsługuje tej wersji programu .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="afc2b-105">A class library that targets the .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of the .NET Standard.</span></span> <span data-ttu-id="afc2b-106">Po zakończeniu biblioteki klas, można wybrać ją rozpowszechnić jako części innych firm lub czy chcesz dołączyć go jako składnik powiązane z jedną lub więcej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="afc2b-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="afc2b-107">Listę wersji platformy .NET Standard i platformy obsługują zawiera [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="afc2b-107">For a list of the .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="afc2b-108">W tym temacie utworzysz biblioteki prostego narzędzia, która zawiera jedną metodę obsługi ciągów.</span><span class="sxs-lookup"><span data-stu-id="afc2b-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="afc2b-109">Będzie zaimplementowaniem go jako [— metoda rozszerzenia](../../csharp/programming-guide/classes-and-structs/extension-methods.md) tak, aby można go wywołać, tak jakby był on członkiem <xref:System.String> klasy.</span><span class="sxs-lookup"><span data-stu-id="afc2b-109">You'll implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="creating-a-class-library-solution"></a><span data-ttu-id="afc2b-110">Tworzenie rozwiązania biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="afc2b-110">Creating a class library solution</span></span>

<span data-ttu-id="afc2b-111">Rozpocznij od utworzenia rozwiązania dla projektu biblioteki klas i jej powiązane projekty.</span><span class="sxs-lookup"><span data-stu-id="afc2b-111">Start by creating a solution for your class library project and its related projects.</span></span> <span data-ttu-id="afc2b-112">Rozwiązanie Visual Studio po prostu służy jako kontener dla jednego lub więcej projektów.</span><span class="sxs-lookup"><span data-stu-id="afc2b-112">A Visual Studio Solution just serves as a container for one or more projects.</span></span> <span data-ttu-id="afc2b-113">Aby utworzyć rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="afc2b-113">To create the solution:</span></span>

1. <span data-ttu-id="afc2b-114">Na pasku menu programu Visual Studio wybierz **pliku** > **nowy** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="afc2b-114">On the Visual Studio menu bar, choose **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="afc2b-115">W **nowy projekt** okna dialogowego, rozwiń węzeł **inne typy projektów** , a następnie wybierz węzeł **rozwiązań programu Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="afc2b-115">In the **New Project** dialog, expand the **Other Project Types** node, and select **Visual Studio Solutions**.</span></span> <span data-ttu-id="afc2b-116">Nazwa rozwiązania "ClassLibraryProjects" i wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="afc2b-116">Name the solution "ClassLibraryProjects" and select the **OK** button.</span></span>

   ![Okno dialogowe nowego projektu](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a><span data-ttu-id="afc2b-118">Tworzenie projektu biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="afc2b-118">Creating the class library project</span></span>

<span data-ttu-id="afc2b-119">Tworzenie projektu biblioteki klas:</span><span class="sxs-lookup"><span data-stu-id="afc2b-119">Create your class library project:</span></span>

1. <span data-ttu-id="afc2b-120">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ClassLibraryProjects** rozwiązania plików i z menu kontekstowego wybierz **Dodaj** > **nowy Projekt**.</span><span class="sxs-lookup"><span data-stu-id="afc2b-120">In **Solution Explorer**, right-click on the **ClassLibraryProjects** solution file and from the context menu, select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="afc2b-121">W **Dodawanie nowego projektu** okna dialogowego, rozwiń węzeł **Visual C#** węzła, następnie wybierz **.NET Standard** węzła następuje **(.NET Standard)bibliotekiklas** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="afc2b-121">In the **Add New Project** dialog, expand the **Visual C#** node, then select the **.NET Standard** node followed by the **Class Library (.NET Standard)** project template.</span></span> <span data-ttu-id="afc2b-122">W **nazwa** tekst Wprowadź "StringLibrary" jako nazwę projektu.</span><span class="sxs-lookup"><span data-stu-id="afc2b-122">In the **Name** text box, enter "StringLibrary" as the name of the project.</span></span> <span data-ttu-id="afc2b-123">Wybierz **OK** do tworzenia projektu biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="afc2b-123">Select **OK** to create the class library project.</span></span>

   ![Dodaj okno dialogowe Nowy projekt](./media/library-with-visual-studio/libproject.png)

   <span data-ttu-id="afc2b-125">W środowisku programowania Visual Studio następnie zostanie otwarte okno kodu.</span><span class="sxs-lookup"><span data-stu-id="afc2b-125">The code window then opens in the Visual Studio development environment.</span></span>

   ![Visual Studio aplikacji okno kod szablonu domyślnego klasy biblioteki](./media/library-with-visual-studio/stringlibrary.png)

1. <span data-ttu-id="afc2b-127">Sprawdź, czy nasza Biblioteka celem poprawna wersja programu .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="afc2b-127">Check to make sure that our library targets the correct version of the .NET Standard.</span></span> <span data-ttu-id="afc2b-128">Kliknij prawym przyciskiem myszy na projekt biblioteki w **Eksploratora rozwiązań** systemu windows, następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="afc2b-128">Right-click on the library project in the **Solution Explorer** windows, then select **Properties**.</span></span> <span data-ttu-id="afc2b-129">**Platformy docelowej** pole tekstowe pokazuje, że firma Microsoft docelowych .NET 2.0 standardowa.</span><span class="sxs-lookup"><span data-stu-id="afc2b-129">The **Target Framework** text box shows that we're targeting .NET Standard 2.0.</span></span>

   ![Właściwości projektu biblioteki klas](./media/library-with-visual-studio/properties.png)

1. <span data-ttu-id="afc2b-131">Zastąp kod w oknie Kod następujący kod i Zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="afc2b-131">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   <span data-ttu-id="afc2b-132">Biblioteka klas `UtilityLibraries.StringLibrary`, zawiera metodę o nazwie `StartsWithUpper`, która zwraca <xref:System.Boolean> wartość, która wskazuje, czy bieżące wystąpienie ciągu rozpoczyna się wielką literę.</span><span class="sxs-lookup"><span data-stu-id="afc2b-132">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`, which returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="afc2b-133">Unicode standard rozróżnia wielkich liter z małych liter.</span><span class="sxs-lookup"><span data-stu-id="afc2b-133">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="afc2b-134"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> Metoda zwraca `true` Jeśli znak jest wielką.</span><span class="sxs-lookup"><span data-stu-id="afc2b-134">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="afc2b-135">Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="afc2b-135">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="afc2b-136">Projekt powinien kompilacji bez błędów.</span><span class="sxs-lookup"><span data-stu-id="afc2b-136">The project should compile without error.</span></span>

   ![W okienku z wyjściem pokazujący, że kompilacja zakończyła się pomyślnie](./media/library-with-visual-studio/buildsucceeds.png)

## <a name="next-step"></a><span data-ttu-id="afc2b-138">Następny krok</span><span class="sxs-lookup"><span data-stu-id="afc2b-138">Next step</span></span>

<span data-ttu-id="afc2b-139">Został pomyślnie skompilowany biblioteki.</span><span class="sxs-lookup"><span data-stu-id="afc2b-139">You've successfully built the library.</span></span> <span data-ttu-id="afc2b-140">Ponieważ nie zostało to jeszcze wywołana dowolnej metody, nie wiadomo, czy działa on zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="afc2b-140">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="afc2b-141">Następny krok w rozwoju biblioteki służy do testowania go przy użyciu [projektu testu jednostki](testing-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="afc2b-141">The next step in developing your library is to test it by using a [Unit Test Project](testing-library-with-visual-studio.md).</span></span>