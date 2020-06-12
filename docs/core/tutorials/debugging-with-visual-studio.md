---
title: Debugowanie aplikacji konsolowej .NET Core przy użyciu programu Visual Studio
description: Dowiedz się, jak debugować aplikację konsolową .NET Core przy użyciu programu Visual Studio.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 743603cb037406948190c7090ca3527bfc40db18
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702070"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="9b686-103">Samouczek: debugowanie aplikacji konsolowej .NET Core przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9b686-103">Tutorial: Debug a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="9b686-104">W tym samouczku przedstawiono narzędzia debugowania dostępne w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9b686-104">This tutorial introduces the debugging tools available in Visual Studio.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9b686-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="9b686-105">Prerequisites</span></span>

- <span data-ttu-id="9b686-106">Ten samouczek współpracuje z aplikacją konsolową utworzoną w temacie [Tworzenie aplikacji konsolowej platformy .NET Core w programie Visual Studio 2019](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="9b686-106">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="9b686-107">Użyj konfiguracji kompilacji debugowania</span><span class="sxs-lookup"><span data-stu-id="9b686-107">Use Debug build configuration</span></span>

<span data-ttu-id="9b686-108">*Debugowanie* i *wydanie* to wbudowane konfiguracje kompilacji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9b686-108">*Debug* and *Release* are Visual Studio's built-in build configurations.</span></span> <span data-ttu-id="9b686-109">Konfiguracja kompilacji debugowania umożliwia debugowanie i konfigurację wydania dla ostatecznej dystrybucji wersji.</span><span class="sxs-lookup"><span data-stu-id="9b686-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="9b686-110">W konfiguracji debugowania program kompiluje z pełnymi symbolicznymi informacjami o debugowaniu i bez optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="9b686-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="9b686-111">Optymalizacja komplikuje debugowanie, ponieważ relacja między kodem źródłowym i wygenerowanymi instrukcjami jest bardziej skomplikowana.</span><span class="sxs-lookup"><span data-stu-id="9b686-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="9b686-112">Konfiguracja wydania programu nie ma symbolicznych informacji o debugowaniu i jest w pełni zoptymalizowana.</span><span class="sxs-lookup"><span data-stu-id="9b686-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

 <span data-ttu-id="9b686-113">Domyślnie Visual Studio Code używa konfiguracji kompilacji debugowania, więc nie trzeba jej zmieniać przed debugowaniem.</span><span class="sxs-lookup"><span data-stu-id="9b686-113">By default, Visual Studio Code uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="9b686-114">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9b686-114">Start Visual Studio.</span></span>

1. <span data-ttu-id="9b686-115">Otwórz projekt, który został utworzony w temacie [Tworzenie aplikacji konsolowej platformy .NET Core w programie Visual Studio 2019](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="9b686-115">Open the project that you created in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

   <span data-ttu-id="9b686-116">Bieżąca konfiguracja kompilacji jest pokazywana na pasku narzędzi.</span><span class="sxs-lookup"><span data-stu-id="9b686-116">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="9b686-117">Poniższy obraz paska narzędzi pokazuje, że program Visual Studio jest skonfigurowany do kompilowania wersji do debugowania aplikacji:</span><span class="sxs-lookup"><span data-stu-id="9b686-117">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

   ![Pasek narzędzi programu Visual Studio z wyróżnioną pozycją Debug](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

## <a name="set-a-breakpoint"></a><span data-ttu-id="9b686-119">Ustawianie punktu przerwania</span><span class="sxs-lookup"><span data-stu-id="9b686-119">Set a breakpoint</span></span>

<span data-ttu-id="9b686-120">*Punkt przerwania* tymczasowo przerywa wykonywanie aplikacji przed wykonaniem wiersza z punktem przerwania.</span><span class="sxs-lookup"><span data-stu-id="9b686-120">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="9b686-121">Ustaw *punkt przerwania* w wierszu, który wyświetla nazwę, datę i godzinę, klikając na lewym marginesie okna kod w tym wierszu.</span><span class="sxs-lookup"><span data-stu-id="9b686-121">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window on that line.</span></span> <span data-ttu-id="9b686-122">Lewy margines znajduje się po lewej stronie numerów wierszy.</span><span class="sxs-lookup"><span data-stu-id="9b686-122">The left margin is to the left of the line numbers.</span></span>  <span data-ttu-id="9b686-123">Innym sposobem ustawienia punktu przerwania jest umieszczenie kursora w wierszu kodu, a następnie wybranie polecenia **Debuguj**  >  **Przełącz punkt przerwania** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="9b686-123">Another way to set a breakpoint is by placing the cursor in the line of code and then choosing **Debug** > **Toggle Breakpoint** from the menu bar.</span></span>

   <span data-ttu-id="9b686-124">Jak widać na poniższej ilustracji, program Visual Studio wskazuje wiersz, w którym jest ustawiony punkt przerwania, zaznaczając go i wyświetlając czerwoną kropkę na lewym marginesie.</span><span class="sxs-lookup"><span data-stu-id="9b686-124">As the following image shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   ![Okno programu Visual Studio z ustawionym punktem przerwania](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. <span data-ttu-id="9b686-126">Naciśnij klawisz <kbd>F5</kbd> , aby uruchomić program w trybie debugowania.</span><span class="sxs-lookup"><span data-stu-id="9b686-126">Press <kbd>F5</kbd> to run the program in Debug mode.</span></span> <span data-ttu-id="9b686-127">Innym sposobem rozpoczęcia debugowania jest wybranie opcji **Debuguj**  >  **Rozpocznij debugowanie** z menu.</span><span class="sxs-lookup"><span data-stu-id="9b686-127">Another way to start debugging is by choosing **Debug** > **Start Debugging** from the menu.</span></span>

1. <span data-ttu-id="9b686-128">Wprowadź ciąg w oknie konsoli, gdy program zapyta o nazwę, a następnie naciśnij klawisz <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9b686-128">Enter a string in the console window when the program prompts for a name, and then press <kbd>Enter</kbd>.</span></span>

1. <span data-ttu-id="9b686-129">Wykonanie programu zostaje zatrzymane po osiągnięciu punktu przerwania i przed wykonaniem `Console.WriteLine` metody.</span><span class="sxs-lookup"><span data-stu-id="9b686-129">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="9b686-130">W oknie **Ustawienia lokalne** są wyświetlane wartości zmiennych, które są zdefiniowane w aktualnie wykonywanej metodzie.</span><span class="sxs-lookup"><span data-stu-id="9b686-130">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span>

   ![Zrzut ekranu punktu przerwania w programie Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

## <a name="use-the-immediate-window"></a><span data-ttu-id="9b686-132">Korzystanie z okna bezpośredniego</span><span class="sxs-lookup"><span data-stu-id="9b686-132">Use the Immediate window</span></span>

<span data-ttu-id="9b686-133">Okno **bezpośrednie** umożliwia korzystanie z debugowanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b686-133">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="9b686-134">Możesz interaktywnie zmienić wartość zmiennych, aby zobaczyć, jak ma to wpływ na program.</span><span class="sxs-lookup"><span data-stu-id="9b686-134">You can interactively change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="9b686-135">Jeśli okno **bezpośrednie** nie jest widoczne, Wyświetl je, wybierając pozycję **Debuguj**  >  **Windows**  >  **natychmiast**Windows.</span><span class="sxs-lookup"><span data-stu-id="9b686-135">If the **Immediate** window is not visible, display it by choosing **Debug** > **Windows** > **Immediate**.</span></span>

1. <span data-ttu-id="9b686-136">Wprowadź `name = "Gracie"` w oknie **bezpośrednim** i naciśnij klawisz <kbd>Enter</kbd> .</span><span class="sxs-lookup"><span data-stu-id="9b686-136">Enter `name = "Gracie"` in the **Immediate** window and press the <kbd>Enter</kbd> key.</span></span>

1. <span data-ttu-id="9b686-137">Wprowadź `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` w oknie **bezpośrednim** i naciśnij klawisz <kbd>Enter</kbd> .</span><span class="sxs-lookup"><span data-stu-id="9b686-137">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` in the **Immediate** window and press the <kbd>Enter</kbd> key.</span></span>

   <span data-ttu-id="9b686-138">W oknie **bezpośrednim** zostanie wyświetlona wartość zmiennej ciągu i właściwości <xref:System.DateTime> wartości.</span><span class="sxs-lookup"><span data-stu-id="9b686-138">The **Immediate** window displays the value of the string variable and the properties of the <xref:System.DateTime> value.</span></span> <span data-ttu-id="9b686-139">Ponadto wartości zmiennych są aktualizowane w oknie **zmiennych lokalnych** .</span><span class="sxs-lookup"><span data-stu-id="9b686-139">In addition, the values of the variables are updated in the **Locals** window.</span></span>

   ![Lokalne i natychmiastowe okna w programie Visual Studio 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. <span data-ttu-id="9b686-141">Naciśnij klawisz <kbd>F5</kbd> , aby kontynuować wykonywanie programu.</span><span class="sxs-lookup"><span data-stu-id="9b686-141">Press <kbd>F5</kbd> to continue program execution.</span></span> <span data-ttu-id="9b686-142">Innym sposobem na kontynuowanie jest wybranie opcji **Debuguj**  >  **Kontynuuj** z menu.</span><span class="sxs-lookup"><span data-stu-id="9b686-142">Another way to continue is by choosing **Debug** > **Continue** from the menu.</span></span>

   <span data-ttu-id="9b686-143">Wartości wyświetlane w oknie konsoli odpowiadają zmianom wprowadzonym w oknie **bezpośrednim** .</span><span class="sxs-lookup"><span data-stu-id="9b686-143">The values displayed in the console window correspond to the changes you made in the **Immediate** window.</span></span>

   ![Okno konsoli pokazujące wprowadzone wartości](./media/debugging-with-visual-studio/console-window.png)

1. <span data-ttu-id="9b686-145">Naciśnij dowolny klawisz, aby zamknąć aplikację i zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="9b686-145">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="9b686-146">Ustaw punkt przerwania warunkowego</span><span class="sxs-lookup"><span data-stu-id="9b686-146">Set a conditional breakpoint</span></span>

<span data-ttu-id="9b686-147">Program wyświetla ciąg wprowadzony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9b686-147">The program displays the string that the user enters.</span></span> <span data-ttu-id="9b686-148">Co się stanie, jeśli użytkownik nie wprowadzi niczego?</span><span class="sxs-lookup"><span data-stu-id="9b686-148">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="9b686-149">Można to sprawdzić za pomocą przydatnej funkcji debugowania zwanej *warunkowym punktem przerwania*.</span><span class="sxs-lookup"><span data-stu-id="9b686-149">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="9b686-150">Kliknij prawym przyciskiem myszy czerwoną kropkę reprezentującą punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="9b686-150">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="9b686-151">W menu kontekstowym wybierz pozycję **warunki** , aby otworzyć okno dialogowe **Ustawienia punktu przerwania** .</span><span class="sxs-lookup"><span data-stu-id="9b686-151">In the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="9b686-152">Wybierz pole **warunki** , jeśli nie zostało jeszcze wybrane.</span><span class="sxs-lookup"><span data-stu-id="9b686-152">Select the box for **Conditions** if it's not already selected.</span></span>

   ![Edytor przedstawiający panel ustawień punktu przerwania-C #](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. <span data-ttu-id="9b686-154">Dla **wyrażenia warunkowego**wprowadź w polu poniższy kod, który pokazuje przykładowy kod, który sprawdza, czy `x` jest 5.</span><span class="sxs-lookup"><span data-stu-id="9b686-154">For the **Conditional Expression**, enter the following code in the field that shows example code that tests if `x` is 5.</span></span> <span data-ttu-id="9b686-155">Jeśli język, którego chcesz użyć, nie jest wyświetlany, Zmień selektor języka w górnej części strony.</span><span class="sxs-lookup"><span data-stu-id="9b686-155">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="9b686-156">Za każdym razem, gdy punkt przerwania został trafiony, debuger wywołuje `String.IsNullOrEmpty(name)` metodę i przerywa w tym wierszu tylko wtedy, gdy wywołanie metody zwróci wartość `true` .</span><span class="sxs-lookup"><span data-stu-id="9b686-156">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="9b686-157">Zamiast wyrażenia warunkowego można określić *liczbę trafień*, która przerywa wykonywanie programu, zanim instrukcja zostanie wykonana określoną liczbę razy.</span><span class="sxs-lookup"><span data-stu-id="9b686-157">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span> <span data-ttu-id="9b686-158">Innym rozwiązaniem jest określenie *warunku filtru*, który przerywa wykonywanie programu w oparciu o takie atrybuty jak identyfikator wątku, nazwa procesu lub nazwa wątku.</span><span class="sxs-lookup"><span data-stu-id="9b686-158">Another option is to specify a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="9b686-159">Wybierz pozycję **Zamknij** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="9b686-159">Select **Close** to close the dialog.</span></span>

1. <span data-ttu-id="9b686-160">Uruchom program z debugowaniem, naciskając klawisz <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9b686-160">Start the program with debugging by pressing <kbd>F5</kbd>.</span></span>

1. <span data-ttu-id="9b686-161">W oknie konsoli naciśnij klawisz <kbd>Enter</kbd> po wyświetleniu monitu, aby wprowadzić swoją nazwę.</span><span class="sxs-lookup"><span data-stu-id="9b686-161">In the console window, press the <kbd>Enter</kbd> key when prompted to enter your name.</span></span>

1. <span data-ttu-id="9b686-162">Ponieważ określony warunek ( `name` is `null` lub <xref:System.String.Empty?displayProperty=nameWithType> ) został spełniony, wykonanie programu zatrzyma się po osiągnięciu punktu przerwania i przed wykonaniem `Console.WriteLine` metody.</span><span class="sxs-lookup"><span data-stu-id="9b686-162">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="9b686-163">Wybierz okno zmienne **lokalne** , które pokazuje wartości zmiennych, które są lokalne dla aktualnie wykonywanej metody.</span><span class="sxs-lookup"><span data-stu-id="9b686-163">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="9b686-164">W tym przypadku `Main` jest obecnie wykonywana metoda.</span><span class="sxs-lookup"><span data-stu-id="9b686-164">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="9b686-165">Zwróć uwagę, że wartość `name` zmiennej to `""` lub <xref:System.String.Empty?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9b686-165">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="9b686-166">Potwierdź, że wartość jest pustym ciągiem, wprowadzając poniższą instrukcję w oknie **bezpośrednim** i naciskając klawisz <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9b686-166">Confirm the value is an empty string by entering the following statement in the **Immediate** window and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="9b686-167">Wynik to `true` .</span><span class="sxs-lookup"><span data-stu-id="9b686-167">The result is `true`.</span></span>

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="9b686-168">Znak zapytania kieruje okno bezpośrednie do [obliczenia wyrażenia](/visualstudio/ide/reference/immediate-window#enter-commands).</span><span class="sxs-lookup"><span data-stu-id="9b686-168">The question mark directs the immediate window to [evaluate an expression](/visualstudio/ide/reference/immediate-window#enter-commands).</span></span>

   ![Bezpośrednie okno zwracające wartość true po wykonaniu instrukcji-C #](./media/debugging-with-visual-studio/immediate-window-output.png)

1. <span data-ttu-id="9b686-170">Naciśnij klawisz <kbd>F5</kbd> , aby kontynuować wykonywanie programu.</span><span class="sxs-lookup"><span data-stu-id="9b686-170">Press <kbd>F5</kbd> to continue program execution.</span></span>

1. <span data-ttu-id="9b686-171">Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="9b686-171">Press any key to close the console window and stop debugging.</span></span>

1. <span data-ttu-id="9b686-172">Wyczyść punkt przerwania, klikając kropkę na lewym marginesie okna kod.</span><span class="sxs-lookup"><span data-stu-id="9b686-172">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="9b686-173">Innym sposobem na wyczyszczenie punktu przerwania jest wybranie opcji **debuguj > przełączenia punktu przerwania** podczas wybierania wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="9b686-173">Another way to clear a breakpoint is by choosing **Debug > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="9b686-174">Przechodzenie przez program</span><span class="sxs-lookup"><span data-stu-id="9b686-174">Step through a program</span></span>

<span data-ttu-id="9b686-175">Program Visual Studio umożliwia również krok po kroku w wierszu przez program i monitorowanie jego wykonania.</span><span class="sxs-lookup"><span data-stu-id="9b686-175">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="9b686-176">Zwykle ustawiasz punkt przerwania i obserwuj przepływ programu za pomocą niewielkiej części kodu programu.</span><span class="sxs-lookup"><span data-stu-id="9b686-176">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="9b686-177">Ponieważ ten program jest mały, możesz przejść przez cały program.</span><span class="sxs-lookup"><span data-stu-id="9b686-177">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="9b686-178">Wybierz pozycję **Debuguj**  >  **krok do**.</span><span class="sxs-lookup"><span data-stu-id="9b686-178">Choose **Debug** > **Step Into**.</span></span> <span data-ttu-id="9b686-179">Innym sposobem debugowania jednej instrukcji w danym momencie jest naciśnięcie klawisza <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9b686-179">Another way to debug one statement at a time is by pressing <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="9b686-180">Program Visual Studio podświetla i wyświetli strzałkę obok następnego wiersza wykonania.</span><span class="sxs-lookup"><span data-stu-id="9b686-180">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   <span data-ttu-id="9b686-181">C#</span><span class="sxs-lookup"><span data-stu-id="9b686-181">C#</span></span>

   ![Visual Studio Wkrocz do metody-C #](./media/debugging-with-visual-studio/step-into-method.png)

   <span data-ttu-id="9b686-183">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9b686-183">Visual Basic</span></span>

   ![Visual Studio Wkrocz do metody-Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   <span data-ttu-id="9b686-185">W tym momencie okno zmienne **lokalne** pokazuje, że `args` Tablica jest pusta i `name` i `date` ma wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="9b686-185">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="9b686-186">Ponadto program Visual Studio otworzył puste okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="9b686-186">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="9b686-187">Naciśnij klawisz <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9b686-187">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="9b686-188">Program Visual Studio teraz podświetla następny wiersz wykonania.</span><span class="sxs-lookup"><span data-stu-id="9b686-188">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="9b686-189">Okno **zmiennych lokalnych** jest niezmienione, a okno konsoli pozostanie puste.</span><span class="sxs-lookup"><span data-stu-id="9b686-189">The **Locals** window is unchanged, and the console window remains blank.</span></span>

   <span data-ttu-id="9b686-190">C#</span><span class="sxs-lookup"><span data-stu-id="9b686-190">C#</span></span>

   ![Visual Studio — krok w źródle metody — C #](./media/debugging-with-visual-studio/step-into-source-method.png)

   <span data-ttu-id="9b686-192">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9b686-192">Visual Basic</span></span>

   ![Visual Studio — przejdź do źródła metody — Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. <span data-ttu-id="9b686-194">Naciśnij klawisz <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9b686-194">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="9b686-195">Program Visual Studio podświetla instrukcję, która zawiera `name` przypisanie zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9b686-195">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="9b686-196">Zostanie wyświetlone okno **Ustawienia lokalne** `name` , które ma wartość `null` , a w oknie konsoli jest wyświetlany ciąg "co to jest Twoja nazwa?".</span><span class="sxs-lookup"><span data-stu-id="9b686-196">The **Locals** window shows that `name` is `null`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="9b686-197">Odpowiedz na monit, wprowadzając ciąg w oknie konsoli i naciskając klawisz <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9b686-197">Respond to the prompt by entering a string in the console window and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="9b686-198">Konsola nie odpowiada, a wprowadzony ciąg nie jest wyświetlany w oknie konsoli, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> Metoda przechwytuje dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="9b686-198">The console is unresponsive, and the string you entered isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="9b686-199">Naciśnij klawisz <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9b686-199">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="9b686-200">Program Visual Studio podświetla instrukcję, która zawiera `date` przypisanie zmiennej ( `currentDate` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="9b686-200">Visual Studio highlights the statement that includes the `date` variable assignment (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="9b686-201">Okno zmienne **lokalne** pokazuje wartość zwracaną przez wywołanie <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="9b686-201">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9b686-202">W oknie konsoli jest również wyświetlany ciąg wprowadzony w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="9b686-202">The console window also displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="9b686-203">Naciśnij klawisz <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9b686-203">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="9b686-204">Okno **lokalne** pokazuje wartość `date` zmiennej po przypisaniu z <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9b686-204">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="9b686-205">Okno konsoli nie jest zmieniane.</span><span class="sxs-lookup"><span data-stu-id="9b686-205">The console window is unchanged.</span></span>

1. <span data-ttu-id="9b686-206">Naciśnij klawisz <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9b686-206">Press <kbd>F11</kbd>.</span></span> <span data-ttu-id="9b686-207">Program Visual Studio wywołuje <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="9b686-207">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9b686-208">W oknie konsoli zostanie wyświetlony sformatowany ciąg.</span><span class="sxs-lookup"><span data-stu-id="9b686-208">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="9b686-209">Wybierz pozycję **Debuguj**  >  **Wyjdź**. Innym sposobem zatrzymania wykonywania krok po kroku jest naciśnięcie klawisza <kbd>SHIFT</kbd> + <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9b686-209">Choose **Debug** > **Step Out**. Another way to stop step-by-step execution is by pressing <kbd>Shift</kbd>+<kbd>F11</kbd>.</span></span>

   <span data-ttu-id="9b686-210">W oknie konsoli zostanie wyświetlony komunikat i czeka na naciśnięcie klawisza.</span><span class="sxs-lookup"><span data-stu-id="9b686-210">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="9b686-211">Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="9b686-211">Press any key to close the console window and stop debugging.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="9b686-212">Użyj konfiguracji kompilacji wydania</span><span class="sxs-lookup"><span data-stu-id="9b686-212">Use Release build configuration</span></span>

<span data-ttu-id="9b686-213">Po przetestowaniu wersji debugowania aplikacji należy również skompilować i przetestować wersję publikacji.</span><span class="sxs-lookup"><span data-stu-id="9b686-213">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="9b686-214">Wersja wydania obejmuje optymalizacje kompilatora, które mogą czasami mieć negatywny wpływ na działanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b686-214">The Release version incorporates compiler optimizations that can sometimes negatively affect the behavior of an application.</span></span> <span data-ttu-id="9b686-215">Na przykład optymalizacje kompilatora, które mają na celu poprawę wydajności, mogą tworzyć sytuacje wyścigu w aplikacjach wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="9b686-215">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="9b686-216">Aby skompilować i przetestować wydaną wersję aplikacji konsolowej, Zmień konfigurację kompilacji na pasku narzędzi z **Debuguj** do **Release**.</span><span class="sxs-lookup"><span data-stu-id="9b686-216">To build and test the Release version of your console application, change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

![domyślny pasek narzędzi programu Visual Studio z wyróżnioną pozycją Debug](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

<span data-ttu-id="9b686-218">Po naciśnięciu klawisza <kbd>F5</kbd> lub wybraniu opcji **Kompiluj rozwiązanie** z menu **kompilacja** program Visual Studio kompiluje wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b686-218">When you press <kbd>F5</kbd> or choose **Build Solution** from the **Build** menu, Visual Studio compiles the Release version of the application.</span></span> <span data-ttu-id="9b686-219">Można go przetestować, tak jak w przypadku wersji do debugowania.</span><span class="sxs-lookup"><span data-stu-id="9b686-219">You can test it as you did the Debug version.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9b686-220">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="9b686-220">Next steps</span></span>

<span data-ttu-id="9b686-221">W tym samouczku użyto narzędzi debugowania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9b686-221">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="9b686-222">W następnym samouczku zostanie opublikowana wersja aplikacji, którą można wdrożyć.</span><span class="sxs-lookup"><span data-stu-id="9b686-222">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9b686-223">Publikowanie aplikacji konsolowej .NET Core za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9b686-223">Publish a .NET Core console application with Visual Studio</span></span>](publishing-with-visual-studio.md)
