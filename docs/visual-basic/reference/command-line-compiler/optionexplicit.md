---
title: /optionexplicit
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1cfdb94ebafa7d6a14253aeb59ab98b3a953fe4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="optionexplicit"></a><span data-ttu-id="0fabf-102">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="0fabf-102">/optionexplicit</span></span>
<span data-ttu-id="0fabf-103">Powoduje, że kompilator może raportować błędy zmiennych nie jest zadeklarowana, zanim zostaną użyte.</span><span class="sxs-lookup"><span data-stu-id="0fabf-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fabf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0fabf-104">Syntax</span></span>  
  
```  
/optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0fabf-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0fabf-105">Arguments</span></span>  
 <span data-ttu-id="0fabf-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="0fabf-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="0fabf-107">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0fabf-107">Optional.</span></span> <span data-ttu-id="0fabf-108">Określ `/optionexplicit+` wymagające jawnej deklaracji zmiennych.</span><span class="sxs-lookup"><span data-stu-id="0fabf-108">Specify `/optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="0fabf-109">`/optionexplicit+` Opcja jest ustawieniem domyślnym i jest taki sam jak `/optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="0fabf-109">The `/optionexplicit+` option is the default and is the same as `/optionexplicit`.</span></span> <span data-ttu-id="0fabf-110">`/optionexplicit-` Opcja umożliwia niejawne deklaracji zmiennych.</span><span class="sxs-lookup"><span data-stu-id="0fabf-110">The `/optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fabf-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0fabf-111">Remarks</span></span>  
 <span data-ttu-id="0fabf-112">Jeśli plik kodu źródłowego zawiera [Option Explicit — instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md), zastępuje instrukcji `/optionexplicit` Ustawienia kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="0fabf-112">If the source code file contains an [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `/optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set-optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="0fabf-113">Aby ustawić/optionexplicit w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0fabf-113">To set /optionexplicit in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="0fabf-114">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="0fabf-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0fabf-115">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="0fabf-115">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="0fabf-116">Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="0fabf-116">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="0fabf-117">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="0fabf-117">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="0fabf-118">Zmodyfikuj wartość w **Option Explicit** pole.</span><span class="sxs-lookup"><span data-stu-id="0fabf-118">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fabf-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="0fabf-119">Example</span></span>  
 <span data-ttu-id="0fabf-120">Poniższy kod kompiluje kiedy `/optionexplicit-` jest używany.</span><span class="sxs-lookup"><span data-stu-id="0fabf-120">The following code compiles when `/optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0fabf-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0fabf-121">See Also</span></span>  
 [<span data-ttu-id="0fabf-122">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0fabf-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="0fabf-123">/ optioncompare</span><span class="sxs-lookup"><span data-stu-id="0fabf-123">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="0fabf-124">/ optionstrict —</span><span class="sxs-lookup"><span data-stu-id="0fabf-124">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="0fabf-125">/ optioninfer</span><span class="sxs-lookup"><span data-stu-id="0fabf-125">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="0fabf-126">Kompilacja przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="0fabf-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="0fabf-127">Option Explicit — instrukcja</span><span class="sxs-lookup"><span data-stu-id="0fabf-127">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="0fabf-128">Okno dialogowe Opcje domyślne, projektów, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0fabf-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
