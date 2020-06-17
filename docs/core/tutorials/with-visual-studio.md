---
title: Tworzenie aplikacji konsolowej platformy .NET Core przy użyciu programu Visual Studio
description: Dowiedz się, jak utworzyć aplikację konsolową .NET Core w języku C# lub Visual Basic przy użyciu programu Visual Studio.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 3c8fc7c4702b786c05e14397dc36d994c77e114d
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/16/2020
ms.locfileid: "84811653"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="2f32a-103">Samouczek: Tworzenie aplikacji konsolowej platformy .NET Core przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2f32a-103">Tutorial: Create a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="2f32a-104">W tym samouczku przedstawiono sposób tworzenia i uruchamiania aplikacji konsolowej .NET Core w programie Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="2f32a-104">This tutorial shows how to create and run a .NET Core console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2f32a-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="2f32a-105">Prerequisites</span></span>

- <span data-ttu-id="2f32a-106">[Program Visual Studio 2019 w wersji 16,6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym **wieloplatformowym obciążeniem programistycznym dla platformy .NET Core** .</span><span class="sxs-lookup"><span data-stu-id="2f32a-106">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="2f32a-107">Zestaw .NET Core 3,1 SDK jest instalowany automatycznie po wybraniu tego obciążenia.</span><span class="sxs-lookup"><span data-stu-id="2f32a-107">The .NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="2f32a-108">Aby uzyskać więcej informacji, zobacz [instalowanie zestaw .NET Core SDK w programie Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="2f32a-108">For more information, see [Install the .NET Core SDK with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="2f32a-109">Tworzymy aplikację.</span><span class="sxs-lookup"><span data-stu-id="2f32a-109">Create the app</span></span>

<span data-ttu-id="2f32a-110">Utwórz projekt aplikacji konsolowej .NET Core o nazwie "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="2f32a-110">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="2f32a-111">Uruchom program Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="2f32a-111">Start Visual Studio 2019.</span></span>

1. <span data-ttu-id="2f32a-112">Na stronie startowej wybierz pozycję **Utwórz nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="2f32a-112">On the start page, choose **Create a new project**.</span></span>

   ![Przycisk Utwórz nowy projekt wybrany na stronie startowej programu Visual Studio](./media/with-visual-studio/start-window.png)

1. <span data-ttu-id="2f32a-114">Na stronie **Tworzenie nowego projektu** wprowadź w polu wyszukiwania **konsolę** .</span><span class="sxs-lookup"><span data-stu-id="2f32a-114">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="2f32a-115">Następnie wybierz pozycję **C#** lub **Visual Basic** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform.</span><span class="sxs-lookup"><span data-stu-id="2f32a-115">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="2f32a-116">Wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="2f32a-116">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   ![Utwórz nowe okno projektu z wybranymi filtrami](./media/with-visual-studio/create-new-project.png)

   > [!TIP]
   > <span data-ttu-id="2f32a-118">Jeśli nie widzisz szablonów .NET Core, prawdopodobnie brakuje wymaganego obciążenia.</span><span class="sxs-lookup"><span data-stu-id="2f32a-118">If you don't see the .NET Core templates, you're probably missing the required workload.</span></span> <span data-ttu-id="2f32a-119">W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** .</span><span class="sxs-lookup"><span data-stu-id="2f32a-119">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="2f32a-120">Zostanie otwarty Instalator programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f32a-120">The Visual Studio Installer opens.</span></span> <span data-ttu-id="2f32a-121">Upewnij się, że masz zainstalowaną **Międzyplatformowe obciążenie programistyczne dla platformy .NET Core** .</span><span class="sxs-lookup"><span data-stu-id="2f32a-121">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

1. <span data-ttu-id="2f32a-122">W oknie dialogowym **Konfigurowanie nowego projektu** wprowadź **HelloWorld** w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="2f32a-122">In the **Configure your new project** dialog,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="2f32a-123">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="2f32a-123">Then choose **Create**.</span></span>

   ![Skonfiguruj okno nowego projektu z nazwą projektu, lokalizacją i polami nazw rozwiązań](./media/with-visual-studio/configure-new-project.png)

<span data-ttu-id="2f32a-125">Szablon tworzy prostą aplikację "Hello world".</span><span class="sxs-lookup"><span data-stu-id="2f32a-125">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="2f32a-126">Wywołuje metodę, <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> Aby wyświetlić "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="2f32a-126">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="2f32a-127">w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="2f32a-127">in the console window.</span></span>

<span data-ttu-id="2f32a-128">Kod szablonu definiuje klasę, `Program` przy użyciu pojedynczej metody, `Main` która przyjmuje <xref:System.String> tablicę jako argument:</span><span class="sxs-lookup"><span data-stu-id="2f32a-128">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="2f32a-129">`Main`jest punktem wejścia aplikacji, metoda, która jest wywoływana automatycznie przez środowisko uruchomieniowe podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2f32a-129">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="2f32a-130">Wszystkie argumenty wiersza polecenia dostarczone podczas uruchamiania aplikacji są dostępne w tablicy *args* .</span><span class="sxs-lookup"><span data-stu-id="2f32a-130">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="2f32a-131">Jeśli język, którego chcesz użyć, nie jest wyświetlany, Zmień selektor języka w górnej części strony.</span><span class="sxs-lookup"><span data-stu-id="2f32a-131">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="2f32a-132">Uruchomienie aplikacji</span><span class="sxs-lookup"><span data-stu-id="2f32a-132">Run the app</span></span>

1. <span data-ttu-id="2f32a-133">Naciśnij klawisz <kbd>SHIFT</kbd> + <kbd>F5</kbd> , aby uruchomić program bez debugowania.</span><span class="sxs-lookup"><span data-stu-id="2f32a-133">Press <kbd>Shift</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

   <span data-ttu-id="2f32a-134">Zostanie otwarte okno konsoli z tekstem "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="2f32a-134">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="2f32a-135">Wydrukowano na ekranie i niektóre informacje debugowania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f32a-135">printed on the screen and some Visual Studio debug information.</span></span>

   ![Okno konsoli z pokazanymi Hello world naciśnij dowolny klawisz, aby kontynuować](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="2f32a-137">Naciśnij dowolny klawisz, aby zamknąć okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="2f32a-137">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="2f32a-138">Ulepszanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="2f32a-138">Enhance the app</span></span>

<span data-ttu-id="2f32a-139">Podnieś poziom aplikacji, aby monitować użytkownika o jego nazwę i wyświetlić go wraz z datą i godziną.</span><span class="sxs-lookup"><span data-stu-id="2f32a-139">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="2f32a-140">W programie *program.cs* lub *program. vb*Zastąp zawartość `Main` metody, która jest wierszem, który wywołuje `Console.WriteLine` , przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="2f32a-140">In *Program.cs* or *Program.vb*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::
   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="MainMethod":::

   <span data-ttu-id="2f32a-141">Ten kod wyświetla "co to jest Twoja nazwa?"</span><span class="sxs-lookup"><span data-stu-id="2f32a-141">This code displays "What is your name?"</span></span> <span data-ttu-id="2f32a-142">w oknie konsoli i czeka, aż użytkownik wprowadzi ciąg, a następnie klawisz <kbd>Enter</kbd> .</span><span class="sxs-lookup"><span data-stu-id="2f32a-142">in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="2f32a-143">Ten ciąg jest przechowywany w zmiennej o nazwie `name` .</span><span class="sxs-lookup"><span data-stu-id="2f32a-143">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="2f32a-144">Pobiera również wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości, która zawiera bieżący czas lokalny i przypisuje go do zmiennej o nazwie `date` ( `currentDate` w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="2f32a-144">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date` (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="2f32a-145">Na koniec wyświetla te wartości w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="2f32a-145">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="2f32a-146">`\n`( `vbCrLf` W Visual Basic) reprezentuje znak nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="2f32a-146">The `\n` (`vbCrLf` in Visual Basic) represents a newline character.</span></span>

   <span data-ttu-id="2f32a-147">Znak dolara ( `$` ) przed ciągiem umożliwia umieszczenie wyrażeń takich jak nazwy zmiennych w nawiasach klamrowych w ciągu.</span><span class="sxs-lookup"><span data-stu-id="2f32a-147">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="2f32a-148">Wartość wyrażenia jest wstawiana do ciągu zamiast wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="2f32a-148">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="2f32a-149">Ta składnia jest określana mianem [ciągów interpolowanych](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="2f32a-149">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="2f32a-150">Naciśnij klawisz <kbd>SHIFT</kbd> + <kbd>F5</kbd> , aby uruchomić program bez debugowania.</span><span class="sxs-lookup"><span data-stu-id="2f32a-150">Press <kbd>Shift</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

1. <span data-ttu-id="2f32a-151">Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz <kbd>Enter</kbd> .</span><span class="sxs-lookup"><span data-stu-id="2f32a-151">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   ![Okno konsoli ze zmodyfikowanym wyjściem programu](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="2f32a-153">Naciśnij dowolny klawisz, aby zamknąć okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="2f32a-153">Press any key to close the console window.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2f32a-154">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="2f32a-154">Next steps</span></span>

<span data-ttu-id="2f32a-155">W tym samouczku utworzono aplikację konsolową .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2f32a-155">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="2f32a-156">W następnym samouczku debugujesz aplikację.</span><span class="sxs-lookup"><span data-stu-id="2f32a-156">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2f32a-157">Debugowanie aplikacji konsolowej .NET Core w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2f32a-157">Debug a .NET Core console application in Visual Studio</span></span>](debugging-with-visual-studio.md)
