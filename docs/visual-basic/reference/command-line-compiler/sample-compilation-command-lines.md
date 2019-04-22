---
title: Kompilacja przykładów — wiersze poleceń (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
ms.openlocfilehash: 0771ed41d6c58ce7cc98435b405f5819e45393db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824310"
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="30f7b-102">Przykładowe wiersze poleceń kompilacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30f7b-102">Sample compilation command lines (Visual Basic)</span></span>
<span data-ttu-id="30f7b-103">Jako alternatywę do kompilowania programów Visual Basic z poziomu programu Visual Studio można kompilować z poziomu wiersza polecenia, aby wygenerować pliki wykonywalne (.exe) lub biblioteka dołączana dynamicznie (dll).</span><span class="sxs-lookup"><span data-stu-id="30f7b-103">As an alternative to compiling Visual Basic programs from within Visual Studio, you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>  
  
 <span data-ttu-id="30f7b-104">Kompilator wiersza polecenia programu Visual Basic obsługuje kompletny zestaw opcji, które kontroli danych wejściowych i wyjściowych plików, zestawów oraz debugowania i opcje preprocesora.</span><span class="sxs-lookup"><span data-stu-id="30f7b-104">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="30f7b-105">Każda opcja jest dostępna w dwóch formach wymienne: `-option` i `/option`.</span><span class="sxs-lookup"><span data-stu-id="30f7b-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="30f7b-106">Ta dokumentacja zawiera tylko `-option` formularza.</span><span class="sxs-lookup"><span data-stu-id="30f7b-106">This documentation shows only the `-option` form.</span></span>  
  
 <span data-ttu-id="30f7b-107">W poniższej tabeli wymieniono niektóre przykładowe wiersze poleceń, które można modyfikować na własny użytek.</span><span class="sxs-lookup"><span data-stu-id="30f7b-107">The following table lists some sample command lines you can modify for your own use.</span></span>  
  
|<span data-ttu-id="30f7b-108">Zadanie</span><span class="sxs-lookup"><span data-stu-id="30f7b-108">To</span></span>|<span data-ttu-id="30f7b-109">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="30f7b-109">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="30f7b-110">Skompilować File.vb i utworzyć File.exe</span><span class="sxs-lookup"><span data-stu-id="30f7b-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|<span data-ttu-id="30f7b-111">Skompilować File.vb i utworzyć File.dll</span><span class="sxs-lookup"><span data-stu-id="30f7b-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|  
|<span data-ttu-id="30f7b-112">Skompilować File.vb i utworzyć My.exe</span><span class="sxs-lookup"><span data-stu-id="30f7b-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|  
|<span data-ttu-id="30f7b-113">Skompilować File.vb i tworzyć biblioteki oraz o nazwie File.dll zestawu odwołania</span><span class="sxs-lookup"><span data-stu-id="30f7b-113">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="30f7b-114">Kompiluj wszystkie pliki języka Visual Basic w bieżącym katalogu, z optymalizacjami na i `DEBUG` symbol zdefiniowany, tworzenie File2.exe</span><span class="sxs-lookup"><span data-stu-id="30f7b-114">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|<span data-ttu-id="30f7b-115">Kompiluj wszystkie pliki języka Visual Basic w bieżącym katalogu, tworzenie wersji debugowania File2.dll bez wyświetlania logo lub ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="30f7b-115">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|<span data-ttu-id="30f7b-116">Kompiluj wszystkie pliki języka Visual Basic w bieżącym katalogu Something.dll</span><span class="sxs-lookup"><span data-stu-id="30f7b-116">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  <span data-ttu-id="30f7b-117">Gdy tworzysz projekt za pomocą środowiska IDE programu Visual Studio można wyświetlić informacje o skojarzonego **vbc** swoich opcje kompilatora w oknie danych wyjściowych polecenia.</span><span class="sxs-lookup"><span data-stu-id="30f7b-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="30f7b-118">Aby wyświetlić te informacje, otwórz [okno dialogowe Opcje, projekty i rozwiązania, kompilacji i uruchomienia](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), a następnie ustaw **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** do **normalny** lub wyższym poziomie szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="30f7b-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="30f7b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30f7b-119">See also</span></span>

- [<span data-ttu-id="30f7b-120">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30f7b-120">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="30f7b-121">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="30f7b-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
