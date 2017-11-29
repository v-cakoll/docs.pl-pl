---
title: "Kompilowanie biblioteki klas z języka Visual Basic i .NET Core w Visual Studio 2017 r."
description: "Informacje o sposobie tworzenia biblioteki klas napisane w języku Visual Basic przy użyciu programu Visual Studio 2017 r."
keywords: Oprogramowanie .NET core, .NET Standard klasy biblioteki 2017 programu Visual Studio, Visual Basic
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-vb
dev_langs: vb
ms.openlocfilehash: 6572f35b1e2b652c9f2ff5448165ece104f0bdf6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="building-a-class-library-with-visual-basic-and-net-core-in-visual-studio-2017"></a><span data-ttu-id="869a2-104">Kompilowanie biblioteki klas z języka Visual Basic i .NET Core w Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="869a2-104">Building a class library with Visual Basic and .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="869a2-105">A *biblioteki klas* definiuje typy i metody, które są wywoływane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="869a2-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="869a2-106">Biblioteka klas, przeznaczonego dla programu .NET 2.0 standardowe umożliwia biblioteki ma być wywoływana przez wszystkie implementacja .NET obsługuje tej wersji programu .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="869a2-106">A class library that targets the .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of the .NET Standard.</span></span> <span data-ttu-id="869a2-107">Po zakończeniu biblioteki klas, można wybrać ją rozpowszechnić jako części innych firm lub czy chcesz dołączyć go jako składnik powiązane z jedną lub więcej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="869a2-107">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="869a2-108">Listę wersji platformy .NET Standard i platformy obsługują zawiera [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="869a2-108">For a list of the .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="869a2-109">W tym temacie utworzysz biblioteki prostego narzędzia, która zawiera jedną metodę obsługi ciągów.</span><span class="sxs-lookup"><span data-stu-id="869a2-109">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="869a2-110">Będzie zaimplementowaniem go jako [— metoda rozszerzenia](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) tak, aby można go wywołać, tak jakby był on członkiem <xref:System.String> klasy.</span><span class="sxs-lookup"><span data-stu-id="869a2-110">You'll implement it as an [extension method](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="creating-a-class-library-solution"></a><span data-ttu-id="869a2-111">Tworzenie rozwiązania biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="869a2-111">Creating a class library solution</span></span>

<span data-ttu-id="869a2-112">Rozpocznij od utworzenia rozwiązania dla projektu biblioteki klas i jej powiązane projekty.</span><span class="sxs-lookup"><span data-stu-id="869a2-112">Start by creating a solution for your class library project and its related projects.</span></span> <span data-ttu-id="869a2-113">Rozwiązanie Visual Studio po prostu służy jako kontener dla jednego lub więcej projektów.</span><span class="sxs-lookup"><span data-stu-id="869a2-113">A Visual Studio Solution just serves as a container for one or more projects.</span></span> <span data-ttu-id="869a2-114">Aby utworzyć rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="869a2-114">To create the solution:</span></span>

