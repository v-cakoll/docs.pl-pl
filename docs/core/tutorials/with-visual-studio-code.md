---
title: Tworzenie aplikacji konsolowej platformy .NET Core przy użyciu Visual Studio Code
description: Dowiedz się, jak utworzyć aplikację konsolową .NET Core przy użyciu Visual Studio Code i interfejs wiersza polecenia platformy .NET Core.
ms.date: 05/22/2020
ms.openlocfilehash: 6d8f9adb2f77dbfd2d1cf54c80f1cdea582b1d96
ms.sourcegitcommit: f6350c2c542e6edd52d7e9d6667b96d85d810e67
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2020
ms.locfileid: "84717513"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-code"></a><span data-ttu-id="21baf-103">Samouczek: Tworzenie aplikacji konsolowej platformy .NET Core przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="21baf-103">Tutorial: Create a .NET Core console application using Visual Studio Code</span></span>

<span data-ttu-id="21baf-104">W tym samouczku pokazano, jak utworzyć i uruchomić aplikację konsolową .NET Core przy użyciu Visual Studio Code i interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="21baf-104">This tutorial shows how to create and run a .NET Core console application by using Visual Studio Code and the .NET Core CLI.</span></span> <span data-ttu-id="21baf-105">Zadania projektu, takie jak tworzenie, kompilowanie i uruchamianie projektu, są wykonywane przy użyciu interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="21baf-105">Project tasks, such as creating, compiling, and running a project are done by using the .NET Core CLI.</span></span> <span data-ttu-id="21baf-106">Możesz wykonać czynności opisane w tym samouczku z innym edytorem kodu i uruchamiać polecenia w terminalu, jeśli wolisz.</span><span class="sxs-lookup"><span data-stu-id="21baf-106">You can follow this tutorial with a different code editor and run commands in a terminal if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="21baf-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="21baf-107">Prerequisites</span></span>

