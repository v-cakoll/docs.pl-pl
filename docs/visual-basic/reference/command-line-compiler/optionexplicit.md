---
title: -optionexplicit
ms.date: 07/20/2015
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
ms.openlocfilehash: 072a816f189a772543fbbd63e7202441469c0177
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653601"
---
# <a name="-optionexplicit"></a><span data-ttu-id="e1145-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="e1145-102">-optionexplicit</span></span>
<span data-ttu-id="e1145-103">Powoduje, że kompilator może raportować błędy zmiennych nie jest zadeklarowana, zanim zostaną użyte.</span><span class="sxs-lookup"><span data-stu-id="e1145-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1145-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1145-104">Syntax</span></span>  
  
```  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e1145-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e1145-105">Arguments</span></span>  
 <span data-ttu-id="e1145-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="e1145-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="e1145-107">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="e1145-107">Optional.</span></span> <span data-ttu-id="e1145-108">Określ `-optionexplicit+` wymagające jawnej deklaracji zmiennych.</span><span class="sxs-lookup"><span data-stu-id="e1145-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="e1145-109">`-optionexplicit+` Opcja jest ustawieniem domyślnym i jest taki sam jak `-optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="e1145-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="e1145-110">`-optionexplicit-` Opcja umożliwia niejawne deklaracji zmiennych.</span><span class="sxs-lookup"><span data-stu-id="e1145-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1145-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1145-111">Remarks</span></span>  
 <span data-ttu-id="e1145-112">Jeśli plik kodu źródłowego zawiera [instrukcji Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), zastępuje instrukcji `-optionexplicit` Ustawienia kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="e1145-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="e1145-113">Aby ustawić - optionexplicit w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e1145-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="e1145-114">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="e1145-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e1145-115">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="e1145-115">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="e1145-116">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="e1145-116">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="e1145-117">Zmodyfikuj wartość w **Option Explicit** pole.</span><span class="sxs-lookup"><span data-stu-id="e1145-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1145-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1145-118">Example</span></span>  
 <span data-ttu-id="e1145-119">Poniższy kod kompiluje kiedy `-optionexplicit-` jest używany.</span><span class="sxs-lookup"><span data-stu-id="e1145-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e1145-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1145-120">See Also</span></span>  
 [<span data-ttu-id="e1145-121">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1145-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="e1145-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="e1145-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="e1145-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="e1145-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="e1145-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="e1145-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="e1145-125">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="e1145-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="e1145-126">Option Explicit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e1145-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="e1145-127">Okno dialogowe Opcje domyślne, projektów, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1145-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
