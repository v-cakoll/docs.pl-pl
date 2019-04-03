---
title: -optioninfer —
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: 89fcd981dbb5442f6150f539db4c7d404fe8d691
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839850"
---
# <a name="-optioninfer"></a><span data-ttu-id="cacbf-102">-optioninfer —</span><span class="sxs-lookup"><span data-stu-id="cacbf-102">-optioninfer</span></span>
<span data-ttu-id="cacbf-103">Umożliwia użycie wnioskowania o typie lokalnym w deklaracjach zmiennych.</span><span class="sxs-lookup"><span data-stu-id="cacbf-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cacbf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cacbf-104">Syntax</span></span>  
  
```  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="cacbf-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cacbf-105">Arguments</span></span>  
  
|<span data-ttu-id="cacbf-106">Termin</span><span class="sxs-lookup"><span data-stu-id="cacbf-106">Term</span></span>|<span data-ttu-id="cacbf-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="cacbf-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="cacbf-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="cacbf-108">`+` &#124; `-`</span></span>|<span data-ttu-id="cacbf-109">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="cacbf-109">Optional.</span></span> <span data-ttu-id="cacbf-110">Określ `-optioninfer+` włączyć wnioskowanie o typie lokalnym, lub `-optioninfer-` do jego blokowania.</span><span class="sxs-lookup"><span data-stu-id="cacbf-110">Specify `-optioninfer+` to enable local type inference, or `-optioninfer-` to block it.</span></span> <span data-ttu-id="cacbf-111">`-optioninfer` Opcji bez wartości określone, jest taka sama jak `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="cacbf-111">The `-optioninfer` option, with no value specified, is the same as `-optioninfer+`.</span></span> <span data-ttu-id="cacbf-112">Wartość domyślna, gdy `-optioninfer` nie ma przełącznika jest również `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="cacbf-112">The default value when the `-optioninfer` switch is not present is also `-optioninfer+`.</span></span> <span data-ttu-id="cacbf-113">Wartość domyślna jest ustawiana w pliku odpowiedzi Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="cacbf-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="cacbf-114">Możesz użyć `-noconfig` opcję, aby zachować ustawienia domyślne wewnętrznych kompilatora, zamiast określone w vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="cacbf-114">You can use the `-noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="cacbf-115">Domyślna wartość kompilatora dla tej opcji jest `-optioninfer-`.</span><span class="sxs-lookup"><span data-stu-id="cacbf-115">The compiler default for this option is `-optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cacbf-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cacbf-116">Remarks</span></span>  
 <span data-ttu-id="cacbf-117">Jeśli plik kodu źródłowego zawiera [Option Infer — instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md), zastępuje instrukcji `-optioninfer` Ustawienia kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="cacbf-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `-optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="cacbf-118">Aby ustawić - optioninfer — w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cacbf-118">To set -optioninfer in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="cacbf-119">Wybierz projekt w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="cacbf-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="cacbf-120">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="cacbf-120">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="cacbf-121">Na **skompilować** Zmień wartość w **Option infer** pole.</span><span class="sxs-lookup"><span data-stu-id="cacbf-121">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cacbf-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="cacbf-122">Example</span></span>  
 <span data-ttu-id="cacbf-123">Poniższy kod kompiluje `test.vb` z włączoną wnioskowanie o typie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="cacbf-123">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="cacbf-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cacbf-124">See also</span></span>

- [<span data-ttu-id="cacbf-125">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cacbf-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="cacbf-126">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="cacbf-126">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="cacbf-127">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="cacbf-127">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="cacbf-128">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="cacbf-128">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="cacbf-129">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="cacbf-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="cacbf-130">Option Infer, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cacbf-130">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="cacbf-131">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="cacbf-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="cacbf-132">Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="cacbf-132">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="cacbf-133">Strona kompilowania, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cacbf-133">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="cacbf-134">/noconfig</span><span class="sxs-lookup"><span data-stu-id="cacbf-134">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="cacbf-135">Tworzenie z wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="cacbf-135">Building from the Command Line</span></span>](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
