---
title: Witaj Świecie — pierwszy program (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 96cad879c843a7b70dc748675123b792137d290e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463120"
---
# <a name="hello-world----your-first-program-c-programming-guide"></a><span data-ttu-id="f3618-102">Witaj Świecie — pierwszy program (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="f3618-102">Hello World -- Your First Program (C# Programming Guide)</span></span>
<span data-ttu-id="f3618-103">Poniższa procedura tworzy wersję języka C# tradycyjny "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="f3618-103">The following procedure creates a C# version of the traditional "Hello World!"</span></span> <span data-ttu-id="f3618-104">program.</span><span class="sxs-lookup"><span data-stu-id="f3618-104">program.</span></span> <span data-ttu-id="f3618-105">Ten program wyświetla ciąg `Hello World!`</span><span class="sxs-lookup"><span data-stu-id="f3618-105">The program displays the string `Hello World!`</span></span>  
  
 <span data-ttu-id="f3618-106">Aby uzyskać więcej przykładów wprowadzających pojęć, zobacz [wprowadzenie do języka Visual C# i Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f3618-106">For more examples of introductory concepts, see [Getting Started with Visual C# and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-and-run-a-console-application"></a><span data-ttu-id="f3618-107">Aby utworzyć i uruchomić aplikację konsoli</span><span class="sxs-lookup"><span data-stu-id="f3618-107">To create and run a console application</span></span>  
  
1.  <span data-ttu-id="f3618-108">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f3618-108">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="f3618-109">Na pasku menu wybierz **pliku**, **New**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="f3618-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="f3618-110">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="f3618-110">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="f3618-111">Rozwiń **zainstalowane**, rozwiń węzeł **szablony**, rozwiń węzeł **Visual C#**, a następnie wybierz **aplikacji konsoli**.</span><span class="sxs-lookup"><span data-stu-id="f3618-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4.  <span data-ttu-id="f3618-112">W **nazwa** , określ nazwę dla projektu, a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="f3618-112">In the **Name** box, specify a name for your project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="f3618-113">Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="f3618-113">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="f3618-114">Jeśli plik Program.cs nie został otwarty w **Edytor kodu**, otwórz menu skrótów dla **Program.cs** w **Eksploratora rozwiązań**, a następnie wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="f3618-114">If Program.cs isn't open in the **Code Editor**, open the shortcut menu for **Program.cs** in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="f3618-115">Zastąp zawartości Program.cs następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="f3618-115">Replace the contents of Program.cs with the following code.</span></span>  
  
     [!code-csharp[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]  
  
7.  <span data-ttu-id="f3618-116">Wybierz klawisz F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="f3618-116">Choose the F5 key to run the project.</span></span> <span data-ttu-id="f3618-117">Zostanie wyświetlone okno wiersza polecenia zawierające następujący wiersz `Hello World!`</span><span class="sxs-lookup"><span data-stu-id="f3618-117">A Command Prompt window appears that contains the line `Hello World!`</span></span>  
  
 <span data-ttu-id="f3618-118">Następnie ważne elementy tego programu są badane.</span><span class="sxs-lookup"><span data-stu-id="f3618-118">Next, the important parts of this program are examined.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="f3618-119">Komentarze</span><span class="sxs-lookup"><span data-stu-id="f3618-119">Comments</span></span>  
 <span data-ttu-id="f3618-120">Pierwszy wiersz zawiera komentarz.</span><span class="sxs-lookup"><span data-stu-id="f3618-120">The first line contains a comment.</span></span> <span data-ttu-id="f3618-121">Znaki `//` przekonwertować pozostałą część wiersza komentarza.</span><span class="sxs-lookup"><span data-stu-id="f3618-121">The characters `//` convert the rest of the line to a comment.</span></span>  
  
 [!code-csharp[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]  
  
 <span data-ttu-id="f3618-122">Możesz również skomentować blok tekstu umieszczając go między `/*` i `*/` znaków.</span><span class="sxs-lookup"><span data-stu-id="f3618-122">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="f3618-123">Jest to pokazane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f3618-123">This is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]  
  
## <a name="main-method"></a><span data-ttu-id="f3618-124">Metoda główna</span><span class="sxs-lookup"><span data-stu-id="f3618-124">Main Method</span></span>  
 <span data-ttu-id="f3618-125">Aplikacja konsolowa C# musi zawierać `Main` metody, w której Kontrola rozpoczyna się i kończy.</span><span class="sxs-lookup"><span data-stu-id="f3618-125">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="f3618-126">`Main` Metodą jest, gdy tworzysz obiekty i wykonujesz inne metody.</span><span class="sxs-lookup"><span data-stu-id="f3618-126">The `Main` method is where you create objects and execute other methods.</span></span>  
  
 <span data-ttu-id="f3618-127">`Main` Metodą jest [statyczne](../../../csharp/language-reference/keywords/static.md) metodę, która znajduje się wewnątrz klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="f3618-127">The `Main` method is a [static](../../../csharp/language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="f3618-128">W poprzednim "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="f3618-128">In the previous "Hello World!"</span></span> <span data-ttu-id="f3618-129">przykład znajduje się on w klasie o nazwie `Hello`.</span><span class="sxs-lookup"><span data-stu-id="f3618-129">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="f3618-130">Można zadeklarować `Main` metody w jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="f3618-130">You can declare the `Main` method in one of the following ways:</span></span>  
  
-   <span data-ttu-id="f3618-131">Może zwracać `void`.</span><span class="sxs-lookup"><span data-stu-id="f3618-131">It can return `void`.</span></span>  
  
     [!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]  
  
-   <span data-ttu-id="f3618-132">Może również zwracać liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="f3618-132">It can also return an integer.</span></span>  
  
     [!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]  
  
-   <span data-ttu-id="f3618-133">Jeden z typów zwracanych może przebierać argumenty.</span><span class="sxs-lookup"><span data-stu-id="f3618-133">With either of the return types, it can take arguments.</span></span>  
  
     [!code-csharp[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]  
  
     <span data-ttu-id="f3618-134">—lub—</span><span class="sxs-lookup"><span data-stu-id="f3618-134">-or-</span></span>  
  
     [!code-csharp[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]  
  
 <span data-ttu-id="f3618-135">Wartość parametru `Main` metody `args`, jest `string` tablica zawierająca argumenty wiersza polecenia używane do wywołania programu.</span><span class="sxs-lookup"><span data-stu-id="f3618-135">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span> <span data-ttu-id="f3618-136">W przeciwieństwie do języka C++, tablica nie zawiera nazwę pliku wykonywalnego (exe).</span><span class="sxs-lookup"><span data-stu-id="f3618-136">Unlike in C++, the array does not include the name of the executable (exe) file.</span></span>  
  
 <span data-ttu-id="f3618-137">Aby uzyskać więcej informacji o tym, jak używać argumentów wiersza polecenia, zobacz przykłady w [Main() i argumenty wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/index.md) i [jak: utworzyć i używać zestawów przy użyciu wiersza polecenia](https://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).</span><span class="sxs-lookup"><span data-stu-id="f3618-137">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) and [How to: Create and Use Assemblies Using the Command Line](https://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).</span></span>  
  
 <span data-ttu-id="f3618-138">Wywołanie <xref:System.Console.ReadKey%2A> na końcu `Main` metoda uniemożliwia zamknięcie, zanim użytkownik zdąży odczytać dane wyjściowe, gdy uruchamiasz program w trybie debugowania, naciskając klawisz F5 okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="f3618-138">The call to <xref:System.Console.ReadKey%2A> at the end of the `Main` method prevents the console window from closing before you have a chance to read the output when you run your program in debug mode, by pressing F5.</span></span>  
  
## <a name="input-and-output"></a><span data-ttu-id="f3618-139">Dane wejściowe i wyjściowe</span><span class="sxs-lookup"><span data-stu-id="f3618-139">Input and Output</span></span>  
 <span data-ttu-id="f3618-140">C# programy używają zwykle wejścia/wyjścia usług dostarczonych przez biblioteki wykonawczej programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f3618-140">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="f3618-141">Wykonywanie instrukcji `System.Console.WriteLine("Hello World!");` używa <xref:System.Console.WriteLine%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f3618-141">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="f3618-142">Jest to jedna z metod wyjścia metod klasy <xref:System.Console> klasy w bibliotece wykonawczej.</span><span class="sxs-lookup"><span data-stu-id="f3618-142">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="f3618-143">Wyświetla własny parametr ciągu na standardowym strumieniu wyjściowym znak nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="f3618-143">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="f3618-144">Inne <xref:System.Console> metody są dostępne różne dane wejściowe i dane wyjściowe operacji.</span><span class="sxs-lookup"><span data-stu-id="f3618-144">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="f3618-145">Jeśli dołączysz `using System;` dyrektywę na początku programu, możesz bezpośrednio użyć <xref:System> klas i metod bez pełnej ich kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="f3618-145">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="f3618-146">Na przykład, można wywołać `Console.WriteLine` zamiast `System.Console.WriteLine`:</span><span class="sxs-lookup"><span data-stu-id="f3618-146">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]  
  
 [!code-csharp[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]  
  
 <span data-ttu-id="f3618-147">Aby uzyskać więcej informacji dotyczących metod wejście/wyjście, zobacz <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="f3618-147">For more information about input/output methods, see <xref:System.IO>.</span></span>  
  
## <a name="command-line-compilation-and-execution"></a><span data-ttu-id="f3618-148">Wiersz polecenia kompilacji i wykonania</span><span class="sxs-lookup"><span data-stu-id="f3618-148">Command-Line Compilation and Execution</span></span>  
 <span data-ttu-id="f3618-149">Można też kompilować "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="f3618-149">You can compile the "Hello World!"</span></span> <span data-ttu-id="f3618-150">program przy użyciu wiersza polecenia zamiast zintegrowanego rozwoju środowiska (IDE) Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f3618-150">program by using the command line instead of the Visual Studio Integrated Development Environment (IDE).</span></span>  
  
#### <a name="to-compile-and-run-from-a-command-prompt"></a><span data-ttu-id="f3618-151">Aby skompilować i uruchomić z wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="f3618-151">To compile and run from a command prompt</span></span>  
  
1.  <span data-ttu-id="f3618-152">Wklej kod z poprzedniej procedury do dowolnego edytora tekstów, a następnie zapisz plik jako plik tekstowy.</span><span class="sxs-lookup"><span data-stu-id="f3618-152">Paste the code from the preceding procedure into any text editor, and then save the file as a text file.</span></span> <span data-ttu-id="f3618-153">Nadaj plikowi nazwę `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="f3618-153">Name the file `Hello.cs`.</span></span> <span data-ttu-id="f3618-154">Pliki kodu źródłowego języka C# za pomocą rozszerzenia `.cs`.</span><span class="sxs-lookup"><span data-stu-id="f3618-154">C# source code files use the extension `.cs`.</span></span>  
  
2.  <span data-ttu-id="f3618-155">Wykonaj jedną z następujących czynności, aby otworzyć okno wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="f3618-155">Perform one of the following steps to open a command-prompt window:</span></span>  
  
    -   <span data-ttu-id="f3618-156">W systemie Windows 10 na **Start** menu, wyszukaj `Developer Command Prompt`, a następnie dotknij lub wybierz **wiersz polecenia programisty dla programu VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="f3618-156">In Windows 10, on the **Start** menu, search for `Developer Command Prompt`, and then tap or choose **Developer Command Prompt for VS 2017**.</span></span>  
  
         <span data-ttu-id="f3618-157">Zostanie wyświetlone okno wiersza polecenia dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="f3618-157">A Developer Command Prompt window appears.</span></span>  
  
    -   <span data-ttu-id="f3618-158">Windows 7, otwórz **Start** menu, rozwiń folder dla bieżącej wersji programu Visual Studio, otwórz menu skrótów dla **Visual Studio Tools**, a następnie wybierz **wiersz polecenia dla deweloperów dla programu VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="f3618-158">In Windows 7, open the **Start** menu, expand the folder for the current version of Visual Studio, open the shortcut menu for **Visual Studio Tools**, and then choose **Developer Command Prompt for VS 2017**.</span></span>  
  
         <span data-ttu-id="f3618-159">Zostanie wyświetlone okno wiersza polecenia dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="f3618-159">A Developer Command Prompt window appears.</span></span>  
  
    -   <span data-ttu-id="f3618-160">Włącz kompilację wiersza polecenia od standardowego okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="f3618-160">Enable command-line builds from a standard Command Prompt window.</span></span>  
  
         <span data-ttu-id="f3618-161">Zobacz [porady: Ustawianie zmiennych środowiskowych dla wiersza polecenia programu Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="f3618-161">See [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>  
  
3.  <span data-ttu-id="f3618-162">W oknie wiersza polecenia przejdź do folderu, który zawiera Twoje `Hello.cs` pliku.</span><span class="sxs-lookup"><span data-stu-id="f3618-162">In the command-prompt window, navigate to the folder that contains your `Hello.cs` file.</span></span>  
  
4.  <span data-ttu-id="f3618-163">Wprowadź następujące polecenie, aby skompilować `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="f3618-163">Enter the following command to compile `Hello.cs`.</span></span>  
  
     `csc Hello.cs`  
  
     <span data-ttu-id="f3618-164">Jeśli program nie ma żadnych błędów kompilacji, plik wykonywalny, który nosi nazwę `Hello.exe` zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="f3618-164">If your program has no compilation errors, an executable file that is named `Hello.exe` is created.</span></span>  
  
5.  <span data-ttu-id="f3618-165">W oknie wiersza polecenia wprowadź następujące polecenie, aby uruchomić program:</span><span class="sxs-lookup"><span data-stu-id="f3618-165">In the command-prompt window, enter the following command to run the program:</span></span>  
  
     `Hello`  
  
 <span data-ttu-id="f3618-166">Aby uzyskać więcej informacji dotyczących kompilatora C# i jego opcji, zobacz [opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md).</span><span class="sxs-lookup"><span data-stu-id="f3618-166">For more information about the C# compiler and its options, see [C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f3618-167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3618-167">See Also</span></span>  
 [<span data-ttu-id="f3618-168">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f3618-168">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f3618-169">Konstrukcja programu C#</span><span class="sxs-lookup"><span data-stu-id="f3618-169">Inside a C# Program</span></span>](../../../csharp/programming-guide/inside-a-program/index.md)  
 [<span data-ttu-id="f3618-170">Ciągi</span><span class="sxs-lookup"><span data-stu-id="f3618-170">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="f3618-171">\<paveover > C# — przykładowe aplikacje</span><span class="sxs-lookup"><span data-stu-id="f3618-171">\<paveover>C# Sample Applications</span></span>](https://msdn.microsoft.com/library/9a9d7aaa-51d3-4224-b564-95409b0f3e15)  
 [<span data-ttu-id="f3618-172">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f3618-172">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f3618-173">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="f3618-173">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="f3618-174">Wprowadzenie do języków Visual C# i Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f3618-174">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