1. <span data-ttu-id="21baf-108">[Visual Studio Code](https://code.visualstudio.com/) z zainstalowanym [rozszerzeniem języka C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) .</span><span class="sxs-lookup"><span data-stu-id="21baf-108">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="21baf-109">Aby uzyskać informacje na temat sposobu instalowania rozszerzeń na Visual Studio Code, zobacz [vs Code rozszerzenia Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="21baf-109">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="21baf-110">[Zestaw SDK platformy .NET Core 3,1 lub nowszy](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="21baf-110">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-the-app"></a><span data-ttu-id="21baf-111">Tworzymy aplikację.</span><span class="sxs-lookup"><span data-stu-id="21baf-111">Create the app</span></span>

<span data-ttu-id="21baf-112">Utwórz projekt aplikacji konsolowej .NET Core o nazwie "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="21baf-112">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="21baf-113">Uruchom program Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="21baf-113">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="21baf-114">Wybierz pozycję **plik**  >  **Otwórz folder** (Otwórz**plik**  >  **...** na macOS) z menu głównego.</span><span class="sxs-lookup"><span data-stu-id="21baf-114">Select **File** > **Open Folder** (**File** > **Open...** on macOS) from the main menu.</span></span>

1. <span data-ttu-id="21baf-115">W oknie dialogowym **Otwieranie folderu** Utwórz folder *HelloWorld* i kliknij pozycję **Wybierz folder** (**Otwórz** w macOS).</span><span class="sxs-lookup"><span data-stu-id="21baf-115">In the **Open Folder** dialog, create a *HelloWorld* folder and click **Select Folder** (**Open** on macOS).</span></span>

   <span data-ttu-id="21baf-116">Nazwa folderu domyślnie zmienia nazwę projektu i nazwę przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="21baf-116">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="21baf-117">Kod zostanie dodany później w samouczku, który zakłada, że przestrzeń nazw projektu to `HelloWorld` .</span><span class="sxs-lookup"><span data-stu-id="21baf-117">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

1. <span data-ttu-id="21baf-118">Otwórz **Terminal** w Visual Studio Code, wybierając pozycję **Wyświetl**  >  **Terminal** z menu głównego.</span><span class="sxs-lookup"><span data-stu-id="21baf-118">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="21baf-119">Zostanie otwarty **Terminal** z wierszem polecenia w folderze *HelloWorld* .</span><span class="sxs-lookup"><span data-stu-id="21baf-119">The **Terminal** opens with the command prompt in the *HelloWorld* folder.</span></span>

1. <span data-ttu-id="21baf-120">W **terminalu**wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="21baf-120">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new console
   ```

<span data-ttu-id="21baf-121">Szablon tworzy prostą aplikację "Hello world".</span><span class="sxs-lookup"><span data-stu-id="21baf-121">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="21baf-122">Wywołuje metodę, <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> Aby wyświetlić "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="21baf-122">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="21baf-123">w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="21baf-123">in the console window.</span></span>

<span data-ttu-id="21baf-124">Kod szablonu definiuje klasę, `Program` przy użyciu pojedynczej metody, `Main` która przyjmuje <xref:System.String> tablicę jako argument:</span><span class="sxs-lookup"><span data-stu-id="21baf-124">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="21baf-125">`Main`jest punktem wejścia aplikacji, metoda, która jest wywoływana automatycznie przez środowisko uruchomieniowe podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21baf-125">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="21baf-126">Wszystkie argumenty wiersza polecenia dostarczone podczas uruchamiania aplikacji są dostępne w tablicy *args* .</span><span class="sxs-lookup"><span data-stu-id="21baf-126">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="21baf-127">Uruchomienie aplikacji</span><span class="sxs-lookup"><span data-stu-id="21baf-127">Run the app</span></span>

<span data-ttu-id="21baf-128">Uruchom następujące polecenie w **terminalu**:</span><span class="sxs-lookup"><span data-stu-id="21baf-128">Run the following command in the **Terminal**:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="21baf-129">Program wyświetla "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="21baf-129">The program displays "Hello World!"</span></span> <span data-ttu-id="21baf-130">i zakończenia.</span><span class="sxs-lookup"><span data-stu-id="21baf-130">and ends.</span></span>

![Polecenie dotnet Run](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a><span data-ttu-id="21baf-132">Ulepszanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="21baf-132">Enhance the app</span></span>

<span data-ttu-id="21baf-133">Podnieś poziom aplikacji, aby monitować użytkownika o jego nazwę i wyświetlić go wraz z datą i godziną.</span><span class="sxs-lookup"><span data-stu-id="21baf-133">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="21baf-134">Otwórz *program.cs* , klikając go.</span><span class="sxs-lookup"><span data-stu-id="21baf-134">Open *Program.cs* by clicking on it.</span></span>

   <span data-ttu-id="21baf-135">Przy pierwszym otwarciu pliku C# w Visual Studio Code [OmniSharp](https://www.omnisharp.net/) ładuje się w edytorze.</span><span class="sxs-lookup"><span data-stu-id="21baf-135">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

   ![Otwórz plik Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="21baf-137">Wybierz opcję **tak** , gdy Visual Studio Code zostanie wyświetlony komunikat z prośbą o dodanie brakujących zasobów do kompilowania i debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21baf-137">Select **Yes** when Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span>

   ![Monituj o brakujące zasoby](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="21baf-139">Zastąp zawartość `Main` metody w *program.cs*, która jest wierszem, który wywołuje `Console.WriteLine` , przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="21baf-139">Replace the contents of the `Main` method in *Program.cs*, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="1":::

   <span data-ttu-id="21baf-140">Ten kod wyświetla "co to jest Twoja nazwa?"</span><span class="sxs-lookup"><span data-stu-id="21baf-140">This code displays "What is your name?"</span></span> <span data-ttu-id="21baf-141">w oknie konsoli i czeka, aż użytkownik wprowadzi ciąg, a następnie klawisz <kbd>Enter</kbd> .</span><span class="sxs-lookup"><span data-stu-id="21baf-141">in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="21baf-142">Ten ciąg jest przechowywany w zmiennej o nazwie `name` .</span><span class="sxs-lookup"><span data-stu-id="21baf-142">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="21baf-143">Pobiera również wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości, która zawiera bieżący czas lokalny i przypisuje go do zmiennej o nazwie `date` .</span><span class="sxs-lookup"><span data-stu-id="21baf-143">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="21baf-144">Na koniec wyświetla te wartości w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="21baf-144">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="21baf-145">`\n`Reprezentuje znak nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="21baf-145">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="21baf-146">Znak dolara ( `$` ) przed ciągiem umożliwia umieszczenie wyrażeń takich jak nazwy zmiennych w nawiasach klamrowych w ciągu.</span><span class="sxs-lookup"><span data-stu-id="21baf-146">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="21baf-147">Wartość wyrażenia jest wstawiana do ciągu zamiast wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="21baf-147">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="21baf-148">Ta składnia jest określana mianem [ciągów interpolowanych](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="21baf-148">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="21baf-149">Zapisz zmiany.</span><span class="sxs-lookup"><span data-stu-id="21baf-149">Save your changes.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="21baf-150">W Visual Studio Code należy jawnie zapisać zmiany.</span><span class="sxs-lookup"><span data-stu-id="21baf-150">In Visual Studio Code, you have to explicitly save changes.</span></span> <span data-ttu-id="21baf-151">W przeciwieństwie do programu Visual Studio zmiany plików nie są automatycznie zapisywane podczas kompilowania i uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21baf-151">Unlike Visual Studio, file changes are not automatically saved when you build and run an app.</span></span>

1. <span data-ttu-id="21baf-152">Ponownie uruchom program:</span><span class="sxs-lookup"><span data-stu-id="21baf-152">Run the program again:</span></span>

   ```dotnetcli
   dotnet run
   ```

1. <span data-ttu-id="21baf-153">Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz <kbd>Enter</kbd> .</span><span class="sxs-lookup"><span data-stu-id="21baf-153">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="Okno terminalu ze zmodyfikowanym wyjściem programu":::

1. <span data-ttu-id="21baf-155">Naciśnij dowolny klawisz, aby wyjść z programu.</span><span class="sxs-lookup"><span data-stu-id="21baf-155">Press any key to exit the program.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="21baf-156">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="21baf-156">Additional resources</span></span>

- [<span data-ttu-id="21baf-157">Konfigurowanie Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="21baf-157">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a><span data-ttu-id="21baf-158">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="21baf-158">Next steps</span></span>

<span data-ttu-id="21baf-159">W tym samouczku utworzono aplikację konsolową .NET Core.</span><span class="sxs-lookup"><span data-stu-id="21baf-159">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="21baf-160">W następnym samouczku debugujesz aplikację.</span><span class="sxs-lookup"><span data-stu-id="21baf-160">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="21baf-161">Debugowanie aplikacji konsolowej .NET Core przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="21baf-161">Debug a .NET Core console application using Visual Studio Code</span></span>](debugging-with-visual-studio-code.md)
