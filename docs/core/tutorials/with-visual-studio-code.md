---
title: Wprowadzenie do języka C# i programu Visual Studio Code
description: Dowiedz się, jak utworzyć i debugować pierwszą aplikację .NET Core w języku C# przy użyciu kodu programu Visual Studio.
author: kendrahavens
ms.date: 12/05/2018
ms.openlocfilehash: 8eaf1ba2314dcab96db615a8691afed82c5011a7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398882"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="63d6a-103">Wprowadzenie do języka C# i programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="63d6a-103">Get started with C# and Visual Studio Code</span></span>

<span data-ttu-id="63d6a-104">.NET Core zapewnia szybką i modułową platformę do tworzenia aplikacji działających w systemach Windows, Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="63d6a-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="63d6a-105">Użyj kodu programu Visual Studio z rozszerzeniem Języka C#, aby uzyskać zaawansowane środowisko edycji z pełną obsługą języka C# IntelliSense (inteligentnego uzupełniania kodu) i debugowania.</span><span class="sxs-lookup"><span data-stu-id="63d6a-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="63d6a-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="63d6a-106">Prerequisites</span></span>

1. <span data-ttu-id="63d6a-107">Zainstaluj narzędzie [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="63d6a-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="63d6a-108">Zainstaluj zestaw [SDK .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="63d6a-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>
3. <span data-ttu-id="63d6a-109">Zainstaluj [rozszerzenie C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) dla kodu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="63d6a-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="63d6a-110">Aby uzyskać więcej informacji na temat instalowania rozszerzeń w kodzie programu Visual Studio, zobacz [Vs Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="63d6a-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="63d6a-111">Witaj, świecie</span><span class="sxs-lookup"><span data-stu-id="63d6a-111">Hello World</span></span>

<span data-ttu-id="63d6a-112">Zacznijmy od prostego programu "Hello World" w programie .NET Core:</span><span class="sxs-lookup"><span data-stu-id="63d6a-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="63d6a-113">Otwórz projekt:</span><span class="sxs-lookup"><span data-stu-id="63d6a-113">Open a project:</span></span>

    - <span data-ttu-id="63d6a-114">Otwórz program Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="63d6a-114">Open Visual Studio Code.</span></span>
    - <span data-ttu-id="63d6a-115">Kliknij ikonę Eksploratora w menu po lewej stronie, a następnie kliknij pozycję **Otwórz folder**.</span><span class="sxs-lookup"><span data-stu-id="63d6a-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    - <span data-ttu-id="63d6a-116">Wybierz **pozycję Otwórz folder pliku** > **Open Folder** z menu głównego, aby otworzyć folder, w którym ma znajdować się projekt języka C#, i kliknij pozycję **Wybierz folder**.</span><span class="sxs-lookup"><span data-stu-id="63d6a-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="63d6a-117">W naszym przykładzie tworzymy folder dla naszego projektu o nazwie *HelloWorld*.</span><span class="sxs-lookup"><span data-stu-id="63d6a-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![Otwarty folder kodu programu Visual Studio](media/with-visual-studio-code/vs-code-open-folder.png)

2. <span data-ttu-id="63d6a-119">Inicjuj projekt języka C#:</span><span class="sxs-lookup"><span data-stu-id="63d6a-119">Initialize a C# project:</span></span>

    - <span data-ttu-id="63d6a-120">Otwórz zintegrowany terminal z kodu Visual Studio, wybierając z menu głównego **opcję Wyświetl** > **zintegrowany terminal.**</span><span class="sxs-lookup"><span data-stu-id="63d6a-120">Open the Integrated Terminal from Visual Studio Code by selecting **View** > **Integrated Terminal** from the main menu.</span></span>
    - <span data-ttu-id="63d6a-121">W oknie terminalu `dotnet new console`wpisz .</span><span class="sxs-lookup"><span data-stu-id="63d6a-121">In the terminal window, type `dotnet new console`.</span></span>
    - <span data-ttu-id="63d6a-122">To polecenie tworzy *plik Program.cs* w folderze z prostym programem "Hello World" już napisanym, wraz z plikiem projektu C# o nazwie *HelloWorld.csproj*.</span><span class="sxs-lookup"><span data-stu-id="63d6a-122">This command creates a *Program.cs* file in your folder with a simple "Hello World" program already written, along with a C# project file named *HelloWorld.csproj*.</span></span>

      ![Nowe polecenie dotnet](media/with-visual-studio-code/dotnet-new-command.png)

3. <span data-ttu-id="63d6a-124">Rozwiąż zasoby kompilacji:</span><span class="sxs-lookup"><span data-stu-id="63d6a-124">Resolve the build assets:</span></span>

    - <span data-ttu-id="63d6a-125">Dla **.NET Core 1.x**, wpisz `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="63d6a-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="63d6a-126">Uruchamianie `dotnet restore` zapewnia dostęp do wymaganych pakietów .NET Core, które są potrzebne do tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="63d6a-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![Polecenie przywracania dotnetu](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="63d6a-128">Uruchom program "Hello World":</span><span class="sxs-lookup"><span data-stu-id="63d6a-128">Run the "Hello World" program:</span></span>

    - <span data-ttu-id="63d6a-129">Wpisz polecenie `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="63d6a-129">Type `dotnet run`.</span></span>

      ![Polecenie uruchamiania dotnet](media/with-visual-studio-code/dotnet-run-command.png)

<span data-ttu-id="63d6a-131">Możesz również obejrzeć krótki film instruktażowy, aby uzyskać dalszą pomoc w konfiguracji w [systemie Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS)lub [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="63d6a-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="63d6a-132">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="63d6a-132">Debug</span></span>

1. <span data-ttu-id="63d6a-133">Otwórz *Program.cs,* klikając na niego.</span><span class="sxs-lookup"><span data-stu-id="63d6a-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="63d6a-134">Przy pierwszym otwarciu pliku C# w kodzie programu Visual Studio [omniSharp](https://www.omnisharp.net/) ładuje się w edytorze.</span><span class="sxs-lookup"><span data-stu-id="63d6a-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

    ![Otwieranie pliku Program.cs](media/with-visual-studio-code/open-program-cs.png)

2. <span data-ttu-id="63d6a-136">Kod programu Visual Studio powinien monitować o dodanie brakujących zasobów do tworzenia i debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="63d6a-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="63d6a-137">Wybierz **pozycję Tak**.</span><span class="sxs-lookup"><span data-stu-id="63d6a-137">Select **Yes**.</span></span>

    ![Monituj o brakujące zasoby](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="63d6a-139">Aby otworzyć widok Debugowania, kliknij ikonę Debugowanie w menu po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="63d6a-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Otwieranie karty Debugowanie w kodzie programu Visual Studio](media/with-visual-studio-code/open-debug-tab.png)

4. <span data-ttu-id="63d6a-141">Zlokalizuj zieloną strzałkę w górnej części okienka.</span><span class="sxs-lookup"><span data-stu-id="63d6a-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="63d6a-142">Upewnij się, że w menu rozwijanym obok jest zaznaczona opcja **.NET Core Launch (konsola).**</span><span class="sxs-lookup"><span data-stu-id="63d6a-142">Make sure the drop-down next to it has **.NET Core Launch (console)** selected.</span></span>

    ![Wybieranie programu .NET Core w kodzie programu Visual Studio](media/with-visual-studio-code/select-net-core.png)

5. <span data-ttu-id="63d6a-144">Dodaj punkt przerwania do projektu, klikając **margines edytora**, który jest miejscem po lewej stronie numerów wierszy w edytorze, obok wiersza 9, lub przenieś kursor tekstu na wiersz 9 w edytorze i naciśnij <kbd>klawisz F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="63d6a-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![Ustawianie punktu przerwania](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. <span data-ttu-id="63d6a-146">Aby rozpocząć debugowanie, naciśnij <kbd>klawisz F5</kbd> lub wybierz zieloną strzałkę.</span><span class="sxs-lookup"><span data-stu-id="63d6a-146">To start debugging, press <kbd>F5</kbd> or select the green arrow.</span></span> <span data-ttu-id="63d6a-147">Debuger zatrzymuje wykonywanie programu po osiągnięciu punktu przerwania ustawionego w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="63d6a-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    - <span data-ttu-id="63d6a-148">Podczas debugowania można wyświetlać zmienne lokalne w lewym górnym okienku lub korzystać z konsoli debugowania.</span><span class="sxs-lookup"><span data-stu-id="63d6a-148">While debugging, you can view your local variables in the top left pane or use the debug console.</span></span>

7. <span data-ttu-id="63d6a-149">Wybierz niebieską strzałkę u góry, aby kontynuować debugowanie, lub wybierz czerwony kwadrat u góry, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="63d6a-149">Select the blue arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

    ![Uruchamianie i debugowanie w kodzie programu Visual Studio](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> <span data-ttu-id="63d6a-151">Aby uzyskać więcej informacji i wskazówki dotyczące rozwiązywania problemów dotyczące debugowania .NET Core za pomocą narzędzia OmniSharp w kodzie programu Visual Studio, zobacz [Instrukcje dotyczące konfigurowania debugera .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="63d6a-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="add-a-class"></a><span data-ttu-id="63d6a-152">Dodawanie klasy</span><span class="sxs-lookup"><span data-stu-id="63d6a-152">Add a class</span></span>

1. <span data-ttu-id="63d6a-153">Aby dodać nową klasę, kliknij prawym przyciskiem myszy eksploratorvscode i wybierz polecenie **Nowy plik**.</span><span class="sxs-lookup"><span data-stu-id="63d6a-153">To add a new class, right click in the VSCode Explorer and select **New File**.</span></span> <span data-ttu-id="63d6a-154">Spowoduje to dodanie nowego pliku do folderu otwartego w VSCode.</span><span class="sxs-lookup"><span data-stu-id="63d6a-154">This adds a new file to the folder you have open in VSCode.</span></span>
2. <span data-ttu-id="63d6a-155">Nazwij plik *MyClass.cs*.</span><span class="sxs-lookup"><span data-stu-id="63d6a-155">Name your file *MyClass.cs*.</span></span> <span data-ttu-id="63d6a-156">Należy zapisać go `.cs` z rozszerzeniem na końcu, aby został rozpoznany jako plik csharp.</span><span class="sxs-lookup"><span data-stu-id="63d6a-156">You must save it with a `.cs` extension at the end for it to be recognized as a csharp file.</span></span>
3. <span data-ttu-id="63d6a-157">Dodaj poniższy kod, aby utworzyć pierwszą klasę.</span><span class="sxs-lookup"><span data-stu-id="63d6a-157">Add the code below to create your first class.</span></span> <span data-ttu-id="63d6a-158">Upewnij się, że zawiera poprawny obszar nazw, dzięki czemu można odwoływać się do niego z pliku *Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="63d6a-158">Make sure to include the correct namespace so you can reference it from your *Program.cs* file:</span></span>

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

4. <span data-ttu-id="63d6a-159">Zadzwoń do nowej klasy z głównej metody w *Program.cs,* dodając poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="63d6a-159">Call your new class from your main method in *Program.cs* by adding the code below:</span></span>

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

5. <span data-ttu-id="63d6a-160">Zapisz zmiany i uruchom program ponownie.</span><span class="sxs-lookup"><span data-stu-id="63d6a-160">Save your changes and run your program again.</span></span> <span data-ttu-id="63d6a-161">Nowa wiadomość powinna pojawić się z dołączonym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="63d6a-161">The new message should appear with the appended string.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="63d6a-162">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="63d6a-162">You get the following output:</span></span>

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a><span data-ttu-id="63d6a-163">Często zadawane pytania</span><span class="sxs-lookup"><span data-stu-id="63d6a-163">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="63d6a-164">Brakuje wymaganych zasobów do tworzenia i debugowania języka C# w kodzie programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="63d6a-164">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="63d6a-165">Mój debuger mówi "Brak konfiguracji".</span><span class="sxs-lookup"><span data-stu-id="63d6a-165">My debugger says "No Configuration."</span></span>

<span data-ttu-id="63d6a-166">Rozszerzenie Kodu C# programu Visual Studio może generować zasoby do tworzenia i debugowania dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="63d6a-166">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="63d6a-167">Kod programu Visual Studio monituje o wygenerowanie tych zasobów po pierwszym otwarciu projektu C#.</span><span class="sxs-lookup"><span data-stu-id="63d6a-167">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="63d6a-168">Jeśli nie wygenerowałeś zasobów, nadal można uruchomić to polecenie, otwierając paletę poleceń **(Widok > paletę poleceń)** i wpisując ">.NET: Generuj zasoby dla kompilacji i debugowania".</span><span class="sxs-lookup"><span data-stu-id="63d6a-168">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="63d6a-169">Wybranie tej opcji generuje pliki konfiguracyjne *.vscode*, *launch.json*i *tasks.json.*</span><span class="sxs-lookup"><span data-stu-id="63d6a-169">Selecting this generates the *.vscode*, *launch.json*, and *tasks.json* configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="63d6a-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63d6a-170">See also</span></span>

- [<span data-ttu-id="63d6a-171">Konfigurowanie kodu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="63d6a-171">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
- [<span data-ttu-id="63d6a-172">Debugowanie w kodzie programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="63d6a-172">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
