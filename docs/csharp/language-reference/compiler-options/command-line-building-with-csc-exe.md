---
title: Kompilacja z wiersza polecenia za pomocą pliku CSC. exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 54306c79bc2856996925756ee4261fbe67692aea
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606980"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="ab1d9-102">Kompilacja z wiersza polecenia za pomocą pliku CSC. exe</span><span class="sxs-lookup"><span data-stu-id="ab1d9-102">Command-line build with csc.exe</span></span>
<span data-ttu-id="ab1d9-103">C# Kompilator można wywołać, wpisując nazwę pliku wykonywalnego (*CSC. exe*) w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-103">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="ab1d9-104">W przypadku korzystania z okna **wiersz polecenia dla deweloperów dla programu Visual Studio** wszystkie wymagane zmienne środowiskowe są ustawiane dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-104">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="ab1d9-105">Aby uzyskać informacje na temat sposobu uzyskiwania dostępu do tego narzędzia, zobacz temat [wiersz polecenia dla deweloperów for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) .</span><span class="sxs-lookup"><span data-stu-id="ab1d9-105">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span> 

<span data-ttu-id="ab1d9-106">Jeśli używasz standardowego okna wiersza polecenia, musisz dostosować ścieżkę przed wywołaniem pliku *CSC. exe* z dowolnego podkatalogu na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-106">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="ab1d9-107">Należy również uruchomić *vsvars32. bat* , aby ustawić odpowiednie zmienne środowiskowe do obsługi kompilacji w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-107">You also must run *vsvars32.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="ab1d9-108">Aby uzyskać więcej informacji na temat *vsvars32. bat*, w tym instrukcje dotyczące sposobu znajdowania i uruchamiania [, zobacz How to: Ustawianie zmiennych środowiskowych dla wiersza](./how-to-set-environment-variables-for-the-visual-studio-command-line.md)polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-108">For more information about *vsvars32.bat*, including instructions for how to find and run it, see [How to: Set Environment Variables for the Visual Studio Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="ab1d9-109">Jeśli pracujesz na komputerze, na którym jest tylko zestaw Windows Software Development Kit (SDK), możesz użyć C# kompilatora w **wierszu polecenia zestawu SDK**, który można otworzyć z poziomu opcji menu **Microsoft .NET Framework SDK** .</span><span class="sxs-lookup"><span data-stu-id="ab1d9-109">If you're working on a computer that has only the Windows Software Development Kit (SDK), you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="ab1d9-110">Można również użyć programu MSBuild do programistycznego kompilowania C# programów.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-110">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="ab1d9-111">Aby uzyskać więcej informacji, zobacz [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="ab1d9-111">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="ab1d9-112">Plik wykonywalny *CSC. exe* zazwyczaj znajduje się w folderze Microsoft. NET\Framework\\ *\<w wersji >* w katalogu *systemu Windows* .</span><span class="sxs-lookup"><span data-stu-id="ab1d9-112">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="ab1d9-113">Jego lokalizacja może się różnić w zależności od dokładnej konfiguracji określonego komputera.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-113">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="ab1d9-114">Jeśli na komputerze zainstalowano więcej niż jedną wersję .NET Framework, znajdziesz wiele wersji tego pliku.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-114">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="ab1d9-115">Aby uzyskać więcej informacji na temat takich instalacji, zobacz [How to: Określanie, które wersje .NET Framework są zainstalowane](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="ab1d9-115">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
>  <span data-ttu-id="ab1d9-116">Podczas kompilowania projektu przy użyciu programu Visual Studio IDE, można wyświetlić polecenie **CSC** i skojarzone z nim opcje kompilatora w oknie **danych wyjściowych** .</span><span class="sxs-lookup"><span data-stu-id="ab1d9-116">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="ab1d9-117">Aby wyświetlić te informacje, postępuj zgodnie z [instrukcjami w temacie How to: Wyświetlanie, zapisywanie i konfigurowanie plików](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) dziennika kompilacji, aby zmienić poziom szczegółowości danych dziennika na **normalny** lub **szczegółowy**.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-117">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="ab1d9-118">Po odbudowaniu projektu Przeszukaj okno **dane wyjściowe** dla **CSC** , aby znaleźć wywołanie C# kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-118">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="ab1d9-119">**W tym temacie**</span><span class="sxs-lookup"><span data-stu-id="ab1d9-119">**In this topic**</span></span>

- [<span data-ttu-id="ab1d9-120">Reguły dla składni wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="ab1d9-120">Rules for command-line syntax</span></span>](#rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="ab1d9-121">Przykładowe wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="ab1d9-121">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="ab1d9-122">Różnice między C# kompilatorem C++ a wyjściem kompilatora</span><span class="sxs-lookup"><span data-stu-id="ab1d9-122">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="ab1d9-123">Reguły dla składni wiersza polecenia C# kompilatora</span><span class="sxs-lookup"><span data-stu-id="ab1d9-123">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="ab1d9-124">C# Kompilator używa następujących reguł, gdy interpretuje argumenty podane w wierszu polecenia systemu operacyjnego:</span><span class="sxs-lookup"><span data-stu-id="ab1d9-124">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="ab1d9-125">Argumenty są rozdzielane znakami odstępu, który jest spacją lub tabulatorem.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-125">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="ab1d9-126">Znak karetki (^) nie jest rozpoznawany jako znak ucieczki lub ogranicznik.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-126">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="ab1d9-127">Ten znak jest obsługiwany przez analizator wiersza polecenia w systemie operacyjnym przed przekazaniem go do `argv` tablicy w programie.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-127">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="ab1d9-128">Ciąg ujęty w znaki podwójnego cudzysłowu ("String") jest interpretowany jako pojedynczy argument, niezależnie od białego miejsca zawartego w.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-128">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="ab1d9-129">Ciąg w cudzysłowie może być osadzony w argumencie.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-129">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="ab1d9-130">Podwójny cudzysłów poprzedzony ukośnikiem odwrotnym (\\") jest interpretowany jako literał podwójnego znaku cudzysłowu (").</span><span class="sxs-lookup"><span data-stu-id="ab1d9-130">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="ab1d9-131">Ukośniki odwrotne są interpretowane dosłownie, chyba że od razu poprzedzają podwójny cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-131">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="ab1d9-132">Jeśli parzysta liczba kresek ułamkowych jest poprzedzona znakiem podwójnego cudzysłowu, jeden ukośnik odwrotny jest `argv` umieszczany w tablicy dla każdej pary ukośników odwrotnych, a podwójny cudzysłów jest interpretowany jako ogranicznik ciągu.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-132">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="ab1d9-133">Jeśli po parzystej liczbie ukośników odwrotnych następuje znak podwójnego cudzysłowu, jeden ukośnik odwrotny jest umieszczany w `argv` tablicy dla każdej pary ukośników odwrotnych, a podwójny cudzysłów jest "ucieczkd" przez resztę ukośnika odwrotnego.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-133">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="ab1d9-134">Powoduje to dodanie `argv`literału podwójnego cudzysłowu (") do elementu.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-134">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="ab1d9-135">Przykładowe wiersze poleceń dla C# kompilatora</span><span class="sxs-lookup"><span data-stu-id="ab1d9-135">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="ab1d9-136">Kompiluje *File.Cser* tworzenia *pliku. exe*:</span><span class="sxs-lookup"><span data-stu-id="ab1d9-136">Compiles *File.cs* producing *File.exe*:</span></span>

```console
csc File.cs 
```

- <span data-ttu-id="ab1d9-137">Kompiluje plik File.cs *. dll*:</span><span class="sxs-lookup"><span data-stu-id="ab1d9-137">Compiles *File.cs* producing *File.dll*:</span></span>

```console
csc -target:library File.cs
```

- <span data-ttu-id="ab1d9-138">Kompiluje *File.cs* i tworzy *My. exe*:</span><span class="sxs-lookup"><span data-stu-id="ab1d9-138">Compiles *File.cs* and creates *My.exe*:</span></span>

```console
csc -out:My.exe File.cs
```

- <span data-ttu-id="ab1d9-139">Kompiluje wszystkie C# pliki w bieżącym katalogu z włączonymi optymalizacjami i definiuje symbol debugowania.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-139">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="ab1d9-140">Dane wyjściowe to *plik2. exe*:</span><span class="sxs-lookup"><span data-stu-id="ab1d9-140">The output is *File2.exe*:</span></span>

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- <span data-ttu-id="ab1d9-141">Kompiluje wszystkie C# pliki w bieżącym katalogu, które wytwarzają wersję debugową *plik2. dll*.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-141">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="ab1d9-142">Brak logo i nie są wyświetlane żadne ostrzeżenia:</span><span class="sxs-lookup"><span data-stu-id="ab1d9-142">No logo and no warnings are displayed:</span></span>

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- <span data-ttu-id="ab1d9-143">Kompiluje wszystkie C# pliki w bieżącym katalogu na *coś. xyz* (Biblioteka DLL):</span><span class="sxs-lookup"><span data-stu-id="ab1d9-143">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="ab1d9-144">Różnice między C# kompilatorem C++ a wyjściem kompilatora</span><span class="sxs-lookup"><span data-stu-id="ab1d9-144">Differences between C# compiler and C++ compiler output</span></span>
<span data-ttu-id="ab1d9-145">Nie ma plików obiektów ( *. obj*) utworzonych w wyniku wywołania C# kompilatora; pliki wyjściowe są tworzone bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-145">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="ab1d9-146">W związku z tym C# kompilator nie potrzebuje konsolidatora.</span><span class="sxs-lookup"><span data-stu-id="ab1d9-146">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab1d9-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab1d9-147">See also</span></span>

- [<span data-ttu-id="ab1d9-148">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="ab1d9-148">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="ab1d9-149">Opcje kompilatora C# w porządku alfabetycznym</span><span class="sxs-lookup"><span data-stu-id="ab1d9-149">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
- [<span data-ttu-id="ab1d9-150">Opcje kompilatora C# w rozbiciu na kategorie</span><span class="sxs-lookup"><span data-stu-id="ab1d9-150">C# Compiler Options Listed by Category</span></span>](./listed-by-category.md)
- [<span data-ttu-id="ab1d9-151">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="ab1d9-151">Main() and Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="ab1d9-152">Argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="ab1d9-152">Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [<span data-ttu-id="ab1d9-153">Instrukcje: Wyświetlanie argumentów wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="ab1d9-153">How to: Display Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="ab1d9-154">Main() — zwracane wartości</span><span class="sxs-lookup"><span data-stu-id="ab1d9-154">Main() Return Values</span></span>](../../programming-guide/main-and-command-args/main-return-values.md)
