---
title: Wprowadzenie do języka C# i programu Visual Studio Code
description: Dowiedz się, jak utworzyć i debugować pierwszą aplikację platformy .NET Core w języku C# przy użyciu Visual Studio Code.
author: kendrahavens
ms.date: 04/23/2020
ms.openlocfilehash: 3dd7c4602fbb27e29bad977f8d3df34b6061bc23
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506909"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="3e212-103">Wprowadzenie do języka C# i programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3e212-103">Get started with C# and Visual Studio Code</span></span>

<span data-ttu-id="3e212-104">Program .NET Core zapewnia szybką i modularną platformę do tworzenia aplikacji działających w systemach Windows, Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="3e212-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="3e212-105">Użyj Visual Studio Code z rozszerzeniem języka C#, aby uzyskać zaawansowane środowisko edycji z pełną obsługą technologii IntelliSense dla języka C# (inteligentnych uzupełniania kodu) i debugowania.</span><span class="sxs-lookup"><span data-stu-id="3e212-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3e212-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="3e212-106">Prerequisites</span></span>

1. <span data-ttu-id="3e212-107">Zainstaluj narzędzie [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="3e212-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="3e212-108">Zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="3e212-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>
3. <span data-ttu-id="3e212-109">Zainstaluj [rozszerzenie C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) dla Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="3e212-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="3e212-110">Aby uzyskać więcej informacji na temat sposobu instalowania rozszerzeń na Visual Studio Code, zobacz [vs Code rozszerzenia Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="3e212-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="3e212-111">Witaj, świecie</span><span class="sxs-lookup"><span data-stu-id="3e212-111">Hello World</span></span>

<span data-ttu-id="3e212-112">Rozpocznij pracę z prostym programem "Hello world" na platformie .NET Core:</span><span class="sxs-lookup"><span data-stu-id="3e212-112">Get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="3e212-113">Otwórz projekt:</span><span class="sxs-lookup"><span data-stu-id="3e212-113">Open a project:</span></span>

    - <span data-ttu-id="3e212-114">Otwórz program Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="3e212-114">Open Visual Studio Code.</span></span>
    - <span data-ttu-id="3e212-115">Wybierz pozycję **plik** > **Otwórz folder** z menu głównego.</span><span class="sxs-lookup"><span data-stu-id="3e212-115">Select **File** > **Open Folder** from the main menu.</span></span>
    - <span data-ttu-id="3e212-116">Utwórz folder o nazwie *HelloWorld*, a następnie kliknij pozycję **Wybierz folder**.</span><span class="sxs-lookup"><span data-stu-id="3e212-116">Create a folder named *HelloWorld*, and click **Select Folder**.</span></span> <span data-ttu-id="3e212-117">Nazwa folderu domyślnie zmienia nazwę projektu i nazwę przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3e212-117">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="3e212-118">Kod zostanie dodany później w samouczku, który zakłada, że przestrzeń nazw `HelloWorld`projektu to.</span><span class="sxs-lookup"><span data-stu-id="3e212-118">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

1. <span data-ttu-id="3e212-119">Zainicjuj projekt C#:</span><span class="sxs-lookup"><span data-stu-id="3e212-119">Initialize a C# project:</span></span>

    - <span data-ttu-id="3e212-120">Otwórz Terminal z Visual Studio Code, wybierając pozycję **Wyświetl** > **Terminal** z menu głównego.</span><span class="sxs-lookup"><span data-stu-id="3e212-120">Open the Terminal from Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>
    - <span data-ttu-id="3e212-121">W oknie terminalu wprowadź `dotnet new console`wartość.</span><span class="sxs-lookup"><span data-stu-id="3e212-121">In the terminal window, enter `dotnet new console`.</span></span>

      <span data-ttu-id="3e212-122">To polecenie tworzy plik *program.cs* w folderze z prostym, zapisanym już programem "Hello World", wraz z plikiem projektu C# o nazwie *HelloWorld. csproj*.</span><span class="sxs-lookup"><span data-stu-id="3e212-122">This command creates a *Program.cs* file in your folder with a simple "Hello World" program already written, along with a C# project file named *HelloWorld.csproj*.</span></span>

      ![Polecenie dotnet New](media/with-visual-studio-code/dotnet-new-command.png)

1. <span data-ttu-id="3e212-124">Uruchom program "Hello world":</span><span class="sxs-lookup"><span data-stu-id="3e212-124">Run the "Hello World" program:</span></span>

    - <span data-ttu-id="3e212-125">W oknie terminalu wprowadź `dotnet run`wartość.</span><span class="sxs-lookup"><span data-stu-id="3e212-125">In the terminal window, enter `dotnet run`.</span></span>

      ![Polecenie dotnet Run](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="debug"></a><span data-ttu-id="3e212-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="3e212-127">Debug</span></span>

1. <span data-ttu-id="3e212-128">Otwórz *program.cs* , klikając go.</span><span class="sxs-lookup"><span data-stu-id="3e212-128">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="3e212-129">Przy pierwszym otwarciu pliku C# w Visual Studio Code [OmniSharp](https://www.omnisharp.net/) ładuje się w edytorze.</span><span class="sxs-lookup"><span data-stu-id="3e212-129">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

    ![Otwórz plik Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="3e212-131">Visual Studio Code zostanie wyświetlony komunikat z prośbą o dodanie brakujących zasobów w celu skompilowania i debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3e212-131">Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="3e212-132">Wybierz pozycję **tak**.</span><span class="sxs-lookup"><span data-stu-id="3e212-132">Select **Yes**.</span></span>

    ![Monituj o brakujące zasoby](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="3e212-134">Aby otworzyć widok debugowanie, kliknij ikonę debugowania w menu po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="3e212-134">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Otwórz kartę debugowanie w Visual Studio Code](media/with-visual-studio-code/open-debug-tab.png)

1. <span data-ttu-id="3e212-136">Znajdź zieloną strzałkę w górnej części okienka.</span><span class="sxs-lookup"><span data-stu-id="3e212-136">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="3e212-137">Upewnij się, że lista rozwijana obok niej ma wybraną wartość **.NET Core Start (Console)** .</span><span class="sxs-lookup"><span data-stu-id="3e212-137">Make sure the drop-down next to it has **.NET Core Launch (console)** selected.</span></span>

    ![Wybieranie platformy .NET Core w Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

1. <span data-ttu-id="3e212-139">Dodaj punkt przerwania do projektu, klikając **margines edytora**, który jest odstępem po lewej stronie numerów wierszy w edytorze, obok pozycji wiersz 9 lub Przenieś kursor tekstu do wiersza 9 w edytorze i naciśnij klawisz <kbd>F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="3e212-139">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![Ustawianie punktu przerwania](media/with-visual-studio-code/set-breakpoint-vs-code.png)

1. <span data-ttu-id="3e212-141">Aby rozpocząć debugowanie, naciśnij klawisz <kbd>F5</kbd> lub wybierz zieloną strzałkę.</span><span class="sxs-lookup"><span data-stu-id="3e212-141">To start debugging, press <kbd>F5</kbd> or select the green arrow.</span></span> <span data-ttu-id="3e212-142">Debuger przerywa wykonywanie programu po osiągnięciu punktu przerwania ustawionego w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="3e212-142">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    - <span data-ttu-id="3e212-143">Podczas debugowania można wyświetlić zmienne lokalne w lewym górnym okienku lub użyć konsoli debugowania.</span><span class="sxs-lookup"><span data-stu-id="3e212-143">While debugging, you can view your local variables in the top-left pane or use the debug console.</span></span>

1. <span data-ttu-id="3e212-144">Wybierz niebieską strzałkę u góry, aby kontynuować debugowanie, lub zaznacz czerwony kwadrat u góry, aby go zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="3e212-144">Select the blue arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

    ![Uruchamianie i debugowanie w Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> <span data-ttu-id="3e212-146">Aby uzyskać więcej informacji i porady dotyczące rozwiązywania problemów dotyczących debugowania .NET Core za pomocą OmniSharp w Visual Studio Code, zobacz [instrukcje dotyczące konfigurowania debugera .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="3e212-146">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="add-a-class"></a><span data-ttu-id="3e212-147">Dodawanie klasy</span><span class="sxs-lookup"><span data-stu-id="3e212-147">Add a class</span></span>

1. <span data-ttu-id="3e212-148">Aby dodać nową klasę, kliknij prawym przyciskiem myszy w Eksploratorze programu vscode poniżej *program.cs* i wybierz pozycję **nowy plik**.</span><span class="sxs-lookup"><span data-stu-id="3e212-148">To add a new class, right-click in the VSCode Explorer below *Program.cs* and select **New File**.</span></span> <span data-ttu-id="3e212-149">Spowoduje to dodanie nowego pliku do folderu, który został otwarty w programu vscode.</span><span class="sxs-lookup"><span data-stu-id="3e212-149">This adds a new file to the folder you have open in VSCode.</span></span>
1. <span data-ttu-id="3e212-150">Nazwij plik *MyClass.cs*.</span><span class="sxs-lookup"><span data-stu-id="3e212-150">Name your file *MyClass.cs*.</span></span> <span data-ttu-id="3e212-151">Musisz zapisać go z `.cs` rozszerzeniem na końcu, aby można go było rozpoznać jako plik CSharp.</span><span class="sxs-lookup"><span data-stu-id="3e212-151">You must save it with a `.cs` extension at the end for it to be recognized as a csharp file.</span></span>
1. <span data-ttu-id="3e212-152">Dodaj następujący kod, aby utworzyć swoją pierwszą klasę.</span><span class="sxs-lookup"><span data-stu-id="3e212-152">Add the following code to create your first class.</span></span>

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

1. <span data-ttu-id="3e212-153">Wywołaj nową klasę z `Main` metody, zastępując kod w *program.cs* następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="3e212-153">Call your new class from your `Main` method by replacing the code in *Program.cs* with the following code:</span></span>

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

1. <span data-ttu-id="3e212-154">Zapisz zmiany.</span><span class="sxs-lookup"><span data-stu-id="3e212-154">Save your changes.</span></span>

1. <span data-ttu-id="3e212-155">Ponownie uruchom program.</span><span class="sxs-lookup"><span data-stu-id="3e212-155">Run the program again.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="3e212-156">Zostanie wyświetlony nowy komunikat z dołączonym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="3e212-156">The new message appears with the appended string.</span></span>

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a><span data-ttu-id="3e212-157">Najczęściej zadawane pytania</span><span class="sxs-lookup"><span data-stu-id="3e212-157">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="3e212-158">Brakuje wymaganych zasobów do kompilowania i debugowania języka C# w Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="3e212-158">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="3e212-159">My Debugger brzmi "Brak konfiguracji".</span><span class="sxs-lookup"><span data-stu-id="3e212-159">My debugger says "No Configuration."</span></span>

<span data-ttu-id="3e212-160">Rozszerzenie C# Visual Studio Code może generować zasoby do kompilowania i debugowania.</span><span class="sxs-lookup"><span data-stu-id="3e212-160">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="3e212-161">Visual Studio Code poprosi o wygenerowanie tych zasobów przy pierwszym otwarciu projektu C#.</span><span class="sxs-lookup"><span data-stu-id="3e212-161">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="3e212-162">Jeśli zasoby nie zostały jeszcze wygenerowane, możesz uruchomić to polecenie, otwierając paletę poleceń (**wyświetl > palecie poleceń**) i wpisując "> .NET: Generate Assets for build and debug".</span><span class="sxs-lookup"><span data-stu-id="3e212-162">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="3e212-163">Wybranie tej opcji spowoduje wygenerowanie plików konfiguracyjnych *. programu vscode*, *Launch. JSON*i *Tasks. JSON* , które są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="3e212-163">Selecting this generates the *.vscode*, *launch.json*, and *tasks.json* configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e212-164">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e212-164">See also</span></span>

- [<span data-ttu-id="3e212-165">Konfigurowanie Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3e212-165">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
- [<span data-ttu-id="3e212-166">Debugowanie w Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3e212-166">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
