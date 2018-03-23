---
title: -optioninfer
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: df01fccd7276f0ec759065306ad3614d735f89ef
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-optioninfer"></a><span data-ttu-id="d2a00-102">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="d2a00-102">-optioninfer</span></span>
<span data-ttu-id="d2a00-103">Umożliwia użycie wnioskowania o typie lokalnym w deklaracjach zmiennych.</span><span class="sxs-lookup"><span data-stu-id="d2a00-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2a00-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2a00-104">Syntax</span></span>  
  
```  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d2a00-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d2a00-105">Arguments</span></span>  
  
|<span data-ttu-id="d2a00-106">Termin</span><span class="sxs-lookup"><span data-stu-id="d2a00-106">Term</span></span>|<span data-ttu-id="d2a00-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="d2a00-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="d2a00-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="d2a00-108">`+` &#124; `-`</span></span>|<span data-ttu-id="d2a00-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d2a00-109">Optional.</span></span> <span data-ttu-id="d2a00-110">Określ `-optioninfer+` umożliwiające wnioskowanie o typie lokalnym, lub `-optioninfer-` do blokowania.</span><span class="sxs-lookup"><span data-stu-id="d2a00-110">Specify `-optioninfer+` to enable local type inference, or `-optioninfer-` to block it.</span></span> <span data-ttu-id="d2a00-111">`-optioninfer` Opcji z wartości, jest taka sama jak `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="d2a00-111">The `-optioninfer` option, with no value specified, is the same as `-optioninfer+`.</span></span> <span data-ttu-id="d2a00-112">Wartość domyślna, kiedy `-optioninfer` przełącznik nie jest obecny jest również `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="d2a00-112">The default value when the `-optioninfer` switch is not present is also `-optioninfer+`.</span></span> <span data-ttu-id="d2a00-113">Wartość domyślna jest ustawiana w pliku odpowiedzi Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="d2a00-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="d2a00-114">Można użyć `-noconfig` opcję, aby zachować domyślne wewnętrznych kompilatora zamiast określone w vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="d2a00-114">You can use the `-noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="d2a00-115">Domyślnie ta opcja kompilatora `-optioninfer-`.</span><span class="sxs-lookup"><span data-stu-id="d2a00-115">The compiler default for this option is `-optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2a00-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2a00-116">Remarks</span></span>  
 <span data-ttu-id="d2a00-117">Jeśli plik kodu źródłowego zawiera [Option Infer — instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md), zastępuje instrukcji `-optioninfer` Ustawienia kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="d2a00-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `-optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="d2a00-118">Aby ustawić - optioninfer w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d2a00-118">To set -optioninfer in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="d2a00-119">Wybierz projekt w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="d2a00-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="d2a00-120">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d2a00-120">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="d2a00-121">Na **skompilować** Zmień wartość w **Option infer** pole.</span><span class="sxs-lookup"><span data-stu-id="d2a00-121">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2a00-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2a00-122">Example</span></span>  
 <span data-ttu-id="d2a00-123">Poniższy kod kompiluje `test.vb` z wnioskowanie o typie lokalnym włączona.</span><span class="sxs-lookup"><span data-stu-id="d2a00-123">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d2a00-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2a00-124">See Also</span></span>  
 [<span data-ttu-id="d2a00-125">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d2a00-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d2a00-126">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="d2a00-126">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="d2a00-127">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="d2a00-127">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="d2a00-128">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="d2a00-128">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="d2a00-129">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="d2a00-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="d2a00-130">Option Infer, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d2a00-130">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="d2a00-131">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="d2a00-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="d2a00-132">Okno dialogowe Opcje domyślne, projektów, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d2a00-132">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [<span data-ttu-id="d2a00-133">Strona kompilowania, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2a00-133">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [<span data-ttu-id="d2a00-134">/noconfig</span><span class="sxs-lookup"><span data-stu-id="d2a00-134">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="d2a00-135">Tworzenie z wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="d2a00-135">Building from the Command Line</span></span>](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
