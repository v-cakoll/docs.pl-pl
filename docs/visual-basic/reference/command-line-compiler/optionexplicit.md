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
ms.openlocfilehash: 54d438541e8840e4394b24b20b4f394ff8cdb820
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788950"
---
# <a name="-optionexplicit"></a><span data-ttu-id="47e5f-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="47e5f-102">-optionexplicit</span></span>
<span data-ttu-id="47e5f-103">Powoduje, że kompilator zgłaszaj błędy jeśli zmienne nie są deklarowane, zanim zostaną użyte.</span><span class="sxs-lookup"><span data-stu-id="47e5f-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47e5f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="47e5f-104">Syntax</span></span>  
  
```  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="47e5f-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="47e5f-105">Arguments</span></span>  
 <span data-ttu-id="47e5f-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="47e5f-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="47e5f-107">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="47e5f-107">Optional.</span></span> <span data-ttu-id="47e5f-108">Określ `-optionexplicit+` będą musieli jawnej deklaracji zmiennych.</span><span class="sxs-lookup"><span data-stu-id="47e5f-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="47e5f-109">`-optionexplicit+` Opcja jest domyślnie i jest taka sama jak `-optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="47e5f-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="47e5f-110">`-optionexplicit-` Opcja umożliwia niejawne deklaracji zmiennych.</span><span class="sxs-lookup"><span data-stu-id="47e5f-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47e5f-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="47e5f-111">Remarks</span></span>  
 <span data-ttu-id="47e5f-112">Jeśli plik kodu źródłowego zawiera [instrukcji Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), zastępuje instrukcji `-optionexplicit` Ustawienia kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="47e5f-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="47e5f-113">Aby ustawić - optionexplicit — w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="47e5f-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="47e5f-114">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="47e5f-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="47e5f-115">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="47e5f-115">On the **Project** menu, click **Properties**.</span></span>   
  
2. <span data-ttu-id="47e5f-116">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="47e5f-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="47e5f-117">Zmodyfikuj wartość w **Option Explicit** pole.</span><span class="sxs-lookup"><span data-stu-id="47e5f-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47e5f-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="47e5f-118">Example</span></span>  
 <span data-ttu-id="47e5f-119">Poniższy kod kompiluje, kiedy `-optionexplicit-` jest używany.</span><span class="sxs-lookup"><span data-stu-id="47e5f-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="47e5f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47e5f-120">See also</span></span>

- [<span data-ttu-id="47e5f-121">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="47e5f-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="47e5f-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="47e5f-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="47e5f-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="47e5f-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="47e5f-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="47e5f-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="47e5f-125">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="47e5f-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="47e5f-126">Option Explicit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="47e5f-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="47e5f-127">Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="47e5f-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
