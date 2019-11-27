---
title: Przykłady kompilacji — wiersze poleceń
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
ms.openlocfilehash: 27a20a5a3525353ffbced729b8ac9c98b3e48fc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350854"
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="23ddd-102">Przykładowe wiersze poleceń kompilacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23ddd-102">Sample compilation command lines (Visual Basic)</span></span>

<span data-ttu-id="23ddd-103">Jako alternatywę do kompilowania Visual Basic programów z poziomu programu Visual Studio można kompilować z wiersza polecenia, aby tworzyć pliki wykonywalne (exe) lub pliki bibliotek dołączanych dynamicznie (. dll).</span><span class="sxs-lookup"><span data-stu-id="23ddd-103">As an alternative to compiling Visual Basic programs from within Visual Studio, you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>

<span data-ttu-id="23ddd-104">Kompilator wiersza polecenia Visual Basic obsługuje kompletny zestaw opcji kontrolujących pliki wejściowe i wyjściowe, zestawy oraz opcje debugowania i preprocesora.</span><span class="sxs-lookup"><span data-stu-id="23ddd-104">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="23ddd-105">Każda opcja jest dostępna w dwóch niezmienionych formularzach: `-option` i `/option`.</span><span class="sxs-lookup"><span data-stu-id="23ddd-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="23ddd-106">Ta dokumentacja zawiera tylko formularz `-option`.</span><span class="sxs-lookup"><span data-stu-id="23ddd-106">This documentation shows only the `-option` form.</span></span>

<span data-ttu-id="23ddd-107">Poniższa tabela zawiera listę przykładowych wierszy poleceń, które można modyfikować do własnych potrzeb.</span><span class="sxs-lookup"><span data-stu-id="23ddd-107">The following table lists some sample command lines you can modify for your own use.</span></span>

|<span data-ttu-id="23ddd-108">Do</span><span class="sxs-lookup"><span data-stu-id="23ddd-108">To</span></span>|<span data-ttu-id="23ddd-109">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="23ddd-109">Use</span></span>|
|--------|---------|
|<span data-ttu-id="23ddd-110">Kompiluj plik. vb i Utwórz plik. exe</span><span class="sxs-lookup"><span data-stu-id="23ddd-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|
|<span data-ttu-id="23ddd-111">Kompiluj plik. vb i Utwórz plik. dll</span><span class="sxs-lookup"><span data-stu-id="23ddd-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|
|<span data-ttu-id="23ddd-112">Kompiluj plik. vb i Utwórz my. exe</span><span class="sxs-lookup"><span data-stu-id="23ddd-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|
|<span data-ttu-id="23ddd-113">Kompiluj plik. vb i Utwórz bibliotekę i zestaw odwołań o nazwie File. dll</span><span class="sxs-lookup"><span data-stu-id="23ddd-113">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="23ddd-114">Kompiluj wszystkie pliki Visual Basic w bieżącym katalogu z optymalizacjami na i zdefiniowanym symbolem `DEBUG`, wytwarzając plik2. exe</span><span class="sxs-lookup"><span data-stu-id="23ddd-114">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|
|<span data-ttu-id="23ddd-115">Kompiluj wszystkie pliki Visual Basic w bieżącym katalogu, generując wersję debugową plik2. dll bez wyświetlania logo lub ostrzeżeń</span><span class="sxs-lookup"><span data-stu-id="23ddd-115">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|
|<span data-ttu-id="23ddd-116">Kompiluj wszystkie pliki Visual Basic w bieżącym katalogu na coś. dll</span><span class="sxs-lookup"><span data-stu-id="23ddd-116">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|

> [!TIP]
> <span data-ttu-id="23ddd-117">Podczas kompilowania projektu przy użyciu programu Visual Studio IDE można wyświetlić informacje o skojarzonym poleceniu **VBC** z jego opcjami kompilatora w oknie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="23ddd-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="23ddd-118">Aby wyświetlić te informacje, Otwórz okno [dialogowe Opcje, projekty i rozwiązania, skompiluj i uruchom](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), a następnie ustaw poziom szczegółowości **danych wyjściowych kompilacji projektu programu MSBuild** na **normalny** lub wyższy.</span><span class="sxs-lookup"><span data-stu-id="23ddd-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>

## <a name="see-also"></a><span data-ttu-id="23ddd-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23ddd-119">See also</span></span>

- [<span data-ttu-id="23ddd-120">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="23ddd-120">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="23ddd-121">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="23ddd-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
