---
title: Tworzenie aplikacji konsolowej z platformą .NET Core przy użyciu Visual Studio Code
description: Dowiedz się, jak utworzyć aplikację konsolową .NET Core przy użyciu Visual Studio Code i interfejs wiersza polecenia platformy .NET Core.
ms.date: 05/22/2020
ms.openlocfilehash: 673c4a639a2cab26261b7cdafd5d8e20acfafb94
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201703"
---
# <a name="tutorial-create-a-console-application-with-net-core-using-visual-studio-code"></a><span data-ttu-id="4ed2c-103">Samouczek: Tworzenie aplikacji konsolowej z platformą .NET Core przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4ed2c-103">Tutorial: Create a console application with .NET Core using Visual Studio Code</span></span>

<span data-ttu-id="4ed2c-104">W tym samouczku pokazano, jak utworzyć i uruchomić aplikację konsolową .NET Core przy użyciu Visual Studio Code i interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-104">This tutorial shows how to create and run a .NET Core console application by using Visual Studio Code and the .NET Core CLI.</span></span> <span data-ttu-id="4ed2c-105">Zadania projektu, takie jak tworzenie, kompilowanie i uruchamianie projektu, są wykonywane za pomocą interfejsu wiersza polecenia, więc można wykonać kroki tego samouczka z innym edytorem kodu i uruchamiać polecenia w terminalu, jeśli wolisz.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-105">Project tasks, such as creating, compiling, and running a project are done by using the CLI, so you can follow this tutorial with a different code editor and run commands in a terminal if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4ed2c-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="4ed2c-106">Prerequisites</span></span>

