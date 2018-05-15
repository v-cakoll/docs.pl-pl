---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 2fefdf81ab25d2e109f265f0c895a3415ad5673d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-addmodule"></a><span data-ttu-id="fda6e-102">-addmodule</span><span class="sxs-lookup"><span data-stu-id="fda6e-102">-addmodule</span></span>
<span data-ttu-id="fda6e-103">Powoduje, że kompilator wszystkie wpisz informacje z określonym dostępnych plików do projektu są obecnie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fda6e-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fda6e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fda6e-104">Syntax</span></span>  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="fda6e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="fda6e-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="fda6e-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="fda6e-106">Required.</span></span> <span data-ttu-id="fda6e-107">Rozdzielana przecinkami lista plików, które zawierają metadanych, ale nie zawierają zestawu manifestów.</span><span class="sxs-lookup"><span data-stu-id="fda6e-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="fda6e-108">Nazwy plików zawierających spacje powinny być ujęte w cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="fda6e-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fda6e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fda6e-109">Remarks</span></span>  
 <span data-ttu-id="fda6e-110">Pliki wyświetlane według `fileList` parametr musi zostać utworzona z `-target:module` opcji lub z innego kompilatora równoważne `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="fda6e-110">The files listed by the `fileList` parameter must be created with the `-target:module` option, or with another compiler's equivalent to `-target:module`.</span></span>  
  
 <span data-ttu-id="fda6e-111">Wszystkie moduły dodawane z `-addmodule` musi być w tym samym katalogu co plik wyjściowy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fda6e-111">All modules added with `-addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="fda6e-112">Oznacza to, że moduł można określić w dowolnym katalogu, w czasie kompilacji, ale moduł musi znajdować się w katalogu aplikacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fda6e-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="fda6e-113">Jeśli nie jest, możesz uzyskać <xref:System.TypeLoadException> błędu.</span><span class="sxs-lookup"><span data-stu-id="fda6e-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="fda6e-114">Jeśli określisz (jawnie ani niejawnie) wszelkie[-docelowego (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) opcji innych niż `-target:module` z `-addmodule`, pliki są przekazywane do `-addmodule` staną się częścią zestawu projektu.</span><span class="sxs-lookup"><span data-stu-id="fda6e-114">If you specify (implicitly or explicitly) any[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `-target:module` with `-addmodule`, the files you pass to `-addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="fda6e-115">Zestawu jest wymagana do uruchamiania pliku wyjściowego, który ma jeden lub więcej plików dodane z `-addmodule`.</span><span class="sxs-lookup"><span data-stu-id="fda6e-115">An assembly is required to run an output file that has one or more files added with `-addmodule`.</span></span>  
  
 <span data-ttu-id="fda6e-116">Użyj [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) Importowanie metadanych z pliku, który zawiera zestaw.</span><span class="sxs-lookup"><span data-stu-id="fda6e-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fda6e-117">`-addmodule` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="fda6e-117">The `-addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fda6e-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="fda6e-118">Example</span></span>  
 <span data-ttu-id="fda6e-119">Poniższy kod tworzy moduł.</span><span class="sxs-lookup"><span data-stu-id="fda6e-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 <span data-ttu-id="fda6e-120">Poniższy kod importuje typów modułów.</span><span class="sxs-lookup"><span data-stu-id="fda6e-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 <span data-ttu-id="fda6e-121">Po uruchomieniu `t1`, generuje on `802`.</span><span class="sxs-lookup"><span data-stu-id="fda6e-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fda6e-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fda6e-122">See Also</span></span>  
 [<span data-ttu-id="fda6e-123">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fda6e-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="fda6e-124">-docelowego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fda6e-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="fda6e-125">-odwołania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fda6e-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="fda6e-126">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="fda6e-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
