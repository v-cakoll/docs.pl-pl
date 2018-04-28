---
title: Kompilacja przykładów — wiersze poleceń (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b61ef6facf33fa043cad28a78405a19308a9864f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="3e85a-102">Polecenie kompilacja przykładów — wiersze (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e85a-102">Sample compilation command lines (Visual Basic)</span></span>
<span data-ttu-id="3e85a-103">Alternatywą wobec kompilowanie programów Visual Basic z poziomu programu Visual Studio można kompilować z poziomu wiersza polecenia, aby utworzyć pliki pliku wykonywalnego (.exe) lub biblioteki dołączanej (dynamicznie dll).</span><span class="sxs-lookup"><span data-stu-id="3e85a-103">As an alternative to compiling Visual Basic programs from within Visual Studio, you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>  
  
 <span data-ttu-id="3e85a-104">Kompilator wiersza polecenia programu Visual Basic obsługuje pełny zestaw opcji kontroli danych wejściowych i wyjściowych plików, zestawy i debugowania i opcje preprocesora.</span><span class="sxs-lookup"><span data-stu-id="3e85a-104">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="3e85a-105">Każda opcja jest dostępna w dwóch formach wymienne: `-option` i `/option`.</span><span class="sxs-lookup"><span data-stu-id="3e85a-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="3e85a-106">Ta dokumentacja zawiera tylko `-option` formularza.</span><span class="sxs-lookup"><span data-stu-id="3e85a-106">This documentation shows only the `-option` form.</span></span>  
  
 <span data-ttu-id="3e85a-107">W poniższej tabeli przedstawiono niektóre przykładowe wiersze poleceń, które można modyfikować na własny użytek.</span><span class="sxs-lookup"><span data-stu-id="3e85a-107">The following table lists some sample command lines you can modify for your own use.</span></span>  
  
|<span data-ttu-id="3e85a-108">Do</span><span class="sxs-lookup"><span data-stu-id="3e85a-108">To</span></span>|<span data-ttu-id="3e85a-109">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="3e85a-109">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="3e85a-110">Kompiluj File.vb i Utwórz File.exe</span><span class="sxs-lookup"><span data-stu-id="3e85a-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|<span data-ttu-id="3e85a-111">Kompiluj File.vb i Utwórz File.dll</span><span class="sxs-lookup"><span data-stu-id="3e85a-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|  
|<span data-ttu-id="3e85a-112">Kompiluj File.vb i Utwórz My.exe</span><span class="sxs-lookup"><span data-stu-id="3e85a-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|  
|<span data-ttu-id="3e85a-113">Kompilowanie File.vb i tworzyć biblioteki oraz zestawu odwołania o nazwie File.dll</span><span class="sxs-lookup"><span data-stu-id="3e85a-113">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="3e85a-114">Kompiluj wszystkie pliki Visual Basic w bieżącym katalogu z optymalizacji na i `DEBUG` symbol zdefiniowany, tworzenie File2.exe</span><span class="sxs-lookup"><span data-stu-id="3e85a-114">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|<span data-ttu-id="3e85a-115">Kompiluj wszystkie pliki Visual Basic w bieżącym katalogu, tworzenie wersji debugowania File2.dll bez wyświetlanie logo lub ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="3e85a-115">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|<span data-ttu-id="3e85a-116">Kompiluj wszystkie pliki Visual Basic w bieżącym katalogu do Something.dll</span><span class="sxs-lookup"><span data-stu-id="3e85a-116">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  <span data-ttu-id="3e85a-117">Podczas tworzenia projektu za pomocą środowiska IDE programu Visual Studio, można wyświetlić informacje o skojarzonych **vbc** z jego — opcje kompilatora w oknie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3e85a-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="3e85a-118">Aby wyświetlić te informacje, otwórz [okno dialogowe Opcje, projekty i rozwiązania, kompilacji i uruchom](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), a następnie ustaw **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** do **normalny** lub wyższy poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="3e85a-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="3e85a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e85a-119">See Also</span></span>  
 [<span data-ttu-id="3e85a-120">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3e85a-120">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="3e85a-121">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="3e85a-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