1. <span data-ttu-id="869a2-115">Na pasku menu programu Visual Studio wybierz **pliku** > **nowy** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="869a2-115">On the Visual Studio menu bar, choose **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="869a2-116">W **nowy projekt** okna dialogowego, rozwiń węzeł **inne typy projektów** , a następnie wybierz węzeł **rozwiązań programu Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="869a2-116">In the **New Project** dialog, expand the **Other Project Types** node, and select **Visual Studio Solutions**.</span></span> <span data-ttu-id="869a2-117">Nazwa rozwiązania "ClassLibraryProjects" i wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="869a2-117">Name the solution "ClassLibraryProjects" and select the **OK** button.</span></span>

   ![Okno dialogowe nowego projektu](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a><span data-ttu-id="869a2-119">Tworzenie projektu biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="869a2-119">Creating the class library project</span></span>

<span data-ttu-id="869a2-120">Tworzenie projektu biblioteki klas:</span><span class="sxs-lookup"><span data-stu-id="869a2-120">Create your class library project:</span></span>

1. <span data-ttu-id="869a2-121">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ClassLibraryProjects** rozwiązania plików i z menu kontekstowego wybierz **Dodaj** > **nowy Projekt**.</span><span class="sxs-lookup"><span data-stu-id="869a2-121">In **Solution Explorer**, right-click on the **ClassLibraryProjects** solution file and from the context menu, select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="869a2-122">W **Dodawanie nowego projektu** okna dialogowego, rozwiń węzeł **Visual Basic** węzła, następnie wybierz **.NET Standard** węzła następuje **biblioteki klas (.NET Standard)**  szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="869a2-122">In the **Add New Project** dialog, expand the **Visual Basic** node, then select the **.NET Standard** node followed by the **Class Library (.NET Standard)** project template.</span></span> <span data-ttu-id="869a2-123">W **nazwa** tekst Wprowadź "StringLibrary" jako nazwę projektu.</span><span class="sxs-lookup"><span data-stu-id="869a2-123">In the **Name** text box, enter "StringLibrary" as the name of the project.</span></span> <span data-ttu-id="869a2-124">Wybierz **OK** do tworzenia projektu biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="869a2-124">Select **OK** to create the class library project.</span></span>

   ![Dodaj okno dialogowe Nowy projekt](./media/vb-library-with-visual-studio/libproject.png)

   <span data-ttu-id="869a2-126">W środowisku programowania Visual Studio następnie zostanie otwarte okno kodu.</span><span class="sxs-lookup"><span data-stu-id="869a2-126">The code window then opens in the Visual Studio development environment.</span></span> 
 
   ![Visual Studio aplikacji okno kod szablonu domyślnego klasy biblioteki](./media/vb-library-with-visual-studio/stringlibrary.png)

1. <span data-ttu-id="869a2-128">Sprawdź, czy biblioteka jest przeznaczony dla poprawna wersja programu .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="869a2-128">Check to make sure that the library targets the correct version of the .NET Standard.</span></span> <span data-ttu-id="869a2-129">Kliknij prawym przyciskiem myszy na projekt biblioteki w **Eksploratora rozwiązań** systemu windows, następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="869a2-129">Right-click on the library project in the **Solution Explorer** windows, then select **Properties**.</span></span> <span data-ttu-id="869a2-130">**Platformy docelowej** pole tekstowe pokazuje, że firma Microsoft docelowych .NET 2.0 standardowa.</span><span class="sxs-lookup"><span data-stu-id="869a2-130">The **Target Framework** text box shows that we're targeting .NET Standard 2.0.</span></span>

   ![Właściwości projektu biblioteki klas](./media/library-with-visual-studio/properties.png)

1. <span data-ttu-id="869a2-132">Również w **właściwości** okna dialogowego, wyczyść tekst w **głównej przestrzeni nazw** pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="869a2-132">Also in the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="869a2-133">Dla każdego projektu Visual Basic automatycznie tworzy przestrzeni nazw, który odpowiada nazwie projektu, a wszystkie przestrzenie nazw zdefiniowane w plików kodu źródłowego są nadrzędne tego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="869a2-133">For each project, Visual Basic automatically creates a namespace that corresponds to the project name, and any namespaces defined in source code files are parents of that namespace.</span></span> <span data-ttu-id="869a2-134">Chcemy zdefiniować przestrzeni nazw najwyższego poziomu za pomocą [ `namespace` ](../../visual-basic/language-reference/statements/namespace-statement.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="869a2-134">We want to define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword.</span></span>
  
1. <span data-ttu-id="869a2-135">Zastąp kod w oknie Kod następujący kod i Zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="869a2-135">Replace the code in the code window with the following code and save the file:</span></span>

  [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="869a2-136">Biblioteka klas `UtilityLibraries.StringLibrary`, zawiera metodę o nazwie `StartsWithUpper`, która zwraca <xref:System.Boolean> wartość, która wskazuje, czy bieżące wystąpienie ciągu rozpoczyna się wielką literę.</span><span class="sxs-lookup"><span data-stu-id="869a2-136">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`, which returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="869a2-137">Unicode standard rozróżnia wielkich liter z małych liter.</span><span class="sxs-lookup"><span data-stu-id="869a2-137">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="869a2-138"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> Metoda zwraca `true` Jeśli znak jest wielką.</span><span class="sxs-lookup"><span data-stu-id="869a2-138">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="869a2-139">Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="869a2-139">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="869a2-140">Projekt powinien kompilacji bez błędów.</span><span class="sxs-lookup"><span data-stu-id="869a2-140">The project should compile without error.</span></span>

   ![W okienku z wyjściem pokazujący, że kompilacja zakończyła się pomyślnie](./media/library-with-visual-studio/buildsucceeds.png)



## <a name="next-step"></a><span data-ttu-id="869a2-142">Następny krok</span><span class="sxs-lookup"><span data-stu-id="869a2-142">Next step</span></span>

<span data-ttu-id="869a2-143">Został pomyślnie skompilowany biblioteki.</span><span class="sxs-lookup"><span data-stu-id="869a2-143">You've successfully built the library.</span></span> <span data-ttu-id="869a2-144">Ponieważ nie zostało to jeszcze wywołana dowolnej metody, nie wiadomo, czy działa on zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="869a2-144">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="869a2-145">Następny krok w rozwoju biblioteki służy do testowania go przy użyciu [projektu testu jednostki](testing-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="869a2-145">The next step in developing your library is to test it by using a [Unit Test Project](testing-library-with-visual-studio.md).</span></span>
