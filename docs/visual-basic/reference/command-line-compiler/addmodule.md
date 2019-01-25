---
title: -addmodule —
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 3e5c94cce8b16649854050855800ac1bf2fc6572
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580580"
---
# <a name="-addmodule"></a><span data-ttu-id="ff4e7-102">-addmodule —</span><span class="sxs-lookup"><span data-stu-id="ff4e7-102">-addmodule</span></span>
<span data-ttu-id="ff4e7-103">Powoduje, że kompilator udostępnia wszystkie informacje z określonego pliku lub plików dostępnych do aktualnie kompilowanemu projektowi typu.</span><span class="sxs-lookup"><span data-stu-id="ff4e7-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff4e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff4e7-104">Syntax</span></span>  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="ff4e7-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ff4e7-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="ff4e7-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="ff4e7-106">Required.</span></span> <span data-ttu-id="ff4e7-107">Rozdzielana przecinkami lista plików, które zawierają metadanych, ale nie zawierają zestawu manifestów.</span><span class="sxs-lookup"><span data-stu-id="ff4e7-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="ff4e7-108">Nazwy plików zawierające spacje powinny być ujęte w znaki cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="ff4e7-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff4e7-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff4e7-109">Remarks</span></span>  
 <span data-ttu-id="ff4e7-110">Pliki według `fileList` parametr musi zostać utworzona z `-target:module` opcji lub innego kompilatora równoważna `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="ff4e7-110">The files listed by the `fileList` parameter must be created with the `-target:module` option, or with another compiler's equivalent to `-target:module`.</span></span>  
  
 <span data-ttu-id="ff4e7-111">Wszystkie moduły dodawane z `-addmodule` musi znajdować się w tym samym katalogu co plik wyjściowy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ff4e7-111">All modules added with `-addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="ff4e7-112">Oznacza to, że można określić modułu w dowolnym katalogu, w czasie kompilacji, ale moduł musi znajdować się w katalogu aplikacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ff4e7-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="ff4e7-113">Jeśli tak nie jest, możesz uzyskać <xref:System.TypeLoadException> błędu.</span><span class="sxs-lookup"><span data-stu-id="ff4e7-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="ff4e7-114">Jeśli określisz (jawnie lub niejawnie) wszelkie[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) opcji innych niż `-target:module` z `-addmodule`, pliki są przekazywane do `-addmodule` stają się częścią zestawu projektu.</span><span class="sxs-lookup"><span data-stu-id="ff4e7-114">If you specify (implicitly or explicitly) any[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `-target:module` with `-addmodule`, the files you pass to `-addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="ff4e7-115">Zestaw jest wymagany do uruchomienia pliku wyjściowego, który ma jeden lub więcej plików dodane przy użyciu `-addmodule`.</span><span class="sxs-lookup"><span data-stu-id="ff4e7-115">An assembly is required to run an output file that has one or more files added with `-addmodule`.</span></span>  
  
 <span data-ttu-id="ff4e7-116">Użyj [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) można zaimportować metadanych z pliku, który zawiera zestaw.</span><span class="sxs-lookup"><span data-stu-id="ff4e7-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff4e7-117">`-addmodule` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="ff4e7-117">The `-addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff4e7-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff4e7-118">Example</span></span>  
 <span data-ttu-id="ff4e7-119">Poniższy kod tworzy moduł.</span><span class="sxs-lookup"><span data-stu-id="ff4e7-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 <span data-ttu-id="ff4e7-120">Poniższy kod importuje typów modułów.</span><span class="sxs-lookup"><span data-stu-id="ff4e7-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 <span data-ttu-id="ff4e7-121">Po uruchomieniu `t1`, wyświetla `802`.</span><span class="sxs-lookup"><span data-stu-id="ff4e7-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff4e7-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff4e7-122">See also</span></span>
- [<span data-ttu-id="ff4e7-123">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ff4e7-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="ff4e7-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff4e7-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="ff4e7-125">— Odwołanie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff4e7-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="ff4e7-126">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="ff4e7-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
