---
title: Wprowadzenie do języka C# i programu Visual Studio Code
description: Dowiedz się, jak utworzyć i debugować pierwszą aplikację .NET Core w języku C# przy użyciu programu Visual Studio Code.
author: kendrahavens
ms.date: 12/05/2018
ms.openlocfilehash: 6722b97cee5ca3672c9dddece6e61f4d13de05a9
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805813"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="c0fff-103">Wprowadzenie do języka C# i programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c0fff-103">Get started with C# and Visual Studio Code</span></span>

<span data-ttu-id="c0fff-104">Program .NET Core zapewnia szybką i modułową platformę do tworzenia aplikacji uruchomionych w systemach Windows, Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="c0fff-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="c0fff-105">Użyj programu Visual Studio Code z rozszerzeniem C#, aby uzyskać zaawansowane środowisko edycji z pełną obsługą języka C# IntelliSense (ukończenie inteligentnego kodu) i debugowanie.</span><span class="sxs-lookup"><span data-stu-id="c0fff-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c0fff-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c0fff-106">Prerequisites</span></span>

1. <span data-ttu-id="c0fff-107">Zainstaluj narzędzie [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="c0fff-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="c0fff-108">Zainstaluj pakiet [.NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="c0fff-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>
3. <span data-ttu-id="c0fff-109">Zainstaluj [rozszerzenie C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) dla programu Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c0fff-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="c0fff-110">Aby uzyskać więcej informacji na temat instalowania rozszerzeń w programie Visual Studio Code, zobacz [vs.](https://code.visualstudio.com/docs/editor/extension-gallery)</span><span class="sxs-lookup"><span data-stu-id="c0fff-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="c0fff-111">Witaj, świecie</span><span class="sxs-lookup"><span data-stu-id="c0fff-111">Hello World</span></span>

<span data-ttu-id="c0fff-112">Zacznijmy od prostego programu "Hello World" w serwisie .NET Core:</span><span class="sxs-lookup"><span data-stu-id="c0fff-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="c0fff-113">Otwórz projekt:</span><span class="sxs-lookup"><span data-stu-id="c0fff-113">Open a project:</span></span>

    - <span data-ttu-id="c0fff-114">Otwórz program Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c0fff-114">Open Visual Studio Code.</span></span>
    - <span data-ttu-id="c0fff-115">Kliknij ikonę Eksploratora w menu po lewej stronie, a następnie kliknij pozycję **Otwórz folder**.</span><span class="sxs-lookup"><span data-stu-id="c0fff-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    - <span data-ttu-id="c0fff-116">Wybierz **polecenie Folder** > **otwierania pliku** z menu głównego, aby otworzyć folder, w który ma znajdować się projekt języka C#, a następnie kliknij pozycję Wybierz **folder**.</span><span class="sxs-lookup"><span data-stu-id="c0fff-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="c0fff-117">Na przykład tworzymy folder dla naszego projektu o nazwie *HelloWorld*.</span><span class="sxs-lookup"><span data-stu-id="c0fff-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![Folder otwarty kodu programu Visual Studio](media/with-visual-studio-code/vs-code-open-folder.png)

2. <span data-ttu-id="c0fff-119">Zainicjowanie projektu języka C#:</span><span class="sxs-lookup"><span data-stu-id="c0fff-119">Initialize a C# project:</span></span>

    - <span data-ttu-id="c0fff-120">Otwórz terminal z programu Visual Studio Code, wybierając **pozycję Wyświetl** > **terminal** z menu głównego.</span><span class="sxs-lookup"><span data-stu-id="c0fff-120">Open the Terminal from Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>
    - <span data-ttu-id="c0fff-121">W oknie terminala `dotnet new console`wpisz .</span><span class="sxs-lookup"><span data-stu-id="c0fff-121">In the terminal window, type `dotnet new console`.</span></span>
    - <span data-ttu-id="c0fff-122">To polecenie tworzy *plik Program.cs* w folderze z prostym programem "Hello World" już napisanym, wraz z plikiem projektu C# o nazwie *HelloWorld.csproj*.</span><span class="sxs-lookup"><span data-stu-id="c0fff-122">This command creates a *Program.cs* file in your folder with a simple "Hello World" program already written, along with a C# project file named *HelloWorld.csproj*.</span></span>

      ![Nowe polecenie dotnet](media/with-visual-studio-code/dotnet-new-command.png)

3. <span data-ttu-id="c0fff-124">Rozwiąż zasoby kompilacji:</span><span class="sxs-lookup"><span data-stu-id="c0fff-124">Resolve the build assets:</span></span>

    - <span data-ttu-id="c0fff-125">W przypadku **.NET Core 1.x**wpisz `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="c0fff-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="c0fff-126">Uruchamianie `dotnet restore` daje dostęp do wymaganych pakietów .NET Core, które są potrzebne do tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="c0fff-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![Polecenie przywracania dotnetu](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="c0fff-128">Uruchom program "Hello World":</span><span class="sxs-lookup"><span data-stu-id="c0fff-128">Run the "Hello World" program:</span></span>

    - <span data-ttu-id="c0fff-129">Wpisz polecenie `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="c0fff-129">Type `dotnet run`.</span></span>

      ![Polecenie dotnet run](media/with-visual-studio-code/dotnet-run-command.png)

<span data-ttu-id="c0fff-131">Można również obejrzeć krótki film instruktażowy dla dalszej pomocy konfiguracji w [systemie Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS)lub [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="c0fff-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="c0fff-132">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="c0fff-132">Debug</span></span>

1. <span data-ttu-id="c0fff-133">Otwórz *Program.cs* klikając na niego.</span><span class="sxs-lookup"><span data-stu-id="c0fff-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="c0fff-134">Przy pierwszym otwarciu pliku języka C# w programie Visual Studio [Code, OmniSharp](https://www.omnisharp.net/) ładuje się w edytorze.</span><span class="sxs-lookup"><span data-stu-id="c0fff-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

    ![Otwieranie pliku Program.cs](media/with-visual-studio-code/open-program-cs.png)

2. <span data-ttu-id="c0fff-136">Visual Studio Kod powinien monitować o dodanie brakujących zasobów do tworzenia i debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0fff-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="c0fff-137">Wybierz **pozycję Tak**.</span><span class="sxs-lookup"><span data-stu-id="c0fff-137">Select **Yes**.</span></span>

    ![Monitowanie o brakujące zasoby](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="c0fff-139">Aby otworzyć widok debugowania, kliknij ikonę debugowania w menu po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="c0fff-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Otwieranie karty Debugowanie w programie Visual Studio Code](media/with-visual-studio-code/open-debug-tab.png)

4. <span data-ttu-id="c0fff-141">Znajdź zieloną strzałkę w górnej części okienka.</span><span class="sxs-lookup"><span data-stu-id="c0fff-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="c0fff-142">Upewnij się, że obok listy rozwijanej jest zaznaczona opcja **.NET Core Launch (konsola).**</span><span class="sxs-lookup"><span data-stu-id="c0fff-142">Make sure the drop-down next to it has **.NET Core Launch (console)** selected.</span></span>

    ![Wybieranie programu .NET Core w programie Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

5. <span data-ttu-id="c0fff-144">Dodaj punkt przerwania do projektu, klikając **na margines edytora**, który jest spacją po lewej stronie numerów wierszy w edytorze, obok wiersza 9, lub przenieś kursor tekstowy na linię 9 w edytorze i naciśnij <kbd>klawisz F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="c0fff-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![Ustawianie punktu przerwania](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. <span data-ttu-id="c0fff-146">Aby rozpocząć debugowanie, naciśnij <kbd>klawisz F5</kbd> lub wybierz zieloną strzałkę.</span><span class="sxs-lookup"><span data-stu-id="c0fff-146">To start debugging, press <kbd>F5</kbd> or select the green arrow.</span></span> <span data-ttu-id="c0fff-147">Debuger zatrzymuje wykonywanie programu, gdy osiągnie punkt przerwania ustawiony w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="c0fff-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    - <span data-ttu-id="c0fff-148">Podczas debugowania można wyświetlić zmienne lokalne w lewym górnym okienku lub użyć konsoli debugowania.</span><span class="sxs-lookup"><span data-stu-id="c0fff-148">While debugging, you can view your local variables in the top-left pane or use the debug console.</span></span>

7. <span data-ttu-id="c0fff-149">Wybierz niebieską strzałkę u góry, aby kontynuować debugowanie, lub wybierz czerwony kwadrat u góry, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="c0fff-149">Select the blue arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

    ![Uruchamianie i debugowanie w programie Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> <span data-ttu-id="c0fff-151">Aby uzyskać więcej informacji i wskazówek dotyczących rozwiązywania problemów z debugowaniem rdzenia .NET za pomocą programu OmniSharp w programie Visual Studio Code, zobacz [Instrukcje konfigurowania debugera .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="c0fff-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="add-a-class"></a><span data-ttu-id="c0fff-152">Dodawanie klasy</span><span class="sxs-lookup"><span data-stu-id="c0fff-152">Add a class</span></span>

1. <span data-ttu-id="c0fff-153">Aby dodać nową klasę, kliknij prawym przyciskiem myszy w Eksploratorze VSCode i wybierz polecenie **Nowy plik**.</span><span class="sxs-lookup"><span data-stu-id="c0fff-153">To add a new class, right-click in the VSCode Explorer and select **New File**.</span></span> <span data-ttu-id="c0fff-154">Spowoduje to dodanie nowego pliku do folderu otwartego w programie VSCode.</span><span class="sxs-lookup"><span data-stu-id="c0fff-154">This adds a new file to the folder you have open in VSCode.</span></span>
2. <span data-ttu-id="c0fff-155">Nadaj nazwę *pliku MyClass.cs*.</span><span class="sxs-lookup"><span data-stu-id="c0fff-155">Name your file *MyClass.cs*.</span></span> <span data-ttu-id="c0fff-156">Musisz zapisać go `.cs` z rozszerzeniem na końcu, aby został rozpoznany jako plik csharp.</span><span class="sxs-lookup"><span data-stu-id="c0fff-156">You must save it with a `.cs` extension at the end for it to be recognized as a csharp file.</span></span>
3. <span data-ttu-id="c0fff-157">Dodaj poniższy kod, aby utworzyć pierwszą klasę.</span><span class="sxs-lookup"><span data-stu-id="c0fff-157">Add the code below to create your first class.</span></span> <span data-ttu-id="c0fff-158">Upewnij się, że zawieraszdytny obszar nazw, aby można było odwoływać się do niego z pliku *Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="c0fff-158">Make sure to include the correct namespace so you can reference it from your *Program.cs* file:</span></span>

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

4. <span data-ttu-id="c0fff-159">Zadzwoń do nowej klasy z głównej metody w *Program.cs,* dodając poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="c0fff-159">Call your new class from your main method in *Program.cs* by adding the code below:</span></span>

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

5. <span data-ttu-id="c0fff-160">Zapisz zmiany i uruchom program ponownie.</span><span class="sxs-lookup"><span data-stu-id="c0fff-160">Save your changes and run your program again.</span></span> <span data-ttu-id="c0fff-161">Nowa wiadomość powinna pojawić się z dołączonym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="c0fff-161">The new message should appear with the appended string.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="c0fff-162">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="c0fff-162">You get the following output:</span></span>

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a><span data-ttu-id="c0fff-163">Często zadawane pytania</span><span class="sxs-lookup"><span data-stu-id="c0fff-163">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="c0fff-164">Brakuje mi wymaganych zasobów do tworzenia i debugowania języka C# w programie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c0fff-164">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="c0fff-165">Mój debuger mówi "Brak konfiguracji".</span><span class="sxs-lookup"><span data-stu-id="c0fff-165">My debugger says "No Configuration."</span></span>

<span data-ttu-id="c0fff-166">Rozszerzenie kodu programu Visual Studio C# może generować zasoby do tworzenia i debugowania dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="c0fff-166">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="c0fff-167">Visual Studio Code monituje o wygenerowanie tych zasobów przy pierwszym otwarciu projektu języka C#.</span><span class="sxs-lookup"><span data-stu-id="c0fff-167">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="c0fff-168">Jeśli nie wygenerowałeś zasobów, to nadal można uruchomić to polecenie, otwierając paletę poleceń **(Wyświetl > paletę poleceń)** i wpisując ">.NET: Generuj zasoby dla kompilacji i debugowania".</span><span class="sxs-lookup"><span data-stu-id="c0fff-168">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="c0fff-169">Wybranie tej opcji powoduje wygenerowanie potrzebnych plików konfiguracyjnych *.vscode*, *launch.json*i *tasks.json.*</span><span class="sxs-lookup"><span data-stu-id="c0fff-169">Selecting this generates the *.vscode*, *launch.json*, and *tasks.json* configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0fff-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0fff-170">See also</span></span>

- [<span data-ttu-id="c0fff-171">Konfigurowanie kodu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c0fff-171">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
- [<span data-ttu-id="c0fff-172">Debugowanie w programie Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c0fff-172">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
