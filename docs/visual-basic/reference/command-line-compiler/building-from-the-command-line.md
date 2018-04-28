---
title: Tworzenie z wiersza polecenia (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers [Visual Basic], invoking from command line
- command-line builds
- compiling source code
- command-line compilers [Visual Basic], Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9a9dee47f06e4f7d9fc8d237376df7707130921d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="e98ad-102">Tworzenie z wiersza polecenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e98ad-102">Building from the Command Line (Visual Basic)</span></span>
<span data-ttu-id="e98ad-103">Projekt Visual Basic składa się z jednego lub więcej plików oddzielne źródło.</span><span class="sxs-lookup"><span data-stu-id="e98ad-103">A Visual Basic project is made up of one or more separate source files.</span></span> <span data-ttu-id="e98ad-104">W trakcie znany jako kompilacji te pliki zostaną połączone razem w jednym pakiecie — pojedynczy plik wykonywalny, który może działać jako aplikacja.</span><span class="sxs-lookup"><span data-stu-id="e98ad-104">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>  
  
 <span data-ttu-id="e98ad-105">Visual Basic zapewnia kompilatora wiersza polecenia zamiast kompilowanie programów w programie Visual Studio zintegrowane środowisko programistyczne (IDE).</span><span class="sxs-lookup"><span data-stu-id="e98ad-105">Visual Basic provides a command-line compiler as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="e98ad-106">Kompilator wiersza polecenia jest przeznaczony do sytuacji, w których nie wymagają pełnego zestawu funkcji w środowisku IDE — na przykład po są przy użyciu lub zapisywania w przypadku komputerów z ograniczoną systemu pamięć lub miejsce do magazynowania.</span><span class="sxs-lookup"><span data-stu-id="e98ad-106">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>  
  
  <span data-ttu-id="e98ad-107">Aby skompilować plików źródłowych z wewnątrz środowiska IDE programu Visual Studio, wybierz **kompilacji** polecenie **kompilacji** menu.</span><span class="sxs-lookup"><span data-stu-id="e98ad-107">To compile source files from within the Visual Studio IDE, choose the **Build** command from the **Build** menu.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="e98ad-108">Podczas tworzenia plików projektu za pomocą środowiska IDE programu Visual Studio, można wyświetlić informacje o skojarzonych **vbc** polecenia i jego przełączników w oknie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="e98ad-108">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="e98ad-109">Aby wyświetlić te informacje, otwórz [okno dialogowe Opcje, projekty i rozwiązania, kompilacji i uruchom](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), a następnie ustaw **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** do **normalny** lub wyższy poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="e98ad-109">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="e98ad-110">Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span><span class="sxs-lookup"><span data-stu-id="e98ad-110">For more information, see [How to: View, Save, and Configure Build Log Files](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span></span>  
  
 <span data-ttu-id="e98ad-111">Pliki projektu (.vbproj) w wierszu polecenia można skompilować przy użyciu programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="e98ad-111">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="e98ad-112">Aby uzyskać więcej informacji, zobacz [dotyczące wiersza polecenia](/visualstudio/msbuild/msbuild-command-line-reference) i [wskazówki: przy użyciu programu MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span><span class="sxs-lookup"><span data-stu-id="e98ad-112">For more information, see [Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e98ad-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e98ad-113">In This Section</span></span>  
 [<span data-ttu-id="e98ad-114">Instrukcje: wywoływanie kompilatora z wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="e98ad-114">How to: Invoke the Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 <span data-ttu-id="e98ad-115">Opisuje sposób wywoływanie kompilatora wiersza polecenia w wierszu polecenia systemu MS-DOS lub z określonego podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="e98ad-115">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>  
  
 [<span data-ttu-id="e98ad-116">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="e98ad-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 <span data-ttu-id="e98ad-117">Lista przykładów — wiersze poleceń, które można modyfikować na własny użytek.</span><span class="sxs-lookup"><span data-stu-id="e98ad-117">Provides a list of sample command lines that you can modify for your own use.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e98ad-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="e98ad-118">Related Sections</span></span>  
 [<span data-ttu-id="e98ad-119">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e98ad-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 <span data-ttu-id="e98ad-120">Zawiera listę opcji kompilatora, uporządkowane alfabetycznie lub według celu.</span><span class="sxs-lookup"><span data-stu-id="e98ad-120">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>  
  
 [<span data-ttu-id="e98ad-121">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="e98ad-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="e98ad-122">Opisuje sposób kompilowania poszczególnych sekcji kodu.</span><span class="sxs-lookup"><span data-stu-id="e98ad-122">Describes how to compile particular sections of code.</span></span>  
  
 [<span data-ttu-id="e98ad-123">Kompilowanie i czyszczenie projektów i rozwiązań w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e98ad-123">Building and Cleaning Projects and Solutions in Visual Studio</span></span>](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="e98ad-124">Opisuje sposób organizowania co mają być uwzględnieni w różnych wersjach, wybierz polecenie Właściwości projektu i upewnij się, że projekty kompilacji w odpowiedniej kolejności.</span><span class="sxs-lookup"><span data-stu-id="e98ad-124">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
