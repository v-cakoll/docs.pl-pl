---
title: Hello world — pierwszy Przewodnik C# programowania programu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 9a50de0bb583a1dfccfa609be1cca732868505ba
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589376"
---
# <a name="hello-world----your-first-program-c-programming-guide"></a><span data-ttu-id="5e378-102">Hello world — pierwszy program (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="5e378-102">Hello World -- Your first program (C# Programming Guide)</span></span>

<span data-ttu-id="5e378-103">Poniższa procedura tworzy C# wersję tradycyjnego "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="5e378-103">The following procedure creates a C# version of the traditional "Hello World!"</span></span> <span data-ttu-id="5e378-104">program.</span><span class="sxs-lookup"><span data-stu-id="5e378-104">program.</span></span> <span data-ttu-id="5e378-105">Program wyświetla ciąg`Hello World!`</span><span class="sxs-lookup"><span data-stu-id="5e378-105">The program displays the string `Hello World!`</span></span>

<span data-ttu-id="5e378-106">Aby uzyskać więcej przykładów dotyczących wprowadzenia, zobacz [wprowadzenie z wizualizacjami C# i Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5e378-106">For more examples of introductory concepts, see [Getting Started with Visual C# and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-and-run-a-console-application"></a><span data-ttu-id="5e378-107">Aby utworzyć i uruchomić aplikację konsoli</span><span class="sxs-lookup"><span data-stu-id="5e378-107">To create and run a console application</span></span>

1. <span data-ttu-id="5e378-108">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5e378-108">Start Visual Studio.</span></span>

2. <span data-ttu-id="5e378-109">Na pasku menu wybierz **pliku**, **New**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="5e378-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="5e378-110">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="5e378-110">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="5e378-111">Rozwiń węzeł **zainstalowane**, rozwiń węzeł **Szablony**, rozwiń węzeł **wizualizacji C#** , a następnie wybierz pozycję **Aplikacja konsolowa**.</span><span class="sxs-lookup"><span data-stu-id="5e378-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>

4. <span data-ttu-id="5e378-112">W polu **Nazwa** Określ nazwę projektu, a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="5e378-112">In the **Name** box, specify a name for your project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="5e378-113">Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="5e378-113">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="5e378-114">Jeśli Program.cs nie jest otwarty w **edytorze kodu**, otwórz menu skrótów dla **program.cs** w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="5e378-114">If Program.cs isn't open in the **Code Editor**, open the shortcut menu for **Program.cs** in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="5e378-115">Zastąp zawartość Program.cs następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="5e378-115">Replace the contents of Program.cs with the following code.</span></span>

     [!code-csharp[csProgGuide#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#21)]

7. <span data-ttu-id="5e378-116">Wybierz klawisz F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="5e378-116">Choose the F5 key to run the project.</span></span> <span data-ttu-id="5e378-117">Zostanie wyświetlone okno wiersza polecenia zawierające wiersz`Hello World!`</span><span class="sxs-lookup"><span data-stu-id="5e378-117">A Command Prompt window appears that contains the line `Hello World!`</span></span>

<span data-ttu-id="5e378-118">Następnie należy sprawdzić ważne części tego programu.</span><span class="sxs-lookup"><span data-stu-id="5e378-118">Next, the important parts of this program are examined.</span></span>

## <a name="comments"></a><span data-ttu-id="5e378-119">Komentarze</span><span class="sxs-lookup"><span data-stu-id="5e378-119">Comments</span></span>

<span data-ttu-id="5e378-120">Pierwszy wiersz zawiera komentarz.</span><span class="sxs-lookup"><span data-stu-id="5e378-120">The first line contains a comment.</span></span> <span data-ttu-id="5e378-121">Znaki `//` konwertują resztę wiersza do komentarza.</span><span class="sxs-lookup"><span data-stu-id="5e378-121">The characters `//` convert the rest of the line to a comment.</span></span>

 [!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="5e378-122">Możesz również dodać komentarz do bloku tekstu, umieszczając go między `/*` znakami i. `*/`</span><span class="sxs-lookup"><span data-stu-id="5e378-122">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="5e378-123">Pokazano to w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5e378-123">This is shown in the following example.</span></span>

 [!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

## <a name="main-method"></a><span data-ttu-id="5e378-124">Metoda główna</span><span class="sxs-lookup"><span data-stu-id="5e378-124">Main method</span></span>

<span data-ttu-id="5e378-125">Aplikacja C# konsolowa musi zawierać `Main` metodę, w której kontrolka zaczyna się i skończy.</span><span class="sxs-lookup"><span data-stu-id="5e378-125">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="5e378-126">Metoda `Main` ta umożliwia tworzenie obiektów i wykonywanie innych metod.</span><span class="sxs-lookup"><span data-stu-id="5e378-126">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="5e378-127">Metoda jest metodą statyczną, która znajduje się wewnątrz klasy lub struktury. [](../../language-reference/keywords/static.md) `Main`</span><span class="sxs-lookup"><span data-stu-id="5e378-127">The `Main` method is a [static](../../language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="5e378-128">W poprzednim "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="5e378-128">In the previous "Hello World!"</span></span> <span data-ttu-id="5e378-129">przykład znajduje się w klasie o nazwie `Hello`.</span><span class="sxs-lookup"><span data-stu-id="5e378-129">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="5e378-130">`Main` Metodę można zadeklarować w jeden z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="5e378-130">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="5e378-131">Może zwrócić `void`.</span><span class="sxs-lookup"><span data-stu-id="5e378-131">It can return `void`.</span></span>

     [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="5e378-132">Może również zwracać liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="5e378-132">It can also return an integer.</span></span>

     [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="5e378-133">Za pomocą jednego z typów zwracanych można przyjmować argumenty.</span><span class="sxs-lookup"><span data-stu-id="5e378-133">With either of the return types, it can take arguments.</span></span>

     [!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

     <span data-ttu-id="5e378-134">—lub—</span><span class="sxs-lookup"><span data-stu-id="5e378-134">-or-</span></span>

     [!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="5e378-135">Parametr `Main` `string` metody,, jest tablicą zawierającą argumenty wiersza polecenia używane do wywołania programu. `args`</span><span class="sxs-lookup"><span data-stu-id="5e378-135">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span> <span data-ttu-id="5e378-136">W przeciwieństwie C++do programu w programie tablica nie zawiera nazwy pliku wykonywalnego (exe).</span><span class="sxs-lookup"><span data-stu-id="5e378-136">Unlike in C++, the array does not include the name of the executable (exe) file.</span></span>

<span data-ttu-id="5e378-137">Aby uzyskać więcej informacji o sposobach używania argumentów wiersza polecenia, zobacz przykłady w [Main () i argumenty wiersza polecenia](../main-and-command-args/index.md) i [instrukcje: Tworzenie i używanie zestawów przy użyciu wiersza](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)polecenia.</span><span class="sxs-lookup"><span data-stu-id="5e378-137">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../main-and-command-args/index.md) and [How to: Create and Use Assemblies Using the Command Line](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span></span>

<span data-ttu-id="5e378-138">Wywołanie <xref:System.Console.ReadKey%2A> na końcu `Main` metody uniemożliwia zamknięcie okna konsoli przed rozpoczęciem odczytywania danych wyjściowych podczas uruchamiania programu w trybie debugowania, naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="5e378-138">The call to <xref:System.Console.ReadKey%2A> at the end of the `Main` method prevents the console window from closing before you have a chance to read the output when you run your program in debug mode, by pressing F5.</span></span>

## <a name="input-and-output"></a><span data-ttu-id="5e378-139">Dane wejściowe i wyjściowe</span><span class="sxs-lookup"><span data-stu-id="5e378-139">Input and output</span></span>

<span data-ttu-id="5e378-140">C#programy zwykle korzystają z usług wejścia/wyjścia dostarczonych przez bibliotekę wykonawczą .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5e378-140">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="5e378-141">`System.Console.WriteLine("Hello World!");` Instrukcja<xref:System.Console.WriteLine%2A> używa metody.</span><span class="sxs-lookup"><span data-stu-id="5e378-141">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="5e378-142">Jest to jedna z metod <xref:System.Console> wyjściowych klasy w bibliotece wykonawczej.</span><span class="sxs-lookup"><span data-stu-id="5e378-142">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="5e378-143">Wyświetla jego parametr String w standardowym strumieniu wyjściowym, po którym następuje nowy wiersz.</span><span class="sxs-lookup"><span data-stu-id="5e378-143">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="5e378-144">Inne <xref:System.Console> metody są dostępne dla różnych operacji wejścia i wyjścia.</span><span class="sxs-lookup"><span data-stu-id="5e378-144">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="5e378-145">Jeśli dołączysz `using System;` dyrektywę na początku programu, możesz bezpośrednio <xref:System> użyć klas i metod bez ich w pełni kwalifikujących się.</span><span class="sxs-lookup"><span data-stu-id="5e378-145">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="5e378-146">Na przykład można wywołać `Console.WriteLine` `System.Console.WriteLine`zamiast:</span><span class="sxs-lookup"><span data-stu-id="5e378-146">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

 [!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="5e378-147">Aby uzyskać więcej informacji na temat metod wejścia/wyjścia <xref:System.IO>, zobacz.</span><span class="sxs-lookup"><span data-stu-id="5e378-147">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="command-line-compilation-and-execution"></a><span data-ttu-id="5e378-148">Kompilacja i wykonywanie w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="5e378-148">Command-line compilation and execution</span></span>

<span data-ttu-id="5e378-149">Można skompilować "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="5e378-149">You can compile the "Hello World!"</span></span> <span data-ttu-id="5e378-150">program przy użyciu wiersza polecenia zamiast zintegrowanego środowiska programistycznego (IDE) programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5e378-150">program by using the command line instead of the Visual Studio Integrated Development Environment (IDE).</span></span>

### <a name="to-compile-and-run-from-a-command-prompt"></a><span data-ttu-id="5e378-151">Aby skompilować i uruchomić z wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="5e378-151">To compile and run from a command prompt</span></span>

1. <span data-ttu-id="5e378-152">Wklej kod z poprzedniej procedury do dowolnego edytora tekstów, a następnie Zapisz plik jako plik tekstowy.</span><span class="sxs-lookup"><span data-stu-id="5e378-152">Paste the code from the preceding procedure into any text editor, and then save the file as a text file.</span></span> <span data-ttu-id="5e378-153">Nazwij plik `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="5e378-153">Name the file `Hello.cs`.</span></span> <span data-ttu-id="5e378-154">C#pliki kodu źródłowego używają rozszerzenia `.cs`.</span><span class="sxs-lookup"><span data-stu-id="5e378-154">C# source code files use the extension `.cs`.</span></span>

2. <span data-ttu-id="5e378-155">Wykonaj jedną z następujących czynności, aby otworzyć okno wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="5e378-155">Perform one of the following steps to open a command-prompt window:</span></span>

    - <span data-ttu-id="5e378-156">W systemie Windows 10, w menu **Start** , Wyszukaj `Developer Command Prompt`, a następnie naciśnij lub wybierz **wiersz polecenia dla deweloperów dla programu vs 2017**.</span><span class="sxs-lookup"><span data-stu-id="5e378-156">In Windows 10, on the **Start** menu, search for `Developer Command Prompt`, and then tap or choose **Developer Command Prompt for VS 2017**.</span></span>

         <span data-ttu-id="5e378-157">Zostanie wyświetlone okno wiersz polecenia dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="5e378-157">A Developer Command Prompt window appears.</span></span>

    - <span data-ttu-id="5e378-158">W systemie Windows 7 Otwórz menu **Start** , rozwiń folder dla bieżącej wersji programu Visual Studio, otwórz menu skrótów dla **Visual Studio Tools**, a następnie wybierz **wiersz polecenia dla deweloperów dla programu vs 2017**.</span><span class="sxs-lookup"><span data-stu-id="5e378-158">In Windows 7, open the **Start** menu, expand the folder for the current version of Visual Studio, open the shortcut menu for **Visual Studio Tools**, and then choose **Developer Command Prompt for VS 2017**.</span></span>

         <span data-ttu-id="5e378-159">Zostanie wyświetlone okno wiersz polecenia dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="5e378-159">A Developer Command Prompt window appears.</span></span>

    - <span data-ttu-id="5e378-160">Włącz kompilacje wiersza polecenia z poziomu standardowego okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5e378-160">Enable command-line builds from a standard Command Prompt window.</span></span>

         <span data-ttu-id="5e378-161">Zobacz [How to: Ustawianie zmiennych środowiskowych dla wiersza](../../language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5e378-161">See [How to: Set Environment Variables for the Visual Studio Command Line](../../language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

3. <span data-ttu-id="5e378-162">W oknie wiersza polecenia przejdź do folderu, który zawiera `Hello.cs` plik.</span><span class="sxs-lookup"><span data-stu-id="5e378-162">In the command-prompt window, navigate to the folder that contains your `Hello.cs` file.</span></span>

4. <span data-ttu-id="5e378-163">Wprowadź następujące polecenie, aby skompilować `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="5e378-163">Enter the following command to compile `Hello.cs`.</span></span>

     `csc Hello.cs`

     <span data-ttu-id="5e378-164">Jeśli program nie ma błędów kompilacji, tworzony jest plik wykonywalny o nazwie `Hello.exe` .</span><span class="sxs-lookup"><span data-stu-id="5e378-164">If your program has no compilation errors, an executable file that is named `Hello.exe` is created.</span></span>

5. <span data-ttu-id="5e378-165">W oknie wiersza polecenia wprowadź następujące polecenie, aby uruchomić program:</span><span class="sxs-lookup"><span data-stu-id="5e378-165">In the command-prompt window, enter the following command to run the program:</span></span>

     `Hello`

 <span data-ttu-id="5e378-166">Aby uzyskać więcej informacji o C# kompilatorze i jego opcjach, zobacz [ C# opcje kompilatora](../../language-reference/compiler-options/index.md).</span><span class="sxs-lookup"><span data-stu-id="5e378-166">For more information about the C# compiler and its options, see [C# Compiler Options](../../language-reference/compiler-options/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5e378-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e378-167">See also</span></span>

- [<span data-ttu-id="5e378-168">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5e378-168">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5e378-169">Konstrukcja programu C#</span><span class="sxs-lookup"><span data-stu-id="5e378-169">Inside a C# Program</span></span>](./index.md)
- [<span data-ttu-id="5e378-170">Ciągi</span><span class="sxs-lookup"><span data-stu-id="5e378-170">Strings</span></span>](../strings/index.md)
- [<span data-ttu-id="5e378-171">Przykłady i samouczki</span><span class="sxs-lookup"><span data-stu-id="5e378-171">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="5e378-172">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5e378-172">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="5e378-173">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="5e378-173">Main() and Command-Line Arguments</span></span>](../main-and-command-args/index.md)
- [<span data-ttu-id="5e378-174">Wprowadzenie do języków Visual C# i Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e378-174">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
