---
title: Hello world — pierwszy program korzystający z programu Visual Studio w systemie Windows lub C# Mac — Przewodnik programowania
ms.custom: seodec18
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 0807e46d36a4cf031bc44ae0dc4efab79dd51d03
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991339"
---
# <a name="hello-world----your-first-program"></a><span data-ttu-id="1ea58-102">Hello world — pierwszy program</span><span class="sxs-lookup"><span data-stu-id="1ea58-102">Hello World -- Your first program</span></span>

<span data-ttu-id="1ea58-103">W tym artykule opisano tworzenie tradycyjnych "Hello world!" przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1ea58-103">In this article, you'll use Visual Studio to create the traditional "Hello World!"</span></span> <span data-ttu-id="1ea58-104">program.</span><span class="sxs-lookup"><span data-stu-id="1ea58-104">program.</span></span> <span data-ttu-id="1ea58-105">Program Visual Studio to profesjonalne zintegrowane środowisko programistyczne (IDE) z wieloma funkcjami przeznaczonymi do programowania na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="1ea58-105">Visual Studio is a professional Integrated Development Environment (IDE) with many features designed for .NET development.</span></span> <span data-ttu-id="1ea58-106">Do utworzenia tego programu będziesz używać tylko kilku funkcji w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1ea58-106">You'll use only a few of the features in Visual Studio to create this program.</span></span> <span data-ttu-id="1ea58-107">Aby dowiedzieć się więcej na temat programu Visual Studio, zobacz [wprowadzenie z wizualizacjami C# i Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="1ea58-107">To learn more about Visual Studio, see [Getting Started with Visual C# and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a><span data-ttu-id="1ea58-108">Utwórz nową aplikację</span><span class="sxs-lookup"><span data-stu-id="1ea58-108">Create a new application</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="1ea58-109">Windows</span><span class="sxs-lookup"><span data-stu-id="1ea58-109">Windows</span></span>](#tab/windows)

<span data-ttu-id="1ea58-110">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1ea58-110">Start Visual Studio.</span></span> <span data-ttu-id="1ea58-111">Zobaczysz następujący obraz w systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="1ea58-111">You'll see the following image on Windows:</span></span>

