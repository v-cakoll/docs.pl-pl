---
title: Tworzenie aplikacji konsolowej przy użyciu platformy .NET Core w programie Visual Studio
description: Dowiedz się, jak utworzyć aplikację konsolową .NET Core w języku C# lub Visual Basic przy użyciu programu Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 9c3456cd8c940e53e8a70c1d3a7c3b09de77c21d
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201586"
---
# <a name="tutorial-create-a-net-core-console-application-in-visual-studio-2019"></a><span data-ttu-id="c9553-103">Samouczek: Tworzenie aplikacji konsolowej .NET Core w programie Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="c9553-103">Tutorial: Create a .NET Core console application in Visual Studio 2019</span></span>

<span data-ttu-id="c9553-104">W tym samouczku przedstawiono sposób tworzenia i uruchamiania aplikacji konsolowej .NET Core w programie Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="c9553-104">This tutorial shows how to create and run a .NET Core console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c9553-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c9553-105">Prerequisites</span></span>

- <span data-ttu-id="c9553-106">[Program Visual Studio 2019 w wersji 16,6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym **wieloplatformowym obciążeniem programistycznym dla platformy .NET Core** .</span><span class="sxs-lookup"><span data-stu-id="c9553-106">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="c9553-107">Zestaw .NET Core 3,1 SDK jest instalowany automatycznie po wybraniu tego obciążenia.</span><span class="sxs-lookup"><span data-stu-id="c9553-107">The .NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="c9553-108">Aby uzyskać więcej informacji, zobacz sekcję [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) w artykule [Instalowanie zestaw .NET Core SDK](../install/sdk.md?pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="c9553-108">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="c9553-109">Tworzymy aplikację.</span><span class="sxs-lookup"><span data-stu-id="c9553-109">Create the app</span></span>

<!-- markdownlint-disable MD025 -->

1. <span data-ttu-id="c9553-110">Otwórz program Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="c9553-110">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="c9553-111">Utwórz nowy projekt aplikacji konsoli .NET Core o nazwie "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="c9553-111">Create a new .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="c9553-112">Na stronie startowej wybierz pozycję **Utwórz nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="c9553-112">On the start page, choose **Create a new project**.</span></span>

      ![Przycisk Utwórz nowy projekt wybrany na stronie startowej programu Visual Studio](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="c9553-114">Na stronie **Tworzenie nowego projektu** wprowadź w polu wyszukiwania **konsolę** .</span><span class="sxs-lookup"><span data-stu-id="c9553-114">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="c9553-115">Następnie wybierz pozycję **C#** lub **Visual Basic** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform.</span><span class="sxs-lookup"><span data-stu-id="c9553-115">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="c9553-116">Wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="c9553-116">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Utwórz nowe okno projektu z wybranymi filtrami](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="c9553-118">Jeśli nie widzisz szablonów .NET Core, prawdopodobnie brakuje wymaganego obciążenia.</span><span class="sxs-lookup"><span data-stu-id="c9553-118">If you don't see the .NET Core templates, you're probably missing the required workload.</span></span> <span data-ttu-id="c9553-119">W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** .</span><span class="sxs-lookup"><span data-stu-id="c9553-119">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="c9553-120">Zostanie otwarty Instalator programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c9553-120">The Visual Studio Installer opens.</span></span> <span data-ttu-id="c9553-121">Upewnij się, że masz zainstalowaną **Międzyplatformowe obciążenie programistyczne dla platformy .NET Core** .</span><span class="sxs-lookup"><span data-stu-id="c9553-121">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="c9553-122">Na stronie **Konfiguruj nowy projekt** wprowadź **HelloWorld** w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="c9553-122">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="c9553-123">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="c9553-123">Then choose **Create**.</span></span>

      ![Skonfiguruj okno nowego projektu z nazwą projektu, lokalizacją i polami nazw rozwiązań](./media/with-visual-studio/configure-new-project.png)

   <span data-ttu-id="c9553-125">Szablon aplikacji konsoli dla platformy .NET Core definiuje klasę, `Program` przy użyciu pojedynczej metody, `Main` która pobiera <xref:System.String> tablicę jako argument.</span><span class="sxs-lookup"><span data-stu-id="c9553-125">The Console Application template for .NET Core defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="c9553-126">`Main`jest punktem wejścia aplikacji, metoda, która jest wywoływana automatycznie przez środowisko uruchomieniowe podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c9553-126">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="c9553-127">Wszystkie argumenty wiersza polecenia dostarczone podczas uruchamiania aplikacji są dostępne w tablicy *args* .</span><span class="sxs-lookup"><span data-stu-id="c9553-127">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   <span data-ttu-id="c9553-128">Jeśli język, którego chcesz użyć, nie jest wyświetlany, Zmień selektor języka w górnej części strony.</span><span class="sxs-lookup"><span data-stu-id="c9553-128">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

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

   ```vb
   Imports System

   Module Program
       Sub Main(args As String())
           Console.WriteLine("Hello World!")
       End Sub
   End Module
   ```

   <span data-ttu-id="c9553-129">Szablon tworzy prostą aplikację "Hello world".</span><span class="sxs-lookup"><span data-stu-id="c9553-129">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="c9553-130">Wywołuje metodę, <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> Aby wyświetlić "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="c9553-130">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="c9553-131">w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="c9553-131">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="c9553-132">Uruchomienie aplikacji</span><span class="sxs-lookup"><span data-stu-id="c9553-132">Run the app</span></span>

1. <span data-ttu-id="c9553-133">Aby uruchomić program, wybierz opcję **HelloWorld** na pasku narzędzi lub naciśnij klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="c9553-133">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

   ![Pasek narzędzi programu Visual Studio z wybranym przyciskiem Uruchom jako HelloWorld](./media/with-visual-studio/run-program.png)

   <span data-ttu-id="c9553-135">Zostanie otwarte okno konsoli z tekstem "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="c9553-135">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="c9553-136">Wydrukowano na ekranie i niektóre informacje debugowania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c9553-136">printed on the screen and some Visual Studio debug information.</span></span>

   ![Okno konsoli z pokazanymi Hello world naciśnij dowolny klawisz, aby kontynuować](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="c9553-138">Naciśnij dowolny klawisz, aby zamknąć okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="c9553-138">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="c9553-139">Ulepszanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="c9553-139">Enhance the app</span></span>

<span data-ttu-id="c9553-140">Podnieś poziom aplikacji, aby monitować użytkownika o jego nazwę i wyświetlić go wraz z datą i godziną.</span><span class="sxs-lookup"><span data-stu-id="c9553-140">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="c9553-141">Poniższe instrukcje modyfikują aplikację i uruchamiają ją ponownie:</span><span class="sxs-lookup"><span data-stu-id="c9553-141">The following instructions modify the app and run it again:</span></span>

1. <span data-ttu-id="c9553-142">Zastąp zawartość `Main` metody, która jest aktualnie tylko wierszem, który wywołuje `Console.WriteLine` , przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="c9553-142">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="Snippet1":::

   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="Snippet1":::

   <span data-ttu-id="c9553-143">Ten kod wyświetla "co to jest Twoja nazwa?"</span><span class="sxs-lookup"><span data-stu-id="c9553-143">This code displays "What is your name?"</span></span> <span data-ttu-id="c9553-144">w oknie konsoli i czeka, aż użytkownik wprowadzi ciąg, a następnie klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="c9553-144">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="c9553-145">Ten ciąg jest przechowywany w zmiennej o nazwie `name` .</span><span class="sxs-lookup"><span data-stu-id="c9553-145">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="c9553-146">Pobiera również wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości, która zawiera bieżący czas lokalny i przypisuje go do zmiennej o nazwie `date` ( `currentDate` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c9553-146">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date` (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="c9553-147">Na koniec wyświetla te wartości w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="c9553-147">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="c9553-148">`\n`( `vbCrLf` W Visual Basic) reprezentuje znak nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="c9553-148">The `\n` (`vbCrLf` in Visual Basic) represents a newline character.</span></span>

   <span data-ttu-id="c9553-149">Znak dolara ( `$` ) przed ciągiem umożliwia umieszczenie wyrażeń takich jak nazwy zmiennych w nawiasach klamrowych w ciągu.</span><span class="sxs-lookup"><span data-stu-id="c9553-149">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="c9553-150">Wartość wyrażenia jest wstawiana do ciągu zamiast wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c9553-150">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="c9553-151">Ta składnia jest określana mianem [ciągów interpolowanych](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="c9553-151">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="c9553-152">Aby uruchomić program, wybierz opcję **HelloWorld** na pasku narzędzi lub naciśnij klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="c9553-152">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="c9553-153">Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz **Enter** .</span><span class="sxs-lookup"><span data-stu-id="c9553-153">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Okno konsoli ze zmodyfikowanym wyjściem programu](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="c9553-155">Naciśnij dowolny klawisz, aby zamknąć okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="c9553-155">Press any key to close the console window.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c9553-156">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="c9553-156">Next steps</span></span>

<span data-ttu-id="c9553-157">W tym samouczku utworzono aplikację .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c9553-157">In this tutorial, you created a .NET Core application.</span></span> <span data-ttu-id="c9553-158">W następnym samouczku debugujesz aplikację.</span><span class="sxs-lookup"><span data-stu-id="c9553-158">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c9553-159">Debugowanie aplikacji konsolowej .NET Core w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c9553-159">Debug a .NET Core console application in Visual Studio</span></span>](debugging-with-visual-studio.md)
