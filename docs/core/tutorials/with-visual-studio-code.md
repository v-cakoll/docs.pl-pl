---
title: Wprowadzenie do języka C# i programu Visual Studio Code
description: Dowiedz się, jak utworzyć i debugować pierwszą aplikację platformy .NET C# Core w programie przy użyciu Visual Studio Code.
author: kendrahavens
ms.date: 12/05/2018
ms.custom: seodec18
ms.openlocfilehash: 4e283f631f463953185a37bf196a1a9b706eee2b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002320"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="a4850-103">Wprowadzenie do języka C# i programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="a4850-103">Get started with C# and Visual Studio Code</span></span>

<span data-ttu-id="a4850-104">Program .NET Core zapewnia szybką i modularną platformę do tworzenia aplikacji działających w systemach Windows, Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="a4850-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="a4850-105">Użyj Visual Studio Code z rozszerzeniem C# , aby uzyskać zaawansowane środowisko edycji z pełną obsługą C# technologii IntelliSense (inteligentnych uzupełniania kodu) i debugowania.</span><span class="sxs-lookup"><span data-stu-id="a4850-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a4850-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a4850-106">Prerequisites</span></span>

1. <span data-ttu-id="a4850-107">Zainstaluj [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="a4850-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="a4850-108">Zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="a4850-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>
3. <span data-ttu-id="a4850-109">Zainstaluj [ C# rozszerzenie](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) dla Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="a4850-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="a4850-110">Aby uzyskać więcej informacji na temat sposobu instalowania rozszerzeń na Visual Studio Code, zobacz [vs Code rozszerzenia Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="a4850-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="a4850-111">Witaj Świecie</span><span class="sxs-lookup"><span data-stu-id="a4850-111">Hello World</span></span>

<span data-ttu-id="a4850-112">Zacznijmy od prostego programu "Hello world" na platformie .NET Core:</span><span class="sxs-lookup"><span data-stu-id="a4850-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="a4850-113">Otwórz projekt:</span><span class="sxs-lookup"><span data-stu-id="a4850-113">Open a project:</span></span>

    - <span data-ttu-id="a4850-114">Otwórz Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="a4850-114">Open Visual Studio Code.</span></span>
    - <span data-ttu-id="a4850-115">Kliknij ikonę Eksploratora w menu po lewej stronie, a następnie kliknij polecenie **Otwórz folder**.</span><span class="sxs-lookup"><span data-stu-id="a4850-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    - <span data-ttu-id="a4850-116">Wybierz pozycję **plik** > **Otwórz folder** z menu głównego, aby otworzyć folder, w którym C# ma się znajdować projekt, a następnie kliknij pozycję **Wybierz folder**.</span><span class="sxs-lookup"><span data-stu-id="a4850-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="a4850-117">W naszym przykładzie tworzymy folder dla naszego projektu o nazwie *HelloWorld*.</span><span class="sxs-lookup"><span data-stu-id="a4850-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![Visual Studio Code Otwórz folder](media/with-visual-studio-code/vs-code-open-folder.png)

2. <span data-ttu-id="a4850-119">Zainicjuj C# projekt:</span><span class="sxs-lookup"><span data-stu-id="a4850-119">Initialize a C# project:</span></span>

    - <span data-ttu-id="a4850-120">Otwórz zintegrowany terminal z Visual Studio Code, wybierając opcję **wyświetl** > **zintegrowany terminal** z menu głównego.</span><span class="sxs-lookup"><span data-stu-id="a4850-120">Open the Integrated Terminal from Visual Studio Code by selecting **View** > **Integrated Terminal** from the main menu.</span></span>
    - <span data-ttu-id="a4850-121">W oknie terminalu wpisz `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="a4850-121">In the terminal window, type `dotnet new console`.</span></span>
    - <span data-ttu-id="a4850-122">To polecenie tworzy plik *program.cs* w folderze z prostym, już zapisanym programem "Hello World", wraz z plikiem C# projektu o nazwie *HelloWorld. csproj*.</span><span class="sxs-lookup"><span data-stu-id="a4850-122">This command creates a *Program.cs* file in your folder with a simple "Hello World" program already written, along with a C# project file named *HelloWorld.csproj*.</span></span>

      ![Polecenie dotnet New](media/with-visual-studio-code/dotnet-new-command.png)

3. <span data-ttu-id="a4850-124">Rozpoznaj zasoby kompilacji:</span><span class="sxs-lookup"><span data-stu-id="a4850-124">Resolve the build assets:</span></span>

    - <span data-ttu-id="a4850-125">W przypadku **platformy .NET Core 1. x**wpisz `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="a4850-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="a4850-126">Uruchomienie `dotnet restore` daje dostęp do wymaganych pakietów .NET Core, które są potrzebne do skompilowania projektu.</span><span class="sxs-lookup"><span data-stu-id="a4850-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![dotnet restore polecenie](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="a4850-128">Uruchom program "Hello world":</span><span class="sxs-lookup"><span data-stu-id="a4850-128">Run the "Hello World" program:</span></span>

    - <span data-ttu-id="a4850-129">Wpisz `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="a4850-129">Type `dotnet run`.</span></span>

      ![Polecenie dotnet Run](media/with-visual-studio-code/dotnet-run-command.png)

<span data-ttu-id="a4850-131">Możesz również obejrzeć krótki samouczek wideo dotyczący dalszej instalacji [systemu Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS)lub [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="a4850-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="a4850-132">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="a4850-132">Debug</span></span>

1. <span data-ttu-id="a4850-133">Otwórz *program.cs* , klikając go.</span><span class="sxs-lookup"><span data-stu-id="a4850-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="a4850-134">Przy pierwszym otwarciu C# pliku w Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) ładuje się w edytorze.</span><span class="sxs-lookup"><span data-stu-id="a4850-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

    ![Otwórz plik Program.cs](media/with-visual-studio-code/open-program-cs.png)

2. <span data-ttu-id="a4850-136">Visual Studio Code powinien monitować o dodanie brakujących zasobów do kompilowania i debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a4850-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="a4850-137">Wybierz pozycję **tak**.</span><span class="sxs-lookup"><span data-stu-id="a4850-137">Select **Yes**.</span></span>

    ![Monituj o brakujące zasoby](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="a4850-139">Aby otworzyć widok debugowanie, kliknij ikonę debugowania w menu po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="a4850-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Otwórz kartę debugowanie w Visual Studio Code](media/with-visual-studio-code/open-debug-tab.png)

4. <span data-ttu-id="a4850-141">Znajdź zieloną strzałkę w górnej części okienka.</span><span class="sxs-lookup"><span data-stu-id="a4850-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="a4850-142">Upewnij się, że lista rozwijana obok niej ma wybraną wartość **.NET Core Start (Console)** .</span><span class="sxs-lookup"><span data-stu-id="a4850-142">Make sure the drop-down next to it has **.NET Core Launch (console)** selected.</span></span>

    ![Wybieranie platformy .NET Core w Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

5. <span data-ttu-id="a4850-144">Dodaj punkt przerwania do projektu, klikając **margines edytora**, który jest odstępem po lewej stronie numerów wierszy w edytorze, obok pozycji wiersz 9 lub Przenieś kursor tekstu do wiersza 9 w edytorze i naciśnij klawisz <kbd>F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="a4850-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![Ustawianie punktu przerwania](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. <span data-ttu-id="a4850-146">Aby rozpocząć debugowanie, naciśnij klawisz <kbd>F5</kbd> lub wybierz zieloną strzałkę.</span><span class="sxs-lookup"><span data-stu-id="a4850-146">To start debugging, press <kbd>F5</kbd> or select the green arrow.</span></span> <span data-ttu-id="a4850-147">Debuger przerywa wykonywanie programu po osiągnięciu punktu przerwania ustawionego w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="a4850-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    - <span data-ttu-id="a4850-148">Podczas debugowania można wyświetlić zmienne lokalne w lewym górnym okienku lub użyć konsoli debugowania.</span><span class="sxs-lookup"><span data-stu-id="a4850-148">While debugging, you can view your local variables in the top left pane or use the debug console.</span></span>

7. <span data-ttu-id="a4850-149">Wybierz niebieską strzałkę u góry, aby kontynuować debugowanie, lub zaznacz czerwony kwadrat u góry, aby go zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="a4850-149">Select the blue arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

    ![Uruchamianie i debugowanie w Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> <span data-ttu-id="a4850-151">Aby uzyskać więcej informacji i porady dotyczące rozwiązywania problemów dotyczących debugowania .NET Core za pomocą OmniSharp w Visual Studio Code, zobacz [instrukcje dotyczące konfigurowania debugera .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="a4850-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="add-a-class"></a><span data-ttu-id="a4850-152">Dodawanie klasy</span><span class="sxs-lookup"><span data-stu-id="a4850-152">Add a class</span></span>

1. <span data-ttu-id="a4850-153">Aby dodać nową klasę, kliknij prawym przyciskiem myszy w Eksploratorze programu vscode i wybierz pozycję **nowy plik**.</span><span class="sxs-lookup"><span data-stu-id="a4850-153">To add a new class, right click in the VSCode Explorer and select **New File**.</span></span> <span data-ttu-id="a4850-154">Spowoduje to dodanie nowego pliku do folderu, który został otwarty w programu vscode.</span><span class="sxs-lookup"><span data-stu-id="a4850-154">This adds a new file to the folder you have open in VSCode.</span></span>
2. <span data-ttu-id="a4850-155">Nazwij plik *MyClass.cs*.</span><span class="sxs-lookup"><span data-stu-id="a4850-155">Name your file *MyClass.cs*.</span></span> <span data-ttu-id="a4850-156">Musisz zapisać go z rozszerzeniem `.cs` na końcu, aby można go było rozpoznać jako plik CSharp.</span><span class="sxs-lookup"><span data-stu-id="a4850-156">You must save it with a `.cs` extension at the end for it to be recognized as a csharp file.</span></span>
3. <span data-ttu-id="a4850-157">Dodaj poniższy kod, aby utworzyć swoją pierwszą klasę.</span><span class="sxs-lookup"><span data-stu-id="a4850-157">Add the code below to create your first class.</span></span> <span data-ttu-id="a4850-158">Upewnij się, że dołączysz poprawną przestrzeń nazw, aby można było odwołać się do niej z pliku *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="a4850-158">Make sure to include the correct namespace so you can reference it from your *Program.cs* file:</span></span>

    ``` csharp
    using System;

    namespace HelloWorld
    {
        public class MyClass
        {
            public string ReturnMessage()
            {
                return "Happy coding!";
            }
        }
    }
    ```

4. <span data-ttu-id="a4850-159">Wywołaj nową klasę z metody Main w *program.cs* , dodając Poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="a4850-159">Call your new class from your main method in *Program.cs* by adding the code below:</span></span>

    ```csharp
    using System;
    
    namespace HelloWorld
    {
        class Program
        {
            static void Main(string[] args)
            {
                var c1 = new MyClass();
                Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
            }
        }
    }
    ```

5. <span data-ttu-id="a4850-160">Zapisz zmiany i ponownie uruchom program.</span><span class="sxs-lookup"><span data-stu-id="a4850-160">Save your changes and run your program again.</span></span> <span data-ttu-id="a4850-161">Nowy komunikat powinien pojawić się z dołączonym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="a4850-161">The new message should appear with the appended string.</span></span>

    ```console
    > dotnet run
    Hello World! Happy coding!
    ```

## <a name="faq"></a><span data-ttu-id="a4850-162">Najczęściej zadawane pytania</span><span class="sxs-lookup"><span data-stu-id="a4850-162">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="a4850-163">Nie mam wymaganych zasobów do kompilowania i debugowania C# w Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="a4850-163">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="a4850-164">My Debugger brzmi "Brak konfiguracji".</span><span class="sxs-lookup"><span data-stu-id="a4850-164">My debugger says "No Configuration."</span></span>

<span data-ttu-id="a4850-165">Rozszerzenie Visual Studio Code C# może generować zasoby do kompilowania i debugowania.</span><span class="sxs-lookup"><span data-stu-id="a4850-165">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="a4850-166">Visual Studio Code poprosi o wygenerowanie tych zasobów przy pierwszym otwarciu C# projektu.</span><span class="sxs-lookup"><span data-stu-id="a4850-166">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="a4850-167">Jeśli zasoby nie zostały jeszcze wygenerowane, możesz uruchomić to polecenie, otwierając paletę poleceń (**wyświetl > palecie poleceń**) i wpisując "> .NET: Generate Assets for build and debug".</span><span class="sxs-lookup"><span data-stu-id="a4850-167">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="a4850-168">Wybranie tej opcji spowoduje wygenerowanie plików konfiguracyjnych *. programu vscode*, *Launch. JSON*i *Tasks. JSON* , które są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="a4850-168">Selecting this generates the *.vscode*, *launch.json*, and *tasks.json* configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4850-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4850-169">See also</span></span>

- [<span data-ttu-id="a4850-170">Konfigurowanie Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="a4850-170">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
- [<span data-ttu-id="a4850-171">Debugowanie w Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="a4850-171">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
