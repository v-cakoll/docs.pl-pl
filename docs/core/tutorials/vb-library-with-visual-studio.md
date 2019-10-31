---
title: Tworzenie biblioteki klas .NET Standard Visual Basic w programie Visual Studio 2017
description: Dowiedz się, jak utworzyć .NET Standard bibliotekę klas zapisaną w Visual Basic przy użyciu programu Visual Studio 2017
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 1daab377abe3b6b89f73ed48eafadeae4d7eee77
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73100867"
---
# <a name="build-a-net-standard-library-with-visual-basic-and-the-net-core-sdk-in-visual-studio-2017"></a><span data-ttu-id="63114-103">Tworzenie biblioteki .NET Standard z Visual Basic i zestaw .NET Core SDK w programie Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="63114-103">Build a .NET Standard library with Visual Basic and the .NET Core SDK in Visual Studio 2017</span></span>

<span data-ttu-id="63114-104">*Biblioteka klas* definiuje typy i metody, które są wywoływane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="63114-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="63114-105">Biblioteka klas, która jest przeznaczona dla .NET Standard 2,0 umożliwia wywoływanie biblioteki przez dowolną implementację platformy .NET, która obsługuje tę wersję .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="63114-105">A class library that targets the .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of the .NET Standard.</span></span> <span data-ttu-id="63114-106">Po zakończeniu biblioteki klas możesz zdecydować, czy chcesz ją rozpowszechnić jako składnik innej firmy, czy chcesz ją dołączyć jako składnik pakietu z co najmniej jedną aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="63114-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="63114-107">Listę wersji .NET Standard i obsługiwanych przez nich platform można znaleźć w temacie [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="63114-107">For a list of the .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="63114-108">W tym temacie utworzysz prostą bibliotekę narzędzi, która zawiera pojedynczą metodę obsługi ciągów.</span><span class="sxs-lookup"><span data-stu-id="63114-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="63114-109">Należy zaimplementować ją jako [metodę rozszerzenia](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) , aby można było wywołać ją tak, jakby była elementem członkowskim klasy <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="63114-109">You'll implement it as an [extension method](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="creating-a-class-library-solution"></a><span data-ttu-id="63114-110">Tworzenie rozwiązania biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="63114-110">Creating a class library solution</span></span>

<span data-ttu-id="63114-111">Zacznij od utworzenia rozwiązania dla projektu biblioteki klas i powiązanych z nim projektów.</span><span class="sxs-lookup"><span data-stu-id="63114-111">Start by creating a solution for your class library project and its related projects.</span></span> <span data-ttu-id="63114-112">Rozwiązanie programu Visual Studio służy tylko jako kontener dla jednego lub wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="63114-112">A Visual Studio Solution just serves as a container for one or more projects.</span></span> <span data-ttu-id="63114-113">Aby utworzyć rozwiązanie:</span><span class="sxs-lookup"><span data-stu-id="63114-113">To create the solution:</span></span>

1. <span data-ttu-id="63114-114">Na pasku menu programu Visual Studio wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="63114-114">On the Visual Studio menu bar, choose **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="63114-115">W oknie dialogowym **Nowy projekt** rozwiń węzeł **Inne typy projektów** , a następnie wybierz pozycję **rozwiązania programu Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="63114-115">In the **New Project** dialog, expand the **Other Project Types** node, and select **Visual Studio Solutions**.</span></span> <span data-ttu-id="63114-116">Nazwij rozwiązanie "ClassLibraryProjects" i wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="63114-116">Name the solution "ClassLibraryProjects" and select the **OK** button.</span></span>

   ![Okno dialogowe tworzenia nowego projektu testowego programu Visual Studio](./media/library-with-visual-studio/new-project-dialog.png)

## <a name="creating-the-class-library-project"></a><span data-ttu-id="63114-118">Tworzenie projektu biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="63114-118">Creating the class library project</span></span>

<span data-ttu-id="63114-119">Utwórz projekt biblioteki klas:</span><span class="sxs-lookup"><span data-stu-id="63114-119">Create your class library project:</span></span>

1. <span data-ttu-id="63114-120">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik rozwiązania **ClassLibraryProjects** i z menu kontekstowego wybierz pozycję **Dodaj** > **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="63114-120">In **Solution Explorer**, right-click on the **ClassLibraryProjects** solution file and from the context menu, select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="63114-121">W oknie dialogowym **Dodaj nowy projekt** rozwiń węzeł **Visual Basic** , a następnie wybierz węzeł **.NET Standard** , po którym następuje szablon projektu **Biblioteka klas (.NET standard)** .</span><span class="sxs-lookup"><span data-stu-id="63114-121">In the **Add New Project** dialog, expand the **Visual Basic** node, then select the **.NET Standard** node followed by the **Class Library (.NET Standard)** project template.</span></span> <span data-ttu-id="63114-122">W polu tekstowym **Nazwa** wprowadź wartość "StringLibrary" jako nazwę projektu.</span><span class="sxs-lookup"><span data-stu-id="63114-122">In the **Name** text box, enter "StringLibrary" as the name of the project.</span></span> <span data-ttu-id="63114-123">Wybierz **przycisk OK** , aby utworzyć projekt biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="63114-123">Select **OK** to create the class library project.</span></span>

   ![Okno dialogowe Dodaj nowy projekt biblioteki programu Visual Studio](./media/vb-library-with-visual-studio/create-new-library-project.png)

   <span data-ttu-id="63114-125">Zostanie otwarte okno kod w środowisku deweloperskim programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="63114-125">The code window then opens in the Visual Studio development environment.</span></span> 
 
   ![Okno aplikacji programu Visual Studio pokazujące domyślny kod szablonu biblioteki klas](./media/vb-library-with-visual-studio/visual-studio-library.png)

1. <span data-ttu-id="63114-127">Upewnij się, że biblioteka jest ukierunkowana na poprawną wersję .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="63114-127">Check to make sure that the library targets the correct version of the .NET Standard.</span></span> <span data-ttu-id="63114-128">Kliknij prawym przyciskiem myszy projekt biblioteki w **Eksplorator rozwiązań** Windows, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="63114-128">Right-click on the library project in the **Solution Explorer** windows, then select **Properties**.</span></span> <span data-ttu-id="63114-129">Pole tekstowe **Struktura docelowa** pokazuje, że są one ukierunkowane na .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="63114-129">The **Target Framework** text box shows that we're targeting .NET Standard 2.0.</span></span>

   ![Właściwości projektu dla biblioteki klas](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="63114-131">W oknie dialogowym **Właściwości** Wyczyść tekst w polu tekstowym **główna przestrzeń nazw** .</span><span class="sxs-lookup"><span data-stu-id="63114-131">Also in the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="63114-132">Dla każdego projektu Visual Basic automatycznie tworzy przestrzeń nazw, która odpowiada nazwie projektu, a wszystkie przestrzenie nazw zdefiniowane w plikach kodu źródłowego są nadrzędne tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="63114-132">For each project, Visual Basic automatically creates a namespace that corresponds to the project name, and any namespaces defined in source code files are parents of that namespace.</span></span> <span data-ttu-id="63114-133">Chcemy zdefiniować przestrzeń nazw najwyższego poziomu za pomocą słowa kluczowego [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="63114-133">We want to define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword.</span></span>
  
1. <span data-ttu-id="63114-134">Zastąp kod w oknie kodu następującym kodem i Zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="63114-134">Replace the code in the code window with the following code and save the file:</span></span>

  [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="63114-135">Biblioteka klas `UtilityLibraries.StringLibrary`, zawiera metodę o nazwie `StartsWithUpper`, która zwraca <xref:System.Boolean> wartość wskazującą, czy bieżące wystąpienie ciągu zaczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="63114-135">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`, which returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="63114-136">Standard Unicode rozróżnia wielkie litery od małych liter.</span><span class="sxs-lookup"><span data-stu-id="63114-136">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="63114-137">Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> zwraca `true`, jeśli znak jest pisany wielką literą.</span><span class="sxs-lookup"><span data-stu-id="63114-137">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="63114-138">Na pasku menu wybierz kolejno opcje **kompiluj** > **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="63114-138">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="63114-139">Projekt powinien zostać skompilowany bez błędu.</span><span class="sxs-lookup"><span data-stu-id="63114-139">The project should compile without error.</span></span>

   ![Okienko danych wyjściowych pokazujące, że kompilacja powiodła się](./media/library-with-visual-studio/output-pane-successful-build.png)

## <a name="next-step"></a><span data-ttu-id="63114-141">Następny krok</span><span class="sxs-lookup"><span data-stu-id="63114-141">Next step</span></span>

<span data-ttu-id="63114-142">Biblioteka została pomyślnie skompilowana.</span><span class="sxs-lookup"><span data-stu-id="63114-142">You've successfully built the library.</span></span> <span data-ttu-id="63114-143">Ponieważ nie została wywołana żadna z jej metod, nie wiesz, czy działa ona zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="63114-143">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="63114-144">Następnym krokiem w opracowaniu biblioteki jest przetestowanie jej przy użyciu [projektu testów jednostkowych](testing-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="63114-144">The next step in developing your library is to test it by using a [Unit Test Project](testing-library-with-visual-studio.md).</span></span>
