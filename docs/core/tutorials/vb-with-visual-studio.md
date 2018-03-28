---
title: Tworzenie aplikacji Hello World z platformy .NET Core i Visual Basic w programie Visual Studio 2017 r.
description: Sposób tworzenia prostej aplikacji konsoli .NET Core za pomocą Visual Basic przy użyciu programu Visual Studio 2017 r.
keywords: Oprogramowanie .NET core aplikacji konsoli .NET Core, programu Visual Studio 2017 r.
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-vb
dev_langs:
- vb
ms.workload:
- dotnetcore
ms.openlocfilehash: c3775fccf8d6e7c544cbd0b05df7043752e8bef9
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="build-a-visual-basic-hello-world-application-with-net-core-in-visual-studio-2017"></a><span data-ttu-id="9afc8-104">Tworzenie aplikacji Visual Basic Hello World z platformą .NET Core w Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="9afc8-104">Build a Visual Basic Hello World application with .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="9afc8-105">Ten temat zawiera wprowadzenie krok po kroku do tworzenia, debugowania i publikowania prostej aplikacji konsoli .NET Core za pomocą języka Visual Basic w programie Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="9afc8-105">This topic provides a step-by-step introduction to building, debugging, and publishing a simple .NET Core console application using Visual Basic in Visual Studio 2017.</span></span> <span data-ttu-id="9afc8-106">Visual Studio 2017 udostępnia środowisko deweloperskie oferujący wszystkie funkcje tworzenia aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9afc8-106">Visual Studio 2017 provides a full-featured development environment for building .NET Core applications.</span></span> <span data-ttu-id="9afc8-107">Tak długo, jak aplikacja nie ma zależności specyficzne dla platformy, aplikację można uruchomić na dowolnej platformie, którego element docelowy .NET Core i w każdym systemie, który ma zainstalowane oprogramowanie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9afc8-107">As long as the application doesn't have platform-specific dependencies, the application can run on any platform that .NET Core targets and on any system that has .NET Core installed.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9afc8-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="9afc8-108">Prerequisites</span></span>

<span data-ttu-id="9afc8-109">[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) z obciążeniem "Programowanie wieloplatformowych .NET Core" zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="9afc8-109">[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) with the ".NET Core cross-platform development" workload installed.</span></span> <span data-ttu-id="9afc8-110">Możesz utworzyć aplikację .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="9afc8-110">You can develop your app with .NET Core 2.0.</span></span>

