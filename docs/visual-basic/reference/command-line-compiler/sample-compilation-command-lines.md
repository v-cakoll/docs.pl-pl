---
title: "Kompilacja przykładów — wiersze poleceń (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e168d40a22ca3737bee18f966df95988a2736a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="91aee-102">Kompilacja przykładów — wiersze poleceń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91aee-102">Sample Compilation Command Lines (Visual Basic)</span></span>
<span data-ttu-id="91aee-103">Alternatywą wobec kompilowanie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programów z poziomu [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], będzie można kompilować z poziomu wiersza polecenia, aby utworzyć pliki pliku wykonywalnego (.exe) lub biblioteki dołączanej (dynamicznie dll).</span><span class="sxs-lookup"><span data-stu-id="91aee-103">As an alternative to compiling [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programs from within [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>  
  
 <span data-ttu-id="91aee-104">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompletny zestaw opcje sterujące plików wejściowych i wyjściowych, zestawy i debugowania i opcje preprocesora obsługuje kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="91aee-104">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="91aee-105">Każda opcja jest dostępna w dwóch formach wymienne: `-``option` i `/``option`.</span><span class="sxs-lookup"><span data-stu-id="91aee-105">Each option is available in two interchangeable forms: `-``option` and `/``option`.</span></span> <span data-ttu-id="91aee-106">Ta dokumentacja zawiera tylko `/``option` formularza.</span><span class="sxs-lookup"><span data-stu-id="91aee-106">This documentation shows only the `/``option` form.</span></span>  
  
 <span data-ttu-id="91aee-107">W poniższej tabeli przedstawiono niektóre przykładowe wiersze poleceń, które można modyfikować na własny użytek.</span><span class="sxs-lookup"><span data-stu-id="91aee-107">The following table lists some sample command lines you can modify for your own use.</span></span>  
  
|<span data-ttu-id="91aee-108">Do</span><span class="sxs-lookup"><span data-stu-id="91aee-108">To</span></span>|<span data-ttu-id="91aee-109">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="91aee-109">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="91aee-110">Kompiluj File.vb i Utwórz File.exe</span><span class="sxs-lookup"><span data-stu-id="91aee-110">Compile File.vb and create File.exe</span></span>|`vbc /reference:Microsoft.VisualBasic.dll File.vb`|  
|<span data-ttu-id="91aee-111">Kompiluj File.vb i Utwórz File.dll</span><span class="sxs-lookup"><span data-stu-id="91aee-111">Compile File.vb and create File.dll</span></span>|`vbc /target:library File.vb`|  
|<span data-ttu-id="91aee-112">Kompiluj File.vb i Utwórz My.exe</span><span class="sxs-lookup"><span data-stu-id="91aee-112">Compile File.vb and create My.exe</span></span>|`vbc /out:My.exe File.vb`|  
|<span data-ttu-id="91aee-113">Kompiluj wszystkie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pliki w bieżącym katalogu z optymalizacji i `DEBUG` symbol zdefiniowany, tworzenie File2.exe</span><span class="sxs-lookup"><span data-stu-id="91aee-113">Compile all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc /define:DEBUG=1 /optimize /out:File2.exe *.vb`|  
|<span data-ttu-id="91aee-114">Kompiluj wszystkie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] plików w bieżącym katalogu, tworzenie wersji debugowania File2.dll bez wyświetlanie logo lub ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="91aee-114">Compile all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc /target:library /out:File2.dll /nowarn /nologo /debug *.vb`|  
|<span data-ttu-id="91aee-115">Kompiluj wszystkie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] plików w bieżącym katalogu do Something.dll</span><span class="sxs-lookup"><span data-stu-id="91aee-115">Compile all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory to Something.dll</span></span>|`vbc /target:library /out:Something.dll *.vb`|  
  
 <span data-ttu-id="91aee-116">W przypadku kompilowania kodu w wierszu polecenia, należy jawnie odwołać Microsoft [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] biblioteki wykonawczej za pośrednictwem `/reference` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="91aee-116">When compiling from the command line, you must explicitly reference the Microsoft [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] run-time library through the `/reference` compiler option.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="91aee-117">Podczas tworzenia projektu za pomocą środowiska IDE programu Visual Studio, można wyświetlić informacje o skojarzonych **vbc** z jego — opcje kompilatora w oknie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="91aee-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="91aee-118">Aby wyświetlić te informacje, otwórz [okno dialogowe Opcje, projekty i rozwiązania, kompilacji i uruchom](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), a następnie ustaw **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** do **normalny** lub wyższy poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="91aee-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="91aee-119">Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span><span class="sxs-lookup"><span data-stu-id="91aee-119">For more information, see [How to: View, Save, and Configure Build Log Files](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91aee-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91aee-120">See Also</span></span>  
 [<span data-ttu-id="91aee-121">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91aee-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="91aee-122">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="91aee-122">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
