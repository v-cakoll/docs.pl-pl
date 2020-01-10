---
title: Korzystanie z biblioteki .NET Standard w programie Visual Studio
description: Tworzenie aplikacji .NET Core, która wywołuje elementy członkowskie innej biblioteki klas z programem Visual Studio 2019.
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: ec9c6f992bcd4a76e2f70018f3facca42b7b660c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714068"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="e2874-103">Korzystanie z biblioteki .NET Standard w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e2874-103">Consume a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="e2874-104">Po utworzeniu biblioteki klas .NET Standard, przetestowaniu i skompilowaniu wersji biblioteki, następnym krokiem jest udostępnienie jej obiektom wywołującym.</span><span class="sxs-lookup"><span data-stu-id="e2874-104">Once you've created a .NET Standard class library, tested it, and built a release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="e2874-105">Możesz to zrobić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="e2874-105">You can do this in two ways:</span></span>

- <span data-ttu-id="e2874-106">Jeśli biblioteka będzie używana przez pojedyncze rozwiązanie (na przykład w przypadku składnika w pojedynczej dużej aplikacji), można dołączyć go jako projekt w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="e2874-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>
- <span data-ttu-id="e2874-107">Jeśli biblioteka będzie publicznie dostępna, możesz ją rozpowszechnić jako pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="e2874-107">If the library will be publicly available, you can distribute it as a NuGet package.</span></span>

<span data-ttu-id="e2874-108">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="e2874-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="e2874-109">Dodaj do rozwiązania aplikację konsolową, która odwołuje się do projektu biblioteki .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="e2874-109">Add a console app to your solution that references a .NET Standard library project.</span></span>
> - <span data-ttu-id="e2874-110">Utwórz pakiet NuGet zawierający projekt biblioteki .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="e2874-110">Create a NuGet package that contains a .NET Standard library project.</span></span>

## <a name="add-a-console-app-to-your-solution"></a><span data-ttu-id="e2874-111">Dodawanie aplikacji konsolowej do rozwiązania</span><span class="sxs-lookup"><span data-stu-id="e2874-111">Add a console app to your solution</span></span>

<span data-ttu-id="e2874-112">Podobnie jak w przypadku testów jednostkowych w tym samym rozwiązaniu co Biblioteka klas w [testowaniu biblioteki .NET standard w programie Visual Studio](testing-library-with-visual-studio.md), możesz dołączyć aplikację jako część tego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="e2874-112">Just as you included unit tests in the same solution as your class library in [Test a .NET Standard library in Visual Studio](testing-library-with-visual-studio.md), you can include your application as part of that solution.</span></span> <span data-ttu-id="e2874-113">Można na przykład użyć biblioteki klas w aplikacji konsolowej, która wyświetla użytkownikowi komunikat, aby wprowadzić ciąg i określić, czy jego pierwszy znak jest pisany wielkimi literami:</span><span class="sxs-lookup"><span data-stu-id="e2874-113">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

1. <span data-ttu-id="e2874-114">Otwórz rozwiązanie `ClassLibraryProjects` utworzone w [bibliotece kompilacja .NET standard w artykule Visual Studio](library-with-visual-studio.md) .</span><span class="sxs-lookup"><span data-stu-id="e2874-114">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="e2874-115">Dodaj nową aplikację konsolową .NET Core do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="e2874-115">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="e2874-116">Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj** > **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="e2874-116">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="e2874-117">Na stronie **Dodawanie nowego projektu** wprowadź w polu wyszukiwania **konsolę** .</span><span class="sxs-lookup"><span data-stu-id="e2874-117">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="e2874-118">Wybierz **C#** lub **Visual Basic** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform.</span><span class="sxs-lookup"><span data-stu-id="e2874-118">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="e2874-119">Wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="e2874-119">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="e2874-120">Na stronie **Konfiguruj nowy projekt** wprowadź wartość **Prezentacja** w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="e2874-120">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="e2874-121">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="e2874-121">Then, choose **Create**.</span></span>

