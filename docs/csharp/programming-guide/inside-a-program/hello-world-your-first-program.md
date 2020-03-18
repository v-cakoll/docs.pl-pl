---
title: Hello World - Twój pierwszy program za pomocą programu Visual Studio w systemie Windows lub Mac - Przewodnik po programowaniu C#
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 910fa4af1b4e45ce627b589a06910dc168490047
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712146"
---
# <a name="hello-world----your-first-program"></a><span data-ttu-id="9269e-102">Hello World - Twój pierwszy program</span><span class="sxs-lookup"><span data-stu-id="9269e-102">Hello World -- Your first program</span></span>

<span data-ttu-id="9269e-103">W tym artykule użyjesz programu Visual Studio do utworzenia tradycyjnego "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="9269e-103">In this article, you'll use Visual Studio to create the traditional "Hello World!"</span></span> <span data-ttu-id="9269e-104">Program.</span><span class="sxs-lookup"><span data-stu-id="9269e-104">program.</span></span> <span data-ttu-id="9269e-105">Visual Studio to profesjonalne zintegrowane środowisko programistyczne (IDE) z wieloma funkcjami przeznaczonymi do tworzenia .NET.</span><span class="sxs-lookup"><span data-stu-id="9269e-105">Visual Studio is a professional Integrated Development Environment (IDE) with many features designed for .NET development.</span></span> <span data-ttu-id="9269e-106">Do utworzenia tego programu użyjesz tylko kilku funkcji w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9269e-106">You'll use only a few of the features in Visual Studio to create this program.</span></span> <span data-ttu-id="9269e-107">Aby dowiedzieć się więcej o programie Visual Studio, zobacz [Wprowadzenie do języka Visual C#](/visualstudio/ide/quickstart-csharp-console).</span><span class="sxs-lookup"><span data-stu-id="9269e-107">To learn more about Visual Studio, see [Getting Started with Visual C#](/visualstudio/ide/quickstart-csharp-console).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a><span data-ttu-id="9269e-108">Tworzenie nowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="9269e-108">Create a new application</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="9269e-109">Windows</span><span class="sxs-lookup"><span data-stu-id="9269e-109">Windows</span></span>](#tab/windows)

<span data-ttu-id="9269e-110">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9269e-110">Start Visual Studio.</span></span> <span data-ttu-id="9269e-111">W systemie Windows zostanie wyświetlony następujący obraz:</span><span class="sxs-lookup"><span data-stu-id="9269e-111">You'll see the following image on Windows:</span></span>

