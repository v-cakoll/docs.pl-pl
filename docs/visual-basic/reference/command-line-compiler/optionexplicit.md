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
ms.openlocfilehash: 37ccd14dae0ebba2535185f2646e312d9bb70390
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266732"
---
# <a name="-optionexplicit"></a><span data-ttu-id="d46fe-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="d46fe-102">-optionexplicit</span></span>
<span data-ttu-id="d46fe-103">Powoduje, że kompilator zgłasza błędy, jeśli zmienne nie są deklarowane przed ich użyciem.</span><span class="sxs-lookup"><span data-stu-id="d46fe-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d46fe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d46fe-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d46fe-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d46fe-105">Arguments</span></span>  
 <span data-ttu-id="d46fe-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="d46fe-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="d46fe-107">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d46fe-107">Optional.</span></span> <span data-ttu-id="d46fe-108">Określ `-optionexplicit+` , aby wymagać jawnej deklaracji zmiennych.</span><span class="sxs-lookup"><span data-stu-id="d46fe-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="d46fe-109">`-optionexplicit+` Opcja jest wartością domyślną i jest taka sama jak `-optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="d46fe-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="d46fe-110">`-optionexplicit-` Opcja włącza niejawną deklarację zmiennych.</span><span class="sxs-lookup"><span data-stu-id="d46fe-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d46fe-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d46fe-111">Remarks</span></span>  
 <span data-ttu-id="d46fe-112">Jeśli plik kodu źródłowego zawiera [instrukcję Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), instrukcja zastępuje ustawienie kompilatora wiersza `-optionexplicit` polecenia.</span><span class="sxs-lookup"><span data-stu-id="d46fe-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="d46fe-113">Aby ustawić-optionexplicit w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d46fe-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="d46fe-114">Zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="d46fe-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d46fe-115">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d46fe-115">On the **Project** menu, click **Properties**.</span></span>
  
2. <span data-ttu-id="d46fe-116">Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="d46fe-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="d46fe-117">Zmodyfikuj wartość w polu **opcja Explicit** .</span><span class="sxs-lookup"><span data-stu-id="d46fe-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d46fe-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="d46fe-118">Example</span></span>  
 <span data-ttu-id="d46fe-119">Poniższy kod kompiluje, kiedy `-optionexplicit-` jest używany.</span><span class="sxs-lookup"><span data-stu-id="d46fe-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="d46fe-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d46fe-120">See also</span></span>

- [<span data-ttu-id="d46fe-121">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d46fe-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d46fe-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="d46fe-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="d46fe-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="d46fe-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="d46fe-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="d46fe-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="d46fe-125">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="d46fe-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="d46fe-126">Option Explicit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d46fe-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="d46fe-127">Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="d46fe-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