1. <span data-ttu-id="e2874-122">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **pokazu** i wybierz polecenie **Ustaw jako projekt startowy** w menu kontekstowym.</span><span class="sxs-lookup"><span data-stu-id="e2874-122">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Menu kontekstowe projektu programu Visual Studio, aby ustawić projekt startowy](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="e2874-124">Początkowo projekt nie ma dostępu do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="e2874-124">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="e2874-125">Aby zezwolić na wywoływanie metod w bibliotece klas, należy utworzyć odwołanie do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="e2874-125">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="e2874-126">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **zależności** projektu `ShowCase`, a następnie wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="e2874-126">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Dodaj menu kontekstowe odwołania w programie Visual Studio](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="e2874-128">W oknie dialogowym **Menedżer odwołań** wybierz pozycję **StringLibrary**, projekt biblioteki klas, a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="e2874-128">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Okno dialogowe programu Reference Manager z wybraną pozycją StringLibrary](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="e2874-130">W oknie kodu dla pliku *program.cs* lub *program. vb* Zastąp cały kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="e2874-130">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code:</span></span>

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="e2874-131">Kod używa zmiennej `row`, aby zachować liczbę wierszy danych zapisaną w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="e2874-131">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="e2874-132">Za każdym razem, gdy jest większy lub równy 25, kod czyści okno konsoli i wyświetla komunikat dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e2874-132">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="e2874-133">Program poprosi użytkownika o wprowadzenie ciągu.</span><span class="sxs-lookup"><span data-stu-id="e2874-133">The program prompts the user to enter a string.</span></span> <span data-ttu-id="e2874-134">Wskazuje, czy ciąg rozpoczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="e2874-134">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="e2874-135">Jeśli użytkownik naciśnie klawisz ENTER bez wprowadzania ciągu, aplikacja zostanie zakończona, a okno konsoli zostanie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="e2874-135">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="e2874-136">W razie potrzeby zmień pasek narzędzi, aby skompilować wydanie **debugowania** projektu `ShowCase`.</span><span class="sxs-lookup"><span data-stu-id="e2874-136">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="e2874-137">Skompiluj i uruchom program, wybierając zieloną strzałkę na przycisku **Pokaz** .</span><span class="sxs-lookup"><span data-stu-id="e2874-137">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Pasek narzędzi projektu programu Visual Studio z widocznym przyciskiem Debuguj](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

<span data-ttu-id="e2874-139">Można debugować i publikować aplikację, która korzysta z tej biblioteki, wykonując czynności opisane w sekcji [debugowanie C# aplikacji .NET Core Hello world lub jej Visual Basic przy użyciu programu Visual Studio](debugging-with-visual-studio.md) i [opublikowanie aplikacji .NET Core Hello World przy użyciu programu Visual Studio](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="e2874-139">You can debug and publish the application that uses this library by following the steps in [Debug your C# or Visual Basic .NET Core Hello World application using Visual Studio](debugging-with-visual-studio.md) and [Publish your .NET Core Hello World application with Visual Studio](publishing-with-visual-studio.md).</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="e2874-140">Tworzenie pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="e2874-140">Create a NuGet package</span></span>

<span data-ttu-id="e2874-141">Bibliotekę klas można udostępnić publicznie, publikując ją jako pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="e2874-141">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="e2874-142">Program Visual Studio nie obsługuje tworzenia pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="e2874-142">Visual Studio doesn't support the creation of NuGet packages.</span></span> <span data-ttu-id="e2874-143">Aby go utworzyć, należy użyć poleceń interfejs wiersza polecenia platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="e2874-143">To create one, you need to use the .NET Core CLI commands:</span></span>

1. <span data-ttu-id="e2874-144">Otwórz okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="e2874-144">Open a console window.</span></span>

   <span data-ttu-id="e2874-145">Na przykład wpisz **wiersz polecenia** w polu wyszukiwania na pasku zadań systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e2874-145">For example, enter **Command Prompt** in the search box on the Windows task bar.</span></span> <span data-ttu-id="e2874-146">Wybierz pozycję **wiersz polecenia** aplikacja klasyczna lub naciśnij klawisz **Enter** , jeśli jest już zaznaczona w wynikach wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="e2874-146">Select the **Command Prompt** desktop app or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="e2874-147">Przejdź do katalogu projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="e2874-147">Navigate to your library's project directory.</span></span> <span data-ttu-id="e2874-148">Katalog zawiera kod źródłowy i plik projektu, *StringLibrary. csproj* lub *StringLibrary. vbproj*.</span><span class="sxs-lookup"><span data-stu-id="e2874-148">The directory contains your source code and a project file, *StringLibrary.csproj* or *StringLibrary.vbproj*.</span></span>

1. <span data-ttu-id="e2874-149">Uruchom polecenie [dotnet Pack](../tools/dotnet-pack.md) , aby wygenerować pakiet z rozszerzeniem *. nupkg* :</span><span class="sxs-lookup"><span data-stu-id="e2874-149">Run the [dotnet pack](../tools/dotnet-pack.md) command to generate a package with a *.nupkg* extension:</span></span>

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > <span data-ttu-id="e2874-150">Jeśli katalog zawierający program *dotnet. exe* nie znajduje się w ścieżce, można znaleźć jego lokalizację, wprowadzając `where dotnet.exe` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="e2874-150">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="e2874-151">Aby uzyskać więcej informacji na temat tworzenia pakietów NuGet, zobacz [jak utworzyć pakiet NuGet za pomocą narzędzi międzyplatformowych](../deploying/creating-nuget-packages.md).</span><span class="sxs-lookup"><span data-stu-id="e2874-151">For more information on creating NuGet packages, see [How to Create a NuGet Package with Cross Platform Tools](../deploying/creating-nuget-packages.md).</span></span>
