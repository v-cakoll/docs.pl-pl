---
title: Debugowanie aplikacji konsolowej .NET Core za pomocą Visual Studio Code
description: Dowiedz się, jak debugować aplikację konsolową .NET Core za pomocą Visual Studio Code.
ms.date: 05/26/2020
ms.openlocfilehash: 82b2798397d702aa2a50c04bf6e4d569b97e3666
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241516"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-code"></a><span data-ttu-id="025d3-103">Samouczek: debugowanie aplikacji konsolowej .NET Core przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="025d3-103">Tutorial: Debug a .NET Core console application using Visual Studio Code</span></span>

<span data-ttu-id="025d3-104">W tym samouczku przedstawiono narzędzia debugowania dostępne w Visual Studio Code do pracy z aplikacjami .NET Core.</span><span class="sxs-lookup"><span data-stu-id="025d3-104">This tutorial introduces the debugging tools available in Visual Studio Code for working with .NET Core apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="025d3-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="025d3-105">Prerequisites</span></span>

- <span data-ttu-id="025d3-106">Ten samouczek współpracuje z aplikacją konsolową utworzoną w temacie [Tworzenie aplikacji konsolowej platformy .NET Core w Visual Studio Code](with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="025d3-106">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="025d3-107">Użyj konfiguracji kompilacji debugowania</span><span class="sxs-lookup"><span data-stu-id="025d3-107">Use Debug build configuration</span></span>

<span data-ttu-id="025d3-108">*Debugowanie* i *wydanie* są dwoma konfiguracjami kompilacji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="025d3-108">*Debug* and *Release* are two of .NET Core's build configurations.</span></span> <span data-ttu-id="025d3-109">Konfiguracja kompilacji debugowania umożliwia debugowanie i konfigurację wydania dla ostatecznej dystrybucji wersji.</span><span class="sxs-lookup"><span data-stu-id="025d3-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="025d3-110">W konfiguracji debugowania program kompiluje z pełnymi symbolicznymi informacjami o debugowaniu i bez optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="025d3-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="025d3-111">Optymalizacja komplikuje debugowanie, ponieważ relacja między kodem źródłowym i wygenerowanymi instrukcjami jest bardziej skomplikowana.</span><span class="sxs-lookup"><span data-stu-id="025d3-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="025d3-112">Konfiguracja wydania programu nie ma symbolicznych informacji o debugowaniu i jest w pełni zoptymalizowana.</span><span class="sxs-lookup"><span data-stu-id="025d3-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

 <span data-ttu-id="025d3-113">Domyślnie Visual Studio Code używa konfiguracji kompilacji debugowania, więc nie trzeba jej zmieniać przed debugowaniem.</span><span class="sxs-lookup"><span data-stu-id="025d3-113">By default, Visual Studio Code uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

## <a name="set-a-breakpoint"></a><span data-ttu-id="025d3-114">Ustawianie punktu przerwania</span><span class="sxs-lookup"><span data-stu-id="025d3-114">Set a breakpoint</span></span>

<span data-ttu-id="025d3-115">Punkt przerwania tymczasowo przerywa wykonywanie aplikacji *przed* wykonaniem wiersza z punktem przerwania.</span><span class="sxs-lookup"><span data-stu-id="025d3-115">A breakpoint temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="025d3-116">Otwórz program Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="025d3-116">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="025d3-117">Otwórz folder projektu *HelloWorld* , który został utworzony w temacie [Tworzenie aplikacji konsolowej platformy .net Core w Visual Studio Code](with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="025d3-117">Open the *HelloWorld* project folder that you created in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

1. <span data-ttu-id="025d3-118">Otwórz plik *program.cs* .</span><span class="sxs-lookup"><span data-stu-id="025d3-118">Open the *Program.cs* file.</span></span>

1. <span data-ttu-id="025d3-119">Ustaw *punkt przerwania* w wierszu, który wyświetla nazwę, datę i godzinę, klikając na lewym marginesie okna kod.</span><span class="sxs-lookup"><span data-stu-id="025d3-119">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window.</span></span> <span data-ttu-id="025d3-120">Lewy margines znajduje się po lewej stronie numerów wierszy.</span><span class="sxs-lookup"><span data-stu-id="025d3-120">The left margin is to the left of the line numbers.</span></span> <span data-ttu-id="025d3-121">Innym sposobem ustawienia punktu przerwania jest umieszczenie kursora w wierszu kodu, a następnie naciśnięcie klawisza <kbd>F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="025d3-121">Another way to set a breakpoint is by placing the cursor in the line of code and then pressing <kbd>F9</kbd>.</span></span>

   <span data-ttu-id="025d3-122">Jak pokazano na poniższej ilustracji, Visual Studio Code wskazuje wiersz, w którym jest ustawiony punkt przerwania, wyświetlając czerwoną kropkę na lewym marginesie.</span><span class="sxs-lookup"><span data-stu-id="025d3-122">As the following image shows, Visual Studio Code indicates the line on which the breakpoint is set by displaying a red dot in the left margin.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-set.png" alt-text="Zestaw punktów przerwania":::

## <a name="set-up-for-terminal-input"></a><span data-ttu-id="025d3-124">Konfiguracja dla danych wejściowych terminalu</span><span class="sxs-lookup"><span data-stu-id="025d3-124">Set up for terminal input</span></span>

<span data-ttu-id="025d3-125">Punkt przerwania znajduje się po `Console.ReadLine` wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="025d3-125">The breakpoint is located after a `Console.ReadLine` method call.</span></span> <span data-ttu-id="025d3-126">**Konsola debugowania** nie akceptuje danych wejściowych terminalu dla uruchomionego programu.</span><span class="sxs-lookup"><span data-stu-id="025d3-126">The **Debug Console** doesn't accept terminal input for a running program.</span></span> <span data-ttu-id="025d3-127">Aby obsłużyć dane wejściowe terminalu podczas debugowania, można użyć zintegrowanego terminalu (jednego z Visual Studio Code systemu Windows) lub terminalu zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="025d3-127">To handle terminal input while debugging, you can use the integrated terminal (one of the Visual Studio Code windows) or an external terminal.</span></span> <span data-ttu-id="025d3-128">W tym samouczku użyjesz zintegrowanego terminalu.</span><span class="sxs-lookup"><span data-stu-id="025d3-128">For this tutorial, you use the integrated terminal.</span></span>

1. <span data-ttu-id="025d3-129">Otwórz plik *. programu vscode/Launch. JSON*.</span><span class="sxs-lookup"><span data-stu-id="025d3-129">Open *.vscode/launch.json*.</span></span>

1. <span data-ttu-id="025d3-130">Zmień `console` ustawienie na `integratedTerminal` .</span><span class="sxs-lookup"><span data-stu-id="025d3-130">Change the `console` setting to `integratedTerminal`.</span></span>

   <span data-ttu-id="025d3-131">Od:</span><span class="sxs-lookup"><span data-stu-id="025d3-131">From:</span></span>

   ```
   "console": "internalConsole",
   ```

   <span data-ttu-id="025d3-132">Do:</span><span class="sxs-lookup"><span data-stu-id="025d3-132">To:</span></span>

   ```
   "console": "integratedTerminal",
   ```

1. <span data-ttu-id="025d3-133">Zapisz zmiany.</span><span class="sxs-lookup"><span data-stu-id="025d3-133">Save your changes.</span></span>

## <a name="start-debugging"></a><span data-ttu-id="025d3-134">Rozpocznij debugowanie</span><span class="sxs-lookup"><span data-stu-id="025d3-134">Start debugging</span></span>

1. <span data-ttu-id="025d3-135">Otwórz widok debugowanie, wybierając ikonę debugowania w menu po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="025d3-135">Open the Debug view by selecting the Debugging icon on the left side menu.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/select-debug-pane.png" alt-text="Otwórz kartę debugowanie w Visual Studio Code":::

1. <span data-ttu-id="025d3-137">Rozpocznij debugowanie, wybierając zieloną strzałkę w górnej części okienka, obok pozycji **.NET Core Launch (konsola)**.</span><span class="sxs-lookup"><span data-stu-id="025d3-137">Start debugging by selecting the green arrow at the top of the pane, next to **.NET Core Launch (console)**.</span></span>  <span data-ttu-id="025d3-138">Innym sposobem rozpoczęcia debugowania jest naciśnięcie klawisza <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="025d3-138">Another way to start debugging is by pressing <kbd>F5</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/start-debugging.png" alt-text="Rozpocznij debugowanie":::

1. <span data-ttu-id="025d3-140">Wybierz kartę **Terminal** , aby zobaczyć "Jaka jest Twoja nazwa?".</span><span class="sxs-lookup"><span data-stu-id="025d3-140">Select the **Terminal** tab to see the "What is your name?"</span></span> <span data-ttu-id="025d3-141">Monituj o wyświetlenie programu przed oczekiwaniem na odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="025d3-141">prompt that the program displays before waiting for a response.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/select-terminal.png" alt-text="Wybierz kartę Terminal":::

1. <span data-ttu-id="025d3-143">Wprowadź ciąg w oknie **terminalu** w odpowiedzi na monit o podanie nazwy, a następnie naciśnij klawisz <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="025d3-143">Enter a string in the **Terminal** window in response to the prompt for a name, and then press <kbd>Enter</kbd>.</span></span>

   <span data-ttu-id="025d3-144">Wykonanie programu zostaje zatrzymane po osiągnięciu punktu przerwania i przed wykonaniem `Console.WriteLine` metody.</span><span class="sxs-lookup"><span data-stu-id="025d3-144">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="025d3-145">Sekcja **locales** w oknie **zmienne** zawiera wartości zmiennych, które są zdefiniowane w aktualnie wykonywanej metodzie.</span><span class="sxs-lookup"><span data-stu-id="025d3-145">The **Locals** section of the **Variables** window displays the values of variables that are defined in the currently executing method.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-hit.png" alt-text="Trafienie punktu przerwania, Wyświetlanie ustawień lokalnych":::

## <a name="change-variable-values"></a><span data-ttu-id="025d3-147">Zmień wartości zmiennych</span><span class="sxs-lookup"><span data-stu-id="025d3-147">Change variable values</span></span>

<span data-ttu-id="025d3-148">Okno **konsoli debugowania** umożliwia korzystanie z debugowanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="025d3-148">The **Debug Console** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="025d3-149">Można zmienić wartość zmiennych, aby zobaczyć, jak ma to wpływ na program.</span><span class="sxs-lookup"><span data-stu-id="025d3-149">You can change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="025d3-150">Wybierz kartę **konsola debugowania** .</span><span class="sxs-lookup"><span data-stu-id="025d3-150">Select the **Debug Console** tab.</span></span>

1. <span data-ttu-id="025d3-151">Wprowadź `name = "Gracie"` w wierszu polecenia u dołu okna **konsoli debugowania** i naciśnij klawisz <kbd>Enter</kbd> .</span><span class="sxs-lookup"><span data-stu-id="025d3-151">Enter `name = "Gracie"` at the prompt at the bottom of the **Debug Console** window and press the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/change-variable-values.png" alt-text="Zmień wartości zmiennych":::

1. <span data-ttu-id="025d3-153">Wprowadź `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` w dolnej części okna **konsoli debugowania** i naciśnij klawisz <kbd>Enter</kbd> .</span><span class="sxs-lookup"><span data-stu-id="025d3-153">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` at the bottom of the **Debug Console** window and press the <kbd>Enter</kbd> key.</span></span>

   <span data-ttu-id="025d3-154">W oknie **zmienne** są wyświetlane nowe wartości `name` `date` zmiennych i.</span><span class="sxs-lookup"><span data-stu-id="025d3-154">The **Variables** window displays the new values of the `name` and `date` variables.</span></span>

1. <span data-ttu-id="025d3-155">Kontynuuj wykonywanie programu, wybierając przycisk **Kontynuuj** na pasku narzędzi.</span><span class="sxs-lookup"><span data-stu-id="025d3-155">Continue program execution by selecting the **Continue** button in the toolbar.</span></span> <span data-ttu-id="025d3-156">Innym sposobem, aby kontynuować, jest naciśnięcie klawisza <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="025d3-156">Another way to continue is by pressing <kbd>F5</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/continue-debugging.png" alt-text="Kontynuuj debugowanie":::

1. <span data-ttu-id="025d3-158">Ponownie wybierz kartę **terminala** .</span><span class="sxs-lookup"><span data-stu-id="025d3-158">Select the **Terminal** tab again.</span></span>

   <span data-ttu-id="025d3-159">Wartości wyświetlane w oknie konsoli odpowiadają zmianom wprowadzonym w **konsoli debugowania**.</span><span class="sxs-lookup"><span data-stu-id="025d3-159">The values displayed in the console window correspond to the changes you made in the **Debug Console**.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/changed-variable-values.png" alt-text="Terminal pokazujący wprowadzone wartości":::

1. <span data-ttu-id="025d3-161">Naciśnij dowolny klawisz, aby zamknąć aplikację i zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="025d3-161">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="025d3-162">Ustaw punkt przerwania warunkowego</span><span class="sxs-lookup"><span data-stu-id="025d3-162">Set a conditional breakpoint</span></span>

<span data-ttu-id="025d3-163">Program wyświetla ciąg wprowadzony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="025d3-163">The program displays the string that the user enters.</span></span> <span data-ttu-id="025d3-164">Co się stanie, jeśli użytkownik nie wprowadzi niczego?</span><span class="sxs-lookup"><span data-stu-id="025d3-164">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="025d3-165">Można to sprawdzić za pomocą przydatnej funkcji debugowania zwanej *warunkowym punktem przerwania*.</span><span class="sxs-lookup"><span data-stu-id="025d3-165">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="025d3-166">Kliknij prawym przyciskiem myszy (<kbd>Ctrl</kbd>+ kliknięcie na macOS) w czerwonej kropki, która reprezentuje punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="025d3-166">Right-click (<kbd>Ctrl</kbd>+click on macOS) on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="025d3-167">W menu kontekstowym wybierz pozycję **Edytuj punkt przerwania** , aby otworzyć okno dialogowe, które umożliwia wprowadzenie wyrażenia warunkowego.</span><span class="sxs-lookup"><span data-stu-id="025d3-167">In the context menu, select **Edit Breakpoint** to open a dialog that lets you enter a conditional expression.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-context-menu.png" alt-text="Menu kontekstowe punktu przerwania":::

1. <span data-ttu-id="025d3-169">Wybierz `Expression` z listy rozwijanej, wprowadź następujące wyrażenie warunkowe, a następnie naciśnij klawisz <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="025d3-169">Select `Expression` in the drop-down, enter the following conditional expression, and press <kbd>Enter</kbd>.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/conditional-expression.png" alt-text="Wprowadź wyrażenie warunkowe":::

   <span data-ttu-id="025d3-171">Za każdym razem, gdy punkt przerwania został trafiony, debuger wywołuje `String.IsNullOrEmpty(name)` metodę i przerywa w tym wierszu tylko wtedy, gdy wywołanie metody zwróci wartość `true` .</span><span class="sxs-lookup"><span data-stu-id="025d3-171">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="025d3-172">Zamiast wyrażenia warunkowego można określić *liczbę trafień*, która przerywa wykonywanie programu, zanim instrukcja zostanie wykonana określoną liczbę razy lub *warunek filtru*, który przerywa wykonywanie programu w oparciu o takie atrybuty jak identyfikator wątku, nazwa procesu lub nazwa wątku.</span><span class="sxs-lookup"><span data-stu-id="025d3-172">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="025d3-173">Uruchom program z debugowaniem, naciskając klawisz <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="025d3-173">Start the program with debugging by pressing <kbd>F5</kbd>.</span></span>

1. <span data-ttu-id="025d3-174">Na karcie **Terminal** naciśnij klawisz <kbd>Enter</kbd> po wyświetleniu monitu, aby wprowadzić swoją nazwę.</span><span class="sxs-lookup"><span data-stu-id="025d3-174">In the **Terminal** tab, press the <kbd>Enter</kbd> key when prompted to enter your name.</span></span>

   <span data-ttu-id="025d3-175">Ponieważ określony warunek ( `name` is `null` lub) został <xref:System.String.Empty?displayProperty=nameWithType> spełniony, wykonanie programu zatrzyma się po osiągnięciu punktu przerwania i przed wykonaniem `Console.WriteLine` metody.</span><span class="sxs-lookup"><span data-stu-id="025d3-175">Because the condition you specified (`name` is `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

   <span data-ttu-id="025d3-176">Okno **zmienne** pokazuje, że wartość `name` zmiennej to `""` , lub <xref:System.String.Empty?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="025d3-176">The **Variables** window shows that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="025d3-177">Potwierdź, że wartość jest pustym ciągiem, wprowadzając poniższą instrukcję w wierszu **konsoli debugowania** i naciskając klawisz <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="025d3-177">Confirm the value is an empty string by entering the following statement at the **Debug Console** prompt and pressing <kbd>Enter</kbd>.</span></span> <span data-ttu-id="025d3-178">Wynik to `true` .</span><span class="sxs-lookup"><span data-stu-id="025d3-178">The result is `true`.</span></span>

   ```csharp
   name == String.Empty
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/expression-in-debug-console.png" alt-text="Konsola debugowania zwracająca wartość true po wykonaniu instrukcji":::

1. <span data-ttu-id="025d3-180">Wybierz przycisk **Kontynuuj** na pasku narzędzi, aby kontynuować wykonywanie programu.</span><span class="sxs-lookup"><span data-stu-id="025d3-180">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="025d3-181">Wybierz kartę **Terminal** i naciśnij dowolny klawisz, aby wyjść z programu i zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="025d3-181">Select the **Terminal** tab, and press any key to exit the program and stop debugging.</span></span>

1. <span data-ttu-id="025d3-182">Wyczyść punkt przerwania, klikając kropkę na lewym marginesie okna kod.</span><span class="sxs-lookup"><span data-stu-id="025d3-182">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="025d3-183">Innym sposobem na wyczyszczenie punktu przerwania jest naciśnięcie klawisza <kbd>F9</kbd> podczas wybierania wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="025d3-183">Another way to clear a breakpoint is by pressing <kbd>F9</kbd> while the line of code is selected.</span></span>

1. <span data-ttu-id="025d3-184">Jeśli zostanie wyświetlone ostrzeżenie, że warunek punktu przerwania zostanie utracony, wybierz pozycję **Usuń punkt przerwania**.</span><span class="sxs-lookup"><span data-stu-id="025d3-184">If you get a warning that the breakpoint condition will be lost, select **Remove Breakpoint**.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="025d3-185">Przechodzenie przez program</span><span class="sxs-lookup"><span data-stu-id="025d3-185">Step through a program</span></span>

<span data-ttu-id="025d3-186">Visual Studio Code umożliwia również krok po kroku w wierszu przez program i monitorowanie jego wykonania.</span><span class="sxs-lookup"><span data-stu-id="025d3-186">Visual Studio Code also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="025d3-187">Zwykle ustawiasz punkt przerwania i obserwuj przepływ programu za pomocą niewielkiej części kodu programu.</span><span class="sxs-lookup"><span data-stu-id="025d3-187">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="025d3-188">Ponieważ ten program jest mały, możesz przejść przez cały program.</span><span class="sxs-lookup"><span data-stu-id="025d3-188">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="025d3-189">Ustaw punkt przerwania w otwierającym nawiasie klamrowym `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="025d3-189">Set a breakpoint on the opening curly brace of the `Main` method.</span></span>

1. <span data-ttu-id="025d3-190">Naciśnij klawisz <kbd>F5</kbd>, aby uruchomić debugowanie.</span><span class="sxs-lookup"><span data-stu-id="025d3-190">Press <kbd>F5</kbd> to start debugging.</span></span>

   <span data-ttu-id="025d3-191">Visual Studio Code podświetla linię punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="025d3-191">Visual Studio Code highlights the breakpoint line.</span></span>

   <span data-ttu-id="025d3-192">W tym momencie okno **zmienne** pokazuje, że `args` Tablica jest pusta i `name` i `date` ma wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="025d3-192">At this point, the **Variables** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span>

1. <span data-ttu-id="025d3-193">Wybierz pozycję **Wkrocz** lub naciśnij klawisz <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="025d3-193">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/step-into.png" alt-text="Przycisk "krok po kroku"":::

   <span data-ttu-id="025d3-195">Visual Studio Code podświetla następny wiersz.</span><span class="sxs-lookup"><span data-stu-id="025d3-195">Visual Studio Code highlights the next line.</span></span>

1. <span data-ttu-id="025d3-196">Wybierz pozycję **Wkrocz** lub naciśnij klawisz <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="025d3-196">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="025d3-197">Visual Studio Code wykonuje `Console.WriteLine` monit o podanie nazwy i wyróżnia następny wiersz wykonania.</span><span class="sxs-lookup"><span data-stu-id="025d3-197">Visual Studio Code executes the `Console.WriteLine` for the name prompt and highlights the next line of execution.</span></span> <span data-ttu-id="025d3-198">Następnym wierszem jest `Console.ReadLine` `name` .</span><span class="sxs-lookup"><span data-stu-id="025d3-198">The next line is the `Console.ReadLine` for the `name`.</span></span> <span data-ttu-id="025d3-199">Okno **zmiennych** jest niezmienione, a na karcie **terminala** zostanie wyświetlona wartość "co to jest Twoja nazwa?"</span><span class="sxs-lookup"><span data-stu-id="025d3-199">The **Variables** window is unchanged, and the **Terminal** tab shows the "What is your name?"</span></span> <span data-ttu-id="025d3-200">pytać.</span><span class="sxs-lookup"><span data-stu-id="025d3-200">prompt.</span></span>

1. <span data-ttu-id="025d3-201">Wybierz pozycję **Wkrocz** lub naciśnij klawisz <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="025d3-201">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="025d3-202">Program Visual Studio podświetla `name` przypisanie zmiennej.</span><span class="sxs-lookup"><span data-stu-id="025d3-202">Visual Studio highlights the `name` variable assignment.</span></span> <span data-ttu-id="025d3-203">Okno **zmienne** pokazuje, że `name` jest nadal `null` .</span><span class="sxs-lookup"><span data-stu-id="025d3-203">The **Variables** window shows that `name` is still `null`.</span></span>

1. <span data-ttu-id="025d3-204">Odpowiedz na monit, wprowadzając ciąg na karcie Terminal i naciskając klawisz <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="025d3-204">Respond to the prompt by entering a string in the Terminal tab and pressing <kbd>Enter</kbd>.</span></span>

   <span data-ttu-id="025d3-205">Na karcie **terminala** może nie być wyświetlany ciąg wprowadzony podczas jego wprowadzania, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> Metoda przechwytuje dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="025d3-205">The **Terminal** tab might not display the string you enter while you're entering it, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will capture your input.</span></span>

1. <span data-ttu-id="025d3-206">Wybierz pozycję **Wkrocz** lub naciśnij klawisz <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="025d3-206">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="025d3-207">Visual Studio Code podświetla `date` przypisanie zmiennej.</span><span class="sxs-lookup"><span data-stu-id="025d3-207">Visual Studio Code highlights the `date` variable assignment.</span></span> <span data-ttu-id="025d3-208">Okno **zmienne** pokazuje wartość zwracaną przez wywołanie <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="025d3-208">The **Variables** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="025d3-209">Na karcie **Terminal** zostanie wyświetlony ciąg wprowadzony w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="025d3-209">The **Terminal** tab displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="025d3-210">Wybierz pozycję **Wkrocz** lub naciśnij klawisz <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="025d3-210">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="025d3-211">Okno **zmienne** zawiera wartość `date` zmiennej po przypisaniu z <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="025d3-211">The **Variables** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span>

1. <span data-ttu-id="025d3-212">Wybierz pozycję **Wkrocz** lub naciśnij klawisz <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="025d3-212">Select **Step Into** or press <kbd>F11</kbd>.</span></span>

   <span data-ttu-id="025d3-213">Visual Studio Code wywołuje <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="025d3-213">Visual Studio Code calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="025d3-214">W oknie konsoli zostanie wyświetlony sformatowany ciąg.</span><span class="sxs-lookup"><span data-stu-id="025d3-214">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="025d3-215">Wybierz pozycję **Wyjdź** lub naciśnij klawisz <kbd>SHIFT</kbd> + <kbd>F11</kbd>.</span><span class="sxs-lookup"><span data-stu-id="025d3-215">Select **Step Out** or press <kbd>Shift</kbd>+<kbd>F11</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/step-out.png" alt-text="Przycisk krok po kroku":::

1. <span data-ttu-id="025d3-217">Wybierz kartę **Terminal** .</span><span class="sxs-lookup"><span data-stu-id="025d3-217">Select the **Terminal** tab.</span></span>

   <span data-ttu-id="025d3-218">W terminalu zostanie wyświetlony komunikat "naciśnij dowolny klawisz, aby wyjść..."</span><span class="sxs-lookup"><span data-stu-id="025d3-218">The terminal displays "Press any key to exit..."</span></span>

1. <span data-ttu-id="025d3-219">Naciśnij dowolny klawisz, aby wyjść z programu.</span><span class="sxs-lookup"><span data-stu-id="025d3-219">Press any key to exit the program.</span></span>

## <a name="select-release-build-configuration"></a><span data-ttu-id="025d3-220">Wybierz konfigurację kompilacji wydania</span><span class="sxs-lookup"><span data-stu-id="025d3-220">Select Release build configuration</span></span>

<span data-ttu-id="025d3-221">Po przetestowaniu wersji debugowania aplikacji należy również skompilować i przetestować wersję publikacji.</span><span class="sxs-lookup"><span data-stu-id="025d3-221">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="025d3-222">Wersja wydania obejmuje optymalizacje kompilatora, które mogą mieć wpływ na zachowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="025d3-222">The Release version incorporates compiler optimizations that can affect the behavior of an application.</span></span> <span data-ttu-id="025d3-223">Na przykład optymalizacje kompilatora, które mają na celu poprawę wydajności, mogą tworzyć sytuacje wyścigu w aplikacjach wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="025d3-223">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="025d3-224">Aby skompilować i przetestować wydaną wersję aplikacji konsolowej, Otwórz **Terminal** i uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="025d3-224">To build and test the Release version of your console application, open the **Terminal** and run the following command:</span></span>

```dotnetcli
dotnet run --configuration Release
```

## <a name="additional-resources"></a><span data-ttu-id="025d3-225">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="025d3-225">Additional resources</span></span>

* [<span data-ttu-id="025d3-226">Debugowanie w Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="025d3-226">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/docs/editor/debugging)

## <a name="next-steps"></a><span data-ttu-id="025d3-227">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="025d3-227">Next steps</span></span>

<span data-ttu-id="025d3-228">W tym samouczku użyto narzędzi debugowania Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="025d3-228">In this tutorial, you used Visual Studio Code debugging tools.</span></span> <span data-ttu-id="025d3-229">W następnym samouczku zostanie opublikowana wersja aplikacji, którą można wdrożyć.</span><span class="sxs-lookup"><span data-stu-id="025d3-229">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="025d3-230">Publikowanie aplikacji konsolowej .NET Core za pomocą Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="025d3-230">Publish a .NET Core console application with Visual Studio Code</span></span>](publishing-with-visual-studio-code.md)
