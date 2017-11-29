---
title: Kompilacji wiersza polecenia z csc.exe
ms.date: 04/19/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5ac357ab20f44de4e0613a7af863ad6789e84ec8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="38d0f-102">Kompilacji wiersza polecenia z csc.exe</span><span class="sxs-lookup"><span data-stu-id="38d0f-102">Command-line build with csc.exe</span></span>
<span data-ttu-id="38d0f-103">Można wywołać kompilatora C#, wpisując nazwę jego pliku wykonywalnego (*csc.exe*) w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="38d0f-103">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="38d0f-104">Jeśli używasz **wiersz polecenia dla programu Visual Studio deweloperów** okna, wszystkie zmienne środowiskowe niezbędne są ustawione dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="38d0f-104">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="38d0f-105">Aby uzyskać informacje na temat tego narzędzia, zobacz [wiersz polecenia dla programu Visual Studio deweloperów](../../../framework/tools/developer-command-prompt-for-vs.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="38d0f-105">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span> 

<span data-ttu-id="38d0f-106">Jeśli używasz standardowego okno wiersza polecenia, należy dostosować ścieżki można było *csc.exe* z wszelkie podkatalogi na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="38d0f-106">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="38d0f-107">Należy także uruchomić *vsvars32.bat* można ustawić zmienne środowiskowe odpowiednie do obsługi kompilacji z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="38d0f-107">You also must run *vsvars32.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="38d0f-108">Aby uzyskać więcej informacji na temat *vsvars32.bat*, w tym instrukcje dotyczące sposobu Znajdź i uruchom go, zobacz [porady: Ustawianie zmiennych środowiskowych dla programu Visual Studio wierszu polecenia](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="38d0f-108">For more information about *vsvars32.bat*, including instructions for how to find and run it, see [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="38d0f-109">Jeśli pracujesz na komputerze, który ma tylko [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], można użyć do kompilatora C# w **SDK Command Prompt**, które można otworzyć z **zestawu Microsoft .NET Framework SDK** opcji menu.</span><span class="sxs-lookup"><span data-stu-id="38d0f-109">If you're working on a computer that has only the [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="38d0f-110">Umożliwia także MSBuild do programowego tworzenia programów C#.</span><span class="sxs-lookup"><span data-stu-id="38d0f-110">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="38d0f-111">Aby uzyskać więcej informacji, zobacz [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="38d0f-111">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="38d0f-112">*Csc.exe* pliku wykonywalnego zazwyczaj znajduje się w Microsoft.NET\Framework\\*\<wersji >* folder *Windows* katalog.</span><span class="sxs-lookup"><span data-stu-id="38d0f-112">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="38d0f-113">Lokalizacji mogą się różnić w zależności od dokładnej konfiguracji określonego komputera.</span><span class="sxs-lookup"><span data-stu-id="38d0f-113">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="38d0f-114">Jeśli więcej niż jedna wersja programu .NET Framework jest zainstalowana na komputerze, można znaleźć wiele wersji tego pliku.</span><span class="sxs-lookup"><span data-stu-id="38d0f-114">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="38d0f-115">Aby uzyskać więcej informacji na temat takich instalacji, zobacz [porady: Określanie, które wersje programu .NET Framework są zainstalowane](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="38d0f-115">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
>  <span data-ttu-id="38d0f-116">Podczas tworzenia projektu za pomocą środowiska IDE programu Visual Studio, możesz wyświetlić **csc** polecenia i jego opcji kompilatora skojarzony w **dane wyjściowe** okna.</span><span class="sxs-lookup"><span data-stu-id="38d0f-116">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="38d0f-117">Aby wyświetlić te informacje, postępuj zgodnie z instrukcjami w [porady: widoku, zapisywanie i konfigurowanie plików dziennika kompilacji](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) Aby zmienić poziom szczegółowości danych dziennika **normalny** lub **szczegółowy**.</span><span class="sxs-lookup"><span data-stu-id="38d0f-117">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="38d0f-118">Po odbudowaniu projektu wyszukiwania **dane wyjściowe** w oknie **csc** można znaleźć wywołanie kompilatora C#.</span><span class="sxs-lookup"><span data-stu-id="38d0f-118">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="38d0f-119">**W tym temacie**</span><span class="sxs-lookup"><span data-stu-id="38d0f-119">**In this topic**</span></span>

- [<span data-ttu-id="38d0f-120">Zasady składni wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="38d0f-120">Rules for command-line syntax</span></span>](#-rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="38d0f-121">Przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="38d0f-121">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="38d0f-122">Różnice między kompilatora C# i dane wyjściowe kompilatora C++</span><span class="sxs-lookup"><span data-stu-id="38d0f-122">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="38d0f-123">Zasady składni wiersza polecenia dla kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="38d0f-123">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="38d0f-124">Gdy będą interpretowane przez argumenty podane w wierszu polecenia systemu operacyjnego kompilatora C# stosowane są następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="38d0f-124">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="38d0f-125">Argumenty są rozdzielone biały znak, który jest spację lub tabulator.</span><span class="sxs-lookup"><span data-stu-id="38d0f-125">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="38d0f-126">Znak daszek (^) nie został rozpoznany jako znak ucieczki lub ogranicznika.</span><span class="sxs-lookup"><span data-stu-id="38d0f-126">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="38d0f-127">Znak jest obsługiwany przez analizator składni wiersza polecenia w systemie operacyjnym, zanim zostanie przekazany do `argv` tablicy w programie.</span><span class="sxs-lookup"><span data-stu-id="38d0f-127">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="38d0f-128">Ciąg ujęty w podwójnym cudzysłowie ("string") jest interpretowana jako jeden argument, niezależnie od biały znak, który jest zawarty w.</span><span class="sxs-lookup"><span data-stu-id="38d0f-128">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="38d0f-129">Ciąg w cudzysłowie, można ją osadzić w argumencie.</span><span class="sxs-lookup"><span data-stu-id="38d0f-129">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="38d0f-130">Podwójny cudzysłów poprzedzony ukośnikiem (\\") jest interpretowany jako znak literału podwójnego cudzysłowu (").</span><span class="sxs-lookup"><span data-stu-id="38d0f-130">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="38d0f-131">Używanie ukośników odwrotnych będą interpretowane jako literału, chyba że bezpośrednio poprzedzać podwójny cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="38d0f-131">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="38d0f-132">Jeśli parzystą liczbą ukośników odwrotnych następuje podwójny cudzysłów, jeden ukośnik odwrotny jest umieszczany `argv` tablicy dla każdej pary ukośników odwrotnych i podwójny cudzysłów jest interpretowana jako ogranicznik ciągu.</span><span class="sxs-lookup"><span data-stu-id="38d0f-132">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="38d0f-133">Jeśli nieparzystą liczbę ukośników odwrotnych następuje podwójny cudzysłów, jeden ukośnik odwrotny jest umieszczany `argv` tablicy dla każdej pary ukośników odwrotnych i podwójny cudzysłów jest "wpisywany" z pozostałych ukośnika odwrotnego.</span><span class="sxs-lookup"><span data-stu-id="38d0f-133">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="38d0f-134">Powoduje to literału podwójny cudzysłów (") do dodania w `argv`.</span><span class="sxs-lookup"><span data-stu-id="38d0f-134">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="38d0f-135">Przykładowe wiersze poleceń dla kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="38d0f-135">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="38d0f-136">Kompiluje *File.cs* produkujących *File.exe*:</span><span class="sxs-lookup"><span data-stu-id="38d0f-136">Compiles *File.cs* producing *File.exe*:</span></span>

```console
csc File.cs 
```

- <span data-ttu-id="38d0f-137">Kompiluje *File.cs* produkujących *File.dll*:</span><span class="sxs-lookup"><span data-stu-id="38d0f-137">Compiles *File.cs* producing *File.dll*:</span></span>

```console
csc /target:library File.cs
```

- <span data-ttu-id="38d0f-138">Kompiluje *File.cs* i tworzy *My.exe*:</span><span class="sxs-lookup"><span data-stu-id="38d0f-138">Compiles *File.cs* and creates *My.exe*:</span></span>

```console
csc /out:My.exe File.cs
```

- <span data-ttu-id="38d0f-139">Kompiluje z włączonymi optymalizacjami wszystkie pliki C# w bieżącym katalogu i określa symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="38d0f-139">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="38d0f-140">Dane wyjściowe *File2.exe*:</span><span class="sxs-lookup"><span data-stu-id="38d0f-140">The output is *File2.exe*:</span></span>

```console
csc /define:DEBUG /optimize /out:File2.exe *.cs
```

- <span data-ttu-id="38d0f-141">Kompiluje wszystkie pliki C# w bieżącym katalogu produkujących wersję debugowania *File2.dll*.</span><span class="sxs-lookup"><span data-stu-id="38d0f-141">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="38d0f-142">Brak logo i ostrzeżenia nie są wyświetlane:</span><span class="sxs-lookup"><span data-stu-id="38d0f-142">No logo and no warnings are displayed:</span></span>

```console
csc /target:library /out:File2.dll /warn:0 /nologo /debug *.cs
```

- <span data-ttu-id="38d0f-143">Kompiluje wszystkie pliki C# w bieżącym katalogu do *Something.xyz* (DLL):</span><span class="sxs-lookup"><span data-stu-id="38d0f-143">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

```console
csc /target:library /out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="38d0f-144">Różnice między kompilatora C# i dane wyjściowe kompilatora C++</span><span class="sxs-lookup"><span data-stu-id="38d0f-144">Differences between C# compiler and C++ compiler output</span></span>
<span data-ttu-id="38d0f-145">Brak Brak obiektu (*.obj*) pliki tworzone w wyniku wywołania kompilatora C#; pliki wyjściowe są tworzone bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="38d0f-145">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="38d0f-146">W wyniku tego kompilatora C# nie musi konsolidator.</span><span class="sxs-lookup"><span data-stu-id="38d0f-146">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="38d0f-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38d0f-147">See also</span></span>
 [<span data-ttu-id="38d0f-148">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="38d0f-148">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="38d0f-149">Opcje kompilatora C# alfabetycznym</span><span class="sxs-lookup"><span data-stu-id="38d0f-149">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [<span data-ttu-id="38d0f-150">Opcje kompilatora C# według kategorii</span><span class="sxs-lookup"><span data-stu-id="38d0f-150">C# Compiler Options Listed by Category</span></span>](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 [<span data-ttu-id="38d0f-151">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="38d0f-151">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="38d0f-152">Argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="38d0f-152">Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
 [<span data-ttu-id="38d0f-153">Porady: wyświetlanie argumentów wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="38d0f-153">How to: Display Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [<span data-ttu-id="38d0f-154">Porady: za pomocą argumentów wiersza polecenia dostępu instrukcji foreach</span><span class="sxs-lookup"><span data-stu-id="38d0f-154">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [<span data-ttu-id="38d0f-155">Main() — zwracane wartości</span><span class="sxs-lookup"><span data-stu-id="38d0f-155">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
