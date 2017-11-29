---
title: /optioninfer
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4400ee58214c8f9990d4b123e17ef0f6553a5a69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="optioninfer"></a><span data-ttu-id="17daa-102">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="17daa-102">/optioninfer</span></span>
<span data-ttu-id="17daa-103">Umożliwia użycie wnioskowania o typie lokalnym w deklaracjach zmiennych.</span><span class="sxs-lookup"><span data-stu-id="17daa-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17daa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="17daa-104">Syntax</span></span>  
  
```  
/optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="17daa-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="17daa-105">Arguments</span></span>  
  
|<span data-ttu-id="17daa-106">Termin</span><span class="sxs-lookup"><span data-stu-id="17daa-106">Term</span></span>|<span data-ttu-id="17daa-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="17daa-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="17daa-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="17daa-108">`+` &#124; `-`</span></span>|<span data-ttu-id="17daa-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="17daa-109">Optional.</span></span> <span data-ttu-id="17daa-110">Określ `/optioninfer+` umożliwiające wnioskowanie o typie lokalnym, lub `/optioninfer-` do blokowania.</span><span class="sxs-lookup"><span data-stu-id="17daa-110">Specify `/optioninfer+` to enable local type inference, or `/optioninfer-` to block it.</span></span> <span data-ttu-id="17daa-111">`/optioninfer` Opcji z wartości, jest taka sama jak `/optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="17daa-111">The `/optioninfer` option, with no value specified, is the same as `/optioninfer+`.</span></span> <span data-ttu-id="17daa-112">Wartość domyślna, kiedy `/optioninfer` przełącznik nie jest obecny jest również `/optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="17daa-112">The default value when the `/optioninfer` switch is not present is also `/optioninfer+`.</span></span> <span data-ttu-id="17daa-113">Wartość domyślna jest ustawiana w pliku odpowiedzi Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="17daa-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="17daa-114">Można użyć `/noconfig` opcję, aby zachować domyślne wewnętrznych kompilatora zamiast określone w vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="17daa-114">You can use the `/noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="17daa-115">Domyślnie ta opcja kompilatora `/optioninfer-`.</span><span class="sxs-lookup"><span data-stu-id="17daa-115">The compiler default for this option is `/optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17daa-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17daa-116">Remarks</span></span>  
 <span data-ttu-id="17daa-117">Jeśli plik kodu źródłowego zawiera [Option Infer — instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md), zastępuje instrukcji `/optioninfer` Ustawienia kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="17daa-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `/optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set-optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="17daa-118">Aby ustawić/optioninfer w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="17daa-118">To set /optioninfer in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="17daa-119">Wybierz projekt w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="17daa-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="17daa-120">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="17daa-120">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="17daa-121">Aby uzyskać więcej informacji, zobacz [NIB: Zarządzanie właściwości projektu przy użyciu projektanta projektów](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span><span class="sxs-lookup"><span data-stu-id="17daa-121">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="17daa-122">Na **skompilować** Zmień wartość w **Option infer** pole.</span><span class="sxs-lookup"><span data-stu-id="17daa-122">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17daa-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="17daa-123">Example</span></span>  
 <span data-ttu-id="17daa-124">Poniższy kod kompiluje `test.vb` z wnioskowanie o typie lokalnym włączona.</span><span class="sxs-lookup"><span data-stu-id="17daa-124">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```  
vbc /optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="17daa-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17daa-125">See Also</span></span>  
 [<span data-ttu-id="17daa-126">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="17daa-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="17daa-127">/ optioncompare</span><span class="sxs-lookup"><span data-stu-id="17daa-127">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="17daa-128">/ optionexplicit</span><span class="sxs-lookup"><span data-stu-id="17daa-128">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="17daa-129">/ optionstrict —</span><span class="sxs-lookup"><span data-stu-id="17daa-129">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="17daa-130">Kompilacja przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="17daa-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="17daa-131">Option Infer — instrukcja</span><span class="sxs-lookup"><span data-stu-id="17daa-131">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="17daa-132">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="17daa-132">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="17daa-133">Okno dialogowe Opcje domyślne, projektów, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="17daa-133">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [<span data-ttu-id="17daa-134">Strona kompilowania, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17daa-134">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [<span data-ttu-id="17daa-135">/ noconfig</span><span class="sxs-lookup"><span data-stu-id="17daa-135">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="17daa-136">Tworzenie z wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="17daa-136">Building from the Command Line</span></span>](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