![Ekran powitalny programu Visual Studio w systemie Windows](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

<span data-ttu-id="1ea58-113">Wybierz pozycję **Utwórz nowy projekt** w prawym dolnym rogu obrazu.</span><span class="sxs-lookup"><span data-stu-id="1ea58-113">Select **Create a new project** in the lower right corner of the image.</span></span> <span data-ttu-id="1ea58-114">Program Visual Studio Wyświetla okno dialogowe **Nowy projekt** :</span><span class="sxs-lookup"><span data-stu-id="1ea58-114">Visual Studio displays the **New Project** dialog:</span></span>

![Ekran nowego projektu programu Visual Studio w systemie Windows](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> <span data-ttu-id="1ea58-116">Jeśli jest to pierwsze uruchomienie programu Visual Studio, lista **ostatnio używanych szablonów projektu** jest pusta.</span><span class="sxs-lookup"><span data-stu-id="1ea58-116">If this is the first time you've started Visual Studio, the **Recent project templates** list is empty.</span></span>

<span data-ttu-id="1ea58-117">W oknie dialogowym Nowy projekt wybierz pozycję "Aplikacja konsolowa (.NET Core)", a następnie naciśnij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="1ea58-117">On the new project dialog, choose "Console App (.NET Core)" and then press **Next**.</span></span> <span data-ttu-id="1ea58-118">Nadaj projektowi nazwę, na przykład "HelloWorld", a następnie naciśnij pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="1ea58-118">Give your project a name, such as "HelloWorld", then press **Create**.</span></span>

<span data-ttu-id="1ea58-119">Program Visual Studio otwiera projekt.</span><span class="sxs-lookup"><span data-stu-id="1ea58-119">Visual Studio opens your project.</span></span> <span data-ttu-id="1ea58-120">To już podstawowy "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="1ea58-120">It's already a basic "Hello World!"</span></span> <span data-ttu-id="1ea58-121">przyklad.</span><span class="sxs-lookup"><span data-stu-id="1ea58-121">example.</span></span> <span data-ttu-id="1ea58-122">Naciśnij `Ctrl` klawisz  +  ,abyuruchomićprojekt`F5` .</span><span class="sxs-lookup"><span data-stu-id="1ea58-122">Press `Ctrl` + `F5` to run your project.</span></span> <span data-ttu-id="1ea58-123">Program Visual Studio kompiluje projekt, konwertując kod źródłowy do pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="1ea58-123">Visual Studio builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="1ea58-124">Następnie uruchamia okno poleceń, w którym jest uruchamiana nowa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="1ea58-124">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="1ea58-125">W oknie powinien zostać wyświetlony następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="1ea58-125">You should see the following text in the window:</span></span>

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="1ea58-126">Naciśnij dowolny klawisz, aby zamknąć okno.</span><span class="sxs-lookup"><span data-stu-id="1ea58-126">Press a key to close the window.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="1ea58-127">macOS</span><span class="sxs-lookup"><span data-stu-id="1ea58-127">macOS</span></span>](#tab/macos)

<span data-ttu-id="1ea58-128">Rozpocznij Visual Studio dla komputerów Mac.</span><span class="sxs-lookup"><span data-stu-id="1ea58-128">Start Visual Studio for Mac.</span></span> <span data-ttu-id="1ea58-129">Na komputerze Mac zobaczysz następujący obraz:</span><span class="sxs-lookup"><span data-stu-id="1ea58-129">You'll see the following image on Mac:</span></span>

![Ekran powitalny programu Visual Studio na komputerze Mac](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> <span data-ttu-id="1ea58-131">Jeśli jest to pierwsze uruchomienie Visual Studio dla komputerów Mac, lista **ostatnich projektów** jest pusta.</span><span class="sxs-lookup"><span data-stu-id="1ea58-131">If this is the first time you've started Visual Studio for Mac, the **Recent projects** list is empty.</span></span>

<span data-ttu-id="1ea58-132">Wybierz pozycję **Nowy** w prawym górnym rogu obrazu.</span><span class="sxs-lookup"><span data-stu-id="1ea58-132">Select **New** in the upper right corner of the image.</span></span> <span data-ttu-id="1ea58-133">Visual Studio dla komputerów Mac wyświetla okno dialogowe **Nowy projekt** :</span><span class="sxs-lookup"><span data-stu-id="1ea58-133">Visual Studio for Mac displays the **New Project** dialog:</span></span>

![Ekran nowego projektu programu Visual Studio na komputerze Mac](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

<span data-ttu-id="1ea58-135">W oknie dialogowym Nowy projekt wybierz pozycję ".NET Core" i "Aplikacja konsolowa", a następnie naciśnij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="1ea58-135">On the new project dialog, choose ".NET Core", and "Console App" and then press **Next**.</span></span> <span data-ttu-id="1ea58-136">Musisz wybrać platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="1ea58-136">You'll need to select the target framework.</span></span> <span data-ttu-id="1ea58-137">Wartość domyślna to "prawidłowo", więc naciśnij przycisk Dalej.</span><span class="sxs-lookup"><span data-stu-id="1ea58-137">The default is fine, so press next.</span></span> <span data-ttu-id="1ea58-138">Nadaj projektowi nazwę, na przykład "HelloWorld", a następnie naciśnij pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="1ea58-138">Give your project a name, such as "HelloWorld", then press **Create**.</span></span> <span data-ttu-id="1ea58-139">Możesz użyć domyślnej lokalizacji projektu.</span><span class="sxs-lookup"><span data-stu-id="1ea58-139">You can use the default project location.</span></span> <span data-ttu-id="1ea58-140">Nie dodawaj tego projektu do kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="1ea58-140">Don't add this project to source control.</span></span>

<span data-ttu-id="1ea58-141">Visual Studio dla komputerów Mac otwiera projekt.</span><span class="sxs-lookup"><span data-stu-id="1ea58-141">Visual Studio for Mac opens your project.</span></span> <span data-ttu-id="1ea58-142">To już podstawowy "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="1ea58-142">It's already a basic "Hello World!"</span></span> <span data-ttu-id="1ea58-143">przyklad.</span><span class="sxs-lookup"><span data-stu-id="1ea58-143">example.</span></span> <span data-ttu-id="1ea58-144">Naciśnij `Ctrl` klawisz  +  ,aby +  uruchomić projekt. `Fn` `F5`</span><span class="sxs-lookup"><span data-stu-id="1ea58-144">Press `Ctrl` + `Fn` + `F5` to run your project.</span></span> <span data-ttu-id="1ea58-145">Visual Studio dla komputerów Mac kompiluje projekt, konwertując kod źródłowy do pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="1ea58-145">Visual Studio for Mac builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="1ea58-146">Następnie uruchamia okno poleceń, w którym jest uruchamiana nowa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="1ea58-146">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="1ea58-147">W oknie powinien zostać wyświetlony następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="1ea58-147">You should see the following text in the window:</span></span>

```console
Hello World!

Press any key to close this window . . .
```

<span data-ttu-id="1ea58-148">Naciśnij klawisz, aby zakończyć sesję.</span><span class="sxs-lookup"><span data-stu-id="1ea58-148">Press a key to end the session.</span></span>

---

## <a name="elements-of-a-c-program"></a><span data-ttu-id="1ea58-149">Elementy C# programu</span><span class="sxs-lookup"><span data-stu-id="1ea58-149">Elements of a C# program</span></span>

<span data-ttu-id="1ea58-150">Przeanalizujmy ważne części tego programu.</span><span class="sxs-lookup"><span data-stu-id="1ea58-150">Let's examine the important parts of this program.</span></span> <span data-ttu-id="1ea58-151">Pierwszy wiersz zawiera komentarz.</span><span class="sxs-lookup"><span data-stu-id="1ea58-151">The first line contains a comment.</span></span> <span data-ttu-id="1ea58-152">Znaki `//` konwertują resztę wiersza do komentarza.</span><span class="sxs-lookup"><span data-stu-id="1ea58-152">The characters `//` convert the rest of the line to a comment.</span></span>

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="1ea58-153">Możesz również dodać komentarz do bloku tekstu, umieszczając go między `/*` znakami i. `*/`</span><span class="sxs-lookup"><span data-stu-id="1ea58-153">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="1ea58-154">Pokazano to w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1ea58-154">This is shown in the following example.</span></span>

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

<span data-ttu-id="1ea58-155">Aplikacja C# konsolowa musi zawierać `Main` metodę, w której kontrolka zaczyna się i skończy.</span><span class="sxs-lookup"><span data-stu-id="1ea58-155">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="1ea58-156">Metoda `Main` ta umożliwia tworzenie obiektów i wykonywanie innych metod.</span><span class="sxs-lookup"><span data-stu-id="1ea58-156">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="1ea58-157">Metoda jest metodą statyczną, która znajduje się wewnątrz klasy lub struktury. [](../../language-reference/keywords/static.md) `Main`</span><span class="sxs-lookup"><span data-stu-id="1ea58-157">The `Main` method is a [static](../../language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="1ea58-158">W poprzednim "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="1ea58-158">In the previous "Hello World!"</span></span> <span data-ttu-id="1ea58-159">przykład znajduje się w klasie o nazwie `Hello`.</span><span class="sxs-lookup"><span data-stu-id="1ea58-159">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="1ea58-160">`Main` Metodę można zadeklarować w jeden z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="1ea58-160">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="1ea58-161">Może zwrócić `void`.</span><span class="sxs-lookup"><span data-stu-id="1ea58-161">It can return `void`.</span></span> <span data-ttu-id="1ea58-162">Oznacza to, że program nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="1ea58-162">That means your program doesn't return a value.</span></span>

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="1ea58-163">Może również zwracać liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="1ea58-163">It can also return an integer.</span></span> <span data-ttu-id="1ea58-164">Liczba całkowita jest **kodem zakończenia** dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1ea58-164">The integer is the **exit code** for your application.</span></span>

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="1ea58-165">Za pomocą jednego z typów zwracanych można przyjmować argumenty.</span><span class="sxs-lookup"><span data-stu-id="1ea58-165">With either of the return types, it can take arguments.</span></span>

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

<span data-ttu-id="1ea58-166">—lub—</span><span class="sxs-lookup"><span data-stu-id="1ea58-166">-or-</span></span>

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="1ea58-167">Parametr `Main` `string` metody,, jest tablicą zawierającą argumenty wiersza polecenia używane do wywołania programu. `args`</span><span class="sxs-lookup"><span data-stu-id="1ea58-167">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span>

<span data-ttu-id="1ea58-168">Aby uzyskać więcej informacji o używaniu argumentów wiersza polecenia, zobacz przykłady w [Main () i argumenty wiersza polecenia](../main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="1ea58-168">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../main-and-command-args/index.md).</span></span>

## <a name="input-and-output"></a><span data-ttu-id="1ea58-169">Dane wejściowe i wyjściowe</span><span class="sxs-lookup"><span data-stu-id="1ea58-169">Input and output</span></span>

<span data-ttu-id="1ea58-170">C#programy zwykle korzystają z usług wejścia/wyjścia dostarczonych przez bibliotekę wykonawczą .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ea58-170">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="1ea58-171">`System.Console.WriteLine("Hello World!");` Instrukcja<xref:System.Console.WriteLine%2A> używa metody.</span><span class="sxs-lookup"><span data-stu-id="1ea58-171">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="1ea58-172">Jest to jedna z metod <xref:System.Console> wyjściowych klasy w bibliotece wykonawczej.</span><span class="sxs-lookup"><span data-stu-id="1ea58-172">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="1ea58-173">Wyświetla jego parametr String w standardowym strumieniu wyjściowym, po którym następuje nowy wiersz.</span><span class="sxs-lookup"><span data-stu-id="1ea58-173">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="1ea58-174">Inne <xref:System.Console> metody są dostępne dla różnych operacji wejścia i wyjścia.</span><span class="sxs-lookup"><span data-stu-id="1ea58-174">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="1ea58-175">Jeśli dołączysz `using System;` dyrektywę na początku programu, możesz bezpośrednio <xref:System> użyć klas i metod bez ich w pełni kwalifikujących się.</span><span class="sxs-lookup"><span data-stu-id="1ea58-175">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="1ea58-176">Na przykład można wywołać `Console.WriteLine` `System.Console.WriteLine`zamiast:</span><span class="sxs-lookup"><span data-stu-id="1ea58-176">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="1ea58-177">Aby uzyskać więcej informacji na temat metod wejścia/wyjścia <xref:System.IO>, zobacz.</span><span class="sxs-lookup"><span data-stu-id="1ea58-177">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ea58-178">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ea58-178">See also</span></span>

- [<span data-ttu-id="1ea58-179">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1ea58-179">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1ea58-180">Przykłady i samouczki</span><span class="sxs-lookup"><span data-stu-id="1ea58-180">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="1ea58-181">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="1ea58-181">Main() and Command-Line Arguments</span></span>](../main-and-command-args/index.md)
- [<span data-ttu-id="1ea58-182">Wprowadzenie do języków Visual C# i Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ea58-182">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
