---
title: Kompilacja wiersza polecenia z csc.exe
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: f692e66672b1804a309c6ac04c158af948a1b1ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789868"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="02cb4-102">Kompilacja wiersza polecenia z csc.exe</span><span class="sxs-lookup"><span data-stu-id="02cb4-102">Command-line build with csc.exe</span></span>

<span data-ttu-id="02cb4-103">Kompilator C# można wywołać, wpisując nazwę jego pliku wykonywalnego *(csc.exe)* w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="02cb4-103">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="02cb4-104">Jeśli używasz **wiersza polecenia dewelopera dla** programu Visual Studio, wszystkie niezbędne zmienne środowiskowe są ustawione dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="02cb4-104">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="02cb4-105">Aby uzyskać informacje na temat uzyskiwania dostępu do tego narzędzia, zobacz [temat Wiersz polecenia dewelopera dla programu Visual Studio.](../../../framework/tools/developer-command-prompt-for-vs.md)</span><span class="sxs-lookup"><span data-stu-id="02cb4-105">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span>

<span data-ttu-id="02cb4-106">Jeśli używasz standardowego okna wiersza polecenia, należy dostosować ścieżkę, zanim będzie można wywołać *csc.exe* z dowolnego podkatalogu na komputerze.</span><span class="sxs-lookup"><span data-stu-id="02cb4-106">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="02cb4-107">Należy również uruchomić *vsvars32.bat,* aby ustawić odpowiednie zmienne środowiskowe do obsługi kompilacji wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="02cb4-107">You also must run *vsvars32.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="02cb4-108">Aby uzyskać więcej informacji na temat *vsvars32.bat*, w tym instrukcje dotyczące znajdowania i uruchamiania, zobacz [Jak ustawić zmienne środowiskowe dla wiersza polecenia programu Visual Studio](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="02cb4-108">For more information about *vsvars32.bat*, including instructions for how to find and run it, see [How to set environment variables for the Visual Studio Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="02cb4-109">Jeśli pracujesz na komputerze, który ma tylko zestaw Windows Software Development Kit (SDK), możesz użyć kompilatora C# w **wierszu polecenia zestawu SDK**, który można otworzyć z menu **zestawu Microsoft .NET Framework SDK.**</span><span class="sxs-lookup"><span data-stu-id="02cb4-109">If you're working on a computer that has only the Windows Software Development Kit (SDK), you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="02cb4-110">Można również użyć MSBuild do tworzenia programów C# programowo.</span><span class="sxs-lookup"><span data-stu-id="02cb4-110">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="02cb4-111">Aby uzyskać więcej informacji, zobacz [MSBuild](/visualstudio/msbuild/msbuild).</span><span class="sxs-lookup"><span data-stu-id="02cb4-111">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="02cb4-112">Plik wykonywalny *programu csc.exe* zwykle znajduje\\się w*\<folderze microsoft.NET\Framework version>* w katalogu systemu *Windows.*</span><span class="sxs-lookup"><span data-stu-id="02cb4-112">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="02cb4-113">Jego lokalizacja może się różnić w zależności od dokładnej konfiguracji określonego komputera.</span><span class="sxs-lookup"><span data-stu-id="02cb4-113">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="02cb4-114">Jeśli na komputerze jest zainstalowana więcej niż jedna wersja programu .NET Framework, znajdziesz wiele wersji tego pliku.</span><span class="sxs-lookup"><span data-stu-id="02cb4-114">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="02cb4-115">Aby uzyskać więcej informacji na temat takich instalacji, zobacz [Jak: określić, które wersje programu .NET Framework są zainstalowane.](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md)</span><span class="sxs-lookup"><span data-stu-id="02cb4-115">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
> <span data-ttu-id="02cb4-116">Podczas tworzenia projektu przy użyciu programu Visual Studio IDE, można wyświetlić polecenie **csc** i skojarzone z nim opcje kompilatora w oknie **Wyjście.**</span><span class="sxs-lookup"><span data-stu-id="02cb4-116">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="02cb4-117">Aby wyświetlić te informacje, postępuj zgodnie z instrukcjami w [jak: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji,](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) aby zmienić poziom szczegółowości danych dziennika na **Normalny** lub **Szczegółowy**.</span><span class="sxs-lookup"><span data-stu-id="02cb4-117">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="02cb4-118">Po odbudowie projektu, wyszukaj w oknie **Wyjście** dla **csc,** aby znaleźć wywołanie kompilatora C#.</span><span class="sxs-lookup"><span data-stu-id="02cb4-118">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="02cb4-119">**W tym temacie**</span><span class="sxs-lookup"><span data-stu-id="02cb4-119">**In this topic**</span></span>

- [<span data-ttu-id="02cb4-120">Reguły składni wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="02cb4-120">Rules for command-line syntax</span></span>](#rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="02cb4-121">Przykładowe wiersze polecenia</span><span class="sxs-lookup"><span data-stu-id="02cb4-121">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="02cb4-122">Różnice między kompilatorem C# a wyjściem kompilatora C++</span><span class="sxs-lookup"><span data-stu-id="02cb4-122">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="02cb4-123">Reguły składni wiersza polecenia kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="02cb4-123">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="02cb4-124">Kompilator Języka C# używa następujących reguł, gdy interpretuje argumenty podane w wierszu polecenia systemu operacyjnego:</span><span class="sxs-lookup"><span data-stu-id="02cb4-124">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="02cb4-125">Argumenty są rozdzielane przez biały znak, który jest spacjaiem lub tabulatorem.</span><span class="sxs-lookup"><span data-stu-id="02cb4-125">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="02cb4-126">Znak karetki (^) nie jest rozpoznawany jako znak ucieczki lub ogranicznik.</span><span class="sxs-lookup"><span data-stu-id="02cb4-126">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="02cb4-127">Znak jest obsługiwany przez analizator wiersza polecenia w systemie operacyjnym, `argv` zanim zostanie przekazany do tablicy w programie.</span><span class="sxs-lookup"><span data-stu-id="02cb4-127">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="02cb4-128">Ciąg ujęty w podwójne cudzysłowy ("ciąg") jest interpretowany jako pojedynczy argument, niezależnie od odstępu, który jest zawarty w środku.</span><span class="sxs-lookup"><span data-stu-id="02cb4-128">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="02cb4-129">Cytowany ciąg może być osadzony w argumencie.</span><span class="sxs-lookup"><span data-stu-id="02cb4-129">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="02cb4-130">Podwójny cudzysłów poprzedzony ukośnikiem odwrotnym (\\") jest interpretowany jako znak znaku znaku cudzysłowu dwurzędowego (dw.).</span><span class="sxs-lookup"><span data-stu-id="02cb4-130">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="02cb4-131">Ukośniki wsteczne są interpretowane dosłownie, chyba że bezpośrednio poprzedzają podwójny cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="02cb4-131">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="02cb4-132">Jeśli po parzystej liczbie ukośników wstecznych następuje `argv` podwójny cudzysłów, jeden ukośnik odwrotny jest umieszczany w tablicy dla każdej pary ukośników odwrotnych, a podwójny cudzysłów jest interpretowany jako ogranicznik ciągu.</span><span class="sxs-lookup"><span data-stu-id="02cb4-132">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="02cb4-133">Jeśli po nieparzystej liczbie ukośni ków występuje podwójny `argv` cudzysłów, jeden ukośnik odwrotny jest umieszczany w tablicy dla każdej pary ukośników odwrotnych, a podwójny cudzysłów jest "unikany" przez pozostały ukośnik odwrotny.</span><span class="sxs-lookup"><span data-stu-id="02cb4-133">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="02cb4-134">Powoduje to dosłowny podwójny cudzysłów `argv`(") dododania w pliku .</span><span class="sxs-lookup"><span data-stu-id="02cb4-134">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="02cb4-135">Przykładowe wiersze polecenia dla kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="02cb4-135">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="02cb4-136">Kompiluje *File.cs* produkując *file.exe:*</span><span class="sxs-lookup"><span data-stu-id="02cb4-136">Compiles *File.cs* producing *File.exe*:</span></span>

  ```console
  csc File.cs
  ```

- <span data-ttu-id="02cb4-137">Kompiluje *File.cs* produkując *plik File.dll:*</span><span class="sxs-lookup"><span data-stu-id="02cb4-137">Compiles *File.cs* producing *File.dll*:</span></span>

  ```console
  csc -target:library File.cs
  ```

- <span data-ttu-id="02cb4-138">Kompiluje *File.cs* i tworzy *My.exe*:</span><span class="sxs-lookup"><span data-stu-id="02cb4-138">Compiles *File.cs* and creates *My.exe*:</span></span>

  ```console
  csc -out:My.exe File.cs
  ```

- <span data-ttu-id="02cb4-139">Kompiluje wszystkie pliki C# w bieżącym katalogu z włączonymi optymalizacjami i definiuje symbol DEBUG.</span><span class="sxs-lookup"><span data-stu-id="02cb4-139">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="02cb4-140">Wyjście m. *File2.exe*:</span><span class="sxs-lookup"><span data-stu-id="02cb4-140">The output is *File2.exe*:</span></span>

  ```console
  csc -define:DEBUG -optimize -out:File2.exe *.cs
  ```

- <span data-ttu-id="02cb4-141">Kompiluje wszystkie pliki C# w bieżącym katalogu, tworząc wersję debugowania *pliku File2.dll*.</span><span class="sxs-lookup"><span data-stu-id="02cb4-141">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="02cb4-142">Nie ma logo i nie są wyświetlane ostrzeżenia:</span><span class="sxs-lookup"><span data-stu-id="02cb4-142">No logo and no warnings are displayed:</span></span>

  ```console
  csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
  ```

- <span data-ttu-id="02cb4-143">Kompiluje wszystkie pliki C# w bieżącym katalogu do *Something.xyz* (DLL):</span><span class="sxs-lookup"><span data-stu-id="02cb4-143">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

  ```console
  csc -target:library -out:Something.xyz *.cs
  ```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="02cb4-144">Różnice między kompilatorem C# a wyjściem kompilatora C++</span><span class="sxs-lookup"><span data-stu-id="02cb4-144">Differences between C# compiler and C++ compiler output</span></span>

<span data-ttu-id="02cb4-145">Nie ma żadnych plików obiektu (*obj*) utworzonych w wyniku wywołania kompilatora C#; pliki wyjściowe są tworzone bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="02cb4-145">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="02cb4-146">W wyniku tego kompilator Języka C# nie wymaga konsolidatora.</span><span class="sxs-lookup"><span data-stu-id="02cb4-146">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="02cb4-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02cb4-147">See also</span></span>

- [<span data-ttu-id="02cb4-148">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="02cb4-148">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="02cb4-149">Opcje kompilatora C# w porządku alfabetycznym</span><span class="sxs-lookup"><span data-stu-id="02cb4-149">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
- [<span data-ttu-id="02cb4-150">Opcje kompilatora C# w rozbiciu na kategorie</span><span class="sxs-lookup"><span data-stu-id="02cb4-150">C# Compiler Options Listed by Category</span></span>](./listed-by-category.md)
- [<span data-ttu-id="02cb4-151">Main() i argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="02cb4-151">Main() and Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="02cb4-152">Argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="02cb4-152">Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [<span data-ttu-id="02cb4-153">Wyświetlanie argumentów wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="02cb4-153">How to display command-line arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="02cb4-154">Main() — zwracane wartości</span><span class="sxs-lookup"><span data-stu-id="02cb4-154">Main() Return Values</span></span>](../../programming-guide/main-and-command-args/main-return-values.md)