1. <span data-ttu-id="4ed2c-107">[Visual Studio Code](https://code.visualstudio.com/) z zainstalowanym [rozszerzeniem języka C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) .</span><span class="sxs-lookup"><span data-stu-id="4ed2c-107">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="4ed2c-108">Aby uzyskać informacje na temat sposobu instalowania rozszerzeń na Visual Studio Code, zobacz [vs Code rozszerzenia Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="4ed2c-108">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="4ed2c-109">[Zestaw SDK platformy .NET Core 3,1 lub nowszy](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="4ed2c-109">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-the-app"></a><span data-ttu-id="4ed2c-110">Tworzymy aplikację.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-110">Create the app</span></span>

1. <span data-ttu-id="4ed2c-111">Otwórz program Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-111">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="4ed2c-112">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-112">Create a project.</span></span>

   1. <span data-ttu-id="4ed2c-113">Wybierz pozycję **plik**  >  **Otwórz folder** / **Otwórz...** z menu głównego, Utwórz folder *HelloWorld* , a następnie kliknij pozycję **Wybierz folder** / **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-113">Select **File** > **Open Folder**/**Open...** from the main menu, create a *HelloWorld* folder, and click **Select Folder**/**Open**.</span></span>

      <span data-ttu-id="4ed2c-114">Nazwa folderu domyślnie zmienia nazwę projektu i nazwę przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-114">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="4ed2c-115">Kod zostanie dodany później w samouczku, który zakłada, że przestrzeń nazw projektu to `HelloWorld` .</span><span class="sxs-lookup"><span data-stu-id="4ed2c-115">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

   1. <span data-ttu-id="4ed2c-116">Otwórz **Terminal** w Visual Studio Code, wybierając pozycję **Wyświetl**  >  **Terminal** z menu głównego.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-116">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

      <span data-ttu-id="4ed2c-117">Zostanie otwarty **Terminal** z wierszem polecenia w folderze *HelloWorld* .</span><span class="sxs-lookup"><span data-stu-id="4ed2c-117">The **Terminal** opens with the command prompt in the *HelloWorld* folder.</span></span>

   1. <span data-ttu-id="4ed2c-118">W **terminalu**wprowadź następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="4ed2c-118">In the **Terminal**, enter the following command:</span></span>

      ```dotnetcli
      dotnet new console
      ```

<span data-ttu-id="4ed2c-119">Szablon aplikacji konsoli dla platformy .NET Core definiuje klasę, `Program` przy użyciu pojedynczej metody, `Main` która pobiera <xref:System.String> tablicę jako argument.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-119">The Console Application template for .NET Core defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="4ed2c-120">Plik *program.cs* ma następujący kod:</span><span class="sxs-lookup"><span data-stu-id="4ed2c-120">The *Program.cs* file has the following code:</span></span>

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

<span data-ttu-id="4ed2c-121">`Main`jest punktem wejścia aplikacji, metoda, która jest wywoływana automatycznie przez środowisko uruchomieniowe podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-121">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="4ed2c-122">Wszystkie argumenty wiersza polecenia dostarczone podczas uruchamiania aplikacji są dostępne w tablicy *args* .</span><span class="sxs-lookup"><span data-stu-id="4ed2c-122">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="4ed2c-123">Szablon tworzy prostą aplikację, która wywołuje <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodę, aby wyświetlić "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="4ed2c-123">The template creates a simple application that calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="4ed2c-124">w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-124">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="4ed2c-125">Uruchomienie aplikacji</span><span class="sxs-lookup"><span data-stu-id="4ed2c-125">Run the app</span></span>

<span data-ttu-id="4ed2c-126">Uruchom następujące polecenie w **terminalu**:</span><span class="sxs-lookup"><span data-stu-id="4ed2c-126">Run the following command in the **Terminal**:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="4ed2c-127">Program wyświetla "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="4ed2c-127">The program displays "Hello World!"</span></span> <span data-ttu-id="4ed2c-128">i zakończenia.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-128">and ends.</span></span>

![Polecenie dotnet Run](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a><span data-ttu-id="4ed2c-130">Ulepszanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="4ed2c-130">Enhance the app</span></span>

<span data-ttu-id="4ed2c-131">Podnieś poziom aplikacji, aby monitować użytkownika o jego nazwę i wyświetlić go wraz z datą i godziną.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-131">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="4ed2c-132">Otwórz *program.cs* , klikając go.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-132">Open *Program.cs* by clicking on it.</span></span>

   <span data-ttu-id="4ed2c-133">Przy pierwszym otwarciu pliku C# w Visual Studio Code [OmniSharp](https://www.omnisharp.net/) ładuje się w edytorze.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-133">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

   ![Otwórz plik Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="4ed2c-135">Wybierz opcję **tak** , gdy Visual Studio Code zostanie wyświetlony komunikat z prośbą o dodanie brakujących zasobów do kompilowania i debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-135">Select **Yes** when Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span>

   ![Monituj o brakujące zasoby](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="4ed2c-137">Zastąp zawartość `Main` metody w *program.cs*, która jest obecnie tylko wierszem, który wywołuje `Console.WriteLine` , przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="4ed2c-137">Replace the contents of the `Main` method in *Program.cs*, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="Snippet1":::

   <span data-ttu-id="4ed2c-138">Ten kod wyświetla "co to jest Twoja nazwa?"</span><span class="sxs-lookup"><span data-stu-id="4ed2c-138">This code displays "What is your name?"</span></span> <span data-ttu-id="4ed2c-139">w oknie konsoli i czeka, aż użytkownik wprowadzi ciąg, a następnie klawisz **Enter** .</span><span class="sxs-lookup"><span data-stu-id="4ed2c-139">in the console window and waits until the user enters a string followed by the **Enter** key.</span></span> <span data-ttu-id="4ed2c-140">Ten ciąg jest przechowywany w zmiennej o nazwie `name` .</span><span class="sxs-lookup"><span data-stu-id="4ed2c-140">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="4ed2c-141">Pobiera również wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości, która zawiera bieżący czas lokalny i przypisuje go do zmiennej o nazwie `date` .</span><span class="sxs-lookup"><span data-stu-id="4ed2c-141">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="4ed2c-142">Na koniec wyświetla te wartości w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-142">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="4ed2c-143">`\n`Reprezentuje znak nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-143">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="4ed2c-144">Znak dolara ( `$` ) przed ciągiem umożliwia umieszczenie wyrażeń takich jak nazwy zmiennych w nawiasach klamrowych w ciągu.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-144">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="4ed2c-145">Wartość wyrażenia jest wstawiana do ciągu zamiast wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-145">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="4ed2c-146">Ta składnia jest określana mianem [ciągów interpolowanych](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="4ed2c-146">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="4ed2c-147">Zapisz zmiany.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-147">Save your changes.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="4ed2c-148">W Visual Studio Code należy jawnie zapisać zmiany.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-148">In Visual Studio Code, you have to explicitly save changes.</span></span> <span data-ttu-id="4ed2c-149">W przeciwieństwie do programu Visual Studio zmiany plików nie są automatycznie zapisywane podczas kompilowania i uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-149">Unlike Visual Studio, file changes are not automatically saved when you build and run an app.</span></span>

1. <span data-ttu-id="4ed2c-150">Ponownie uruchom program:</span><span class="sxs-lookup"><span data-stu-id="4ed2c-150">Run the program again:</span></span>

   ```dotnetcli
   dotnet run
   ```

1. <span data-ttu-id="4ed2c-151">Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz **Enter** .</span><span class="sxs-lookup"><span data-stu-id="4ed2c-151">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="Okno terminalu ze zmodyfikowanym wyjściem programu":::

1. <span data-ttu-id="4ed2c-153">Naciśnij dowolny klawisz, aby wyjść z programu.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-153">Press any key to exit the program.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="4ed2c-154">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="4ed2c-154">Additional resources</span></span>

- [<span data-ttu-id="4ed2c-155">Konfigurowanie Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4ed2c-155">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a><span data-ttu-id="4ed2c-156">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="4ed2c-156">Next steps</span></span>

<span data-ttu-id="4ed2c-157">W tym samouczku utworzono aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-157">In this tutorial, you created a .NET Core application.</span></span> <span data-ttu-id="4ed2c-158">W następnym samouczku debugujesz aplikację.</span><span class="sxs-lookup"><span data-stu-id="4ed2c-158">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4ed2c-159">Debugowanie aplikacji konsolowej .NET Core przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4ed2c-159">Debug a .NET Core console application using Visual Studio Code</span></span>](debugging-with-visual-studio-code.md)
