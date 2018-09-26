---
title: Kompilacji wiersza polecenia przy użyciu csc.exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 4b6dfdbce131371553fc729206de29794266bfbe
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47111376"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="12ede-102">Kompilacji wiersza polecenia przy użyciu csc.exe</span><span class="sxs-lookup"><span data-stu-id="12ede-102">Command-line build with csc.exe</span></span>
<span data-ttu-id="12ede-103">Można wywołać kompilatora języka C#, wpisując nazwę jego pliku wykonywalnego (*csc.exe*) w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="12ede-103">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="12ede-104">Jeśli używasz **wiersz polecenia programisty dla programu Visual Studio** oknie wszystkie potrzebne zmienne środowiskowe są ustawiane dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="12ede-104">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="12ede-105">Aby uzyskać informacje na temat sposobu dostęp do tego narzędzia, zobacz [wiersz polecenia programisty dla programu Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="12ede-105">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span> 

<span data-ttu-id="12ede-106">Jeśli używasz standardowego okna wiersza polecenia, należy dostosować swoją ścieżkę przed może wywołać *csc.exe* z wszelkie podkatalogi na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="12ede-106">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="12ede-107">Należy również uruchomić *vsvars32.bat* można ustawić odpowiednie zmienne środowiskowe do obsługi kompilacji z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="12ede-107">You also must run *vsvars32.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="12ede-108">Aby uzyskać więcej informacji na temat *vsvars32.bat*, w tym instrukcje dotyczące sposobu Znajdź i uruchom go, zobacz [porady: Ustawianie zmiennych środowiskowych dla programu Visual Studio wierszu polecenia](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="12ede-108">For more information about *vsvars32.bat*, including instructions for how to find and run it, see [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="12ede-109">Jeśli pracujesz na komputerze, który ma tylko [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], można użyć kompilatora języka C# w **SDK Command Prompt**, które można otworzyć **Microsoft .NET Framework SDK** opcji menu.</span><span class="sxs-lookup"><span data-stu-id="12ede-109">If you're working on a computer that has only the [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="12ede-110">Umożliwia także programu MSBuild do kompilowania programów C#, programowo.</span><span class="sxs-lookup"><span data-stu-id="12ede-110">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="12ede-111">Aby uzyskać więcej informacji, zobacz [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="12ede-111">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="12ede-112">*Csc.exe* pliku wykonywalnego zwykle znajduje się w Microsoft.NET\Framework\\*\<wersji >* folderze *Windows* katalog.</span><span class="sxs-lookup"><span data-stu-id="12ede-112">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="12ede-113">Lokalizacji może się różnić w zależności od dokładnej konfiguracji określonego komputera.</span><span class="sxs-lookup"><span data-stu-id="12ede-113">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="12ede-114">Jeśli więcej niż jedna wersja programu .NET Framework jest zainstalowany na komputerze, znajdziesz wiele wersji tego pliku.</span><span class="sxs-lookup"><span data-stu-id="12ede-114">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="12ede-115">Aby uzyskać więcej informacji na temat tych instalacji, zobacz [porady: Określanie, które wersje programu .NET Framework są zainstalowane](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="12ede-115">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
>  <span data-ttu-id="12ede-116">Gdy tworzysz projekt za pomocą środowiska IDE programu Visual Studio możesz wyświetlać **csc** polecenia i jego opcji kompilatora skojarzone w **dane wyjściowe** okna.</span><span class="sxs-lookup"><span data-stu-id="12ede-116">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="12ede-117">Aby wyświetlić te informacje, postępuj zgodnie z instrukcjami [jak: widoku, zapisywanie i konfigurowanie plików dziennika kompilacji](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) Aby zmienić poziom szczegółowości danych dziennika, aby **normalny** lub **szczegółowe**.</span><span class="sxs-lookup"><span data-stu-id="12ede-117">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="12ede-118">Wyszukiwanie po ponownym skompilowaniu projektu **dane wyjściowe** okno **csc** można znaleźć wywołania kompilator języka C#.</span><span class="sxs-lookup"><span data-stu-id="12ede-118">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="12ede-119">**W tym temacie**</span><span class="sxs-lookup"><span data-stu-id="12ede-119">**In this topic**</span></span>

- [<span data-ttu-id="12ede-120">Zasady składni wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="12ede-120">Rules for command-line syntax</span></span>](#-rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="12ede-121">Przykładowe wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="12ede-121">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="12ede-122">Różnice między kompilatorem C# i danymi wyjściowymi kompilatora C++</span><span class="sxs-lookup"><span data-stu-id="12ede-122">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="12ede-123">Zasady składni wiersza polecenia dla kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="12ede-123">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="12ede-124">Kompilator języka C# używa następujących reguł, gdy interpretuje argumenty podane w wierszu polecenia systemu operacyjnego:</span><span class="sxs-lookup"><span data-stu-id="12ede-124">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="12ede-125">Argumenty są rozdzielone biały znak, który jest spacja lub tabulator.</span><span class="sxs-lookup"><span data-stu-id="12ede-125">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="12ede-126">Znak daszka (^) nie została rozpoznana jako znak ucieczki lub ogranicznik.</span><span class="sxs-lookup"><span data-stu-id="12ede-126">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="12ede-127">Znak jest obsługiwany przez analizator składni wiersza polecenia w systemie operacyjnym, zanim zostanie przekazany do `argv` tablicy w programie.</span><span class="sxs-lookup"><span data-stu-id="12ede-127">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="12ede-128">Ciąg ujęty w znaki podwójnego cudzysłowu ("string") jest interpretowany jako jeden argument, niezależnie od tego, biały znak znajdującą się wewnątrz.</span><span class="sxs-lookup"><span data-stu-id="12ede-128">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="12ede-129">Ciąg w cudzysłowach można osadzać w argumencie.</span><span class="sxs-lookup"><span data-stu-id="12ede-129">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="12ede-130">Podwójny cudzysłów poprzedzone znakiem ukośnika odwrotnego (\\") jest interpretowany jako znak literału podwójny cudzysłów (").</span><span class="sxs-lookup"><span data-stu-id="12ede-130">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="12ede-131">Ukośników odwrotnych jest interpretowany dosłownie, chyba że bezpośrednio poprzedzać znak podwójnego cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="12ede-131">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="12ede-132">Jeśli parzysta liczba ukośników odwrotnych następuje podwójny cudzysłów, jednej kreski ułamkowej odwróconej jest umieszczany w `argv` tablicy dla każdej pary ukośników odwrotnych i podwójnego cudzysłowu jest interpretowany jako ogranicznik ciągu.</span><span class="sxs-lookup"><span data-stu-id="12ede-132">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="12ede-133">Jeśli nieparzysta liczba ukośników odwrotnych następuje podwójny cudzysłów, jednej kreski ułamkowej odwróconej jest umieszczany w `argv` tablicy dla każdej pary ukośników odwrotnych i podwójnego cudzysłowu jest "poprzedzone znakiem zmiany znaczenia" przez pozostałe ukośnika odwrotnego.</span><span class="sxs-lookup"><span data-stu-id="12ede-133">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="12ede-134">Powoduje to, że literał podwójny cudzysłów (") mają zostać dodane w `argv`.</span><span class="sxs-lookup"><span data-stu-id="12ede-134">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="12ede-135">Przykładowe wiersze poleceń dla kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="12ede-135">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="12ede-136">Kompiluje *File.cs* produkujących *File.exe*:</span><span class="sxs-lookup"><span data-stu-id="12ede-136">Compiles *File.cs* producing *File.exe*:</span></span>

```console
csc File.cs 
```

- <span data-ttu-id="12ede-137">Kompiluje *File.cs* produkujących *File.dll*:</span><span class="sxs-lookup"><span data-stu-id="12ede-137">Compiles *File.cs* producing *File.dll*:</span></span>

```console
csc -target:library File.cs
```

- <span data-ttu-id="12ede-138">Kompiluje *File.cs* i tworzy *My.exe*:</span><span class="sxs-lookup"><span data-stu-id="12ede-138">Compiles *File.cs* and creates *My.exe*:</span></span>

```console
csc -out:My.exe File.cs
```

- <span data-ttu-id="12ede-139">Kompiluje wszystkie pliki C# w bieżącym katalogu z włączonymi optymalizacjami i definiuje DEBUG symbol.</span><span class="sxs-lookup"><span data-stu-id="12ede-139">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="12ede-140">Dane wyjściowe są *File2.exe*:</span><span class="sxs-lookup"><span data-stu-id="12ede-140">The output is *File2.exe*:</span></span>

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- <span data-ttu-id="12ede-141">Kompiluje wszystkie pliki C# w bieżącym katalogu, tworzenie wersji debugowania *File2.dll*.</span><span class="sxs-lookup"><span data-stu-id="12ede-141">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="12ede-142">Brak logo i żadne ostrzeżenia nie są wyświetlane:</span><span class="sxs-lookup"><span data-stu-id="12ede-142">No logo and no warnings are displayed:</span></span>

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- <span data-ttu-id="12ede-143">Kompiluje wszystkie pliki C# w bieżącym katalogu do *Something.xyz* (DLL):</span><span class="sxs-lookup"><span data-stu-id="12ede-143">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="12ede-144">Różnice między kompilatorem C# i danymi wyjściowymi kompilatora C++</span><span class="sxs-lookup"><span data-stu-id="12ede-144">Differences between C# compiler and C++ compiler output</span></span>
<span data-ttu-id="12ede-145">Istnieją żaden obiekt (*.obj*) pliki utworzone w wyniku wywołania kompilator języka C#; pliki wyjściowe są tworzone bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="12ede-145">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="12ede-146">W efekcie kompilator języka C# nie jest konieczne konsolidatora.</span><span class="sxs-lookup"><span data-stu-id="12ede-146">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="12ede-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12ede-147">See also</span></span>

- [<span data-ttu-id="12ede-148">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="12ede-148">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="12ede-149">Opcje kompilatora C# w porządku alfabetycznym</span><span class="sxs-lookup"><span data-stu-id="12ede-149">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
- [<span data-ttu-id="12ede-150">Opcje kompilatora C# w rozbiciu na kategorie</span><span class="sxs-lookup"><span data-stu-id="12ede-150">C# Compiler Options Listed by Category</span></span>](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
- [<span data-ttu-id="12ede-151">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="12ede-151">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
- [<span data-ttu-id="12ede-152">Argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="12ede-152">Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
- [<span data-ttu-id="12ede-153">Porady: wyświetlanie argumentów wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="12ede-153">How to: Display Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
- [<span data-ttu-id="12ede-154">Instrukcje: uzyskiwanie dostępu do argumentów wiersza polecenia za pomocą instrukcji foreach</span><span class="sxs-lookup"><span data-stu-id="12ede-154">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
- [<span data-ttu-id="12ede-155">Main() — zwracane wartości</span><span class="sxs-lookup"><span data-stu-id="12ede-155">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
