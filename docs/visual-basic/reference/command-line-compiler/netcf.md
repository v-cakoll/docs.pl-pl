---
title: -netcf
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82a0adc9e821df3a789cf19e798d4bad9e9a69e3
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-netcf"></a><span data-ttu-id="939b4-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="939b4-102">-netcf</span></span>
<span data-ttu-id="939b4-103">Ustawia kompilatora do docelowego [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="939b4-103">Sets the compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="939b4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="939b4-104">Syntax</span></span>  
  
```  
-netcf  
```  
  
## <a name="remarks"></a><span data-ttu-id="939b4-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="939b4-105">Remarks</span></span>  
 <span data-ttu-id="939b4-106">`-netcf` Opcji powoduje, że [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora do docelowego [!INCLUDE[Compact](~/includes/compact-md.md)] zamiast pełnego [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="939b4-106">The `-netcf` option causes the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)] rather than the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="939b4-107">Funkcje języka, które są dostępne tylko w pełni [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="939b4-107">Language functionality that is present only in the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] is disabled.</span></span>  
  
 <span data-ttu-id="939b4-108">`-netcf` Opcja jest przeznaczona do użycia z [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span><span class="sxs-lookup"><span data-stu-id="939b4-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="939b4-109">Funkcje języka wyłączone przez `-netcf` są takie same funkcje języka nie znajduje się w plikach z `-sdkpath`.</span><span class="sxs-lookup"><span data-stu-id="939b4-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="939b4-110">`-netcf` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="939b4-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="939b4-111">`-netcf` Opcja jest ustawiona, gdy [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] urządzenia projektu jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="939b4-111">The `-netcf` option is set when a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] device project is loaded.</span></span>  
  
 <span data-ttu-id="939b4-112">`-netcf` Opcja zmiany następujące funkcje języka:</span><span class="sxs-lookup"><span data-stu-id="939b4-112">The `-netcf` option changes the following language features:</span></span>  
  
-   <span data-ttu-id="939b4-113">[Zakończenia \<— słowo kluczowe > instrukcji](../../../visual-basic/language-reference/statements/end-keyword-statement.md) — słowo kluczowe, w którym kończy wykonywanie programu, jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="939b4-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="939b4-114">Następujący program kompiluje i uruchamia bez `-netcf` , ale nie powiedzie się w czasie kompilacji z `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="939b4-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   <span data-ttu-id="939b4-115">Późne wiązanie w wszystkich formularzy jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="939b4-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="939b4-116">Błędy kompilacji są generowane, gdy wystąpią rozpoznanym scenariusze późne powiązania.</span><span class="sxs-lookup"><span data-stu-id="939b4-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="939b4-117">Następujący program kompiluje i uruchamia bez `-netcf` , ale nie powiedzie się w czasie kompilacji z `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="939b4-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   <span data-ttu-id="939b4-118">[Automatycznie](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), i [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) Modyfikatory są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="939b4-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="939b4-119">Składnia [instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) instrukcji również są modyfikowane w celu `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span><span class="sxs-lookup"><span data-stu-id="939b4-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="939b4-120">Poniższy kod ilustruje efekt `-netcf` w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="939b4-120">The following code shows the effect of `-netcf` on a compilation.</span></span>  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   <span data-ttu-id="939b4-121">Za pomocą słów kluczowych Visual Basic 6.0, które zostały usunięte z [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] generuje inny błąd podczas `-netcf` jest używany.</span><span class="sxs-lookup"><span data-stu-id="939b4-121">Using Visual Basic 6.0 keywords that were removed from [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="939b4-122">Ma to wpływ na komunikaty o błędach dla następujących słów kluczowych:</span><span class="sxs-lookup"><span data-stu-id="939b4-122">This affects the error messages for the following keywords:</span></span>  
  
    -   `Open`  
  
    -   `Close`  
  
    -   `Put`  
  
    -   `Print`  
  
    -   `Write`  
  
    -   `Input`  
  
    -   `Lock`  
  
    -   `Unlock`  
  
    -   `Seek`  
  
    -   `Width`  
  
    -   `Name`  
  
    -   `FreeFile`  
  
    -   `EOF`  
  
    -   `Loc`  
  
    -   `LOF`  
  
    -   `Line`  
  
## <a name="example"></a><span data-ttu-id="939b4-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="939b4-123">Example</span></span>  
 <span data-ttu-id="939b4-124">Poniższy kod kompiluje `Myfile.vb` z [!INCLUDE[Compact](~/includes/compact-md.md)], przy użyciu wersji biblioteki mscorlib.dll i pliku Microsoft.VisualBasic.dll znajdujące się w katalogu instalacji domyślnej z [!INCLUDE[Compact](~/includes/compact-md.md)] na dysku C.</span><span class="sxs-lookup"><span data-stu-id="939b4-124">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="939b4-125">Zazwyczaj należy użyć najnowszej wersji [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="939b4-125">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```console  
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="939b4-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="939b4-126">See Also</span></span>  
 [<span data-ttu-id="939b4-127">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="939b4-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="939b4-128">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="939b4-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="939b4-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="939b4-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
