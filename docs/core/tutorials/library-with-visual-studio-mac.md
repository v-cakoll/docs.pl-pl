---
title: Tworzenie biblioteki klas .NET Standard przy użyciu Visual Studio dla komputerów Mac
description: Dowiedz się, jak utworzyć bibliotekę klas .NET Standard przy użyciu Visual Studio dla komputerów Mac.
ms.date: 06/08/2020
ms.openlocfilehash: 3a107fff2fd6aef5e06d9af3eac334fbf5688fa5
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2020
ms.locfileid: "84713743"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-for-mac"></a><span data-ttu-id="a8f54-103">Samouczek: Tworzenie biblioteki .NET Standard przy użyciu Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="a8f54-103">Tutorial: Create a .NET Standard library using Visual Studio for Mac</span></span>

<span data-ttu-id="a8f54-104">W tym samouczku utworzysz prostą bibliotekę klas, która zawiera pojedynczą metodę obsługi ciągów.</span><span class="sxs-lookup"><span data-stu-id="a8f54-104">In this tutorial, you create a simple class library that contains a single string-handling method.</span></span> <span data-ttu-id="a8f54-105">Implementuje ją jako [metodę rozszerzenia](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , aby można było wywołać ją tak, jakby była elementem członkowskim <xref:System.String> klasy.</span><span class="sxs-lookup"><span data-stu-id="a8f54-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="a8f54-106">*Biblioteka klas* definiuje typy i metody, które są wywoływane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="a8f54-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="a8f54-107">Biblioteka klas przeznaczona dla .NET Standard 2,1 może być używana przez aplikację, która jest przeznaczona dla dowolnej implementacji platformy .NET, która obsługuje wersję 2,1 .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="a8f54-107">A class library that targets .NET Standard 2.1 can be used by an application that targets any .NET implementation that supports version 2.1 of .NET Standard.</span></span> <span data-ttu-id="a8f54-108">Po zakończeniu biblioteki klas można ją rozpowszechnić jako składnik innej firmy lub jako składnik pakietu z jedną lub wieloma aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="a8f54-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="a8f54-109">Opinie są wysoce wyceniane.</span><span class="sxs-lookup"><span data-stu-id="a8f54-109">Your feedback is highly valued.</span></span> <span data-ttu-id="a8f54-110">Istnieją dwa sposoby przekazywania opinii zespołowi programistycznemu na Visual Studio dla komputerów Mac:</span><span class="sxs-lookup"><span data-stu-id="a8f54-110">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> - <span data-ttu-id="a8f54-111">W Visual Studio dla komputerów Mac wybierz pozycję **Pomoc**  >  **Zgłoś problem** z menu lub **Zgłoś problem** na ekranie powitalnym, co spowoduje otwarcie okna umożliwiającego zgłoszenie usterki.</span><span class="sxs-lookup"><span data-stu-id="a8f54-111">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which opens a window for filing a bug report.</span></span> <span data-ttu-id="a8f54-112">Swoje opinie możesz śledzić w portalu [Społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/41/index.html).</span><span class="sxs-lookup"><span data-stu-id="a8f54-112">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/41/index.html) portal.</span></span>
> - <span data-ttu-id="a8f54-113">Aby dokonać sugestii, wybierz pozycję **Pomoc**  >  **Podaj sugestię** z menu lub **Podaj sugestię** z ekranu powitalnego, który przeprowadzi Cię do [witryny internetowej społeczność deweloperów Visual Studio dla komputerów Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="a8f54-113">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which takes you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a8f54-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a8f54-114">Prerequisites</span></span>

* <span data-ttu-id="a8f54-115">[Zainstaluj program Visual Studio dla komputerów Mac w wersji 8,6 lub nowszej](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="a8f54-115">[Install Visual Studio for Mac version 8.6 or later](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="a8f54-116">Wybierz opcję zainstalowania platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a8f54-116">Select the option to install .NET Core.</span></span> <span data-ttu-id="a8f54-117">Instalowanie platformy Xamarin jest opcjonalne w przypadku programowania .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a8f54-117">Installing Xamarin is optional for .NET Core development.</span></span> <span data-ttu-id="a8f54-118">Więcej informacji zawierają następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="a8f54-118">For more information, see the following resources:</span></span>

  * <span data-ttu-id="a8f54-119">[Samouczek: instalowanie Visual Studio dla komputerów Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="a8f54-119">[Tutorial: Install Visual Studio for Mac](/visualstudio/mac/installation).</span></span>
  * <span data-ttu-id="a8f54-120">[Obsługiwane wersje macOS](../install/dependencies.md?pivots=os-macos).</span><span class="sxs-lookup"><span data-stu-id="a8f54-120">[Supported macOS versions](../install/dependencies.md?pivots=os-macos).</span></span>
  * <span data-ttu-id="a8f54-121">[Wersje programu .NET Core obsługiwane przez Visual Studio dla komputerów Mac](/visualstudio/mac/net-core-support).</span><span class="sxs-lookup"><span data-stu-id="a8f54-121">[.NET Core versions supported by Visual Studio for Mac](/visualstudio/mac/net-core-support).</span></span>

## <a name="create-a-solution-with-a-class-library-project"></a><span data-ttu-id="a8f54-122">Utwórz rozwiązanie z projektem biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="a8f54-122">Create a solution with a class library project</span></span>

<span data-ttu-id="a8f54-123">Rozwiązanie programu Visual Studio służy jako kontener dla jednego lub wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="a8f54-123">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="a8f54-124">Utwórz rozwiązanie i projekt biblioteki klas w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="a8f54-124">Create a solution and a class library project in the solution.</span></span> <span data-ttu-id="a8f54-125">Kolejne powiązane projekty zostaną dodane do tego samego rozwiązania później.</span><span class="sxs-lookup"><span data-stu-id="a8f54-125">You'll add additional, related projects to the same solution later.</span></span>

1. <span data-ttu-id="a8f54-126">Rozpocznij Visual Studio dla komputerów Mac.</span><span class="sxs-lookup"><span data-stu-id="a8f54-126">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="a8f54-127">W oknie uruchamiania wybierz pozycję **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="a8f54-127">In the start window, select **New Project**.</span></span>

1. <span data-ttu-id="a8f54-128">W oknie dialogowym **Nowy projekt** w węźle **wiele platform** wybierz pozycję **Biblioteka**, a następnie wybierz szablon **Biblioteka .NET Standard** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="a8f54-128">In the **New Project** dialog under the **Multi-Platform** node, select **Library**, then select the **.NET Standard Library** template, and select **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Okno dialogowe Nowy projekt":::

1. <span data-ttu-id="a8f54-130">W oknie dialogowym **Konfigurowanie nowej biblioteki .NET Standard** wybierz pozycję ".NET Standard 2,1", a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="a8f54-130">In the **Configure your new .NET Standard Library** dialog, choose ".NET Standard 2.1", and select **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/choose-net-std-21.png" alt-text="Wybierz .NET Standard 2,1":::

1. <span data-ttu-id="a8f54-132">Nadaj projektowi nazwę "StringLibrary" i rozwiązanie "ClassLibraryProjects".</span><span class="sxs-lookup"><span data-stu-id="a8f54-132">Name the project "StringLibrary" and the solution "ClassLibraryProjects".</span></span> <span data-ttu-id="a8f54-133">Pozostaw opcję **Utwórz katalog projektu w wybranym katalogu rozwiązania** .</span><span class="sxs-lookup"><span data-stu-id="a8f54-133">Leave **Create a project directory within the solution directory** selected.</span></span> <span data-ttu-id="a8f54-134">Wybierz przycisk **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="a8f54-134">Select **Create**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project-options.png" alt-text="Opcje okna dialogowego Visual Studio dla komputerów Mac nowego projektu":::

1. <span data-ttu-id="a8f54-136">Z menu głównego wybierz pozycję **Widok**  >  **okienka**  >  **Solution**, a następnie wybierz ikonę dokowania, aby zachować otwartą konsolę.</span><span class="sxs-lookup"><span data-stu-id="a8f54-136">From the main menu, select **View** > **Pads** > **Solution**, and select the dock icon to keep the pad open.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/solution-dock-icon.png" alt-text="Ikona dokowania dla konsoli rozwiązania":::

1. <span data-ttu-id="a8f54-138">W konsoli **rozwiązania** rozwiń `StringLibrary` węzeł, aby odsłonić plik klasy dostarczony przez szablon, *Class1.cs*.</span><span class="sxs-lookup"><span data-stu-id="a8f54-138">In the **Solution** pad, expand the `StringLibrary` node to reveal the class file provided by the template, *Class1.cs*.</span></span> <span data-ttu-id="a8f54-139"><kbd>naciśnij klawisz Ctrl</kbd>i kliknij plik, wybierz polecenie **Zmień nazwę** z menu kontekstowego, a następnie zmień nazwę pliku na *StringLibrary.cs*.</span><span class="sxs-lookup"><span data-stu-id="a8f54-139"><kbd>ctrl</kbd>-click the file, select **Rename** from the context menu, and rename the file to *StringLibrary.cs*.</span></span> <span data-ttu-id="a8f54-140">Otwórz plik i Zastąp jego zawartość następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="a8f54-140">Open the file and replace the contents with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

1. <span data-ttu-id="a8f54-141">Naciśnij pozycję <kbd>⌘</kbd><kbd>s</kbd> (<kbd>Command</kbd> + <kbd>s</kbd>), aby zapisać plik.</span><span class="sxs-lookup"><span data-stu-id="a8f54-141">Press <kbd>⌘</kbd><kbd>S</kbd> (<kbd>command</kbd>+<kbd>S</kbd>) to save the file.</span></span>

1. <span data-ttu-id="a8f54-142">Wybierz pozycję **Błędy** na marginesie u dołu okna IDE, aby otworzyć panel **Błędy** .</span><span class="sxs-lookup"><span data-stu-id="a8f54-142">Select **Errors** in the margin at the bottom of the IDE window to open the **Errors** panel.</span></span> <span data-ttu-id="a8f54-143">Wybierz przycisk **kompilacja danych wyjściowych** .</span><span class="sxs-lookup"><span data-stu-id="a8f54-143">Select the **Build Output** button.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-error-button.png" alt-text="Dolny margines środowiska IDE programu Visual Studio Mac przedstawiającego przycisk błędy":::

1. <span data-ttu-id="a8f54-145">Z menu wybierz pozycję **kompilacja**  >  **Kompiluj wszystko** .</span><span class="sxs-lookup"><span data-stu-id="a8f54-145">Select **Build** > **Build All** from the menu.</span></span>

   <span data-ttu-id="a8f54-146">Rozwiązanie kompiluje.</span><span class="sxs-lookup"><span data-stu-id="a8f54-146">The solution builds.</span></span> <span data-ttu-id="a8f54-147">Panel dane wyjściowe kompilacji pokazuje, że kompilacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a8f54-147">The build output panel shows that the build is successful.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-build-panel.png" alt-text="Okienko danych wyjściowych kompilacji programu Visual Studio dla komputerów Mac w panelu Błędy z komunikatem Kompilacja zakończona pomyślnie":::

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="a8f54-149">Dodawanie aplikacji konsolowej do rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a8f54-149">Add a console app to the solution</span></span>

<span data-ttu-id="a8f54-150">Dodaj aplikację konsolową, która używa biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="a8f54-150">Add a console application that uses the class library.</span></span> <span data-ttu-id="a8f54-151">Aplikacja wyświetli monit o wprowadzenie ciągu i zgłoszenie, czy ciąg rozpoczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="a8f54-151">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="a8f54-152">W konsoli **rozwiązania** <kbd>naciśnij klawisz Ctrl</kbd>i kliknij `ClassLibraryProjects` rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="a8f54-152">In the **Solution** pad, <kbd>ctrl</kbd>-click the `ClassLibraryProjects` solution.</span></span> <span data-ttu-id="a8f54-153">Dodaj nowy projekt **aplikacji konsoli** , wybierając szablon z szablonów aplikacji **sieci Web i konsoli**  >  **App** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="a8f54-153">Add a new **Console Application** project by selecting the template from the **Web and Console** > **App** templates, and select **Next**.</span></span>

1. <span data-ttu-id="a8f54-154">Wybierz pozycję **.NET Core 3,1** jako **platformę docelową** i wybierz pozycję **dalej**.</span><span class="sxs-lookup"><span data-stu-id="a8f54-154">Select **.NET Core 3.1** as the **Target Framework** and select **Next**.</span></span>

1. <span data-ttu-id="a8f54-155">Nadaj nazwę **pokazowi**projektu.</span><span class="sxs-lookup"><span data-stu-id="a8f54-155">Name the project **ShowCase**.</span></span> <span data-ttu-id="a8f54-156">Wybierz pozycję **Utwórz** , aby utworzyć projekt w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="a8f54-156">Select **Create** to create the project in the solution.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/add-showcase-project.png" alt-text="Dodaj projekt pokazu":::

1. <span data-ttu-id="a8f54-158">Otwórz plik *program.cs* .</span><span class="sxs-lookup"><span data-stu-id="a8f54-158">Open the *Program.cs* file.</span></span> <span data-ttu-id="a8f54-159">Zastąp kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="a8f54-159">Replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="a8f54-160">Program poprosi użytkownika o wprowadzenie ciągu.</span><span class="sxs-lookup"><span data-stu-id="a8f54-160">The program prompts the user to enter a string.</span></span> <span data-ttu-id="a8f54-161">Wskazuje, czy ciąg rozpoczyna się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="a8f54-161">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="a8f54-162">Jeśli użytkownik naciśnie klawisz <kbd>Enter</kbd> bez wprowadzania ciągu, aplikacja zostanie zakończona, a okno konsoli zostanie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="a8f54-162">If the user presses the <kbd>enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

   <span data-ttu-id="a8f54-163">Kod używa `row` zmiennej do obsługi liczby wierszy danych zapisywana w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="a8f54-163">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="a8f54-164">Za każdym razem, gdy jest większy lub równy 25, kod czyści okno konsoli i wyświetla komunikat dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a8f54-164">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="a8f54-165">Dodaj odwołanie do projektu</span><span class="sxs-lookup"><span data-stu-id="a8f54-165">Add a project reference</span></span>

<span data-ttu-id="a8f54-166">Początkowo nowy projekt aplikacji konsolowej nie ma dostępu do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="a8f54-166">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="a8f54-167">Aby zezwolić na wywoływanie metod w bibliotece klas, Utwórz odwołanie do projektu do projektu biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="a8f54-167">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="a8f54-168">W konsoli **rozwiązania** <kbd>, kliknij</kbd>węzeł **zależności** w nowym projekcie **pokazu** .</span><span class="sxs-lookup"><span data-stu-id="a8f54-168">In the **Solutions** pad, <kbd>ctrl</kbd>-click the **Dependencies** node of the new **ShowCase** project.</span></span> <span data-ttu-id="a8f54-169">W menu kontekstowym wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="a8f54-169">In the context menu, select **Add Reference**.</span></span>

1. <span data-ttu-id="a8f54-170">W oknie dialogowym **odwołania** wybierz pozycję **StringLibrary** , a następnie wybierz pozycję **OK**.</span><span class="sxs-lookup"><span data-stu-id="a8f54-170">In the **References** dialog, select **StringLibrary** and select **OK**.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="a8f54-171">Uruchomienie aplikacji</span><span class="sxs-lookup"><span data-stu-id="a8f54-171">Run the app</span></span>

1. <span data-ttu-id="a8f54-172"><kbd>naciśnij klawisz Ctrl</kbd>i kliknij projekt pokazu i wybierz polecenie **Uruchom projekt** z menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="a8f54-172"><kbd>ctrl</kbd>-click on the ShowCase project and select **Run project** from the context menu.</span></span>

1. <span data-ttu-id="a8f54-173">Wypróbuj program, wprowadzając ciągi i naciskając klawisz <kbd>Enter</kbd>, a następnie naciśnij klawisz <kbd>Enter</kbd> , aby wyjść.</span><span class="sxs-lookup"><span data-stu-id="a8f54-173">Try out the program by entering strings and pressing <kbd>enter</kbd>, then press <kbd>enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-console-window.png" alt-text="Visual Studio dla komputerów Mac okno konsoli z uruchomioną aplikacją":::

## <a name="additional-resources"></a><span data-ttu-id="a8f54-175">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="a8f54-175">Additional resources</span></span>

* [<span data-ttu-id="a8f54-176">Tworzenie bibliotek przy użyciu interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="a8f54-176">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="a8f54-177">[Wersje .NET Standard i obsługiwane przez nich platformy](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="a8f54-177">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>
* [<span data-ttu-id="a8f54-178">Visual Studio 2019 dla komputerów Mac — Informacje o wersji</span><span class="sxs-lookup"><span data-stu-id="a8f54-178">Visual Studio 2019 for Mac Release Notes</span></span>](/visualstudio/releasenotes/vs2019-mac-relnotes)

## <a name="next-steps"></a><span data-ttu-id="a8f54-179">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="a8f54-179">Next steps</span></span>

<span data-ttu-id="a8f54-180">W tym samouczku utworzono rozwiązanie i projekt biblioteki oraz dodano projekt aplikacji konsoli, który używa biblioteki.</span><span class="sxs-lookup"><span data-stu-id="a8f54-180">In this tutorial, you created a solution and a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="a8f54-181">W następnym samouczku dodasz projekt testu jednostkowego do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="a8f54-181">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a8f54-182">Testowanie biblioteki .NET Standard za pomocą platformy .NET Core przy użyciu Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="a8f54-182">Test a .NET Standard library with .NET Core using Visual Studio for Mac</span></span>](testing-library-with-visual-studio-mac.md)
