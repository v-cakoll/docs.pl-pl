---
title: Wprowadzenie do języka C# i Visual Studio Code
description: Informacje o sposobie tworzenia i debugowania pierwszej aplikacji platformy .NET Core w języku C# za pomocą programu Visual Studio Code.
author: kendrahavens
ms.date: 12/05/2018
ms.custom: seodec18
ms.openlocfilehash: d91427197662d61c1c3ffc242de9b1128b81b9c6
ms.sourcegitcommit: 5c2176883dc3107445702724a7caa7ac2f6cb0d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2019
ms.locfileid: "58890556"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="ca14e-103">Wprowadzenie do języka C# i Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ca14e-103">Get started with C# and Visual Studio Code</span></span>

<span data-ttu-id="ca14e-104">.NET core udostępnia szybka, modularna platforma do tworzenia aplikacji działających w Windows, Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="ca14e-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="ca14e-105">Użyj programu Visual Studio Code z rozszerzeniem języka C#, aby uzyskać Zaawansowane edytowanie z pełnym wsparciem dla języka C# IntelliSense (uzupełnianie kodu inteligentnych) i debugowania.</span><span class="sxs-lookup"><span data-stu-id="ca14e-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ca14e-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ca14e-106">Prerequisites</span></span>

1. <span data-ttu-id="ca14e-107">Zainstaluj [programu Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="ca14e-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="ca14e-108">Zainstaluj [platformy .NET Core SDK](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="ca14e-108">Install the [.NET Core SDK](https://www.microsoft.com/net/download/core).</span></span>
3. <span data-ttu-id="ca14e-109">Zainstaluj [rozszerzenie języka C#](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) dla programu Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ca14e-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="ca14e-110">Aby uzyskać więcej informacji na temat instalowania rozszerzeń w programie Visual Studio Code, zobacz [Portal Marketplace z rozszerzeniami kodu programu VS](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="ca14e-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="ca14e-111">Witaj Świecie</span><span class="sxs-lookup"><span data-stu-id="ca14e-111">Hello World</span></span>

<span data-ttu-id="ca14e-112">Zacznijmy od prostego programu "Hello World" na platformie .NET Core:</span><span class="sxs-lookup"><span data-stu-id="ca14e-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="ca14e-113">Otwórz projekt:</span><span class="sxs-lookup"><span data-stu-id="ca14e-113">Open a project:</span></span>

    * <span data-ttu-id="ca14e-114">Open Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ca14e-114">Open Visual Studio Code.</span></span>
    * <span data-ttu-id="ca14e-115">Kliknij ikonę Explorer z menu po lewej stronie, a następnie kliknij przycisk **Otwórz Folder**.</span><span class="sxs-lookup"><span data-stu-id="ca14e-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    * <span data-ttu-id="ca14e-116">Wybierz **pliku** > **Otwórz Folder** z menu głównego, aby otworzyć folder dla której projekt C# w, a następnie kliknij przycisk **wybierz Folder**.</span><span class="sxs-lookup"><span data-stu-id="ca14e-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="ca14e-117">W tym przykładzie tworzymy folderem naszego projektu o nazwie *HelloWorld*.</span><span class="sxs-lookup"><span data-stu-id="ca14e-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![Visual Studio Code Otwórz folder.](media/with-visual-studio-code/vs-code-open-folder.png)

2. <span data-ttu-id="ca14e-119">Inicjowanie projektu C#:</span><span class="sxs-lookup"><span data-stu-id="ca14e-119">Initialize a C# project:</span></span>
    * <span data-ttu-id="ca14e-120">Otworzyć zintegrowany Terminal programu z Visual Studio Code, wybierając **widoku** > **zintegrowany Terminal** z menu głównego.</span><span class="sxs-lookup"><span data-stu-id="ca14e-120">Open the Integrated Terminal from Visual Studio Code by selecting **View** > **Integrated Terminal** from the main menu.</span></span>
    * <span data-ttu-id="ca14e-121">W oknie terminalu wpisz `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="ca14e-121">In the terminal window, type `dotnet new console`.</span></span>
    * <span data-ttu-id="ca14e-122">To polecenie umożliwia utworzenie `Program.cs` plik w folderze przy użyciu programu proste "Hello World", została ona już zapisana, wraz z plikiem projektu C# o nazwie `HelloWorld.csproj`.</span><span class="sxs-lookup"><span data-stu-id="ca14e-122">This command creates a `Program.cs` file in your folder with a simple "Hello World" program already written, along with a C# project file named `HelloWorld.csproj`.</span></span>

      ![Nowe polecenie dotnet](media/with-visual-studio-code/dotnet-new-command.png)

3. <span data-ttu-id="ca14e-124">Aby usunąć zasoby kompilacji:</span><span class="sxs-lookup"><span data-stu-id="ca14e-124">Resolve the build assets:</span></span>

    * <span data-ttu-id="ca14e-125">Aby uzyskać **platformy .NET Core 1.x**, typ `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="ca14e-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="ca14e-126">Uruchamianie `dotnet restore` zapewnia dostęp do wymaganych pakietów .NET Core, które są wymagane do kompilowania projektu.</span><span class="sxs-lookup"><span data-stu-id="ca14e-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![Polecenie restore dotnet](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="ca14e-128">Uruchom program "Hello World":</span><span class="sxs-lookup"><span data-stu-id="ca14e-128">Run the "Hello World" program:</span></span>

    * <span data-ttu-id="ca14e-129">Typ `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="ca14e-129">Type `dotnet run`.</span></span>

      ![Polecenia dotnet, uruchom polecenie](media/with-visual-studio-code/dotnet-run-command.png)

<span data-ttu-id="ca14e-131">Możesz też obejrzeć krótki samouczek wideo, aby uzyskać dalszą pomoc Instalatora na [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), lub [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="ca14e-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="ca14e-132">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ca14e-132">Debug</span></span>

1. <span data-ttu-id="ca14e-133">Otwórz *Program.cs* , klikając ją.</span><span class="sxs-lookup"><span data-stu-id="ca14e-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="ca14e-134">Przy pierwszym otwarciu pliku C# w programie Visual Studio Code [technologię OmniSharp](https://www.omnisharp.net/) ładuje w edytorze.</span><span class="sxs-lookup"><span data-stu-id="ca14e-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

    ![Otwórz plik Program.cs](media/with-visual-studio-code/open-program-cs.png)

2. <span data-ttu-id="ca14e-136">Visual Studio Code powinien zostać wyświetlony monit można dodać brakujące zasoby do tworzenia i debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ca14e-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="ca14e-137">Wybierz **tak**.</span><span class="sxs-lookup"><span data-stu-id="ca14e-137">Select **Yes**.</span></span>

    ![Monituj o brakujących zasobów](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="ca14e-139">Aby otworzyć widok debugowania, kliknij ikonę debugowanie z menu po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="ca14e-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Otwórz kartę debugowania w programie Visual Studio Codee](media/with-visual-studio-code/open-debug-tab.png)

4. <span data-ttu-id="ca14e-141">Znajdź zieloną strzałkę w górnej części okienka.</span><span class="sxs-lookup"><span data-stu-id="ca14e-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="ca14e-142">Upewnij się, ma listę rozwijaną obok niego `.NET Core Launch (console)` wybrane.</span><span class="sxs-lookup"><span data-stu-id="ca14e-142">Make sure the drop-down next to it has `.NET Core Launch (console)` selected.</span></span>

    ![Wybieranie platformy .NET Core w programie Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

5. <span data-ttu-id="ca14e-144">Dodaj punkt przerwania do projektu, klikając **marginesu edytora**, która jest miejsce po lewej stronie numery wierszy w edytorze, obok wiersza 9, lub Przesuń kursor tekst w wierszu 9 w edytorze i naciśnij klawisz <kbd>F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="ca14e-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![Ustawienie punktu przerwania](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. <span data-ttu-id="ca14e-146">Aby rozpocząć debugowanie, wybierz <kbd>F5</kbd> lub zieloną strzałkę.</span><span class="sxs-lookup"><span data-stu-id="ca14e-146">To start debugging, select <kbd>F5</kbd> or the green arrow.</span></span> <span data-ttu-id="ca14e-147">Debuger zatrzymuje wykonanie programu, po osiągnięciu punktu przerwania ustawione w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="ca14e-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    * <span data-ttu-id="ca14e-148">Podczas debugowania, można wyświetlać swoje zmienne lokalne w górnym okienku po lewej stronie, lub za pomocą konsoli debugowania.</span><span class="sxs-lookup"><span data-stu-id="ca14e-148">While debugging, you can view your local variables in the top left pane or use the debug console.</span></span>

7. <span data-ttu-id="ca14e-149">Wybierz niebieską strzałką u góry, aby kontynuować debugowanie lub wybrać czerwony kwadrat u góry, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="ca14e-149">Select the blue arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

    ![Uruchamianie i debugowanie w programie Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> <span data-ttu-id="ca14e-151">Aby uzyskać więcej informacji i rozwiązywanie problemów z porad na temat platformy .NET Core debugowania przy użyciu technologię OmniSharp w programie Visual Studio Code, zobacz [instrukcje dotyczące konfigurowania debugera platformy .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="ca14e-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="add-a-class"></a><span data-ttu-id="ca14e-152">Dodaj klasę</span><span class="sxs-lookup"><span data-stu-id="ca14e-152">Add a class</span></span>

1. <span data-ttu-id="ca14e-153">Aby dodać nowe kliknij prawym przyciskiem myszy klasy w Eksploratorze programu VSCode i wybierz **nowy plik**.</span><span class="sxs-lookup"><span data-stu-id="ca14e-153">To add a new class right-click in the VSCode Explorer and select **New File**.</span></span> <span data-ttu-id="ca14e-154">Spowoduje to dodanie nowego pliku do folderu otwartych w VSCode.</span><span class="sxs-lookup"><span data-stu-id="ca14e-154">This adds a new file to the folder you have open in VSCode.</span></span>
2. <span data-ttu-id="ca14e-155">Nadaj plikowi nazwę `MyClass.cs`.</span><span class="sxs-lookup"><span data-stu-id="ca14e-155">Name your file `MyClass.cs`.</span></span> <span data-ttu-id="ca14e-156">Musisz zapisać ją z `.cs` rozszerzenia na końcu, aby mogła zostać rozpoznany jako plik csharp.</span><span class="sxs-lookup"><span data-stu-id="ca14e-156">You must save it with a `.cs` extension at the end for it to be recognized as a csharp file.</span></span>
3. <span data-ttu-id="ca14e-157">Dodaj poniższy kod, aby tworzenie swojej pierwszej klasy.</span><span class="sxs-lookup"><span data-stu-id="ca14e-157">Add the code below to create your first class.</span></span> <span data-ttu-id="ca14e-158">Upewnij się, że zawiera poprawną przestrzeń nazw, więc możesz odwoływać się do niej z usługi `Program.cs` pliku.</span><span class="sxs-lookup"><span data-stu-id="ca14e-158">Make sure to include the correct namespace so you can reference it from your `Program.cs` file.</span></span>
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

4. <span data-ttu-id="ca14e-159">Wywoływanie nowej klasie z głównej metody w `Program.cs` , dodając poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="ca14e-159">Call your new class from your main method in `Program.cs` by adding the code below.</span></span>

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            MyClass c1 = new MyClass();
            Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
        }
    }
}
```

5. <span data-ttu-id="ca14e-160">Zapisz zmiany, a następnie ponownie uruchom program.</span><span class="sxs-lookup"><span data-stu-id="ca14e-160">Save your changes and run your program again.</span></span> <span data-ttu-id="ca14e-161">Nowa wiadomość powinna zostać wyświetlona z dołączonym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="ca14e-161">The new message should appear with the appended string.</span></span>
```console
> dotnet run
Hello World! Happy coding!
```

## <a name="faq"></a><span data-ttu-id="ca14e-162">Najczęściej zadawane pytania</span><span class="sxs-lookup"><span data-stu-id="ca14e-162">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="ca14e-163">Brakiem wymagane zasoby do tworzenia i debugowania języka C# w programie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ca14e-163">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="ca14e-164">Moje debugera jest wyświetlany komunikat "Brak konfiguracji".</span><span class="sxs-lookup"><span data-stu-id="ca14e-164">My debugger says "No Configuration."</span></span>

<span data-ttu-id="ca14e-165">Rozszerzenia programu Visual Studio kodu C# można wygenerować zasoby do tworzenia i debugowania dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="ca14e-165">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="ca14e-166">Visual Studio Code jest wyświetlany monit o generowanie tych zasobów, przy pierwszym otwarciu projektu C#.</span><span class="sxs-lookup"><span data-stu-id="ca14e-166">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="ca14e-167">Jeśli nie Generuj elementy zawartości, to nadal można uruchomić tego polecenia, otwierając paletę poleceń (**Widok > paletę poleceń**) i wprowadzając polecenie "> .NET: Wygenerować zasoby kompilacji i debugowania".</span><span class="sxs-lookup"><span data-stu-id="ca14e-167">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="ca14e-168">Wybranie tej generuje .vscode pliku launch.json i tasks.json pliki konfiguracji, które należy.</span><span class="sxs-lookup"><span data-stu-id="ca14e-168">Selecting this generates the .vscode, launch.json, and tasks.json configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca14e-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca14e-169">See also</span></span>

- [<span data-ttu-id="ca14e-170">Konfigurowanie programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ca14e-170">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
- [<span data-ttu-id="ca14e-171">Debugowanie w programie Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ca14e-171">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
