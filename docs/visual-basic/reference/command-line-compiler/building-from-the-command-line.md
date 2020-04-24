---
title: Tworzenie z wiersza polecenia
ms.date: 07/20/2015
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
ms.openlocfilehash: c7219c0497bb87f0cc44f27229eaf25f9b3eebce
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344791"
---
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="fe174-102">Tworzenie z wiersza polecenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe174-102">Building from the Command Line (Visual Basic)</span></span>

<span data-ttu-id="fe174-103">Projekt Visual Basic składa się z co najmniej jednego oddzielnego pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="fe174-103">A Visual Basic project is made up of one or more separate source files.</span></span> <span data-ttu-id="fe174-104">Podczas procesu znanego jako kompilacja te pliki są łączone w jeden pakiet — pojedynczy plik wykonywalny, który może być uruchamiany jako aplikacja.</span><span class="sxs-lookup"><span data-stu-id="fe174-104">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>

<span data-ttu-id="fe174-105">Visual Basic udostępnia kompilator wiersza polecenia jako alternatywę do kompilowania programów z poziomu zintegrowanego środowiska programistycznego (IDE) programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fe174-105">Visual Basic provides a command-line compiler as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="fe174-106">Kompilator wiersza polecenia jest przeznaczony do sytuacji, w których nie jest wymagany pełny zestaw funkcji w środowisku IDE — na przykład podczas korzystania z programu lub zapisywania na komputerach z ograniczoną ilością pamięci systemowej lub miejscem do magazynowania.</span><span class="sxs-lookup"><span data-stu-id="fe174-106">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>

<span data-ttu-id="fe174-107">Aby kompilować pliki źródłowe z poziomu środowiska IDE programu Visual Studio, wybierz polecenie **Kompiluj** z menu **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="fe174-107">To compile source files from within the Visual Studio IDE, choose the **Build** command from the **Build** menu.</span></span>

> [!TIP]
> <span data-ttu-id="fe174-108">Podczas kompilowania plików projektu przy użyciu programu Visual Studio IDE można wyświetlić informacje o skojarzonym poleceniu **VBC** i jego przełącznikach w oknie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="fe174-108">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="fe174-109">Aby wyświetlić te informacje, Otwórz okno [dialogowe Opcje, projekty i rozwiązania, skompiluj i uruchom](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), a następnie ustaw poziom szczegółowości **danych wyjściowych kompilacji projektu programu MSBuild** na **normalny** lub wyższy.</span><span class="sxs-lookup"><span data-stu-id="fe174-109">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="fe174-110">Aby uzyskać więcej informacji, zobacz [jak: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).</span><span class="sxs-lookup"><span data-stu-id="fe174-110">For more information, see [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).</span></span>

<span data-ttu-id="fe174-111">Pliki projektu (. vbproj) można kompilować w wierszu polecenia przy użyciu programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="fe174-111">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="fe174-112">Aby uzyskać więcej informacji, zobacz informacje [dotyczące wiersza polecenia](/visualstudio/msbuild/msbuild-command-line-reference) i [Przewodnik: korzystanie z programu MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span><span class="sxs-lookup"><span data-stu-id="fe174-112">For more information, see [Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="fe174-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fe174-113">In This Section</span></span>

<span data-ttu-id="fe174-114">[Instrukcje: wywoływanie kompilatora wiersza polecenia](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) </span><span class="sxs-lookup"><span data-stu-id="fe174-114">[How to: Invoke the Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) </span></span>\
<span data-ttu-id="fe174-115">Opisuje sposób wywoływania kompilatora wiersza polecenia w wierszu systemu MS-DOS lub z określonego podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="fe174-115">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>

<span data-ttu-id="fe174-116">[Przykładowe wiersze poleceń kompilacji](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="fe174-116">[Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>\
<span data-ttu-id="fe174-117">Zawiera listę przykładowych wierszy poleceń, które można modyfikować do własnych potrzeb.</span><span class="sxs-lookup"><span data-stu-id="fe174-117">Provides a list of sample command lines that you can modify for your own use.</span></span>

## <a name="related-sections"></a><span data-ttu-id="fe174-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="fe174-118">Related Sections</span></span>

<span data-ttu-id="fe174-119">[Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="fe174-119">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>\
<span data-ttu-id="fe174-120">Zawiera listy opcji kompilatora, zorganizowane w porządku alfabetycznym lub według przeznaczenie.</span><span class="sxs-lookup"><span data-stu-id="fe174-120">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>

<span data-ttu-id="fe174-121">[Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span><span class="sxs-lookup"><span data-stu-id="fe174-121">[Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span></span>\
<span data-ttu-id="fe174-122">Opisuje sposób kompilowania określonych sekcji kodu.</span><span class="sxs-lookup"><span data-stu-id="fe174-122">Describes how to compile particular sections of code.</span></span>

<span data-ttu-id="fe174-123">[Kompilowanie i czyszczenie projektów i rozwiązań w programie Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) </span><span class="sxs-lookup"><span data-stu-id="fe174-123">[Building and Cleaning Projects and Solutions in Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) </span></span>\
<span data-ttu-id="fe174-124">W tym artykule opisano sposób organizowania, co zostanie uwzględnione w różnych kompilacjach, wybrać właściwości projektu i upewnić się, że projekty kompilują się w poprawnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="fe174-124">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