![Ekran powitalny programu Visual Studio w systemie Windows](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

<span data-ttu-id="9269e-113">Wybierz **pozycję Utwórz nowy projekt** w prawym dolnym rogu obrazu.</span><span class="sxs-lookup"><span data-stu-id="9269e-113">Select **Create a new project** in the lower right corner of the image.</span></span> <span data-ttu-id="9269e-114">Program Visual Studio wyświetla okno dialogowe **Nowy projekt:**</span><span class="sxs-lookup"><span data-stu-id="9269e-114">Visual Studio displays the **New Project** dialog:</span></span>

![Nowy ekran projektu programu Visual Studio w systemie Windows](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> <span data-ttu-id="9269e-116">Jeśli jest to pierwszy raz, gdy uruchomiono program Visual Studio, lista **Ostatnie szablony projektów** jest pusta.</span><span class="sxs-lookup"><span data-stu-id="9269e-116">If this is the first time you've started Visual Studio, the **Recent project templates** list is empty.</span></span>

<span data-ttu-id="9269e-117">W nowym oknie dialogowym projektu wybierz "Aplikacja konsoli (.NET Core)", a następnie naciśnij klawisz **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="9269e-117">On the new project dialog, choose "Console App (.NET Core)" and then press **Next**.</span></span> <span data-ttu-id="9269e-118">Nadaj projektowi nazwę, na przykład "HelloWorld", a następnie naciśnij klawisz **Create**.</span><span class="sxs-lookup"><span data-stu-id="9269e-118">Give your project a name, such as "HelloWorld", then press **Create**.</span></span>

<span data-ttu-id="9269e-119">Visual Studio otwiera projekt.</span><span class="sxs-lookup"><span data-stu-id="9269e-119">Visual Studio opens your project.</span></span> <span data-ttu-id="9269e-120">To już podstawowy "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="9269e-120">It's already a basic "Hello World!"</span></span> <span data-ttu-id="9269e-121">Przykład.</span><span class="sxs-lookup"><span data-stu-id="9269e-121">example.</span></span> <span data-ttu-id="9269e-122">Naciśnij, `Ctrl`  +  `F5` aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="9269e-122">Press `Ctrl` + `F5` to run your project.</span></span> <span data-ttu-id="9269e-123">Visual Studio tworzy projekt, konwertując kod źródłowy do pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="9269e-123">Visual Studio builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="9269e-124">Następnie uruchamia okno polecenia, które uruchamia nową aplikację.</span><span class="sxs-lookup"><span data-stu-id="9269e-124">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="9269e-125">W oknie powinien zostać wyświetlony następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="9269e-125">You should see the following text in the window:</span></span>

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="9269e-126">Naciśnij klawisz, aby zamknąć okno.</span><span class="sxs-lookup"><span data-stu-id="9269e-126">Press a key to close the window.</span></span>

# <a name="macos"></a>[<span data-ttu-id="9269e-127">Macos</span><span class="sxs-lookup"><span data-stu-id="9269e-127">macOS</span></span>](#tab/macos)

<span data-ttu-id="9269e-128">Uruchom program Visual Studio dla komputerów Mac.</span><span class="sxs-lookup"><span data-stu-id="9269e-128">Start Visual Studio for Mac.</span></span> <span data-ttu-id="9269e-129">Na komputerze Mac zostanie wyświetlony następujący obraz:</span><span class="sxs-lookup"><span data-stu-id="9269e-129">You'll see the following image on Mac:</span></span>

![Ekran powitalny programu Visual Studio na komputerze Mac](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> <span data-ttu-id="9269e-131">Jeśli jest to pierwszy raz, gdy program Visual Studio dla komputerów Mac został uruchomiony, lista **Ostatnie projekty** jest pusta.</span><span class="sxs-lookup"><span data-stu-id="9269e-131">If this is the first time you've started Visual Studio for Mac, the **Recent projects** list is empty.</span></span>

<span data-ttu-id="9269e-132">Wybierz **pozycję Nowy** w prawym górnym rogu obrazu.</span><span class="sxs-lookup"><span data-stu-id="9269e-132">Select **New** in the upper right corner of the image.</span></span> <span data-ttu-id="9269e-133">Program Visual Studio dla komputerów Mac wyświetla okno dialogowe **Nowy projekt:**</span><span class="sxs-lookup"><span data-stu-id="9269e-133">Visual Studio for Mac displays the **New Project** dialog:</span></span>

![Visual Studio nowy ekran projektu na komputerze Mac](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

<span data-ttu-id="9269e-135">W nowym oknie dialogowym projektu wybierz ".NET Core" i "Aplikacja konsoli", a następnie naciśnij klawisz **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="9269e-135">On the new project dialog, choose ".NET Core", and "Console App" and then press **Next**.</span></span> <span data-ttu-id="9269e-136">Należy wybrać platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="9269e-136">You'll need to select the target framework.</span></span> <span data-ttu-id="9269e-137">Domyślnie jest w porządku, więc naciśnij dalej.</span><span class="sxs-lookup"><span data-stu-id="9269e-137">The default is fine, so press next.</span></span> <span data-ttu-id="9269e-138">Nadaj projektowi nazwę, na przykład "HelloWorld", a następnie naciśnij klawisz **Create**.</span><span class="sxs-lookup"><span data-stu-id="9269e-138">Give your project a name, such as "HelloWorld", then press **Create**.</span></span> <span data-ttu-id="9269e-139">Można użyć domyślnej lokalizacji projektu.</span><span class="sxs-lookup"><span data-stu-id="9269e-139">You can use the default project location.</span></span> <span data-ttu-id="9269e-140">Nie dodawaj tego projektu do kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="9269e-140">Don't add this project to source control.</span></span>

<span data-ttu-id="9269e-141">Visual Studio dla komputerów Mac otwiera projekt.</span><span class="sxs-lookup"><span data-stu-id="9269e-141">Visual Studio for Mac opens your project.</span></span> <span data-ttu-id="9269e-142">To już podstawowy "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="9269e-142">It's already a basic "Hello World!"</span></span> <span data-ttu-id="9269e-143">Przykład.</span><span class="sxs-lookup"><span data-stu-id="9269e-143">example.</span></span> <span data-ttu-id="9269e-144">`Ctrl`  +  `Fn` Naciśnij,  +  `F5` aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="9269e-144">Press `Ctrl` + `Fn` + `F5` to run your project.</span></span> <span data-ttu-id="9269e-145">Visual Studio dla komputerów Mac tworzy projekt, konwertując kod źródłowy do pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="9269e-145">Visual Studio for Mac builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="9269e-146">Następnie uruchamia okno polecenia, które uruchamia nową aplikację.</span><span class="sxs-lookup"><span data-stu-id="9269e-146">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="9269e-147">W oknie powinien zostać wyświetlony następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="9269e-147">You should see the following text in the window:</span></span>

```console
Hello World!

Press any key to close this window . . .
```

<span data-ttu-id="9269e-148">Naciśnij klawisz, aby zakończyć sesję.</span><span class="sxs-lookup"><span data-stu-id="9269e-148">Press a key to end the session.</span></span>

---

## <a name="elements-of-a-c-program"></a><span data-ttu-id="9269e-149">Elementy programu C#</span><span class="sxs-lookup"><span data-stu-id="9269e-149">Elements of a C# program</span></span>

<span data-ttu-id="9269e-150">Przeanalizujmy ważne części tego programu.</span><span class="sxs-lookup"><span data-stu-id="9269e-150">Let's examine the important parts of this program.</span></span> <span data-ttu-id="9269e-151">Pierwszy wiersz zawiera komentarz.</span><span class="sxs-lookup"><span data-stu-id="9269e-151">The first line contains a comment.</span></span> <span data-ttu-id="9269e-152">Znaki `//` konwertują resztę wiersza na komentarz.</span><span class="sxs-lookup"><span data-stu-id="9269e-152">The characters `//` convert the rest of the line to a comment.</span></span>

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="9269e-153">Możesz również skomentować blok tekstu, załączając go między `/*` znakami. `*/`</span><span class="sxs-lookup"><span data-stu-id="9269e-153">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="9269e-154">Jest to pokazane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9269e-154">This is shown in the following example.</span></span>

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

<span data-ttu-id="9269e-155">Aplikacja konsoli Języka C# `Main` musi zawierać metodę, w której formant rozpoczyna się i kończy.</span><span class="sxs-lookup"><span data-stu-id="9269e-155">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="9269e-156">Metoda `Main` jest, gdzie można tworzyć obiekty i wykonywać inne metody.</span><span class="sxs-lookup"><span data-stu-id="9269e-156">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="9269e-157">Metoda `Main` jest metodą [statyczną,](../../language-reference/keywords/static.md) która znajduje się wewnątrz klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="9269e-157">The `Main` method is a [static](../../language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="9269e-158">W poprzednim "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="9269e-158">In the previous "Hello World!"</span></span> <span data-ttu-id="9269e-159">na przykład znajduje się w `Hello`klasie o nazwie .</span><span class="sxs-lookup"><span data-stu-id="9269e-159">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="9269e-160">Metodę można `Main` zadeklarować w jeden z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="9269e-160">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="9269e-161">Może powrócić `void`.</span><span class="sxs-lookup"><span data-stu-id="9269e-161">It can return `void`.</span></span> <span data-ttu-id="9269e-162">Oznacza to, że program nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="9269e-162">That means your program doesn't return a value.</span></span>

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="9269e-163">Może również zwrócić liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="9269e-163">It can also return an integer.</span></span> <span data-ttu-id="9269e-164">Liczba całkowita jest **kodem zakończenia** dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9269e-164">The integer is the **exit code** for your application.</span></span>

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="9269e-165">Z jednego z typów zwracanych może przyjmować argumenty.</span><span class="sxs-lookup"><span data-stu-id="9269e-165">With either of the return types, it can take arguments.</span></span>

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

<span data-ttu-id="9269e-166">— lub —</span><span class="sxs-lookup"><span data-stu-id="9269e-166">-or-</span></span>

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="9269e-167">Parametr `Main` metody , `args`jest tablicą zawierającą `string` argumenty wiersza polecenia używane do wywoływania programu.</span><span class="sxs-lookup"><span data-stu-id="9269e-167">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span>

<span data-ttu-id="9269e-168">Aby uzyskać więcej informacji na temat używania argumentów wiersza polecenia, zobacz przykłady w [argumentach Main() i Command-Line](../main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="9269e-168">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../main-and-command-args/index.md).</span></span>

## <a name="input-and-output"></a><span data-ttu-id="9269e-169">Dane wejściowe i wyjściowe</span><span class="sxs-lookup"><span data-stu-id="9269e-169">Input and output</span></span>

<span data-ttu-id="9269e-170">Programy C# zazwyczaj używają usług wejścia/wyjścia dostarczanych przez bibliotekę wykonywania programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9269e-170">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="9269e-171">Instrukcja `System.Console.WriteLine("Hello World!");` używa <xref:System.Console.WriteLine%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9269e-171">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="9269e-172">Jest to jedna z metod <xref:System.Console> wyjściowych klasy w bibliotece czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9269e-172">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="9269e-173">Wyświetla jego parametr ciągu w standardowym strumieniu wyjściowym, po którym następuje nowy wiersz.</span><span class="sxs-lookup"><span data-stu-id="9269e-173">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="9269e-174">Inne <xref:System.Console> metody są dostępne dla różnych operacji wejścia i wyjścia.</span><span class="sxs-lookup"><span data-stu-id="9269e-174">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="9269e-175">Jeśli uwzględnisz dyrektywę `using System;` na początku programu, można <xref:System> bezpośrednio użyć klas i metod bez ich pełnego kwalifikowania.</span><span class="sxs-lookup"><span data-stu-id="9269e-175">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="9269e-176">Na przykład można `Console.WriteLine` wywołać `System.Console.WriteLine`zamiast :</span><span class="sxs-lookup"><span data-stu-id="9269e-176">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="9269e-177">Aby uzyskać więcej informacji na temat <xref:System.IO>metod wejścia/wyjścia, zobacz .</span><span class="sxs-lookup"><span data-stu-id="9269e-177">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="see-also"></a><span data-ttu-id="9269e-178">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9269e-178">See also</span></span>

- [<span data-ttu-id="9269e-179">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="9269e-179">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9269e-180">Przykłady i samouczki</span><span class="sxs-lookup"><span data-stu-id="9269e-180">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="9269e-181">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="9269e-181">Main() and Command-Line Arguments</span></span>](../main-and-command-args/index.md)
- [<span data-ttu-id="9269e-182">Wprowadzenie do programu Visual C #</span><span class="sxs-lookup"><span data-stu-id="9269e-182">Getting Started with Visual C#</span></span>](/visualstudio/ide/quickstart-csharp-console)
