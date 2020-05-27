---
title: Debugowanie aplikacji konsolowej .NET Core za pomocą programu Visual Studio
description: Dowiedz się, jak debugować aplikację konsolową .NET Core za pomocą programu Visual Studio.
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4bd2a8a0e4b3cea55e209306dd3788552e4b61f3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005417"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="5e1ac-103">Samouczek: debugowanie aplikacji konsolowej .NET Core przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5e1ac-103">Tutorial: Debug a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="5e1ac-104">W tym samouczku przedstawiono narzędzia debugowania dostępne w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-104">This tutorial introduces the debugging tools available in Visual Studio.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5e1ac-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5e1ac-105">Prerequisites</span></span>

- <span data-ttu-id="5e1ac-106">Ten samouczek współpracuje z aplikacją konsolową utworzoną w temacie [Tworzenie aplikacji konsolowej platformy .NET Core w programie Visual Studio 2019](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="5e1ac-106">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

## <a name="debug-build-configuration"></a><span data-ttu-id="5e1ac-107">Debuguj konfigurację kompilacji</span><span class="sxs-lookup"><span data-stu-id="5e1ac-107">Debug build configuration</span></span>

<span data-ttu-id="5e1ac-108">*Debugowanie* i *wydanie* są dwiema domyślnymi konfiguracjami kompilacji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-108">*Debug* and *Release* are two of Visual Studio's default build configurations.</span></span> <span data-ttu-id="5e1ac-109">Bieżąca konfiguracja kompilacji jest pokazywana na pasku narzędzi.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-109">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="5e1ac-110">Poniższy obraz paska narzędzi pokazuje, że program Visual Studio jest skonfigurowany do kompilowania wersji do debugowania aplikacji:</span><span class="sxs-lookup"><span data-stu-id="5e1ac-110">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

![Pasek narzędzi programu Visual Studio z wyróżnioną pozycją Debug](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

<span data-ttu-id="5e1ac-112">Zacznij od uruchomienia wersji debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-112">Begin by running the Debug version of the app.</span></span> <span data-ttu-id="5e1ac-113">Konfiguracja kompilacji debugowania powoduje wyłączenie większości optymalizacji kompilatora i zapewnia bogatsze informacje podczas procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-113">The Debug build configuration turns off most compiler optimizations and provides richer information during the build process.</span></span>

## <a name="set-a-breakpoint"></a><span data-ttu-id="5e1ac-114">Ustawianie punktu przerwania</span><span class="sxs-lookup"><span data-stu-id="5e1ac-114">Set a breakpoint</span></span>

<!-- markdownlint-disable MD025 -->

1. <span data-ttu-id="5e1ac-115">Ustaw *punkt przerwania* w wierszu, który wyświetla nazwę, datę i godzinę, klikając na lewym marginesie okna kod w tym wierszu.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-115">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window on that line.</span></span> <span data-ttu-id="5e1ac-116">Innym sposobem ustawienia punktu przerwania jest umieszczenie kursora w wierszu kodu, a następnie naciśnięcie klawisza **F9** lub wybranie polecenia **Debuguj**  >  **Przełącz punkt przerwania** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-116">Another way to set a breakpoint is by placing the cursor in the line of code and then pressing **F9** or choosing **Debug** > **Toggle Breakpoint** from the menu bar.</span></span>

   <span data-ttu-id="5e1ac-117">Punkt przerwania tymczasowo przerywa wykonywanie aplikacji *przed* wykonaniem wiersza z punktem przerwania.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-117">A breakpoint temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span>

   <span data-ttu-id="5e1ac-118">Jak widać na poniższej ilustracji, program Visual Studio wskazuje wiersz, w którym jest ustawiony punkt przerwania, zaznaczając go i wyświetlając czerwoną kropkę na lewym marginesie.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-118">As the following image shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   ![Okno programu Visual Studio z ustawionym punktem przerwania](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. <span data-ttu-id="5e1ac-120">Uruchom program w trybie debugowania, wybierając przycisk **HelloWorld** z zieloną strzałką na pasku narzędzi.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-120">Run the program in Debug mode by selecting the **HelloWorld** button with the green arrow on the toolbar.</span></span> <span data-ttu-id="5e1ac-121">Innymi sposobami rozpoczęcia debugowania są naciśnięcie klawisza **F5** lub wybranie polecenia **Debuguj**  >  **Rozpocznij debugowanie**.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-121">Other ways to start debugging are by pressing **F5** or by choosing **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="5e1ac-122">Wprowadź ciąg w oknie konsoli, gdy program zapyta o nazwę, a następnie naciśnij klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-122">Enter a string in the console window when the program prompts for a name, and then press **Enter**.</span></span>

1. <span data-ttu-id="5e1ac-123">Wykonanie programu zostaje zatrzymane po osiągnięciu punktu przerwania i przed wykonaniem `Console.WriteLine` metody.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-123">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="5e1ac-124">W oknie **Ustawienia lokalne** są wyświetlane wartości zmiennych, które są zdefiniowane w aktualnie wykonywanej metodzie.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-124">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span>

   ![Zrzut ekranu punktu przerwania w programie Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. <span data-ttu-id="5e1ac-126">Okno **bezpośrednie** umożliwia korzystanie z debugowanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-126">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="5e1ac-127">Możesz interaktywnie zmienić wartość zmiennych, aby zobaczyć, jak ma to wpływ na program.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-127">You can interactively change the value of variables to see how it affects your program.</span></span>

   1. <span data-ttu-id="5e1ac-128">Jeśli okno **bezpośrednie** nie jest widoczne, Wyświetl je, wybierając pozycję **Debuguj**  >  **Windows**  >  **natychmiast**Windows.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-128">If the **Immediate** window is not visible, display it by choosing **Debug** > **Windows** > **Immediate**.</span></span>

   1. <span data-ttu-id="5e1ac-129">Wprowadź `name = "Gracie"` w oknie **bezpośrednim** i naciśnij klawisz **Enter** .</span><span class="sxs-lookup"><span data-stu-id="5e1ac-129">Enter `name = "Gracie"` in the **Immediate** window and press the **Enter** key.</span></span>

   1. <span data-ttu-id="5e1ac-130">Wprowadź `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` w oknie **bezpośrednim** i naciśnij klawisz **Enter** .</span><span class="sxs-lookup"><span data-stu-id="5e1ac-130">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` in the **Immediate** window and press the **Enter** key.</span></span>

   <span data-ttu-id="5e1ac-131">W oknie **bezpośrednim** zostanie wyświetlona wartość zmiennej ciągu i właściwości <xref:System.DateTime> wartości.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-131">The **Immediate** window displays the value of the string variable and the properties of the <xref:System.DateTime> value.</span></span> <span data-ttu-id="5e1ac-132">Ponadto wartości zmiennych są aktualizowane w oknie **zmiennych lokalnych** .</span><span class="sxs-lookup"><span data-stu-id="5e1ac-132">In addition, the values of the variables are updated in the **Locals** window.</span></span>

   ![Lokalne i natychmiastowe okna w programie Visual Studio 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. <span data-ttu-id="5e1ac-134">Kontynuuj wykonywanie programu, wybierając przycisk **Kontynuuj** na pasku narzędzi.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-134">Continue program execution by selecting the **Continue** button in the toolbar.</span></span> <span data-ttu-id="5e1ac-135">Innym sposobem na kontynuowanie jest wybranie opcji **Debuguj**  >  **Kontynuuj**.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-135">Another way to continue is by choosing **Debug** > **Continue**.</span></span>

   <span data-ttu-id="5e1ac-136">Wartości wyświetlane w oknie konsoli odpowiadają zmianom wprowadzonym w oknie **bezpośrednim** .</span><span class="sxs-lookup"><span data-stu-id="5e1ac-136">The values displayed in the console window correspond to the changes you made in the **Immediate** window.</span></span>

   ![Okno konsoli pokazujące wprowadzone wartości](./media/debugging-with-visual-studio/console-window.png)

1. <span data-ttu-id="5e1ac-138">Naciśnij dowolny klawisz, aby zamknąć aplikację i zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-138">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="5e1ac-139">Ustaw punkt przerwania warunkowego</span><span class="sxs-lookup"><span data-stu-id="5e1ac-139">Set a conditional breakpoint</span></span>

<span data-ttu-id="5e1ac-140">Program wyświetla ciąg wprowadzony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-140">The program displays the string that the user enters.</span></span> <span data-ttu-id="5e1ac-141">Co się stanie, jeśli użytkownik nie wprowadzi niczego?</span><span class="sxs-lookup"><span data-stu-id="5e1ac-141">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="5e1ac-142">Można to sprawdzić za pomocą przydatnej funkcji debugowania nazywanej *warunkowym punktem przerwania*, która przerywa wykonywanie programu po spełnieniu jednego lub kilku warunków.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-142">You can test this with a useful debugging feature called a *conditional breakpoint*, which breaks program execution when one or more conditions are met.</span></span>

<span data-ttu-id="5e1ac-143">Aby ustawić warunkowy punkt przerwania i sprawdzić, co się dzieje, gdy użytkownik nie może wprowadzić ciągu, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5e1ac-143">To set a conditional breakpoint and test what happens when the user fails to enter a string, do the following:</span></span>

1. <span data-ttu-id="5e1ac-144">Kliknij prawym przyciskiem myszy czerwoną kropkę reprezentującą punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-144">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="5e1ac-145">W menu kontekstowym wybierz pozycję **warunki** , aby otworzyć okno dialogowe **Ustawienia punktu przerwania** .</span><span class="sxs-lookup"><span data-stu-id="5e1ac-145">In the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="5e1ac-146">Wybierz pole **warunki** , jeśli nie zostało jeszcze wybrane.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-146">Select the box for **Conditions** if it's not already selected.</span></span>

   ![Edytor przedstawiający panel ustawień punktu przerwania-C #](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. <span data-ttu-id="5e1ac-148">Dla **wyrażenia warunkowego**wprowadź w polu poniższy kod, który pokazuje przykładowy kod, który sprawdza, czy `x` jest 5.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-148">For the **Conditional Expression**, enter the following code in the field that shows example code that tests if `x` is 5.</span></span> <span data-ttu-id="5e1ac-149">Jeśli język, którego chcesz użyć, nie jest wyświetlany, Zmień selektor języka w górnej części strony.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-149">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="5e1ac-150">Za każdym razem, gdy punkt przerwania został trafiony, debuger wywołuje `String.IsNullOrEmpty(name)` metodę i przerywa w tym wierszu tylko wtedy, gdy wywołanie metody zwróci wartość `true` .</span><span class="sxs-lookup"><span data-stu-id="5e1ac-150">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="5e1ac-151">Zamiast wyrażenia warunkowego można określić *liczbę trafień*, która przerywa wykonywanie programu, zanim instrukcja zostanie wykonana określoną liczbę razy lub *warunek filtru*, który przerywa wykonywanie programu w oparciu o takie atrybuty jak identyfikator wątku, nazwa procesu lub nazwa wątku.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-151">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="5e1ac-152">Wybierz pozycję **Zamknij** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-152">Select **Close** to close the dialog.</span></span>

1. <span data-ttu-id="5e1ac-153">Uruchom program z debugowaniem, naciskając klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-153">Start the program with debugging by pressing **F5**.</span></span>

1. <span data-ttu-id="5e1ac-154">W oknie konsoli naciśnij klawisz **Enter** po wyświetleniu monitu, aby wprowadzić swoją nazwę.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-154">In the console window, press the **Enter** key when prompted to enter your name.</span></span>

1. <span data-ttu-id="5e1ac-155">Ponieważ określony warunek ( `name` is `null` lub <xref:System.String.Empty?displayProperty=nameWithType> ) został spełniony, wykonanie programu zatrzyma się po osiągnięciu punktu przerwania i przed wykonaniem `Console.WriteLine` metody.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-155">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="5e1ac-156">Wybierz okno zmienne **lokalne** , które pokazuje wartości zmiennych, które są lokalne dla aktualnie wykonywanej metody.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-156">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="5e1ac-157">W tym przypadku `Main` jest obecnie wykonywana metoda.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-157">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="5e1ac-158">Zwróć uwagę, że wartość `name` zmiennej to `""` lub <xref:System.String.Empty?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5e1ac-158">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="5e1ac-159">Potwierdź, że wartość jest pustym ciągiem, wprowadzając poniższą instrukcję w oknie **bezpośrednim** i naciskając klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-159">Confirm the value is an empty string by entering the following statement in the **Immediate** window and pressing **Enter**.</span></span> <span data-ttu-id="5e1ac-160">Wynik to `true` .</span><span class="sxs-lookup"><span data-stu-id="5e1ac-160">The result is `true`.</span></span>

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="5e1ac-161">Znak zapytania kieruje okno bezpośrednie do [obliczenia wyrażenia](/visualstudio/ide/reference/immediate-window#enter-commands).</span><span class="sxs-lookup"><span data-stu-id="5e1ac-161">The question mark directs the immediate window to [evaluate an expression](/visualstudio/ide/reference/immediate-window#enter-commands).</span></span>

   ![Bezpośrednie okno zwracające wartość true po wykonaniu instrukcji-C #](./media/debugging-with-visual-studio/immediate-window-output.png)

1. <span data-ttu-id="5e1ac-163">Wybierz przycisk **Kontynuuj** na pasku narzędzi, aby kontynuować wykonywanie programu.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-163">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="5e1ac-164">Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-164">Press any key to close the console window and stop debugging.</span></span>

1. <span data-ttu-id="5e1ac-165">Wyczyść punkt przerwania, klikając kropkę na lewym marginesie okna kod.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-165">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="5e1ac-166">Innym sposobem na wyczyszczenie punktu przerwania jest wybranie opcji **debuguj > przełączenia punktu przerwania** podczas wybierania wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-166">Another way to clear a breakpoint is by choosing **Debug > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="5e1ac-167">Przechodzenie przez program</span><span class="sxs-lookup"><span data-stu-id="5e1ac-167">Step through a program</span></span>

<span data-ttu-id="5e1ac-168">Program Visual Studio umożliwia również krok po kroku w wierszu przez program i monitorowanie jego wykonania.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-168">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="5e1ac-169">Zwykle ustawiasz punkt przerwania i obserwuj przepływ programu za pomocą niewielkiej części kodu programu.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-169">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="5e1ac-170">Ponieważ program jest mały, możesz przejść przez cały program.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-170">Since your program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="5e1ac-171">Wybierz pozycję **Debuguj**  >  **krok do**.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-171">Choose **Debug** > **Step Into**.</span></span> <span data-ttu-id="5e1ac-172">Innym sposobem debugowania jednej instrukcji w danym momencie jest naciśnięcie klawisza **F11**.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-172">Another way to debug one statement at a time is by pressing **F11**.</span></span>

   <span data-ttu-id="5e1ac-173">Program Visual Studio podświetla i wyświetli strzałkę obok następnego wiersza wykonania.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-173">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   <span data-ttu-id="5e1ac-174">C#</span><span class="sxs-lookup"><span data-stu-id="5e1ac-174">C#</span></span>

   ![Visual Studio Wkrocz do metody-C #](./media/debugging-with-visual-studio/step-into-method.png)

   <span data-ttu-id="5e1ac-176">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e1ac-176">Visual Basic</span></span>

   ![Visual Studio Wkrocz do metody-Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   <span data-ttu-id="5e1ac-178">W tym momencie okno zmienne **lokalne** pokazuje, że `args` Tablica jest pusta i `name` i `date` ma wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-178">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="5e1ac-179">Ponadto program Visual Studio otworzył puste okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-179">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="5e1ac-180">Naciśnij klawisz **F11**.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-180">Press **F11**.</span></span> <span data-ttu-id="5e1ac-181">Program Visual Studio teraz podświetla następny wiersz wykonania.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-181">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="5e1ac-182">Okno **zmiennych lokalnych** jest niezmienione, a okno konsoli pozostanie puste.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-182">The **Locals** window is unchanged, and the console window remains blank.</span></span>

   <span data-ttu-id="5e1ac-183">C#</span><span class="sxs-lookup"><span data-stu-id="5e1ac-183">C#</span></span>

   ![Visual Studio — krok w źródle metody — C #](./media/debugging-with-visual-studio/step-into-source-method.png)

   <span data-ttu-id="5e1ac-185">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e1ac-185">Visual Basic</span></span>

   ![Visual Studio — przejdź do źródła metody — Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. <span data-ttu-id="5e1ac-187">Naciśnij klawisz **F11**.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-187">Press **F11**.</span></span> <span data-ttu-id="5e1ac-188">Program Visual Studio podświetla instrukcję, która zawiera `name` przypisanie zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-188">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="5e1ac-189">Zostanie wyświetlone okno **Ustawienia lokalne** `name` , które ma wartość `null` , a w oknie konsoli jest wyświetlany ciąg "co to jest Twoja nazwa?".</span><span class="sxs-lookup"><span data-stu-id="5e1ac-189">The **Locals** window shows that `name` is `null`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="5e1ac-190">Odpowiedz na monit, wprowadzając ciąg w oknie konsoli i naciskając klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-190">Respond to the prompt by entering a string in the console window and pressing **Enter**.</span></span> <span data-ttu-id="5e1ac-191">Konsola nie odpowiada, a wprowadzony ciąg nie jest wyświetlany w oknie konsoli, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> Metoda przechwytuje dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-191">The console is unresponsive, and the string you entered isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="5e1ac-192">Naciśnij klawisz **F11**.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-192">Press **F11**.</span></span> <span data-ttu-id="5e1ac-193">Program Visual Studio podświetla instrukcję, która zawiera `date` przypisanie zmiennej ( `currentDate` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5e1ac-193">Visual Studio highlights the statement that includes the `date` variable assignment (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="5e1ac-194">Okno zmienne **lokalne** pokazuje wartość zwracaną przez wywołanie <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-194">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5e1ac-195">W oknie konsoli jest również wyświetlany ciąg wprowadzony w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-195">The console window also displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="5e1ac-196">Naciśnij klawisz **F11**.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-196">Press **F11**.</span></span> <span data-ttu-id="5e1ac-197">Okno **lokalne** pokazuje wartość `date` zmiennej po przypisaniu z <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-197">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="5e1ac-198">Okno konsoli nie jest zmieniane.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-198">The console window is unchanged.</span></span>

1. <span data-ttu-id="5e1ac-199">Naciśnij klawisz **F11**.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-199">Press **F11**.</span></span> <span data-ttu-id="5e1ac-200">Program Visual Studio wywołuje <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-200">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5e1ac-201">W oknie konsoli zostanie wyświetlony sformatowany ciąg.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-201">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="5e1ac-202">Wybierz pozycję **Debuguj**  >  **Wyjdź**. Innym sposobem zatrzymania wykonywania krok po kroku jest naciśnięcie klawisza **SHIFT** + **F11**.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-202">Choose **Debug** > **Step Out**. Another way to stop step-by-step execution is by pressing **Shift**+**F11**.</span></span>

   <span data-ttu-id="5e1ac-203">W oknie konsoli zostanie wyświetlony komunikat i czeka na naciśnięcie klawisza.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-203">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="5e1ac-204">Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-204">Press any key to close the console window and stop debugging.</span></span>

## <a name="build-a-release-version"></a><span data-ttu-id="5e1ac-205">Tworzenie wersji wydania</span><span class="sxs-lookup"><span data-stu-id="5e1ac-205">Build a Release version</span></span>

<span data-ttu-id="5e1ac-206">Po przetestowaniu wersji debugowania aplikacji należy również skompilować i przetestować wersję publikacji.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-206">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="5e1ac-207">Wersja wydania obejmuje optymalizacje kompilatora, które mogą czasami mieć negatywny wpływ na działanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-207">The Release version incorporates compiler optimizations that can sometimes negatively affect the behavior of an application.</span></span> <span data-ttu-id="5e1ac-208">Na przykład optymalizacje kompilatora, które mają na celu poprawę wydajności, mogą tworzyć sytuacje wyścigu w aplikacjach wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-208">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="5e1ac-209">Aby skompilować i przetestować wydaną wersję aplikacji konsolowej, Zmień konfigurację kompilacji na pasku narzędzi z **Debuguj** do **Release**.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-209">To build and test the Release version of your console application, change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

![domyślny pasek narzędzi programu Visual Studio z wyróżnioną pozycją Debug](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

<span data-ttu-id="5e1ac-211">Po naciśnięciu klawisza **F5** lub wybraniu opcji **Kompiluj rozwiązanie** z menu **kompilacja** program Visual Studio kompiluje wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-211">When you press **F5** or choose **Build Solution** from the **Build** menu, Visual Studio compiles the Release version of the application.</span></span> <span data-ttu-id="5e1ac-212">Można go przetestować, tak jak w przypadku wersji do debugowania.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-212">You can test it as you did the Debug version.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5e1ac-213">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="5e1ac-213">Next steps</span></span>

<span data-ttu-id="5e1ac-214">W tym samouczku użyto narzędzi debugowania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-214">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="5e1ac-215">W następnym samouczku zostanie opublikowana wersja aplikacji, którą można wdrożyć.</span><span class="sxs-lookup"><span data-stu-id="5e1ac-215">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5e1ac-216">Publikowanie aplikacji konsolowej .NET Core za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5e1ac-216">Publish a .NET Core console application with Visual Studio</span></span>](publishing-with-visual-studio.md)
