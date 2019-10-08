---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: fbe3634d1fbc03acd56ef7276d65fd54493b9806
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002415"
---
# <a name="-addmodule"></a><span data-ttu-id="4b098-102">-addmodule</span><span class="sxs-lookup"><span data-stu-id="4b098-102">-addmodule</span></span>
<span data-ttu-id="4b098-103">Powoduje, że kompilator udostępnił wszystkie informacje o typie z określonych plików dla aktualnie kompilowanego projektu.</span><span class="sxs-lookup"><span data-stu-id="4b098-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b098-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b098-104">Syntax</span></span>  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="4b098-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4b098-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="4b098-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="4b098-106">Required.</span></span> <span data-ttu-id="4b098-107">Rozdzielana przecinkami lista plików, które zawierają metadane, ale nie zawierają manifestów zestawów.</span><span class="sxs-lookup"><span data-stu-id="4b098-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="4b098-108">Nazwy plików zawierające spacje powinny być ujęte w znaki cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="4b098-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b098-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b098-109">Remarks</span></span>  
 <span data-ttu-id="4b098-110">Pliki wymienione przez parametr `fileList` muszą zostać utworzone za pomocą opcji `-target:module` lub z innym kompilatorem równoważnym do `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="4b098-110">The files listed by the `fileList` parameter must be created with the `-target:module` option, or with another compiler's equivalent to `-target:module`.</span></span>  
  
 <span data-ttu-id="4b098-111">Wszystkie moduły dodane z `-addmodule` muszą znajdować się w tym samym katalogu co plik wyjściowy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4b098-111">All modules added with `-addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="4b098-112">Oznacza to, że można określić moduł w dowolnym katalogu w czasie kompilacji, ale moduł musi znajdować się w katalogu aplikacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4b098-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="4b098-113">Jeśli tak nie jest, zostanie wyświetlony błąd <xref:System.TypeLoadException>.</span><span class="sxs-lookup"><span data-stu-id="4b098-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="4b098-114">Jeśli określisz (niejawnie lub jawnie) opcję[docelową (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) inną niż `-target:module` z `-addmodule`, pliki przekazywane do `-addmodule` staną się częścią zestawu projektu.</span><span class="sxs-lookup"><span data-stu-id="4b098-114">If you specify (implicitly or explicitly) any[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `-target:module` with `-addmodule`, the files you pass to `-addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="4b098-115">Zestaw jest wymagany do uruchomienia pliku wyjściowego, który ma co najmniej jeden plik dodany z `-addmodule`.</span><span class="sxs-lookup"><span data-stu-id="4b098-115">An assembly is required to run an output file that has one or more files added with `-addmodule`.</span></span>  
  
 <span data-ttu-id="4b098-116">Użyj [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) do zaimportowania metadanych z pliku, który zawiera zestaw.</span><span class="sxs-lookup"><span data-stu-id="4b098-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b098-117">Opcja `-addmodule` nie jest dostępna w środowisku deweloperskim programu Visual Studio. jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4b098-117">The `-addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b098-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b098-118">Example</span></span>  
 <span data-ttu-id="4b098-119">Poniższy kod tworzy moduł.</span><span class="sxs-lookup"><span data-stu-id="4b098-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 <span data-ttu-id="4b098-120">Poniższy kod importuje typy modułu.</span><span class="sxs-lookup"><span data-stu-id="4b098-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 <span data-ttu-id="4b098-121">Po uruchomieniu `t1` dane wyjściowe `802`.</span><span class="sxs-lookup"><span data-stu-id="4b098-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b098-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b098-122">See also</span></span>

- [<span data-ttu-id="4b098-123">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4b098-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="4b098-124">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b098-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="4b098-125">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b098-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="4b098-126">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="4b098-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
