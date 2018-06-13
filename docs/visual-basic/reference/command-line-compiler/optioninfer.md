---
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: e7dbc4d5f06096978c4d93ea20677dcb60bc3fcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655928"
---
# <a name="-optioninfer"></a><span data-ttu-id="bb9c5-102">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="bb9c5-102">-optioninfer</span></span>
<span data-ttu-id="bb9c5-103">Umożliwia użycie wnioskowania o typie lokalnym w deklaracjach zmiennych.</span><span class="sxs-lookup"><span data-stu-id="bb9c5-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb9c5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb9c5-104">Syntax</span></span>  
  
```  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="bb9c5-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="bb9c5-105">Arguments</span></span>  
  
|<span data-ttu-id="bb9c5-106">Termin</span><span class="sxs-lookup"><span data-stu-id="bb9c5-106">Term</span></span>|<span data-ttu-id="bb9c5-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="bb9c5-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="bb9c5-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="bb9c5-108">`+` &#124; `-`</span></span>|<span data-ttu-id="bb9c5-109">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="bb9c5-109">Optional.</span></span> <span data-ttu-id="bb9c5-110">Określ `-optioninfer+` umożliwiające wnioskowanie o typie lokalnym, lub `-optioninfer-` do blokowania.</span><span class="sxs-lookup"><span data-stu-id="bb9c5-110">Specify `-optioninfer+` to enable local type inference, or `-optioninfer-` to block it.</span></span> <span data-ttu-id="bb9c5-111">`-optioninfer` Opcji z wartości, jest taka sama jak `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="bb9c5-111">The `-optioninfer` option, with no value specified, is the same as `-optioninfer+`.</span></span> <span data-ttu-id="bb9c5-112">Wartość domyślna, kiedy `-optioninfer` przełącznik nie jest obecny jest również `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="bb9c5-112">The default value when the `-optioninfer` switch is not present is also `-optioninfer+`.</span></span> <span data-ttu-id="bb9c5-113">Wartość domyślna jest ustawiana w pliku odpowiedzi Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="bb9c5-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="bb9c5-114">Można użyć `-noconfig` opcję, aby zachować domyślne wewnętrznych kompilatora zamiast określone w vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="bb9c5-114">You can use the `-noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="bb9c5-115">Domyślnie ta opcja kompilatora `-optioninfer-`.</span><span class="sxs-lookup"><span data-stu-id="bb9c5-115">The compiler default for this option is `-optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb9c5-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bb9c5-116">Remarks</span></span>  
 <span data-ttu-id="bb9c5-117">Jeśli plik kodu źródłowego zawiera [Option Infer — instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md), zastępuje instrukcji `-optioninfer` Ustawienia kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="bb9c5-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `-optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="bb9c5-118">Aby ustawić - optioninfer w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bb9c5-118">To set -optioninfer in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="bb9c5-119">Wybierz projekt w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="bb9c5-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="bb9c5-120">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="bb9c5-120">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="bb9c5-121">Na **skompilować** Zmień wartość w **Option infer** pole.</span><span class="sxs-lookup"><span data-stu-id="bb9c5-121">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb9c5-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb9c5-122">Example</span></span>  
 <span data-ttu-id="bb9c5-123">Poniższy kod kompiluje `test.vb` z wnioskowanie o typie lokalnym włączona.</span><span class="sxs-lookup"><span data-stu-id="bb9c5-123">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb9c5-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb9c5-124">See Also</span></span>  
 [<span data-ttu-id="bb9c5-125">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb9c5-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="bb9c5-126">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="bb9c5-126">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="bb9c5-127">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="bb9c5-127">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="bb9c5-128">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="bb9c5-128">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="bb9c5-129">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="bb9c5-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="bb9c5-130">Option Infer, instrukcja</span><span class="sxs-lookup"><span data-stu-id="bb9c5-130">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="bb9c5-131">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="bb9c5-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="bb9c5-132">Okno dialogowe Opcje domyślne, projektów, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb9c5-132">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [<span data-ttu-id="bb9c5-133">Strona kompilowania, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb9c5-133">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [<span data-ttu-id="bb9c5-134">/noconfig</span><span class="sxs-lookup"><span data-stu-id="bb9c5-134">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="bb9c5-135">Tworzenie z wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="bb9c5-135">Building from the Command Line</span></span>](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