<span data-ttu-id="9afc8-111">Aby uzyskać więcej informacji, zobacz [wymagania wstępne dotyczące .NET Core w systemie Windows](../../core/windows-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="9afc8-111">For more information, see [Prerequisites for .NET Core on Windows](../../core/windows-prerequisites.md).</span></span>

## <a name="a-simple-hello-world-application"></a><span data-ttu-id="9afc8-112">Prostej aplikacji Hello World</span><span class="sxs-lookup"><span data-stu-id="9afc8-112">A simple Hello World application</span></span>

<span data-ttu-id="9afc8-113">Rozpocznij od utworzenia prostej aplikacji konsoli "Hello World".</span><span class="sxs-lookup"><span data-stu-id="9afc8-113">Begin by creating a simple "Hello World" console application.</span></span> <span data-ttu-id="9afc8-114">Wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="9afc8-114">Follow these steps:</span></span>

1. <span data-ttu-id="9afc8-115">Launch Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="9afc8-115">Launch Visual Studio 2017.</span></span> <span data-ttu-id="9afc8-116">Wybierz **pliku** > **nowy** > **projektu** na pasku menu.</span><span class="sxs-lookup"><span data-stu-id="9afc8-116">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="9afc8-117">W *nowy projekt*\* okno dialogowe, wybierz opcję **Visual Basic** węzła następuje **.NET Core** węzła.</span><span class="sxs-lookup"><span data-stu-id="9afc8-117">In the *New Project*\* dialog, select the **Visual Basic** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="9afc8-118">Następnie wybierz **aplikacji konsoli (.NET Core)** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="9afc8-118">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="9afc8-119">W **nazwa** tekstu wpisz "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="9afc8-119">In the **Name** text box, type "HelloWorld".</span></span> <span data-ttu-id="9afc8-120">Wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9afc8-120">Select the **OK** button.</span></span>

   ![Okno dialogowe nowego projektu z aplikacji konsoli wybrane](./media/vb-with-visual-studio/new-project.png)
   
1. <span data-ttu-id="9afc8-122">Visual Studio używa tego szablonu do tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="9afc8-122">Visual Studio uses the template to create your project.</span></span> <span data-ttu-id="9afc8-123">Szablon aplikacji konsoli języka Visual Basic .NET Core automatycznie definiuje klasę, `Program`, z jedną metodę `Main`, która pobiera <xref:System.String> tablic jako argumentu.</span><span class="sxs-lookup"><span data-stu-id="9afc8-123">The Visual Basic Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="9afc8-124">`Main` jest punkt wejścia aplikacji, metody, która jest wywoływana automatycznie przez środowisko uruchomieniowe uruchamianiem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9afc8-124">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="9afc8-125">Są dostępne w żadnych argumentów wiersza polecenia dostarczana, gdy aplikacja jest uruchamiana *argumentów* tablicy.</span><span class="sxs-lookup"><span data-stu-id="9afc8-125">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Nowy projekt HelloWorld i Visual Studio](./media/vb-with-visual-studio/devenv.png)

   <span data-ttu-id="9afc8-127">Szablon tworzy prostą aplikację "Hello World".</span><span class="sxs-lookup"><span data-stu-id="9afc8-127">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="9afc8-128">Wywołuje <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodę w celu wyświetlenia literału ciągu "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="9afc8-128">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="9afc8-129">w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="9afc8-129">in the console window.</span></span> <span data-ttu-id="9afc8-130">Wybierając **HelloWorld** przycisk z zieloną strzałką na pasku narzędzi, można uruchomić program w trybie debugowania.</span><span class="sxs-lookup"><span data-stu-id="9afc8-130">By selecting the **HelloWorld** button with the green arrow on the toolbar, you can run the program in Debug mode.</span></span> <span data-ttu-id="9afc8-131">Jeśli to zrobisz, w oknie konsoli jest widoczna tylko interwał krótki czas przed jego zamknięciem.</span><span class="sxs-lookup"><span data-stu-id="9afc8-131">If you do, the console window is visible for only a brief time interval before it closes.</span></span> <span data-ttu-id="9afc8-132">Dzieje się tak dlatego `Main` kończy — metoda i kończenia aplikacji tak szybko, jak jednej instrukcji w `Main` metoda jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="9afc8-132">This occurs because the `Main` method terminates and the application ends as soon as the single statement in the `Main` method executes.</span></span>

1. <span data-ttu-id="9afc8-133">Aby spowodować, że aplikacja wstrzymać przed jego zamknięciem okna konsoli, Dodaj następujący kod bezpośrednio po wywołaniu <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metody:</span><span class="sxs-lookup"><span data-stu-id="9afc8-133">To cause the application to pause before it closes the console window, add the following code immediately after the call to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method:</span></span>

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```
   <span data-ttu-id="9afc8-134">Ten kod monituje użytkownika o naciśnij dowolny klawisz, a następnie zatrzymuje program, dopóki nie zostanie naciśnięty klawisz.</span><span class="sxs-lookup"><span data-stu-id="9afc8-134">This code prompts the user to press any key and then pauses the program until a key is pressed.</span></span>

1. <span data-ttu-id="9afc8-135">Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="9afc8-135">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="9afc8-136">Program to kompiluje się na język pośredni (IL), który jest konwertowany na kod binarny za pomocą kompilatora just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="9afc8-136">This compiles your program into an intermediate language (IL) that's converted into binary code by a just-in-time (JIT) compiler.</span></span>

1. <span data-ttu-id="9afc8-137">Uruchom program wybierając **HelloWorld** przycisk z zieloną strzałkę na pasku narzędzi.</span><span class="sxs-lookup"><span data-stu-id="9afc8-137">Run the program by selecting the **HelloWorld** button with the green arrow on the toolbar.</span></span>

   ![Okno konsoli przedstawiający Hello World naciśnij dowolny klawisz, aby kontynuować](./media/with-visual-studio/helloworld1.png)

1. <span data-ttu-id="9afc8-139">Naciśnij dowolny klawisz, aby zamknąć okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="9afc8-139">Press any key to close the console window.</span></span>

## <a name="enhancing-the-hello-world-application"></a><span data-ttu-id="9afc8-140">Rozszerzanie aplikacji Hello World</span><span class="sxs-lookup"><span data-stu-id="9afc8-140">Enhancing the Hello World application</span></span>

<span data-ttu-id="9afc8-141">Ulepszanie aplikację do monitowania użytkownika o jej nazwę, aby go wyświetlić, oraz datę i godzinę.</span><span class="sxs-lookup"><span data-stu-id="9afc8-141">Enhance your application to prompt the user for his or her name and to display it along with the date and time.</span></span> <span data-ttu-id="9afc8-142">Aby zmodyfikować i przetestować program, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="9afc8-142">To modify and test the program, do the following:</span></span>

1. <span data-ttu-id="9afc8-143">Wprowadź poniższy kod Visual Basic w oknie Kod bezpośrednio po otwierającym znajdujący się `Sub Main(args As String())` wierszu i przed pierwszym zamykający nawias kwadratowy:</span><span class="sxs-lookup"><span data-stu-id="9afc8-143">Enter the following Visual Basic code in the code window immediately after the opening bracket that follows the `Sub Main(args As String())` line and before the first closing bracket:</span></span>

   [!code-vb[GettingStarted#1](../../../samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   <span data-ttu-id="9afc8-144">Ten kod zastępuje istniejące <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, i <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> instrukcje.</span><span class="sxs-lookup"><span data-stu-id="9afc8-144">This code replaces the existing <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, and <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> statements.</span></span>

   ![Visual Studio Program pliku z zaktualizowana metoda Main](./media/vb-with-visual-studio/codewindow.png)

   <span data-ttu-id="9afc8-146">Ten kod wyświetla "Co to jest nazwa?"</span><span class="sxs-lookup"><span data-stu-id="9afc8-146">This code displays "What is your name?"</span></span> <span data-ttu-id="9afc8-147">w oknie konsoli i czeka, dopóki użytkownik wprowadza ciąg, a następnie klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="9afc8-147">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="9afc8-148">Ten ciąg jest przechowywana w zmiennej o nazwie `name`.</span><span class="sxs-lookup"><span data-stu-id="9afc8-148">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="9afc8-149">Również pobiera wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwość, która zawiera bieżącym czasem lokalnym i przypisuje go do zmiennej o nazwie `currentDate`.</span><span class="sxs-lookup"><span data-stu-id="9afc8-149">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `currentDate`.</span></span> <span data-ttu-id="9afc8-150">Na koniec używa [interpolowane ciąg](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) do wyświetlania tych wartości w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="9afc8-150">Finally, it uses an [interpolated string](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="9afc8-151">Kompiluj program, wybierając **kompilacji** > **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="9afc8-151">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="9afc8-152">Uruchom program w trybie debugowania w programie Visual Studio, wybierając zieloną strzałkę na pasku narzędzi, naciskając klawisz F5 lub wybierając pozycję **debugowania** > **Rozpocznij debugowanie** elementu menu.</span><span class="sxs-lookup"><span data-stu-id="9afc8-152">Run the program in Debug mode in Visual Studio by selecting the green arrow on the toolbar, pressing F5, or choosing the **Debug** > **Start Debugging** menu item.</span></span> <span data-ttu-id="9afc8-153">Odpowiadanie na ten monit wprowadzania nazwy i naciskając klawisz Enter.</span><span class="sxs-lookup"><span data-stu-id="9afc8-153">Respond to the prompt by entering a name and pressing the Enter key.</span></span>

   ![Okno konsoli z danych wyjściowych programu zmodyfikowane](./media/with-visual-studio/helloworld2.png)

1. <span data-ttu-id="9afc8-155">Naciśnij dowolny klawisz, aby zamknąć okno konsoli.</span><span class="sxs-lookup"><span data-stu-id="9afc8-155">Press any key to close the console window.</span></span>

<span data-ttu-id="9afc8-156">Utworzeniu i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="9afc8-156">You've created and run your application.</span></span> <span data-ttu-id="9afc8-157">Aby opracować professional aplikacji, należy wykonać dodatkowe kroki w celu przygotowania aplikacji do wersji:</span><span class="sxs-lookup"><span data-stu-id="9afc8-157">To develop a professional application, take some additional steps to make your application ready for release:</span></span>

- <span data-ttu-id="9afc8-158">Informacje dotyczące debugowania aplikacji znajdują się w temacie [debugowania aplikacji C# Hello World z programu Visual Studio 2017](debugging-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="9afc8-158">For information on debugging your application, see [Debugging your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md).</span></span>

- <span data-ttu-id="9afc8-159">Informacje dotyczące tworzenia i publikowania dystrybucyjnego wersji aplikacji, zobacz [publikowania aplikacji C# Hello World z programu Visual Studio 2017](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="9afc8-159">For information on developing and publishing a distributable version of your application, see [Publishing your C# Hello World application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

<!--
## Related topics

Instead of a console application, you can also build a class library with .NET Core and Visual Studio 2017. For a step-by-step introduction, see [Building a class library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md).

You can also develop a .NET Core console app on Mac, Linux, and Windows by using [Visual Studio Code](https://code.visualstudio.com/), a downloadable code editor. For a step-by-step tutorial, see [Getting Started with Visual Studio Code](with-visual-studio-code.md). -->
