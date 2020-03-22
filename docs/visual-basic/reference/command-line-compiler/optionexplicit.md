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
# <a name="-optionexplicit"></a><span data-ttu-id="4d8d5-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="4d8d5-102">-optionexplicit</span></span>
<span data-ttu-id="4d8d5-103">Powoduje, że kompilator do raportowania błędów, jeśli zmienne nie są zadeklarowane przed ich użyciem.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d8d5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d8d5-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4d8d5-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4d8d5-105">Arguments</span></span>  
 <span data-ttu-id="4d8d5-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="4d8d5-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="4d8d5-107">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-107">Optional.</span></span> <span data-ttu-id="4d8d5-108">Określ, aby wymagać `-optionexplicit+` jawnej deklaracji zmiennych.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="4d8d5-109">Opcja `-optionexplicit+` jest domyślna i jest `-optionexplicit`taka sama jak .</span><span class="sxs-lookup"><span data-stu-id="4d8d5-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="4d8d5-110">Opcja `-optionexplicit-` umożliwia niejawną deklarację zmiennych.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d8d5-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d8d5-111">Remarks</span></span>  
 <span data-ttu-id="4d8d5-112">Jeśli plik kodu źródłowego zawiera [instrukcję Option](../../../visual-basic/language-reference/statements/option-explicit-statement.md)Explicit `-optionexplicit` , instrukcja zastępuje ustawienie kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="4d8d5-113">Aby ustawić -optionexplicit w programie Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="4d8d5-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="4d8d5-114">Wybierz projekt w **Eksploratorze rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4d8d5-115">W menu **Projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-115">On the **Project** menu, click **Properties**.</span></span>
  
2. <span data-ttu-id="4d8d5-116">Kliknij kartę **Kompilowanie.**</span><span class="sxs-lookup"><span data-stu-id="4d8d5-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="4d8d5-117">Zmodyfikuj wartość w polu **Opcja Jawna.**</span><span class="sxs-lookup"><span data-stu-id="4d8d5-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d8d5-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d8d5-118">Example</span></span>  
 <span data-ttu-id="4d8d5-119">Poniższy kod kompiluje, gdy `-optionexplicit-` jest używany.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="4d8d5-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d8d5-120">See also</span></span>

- [<span data-ttu-id="4d8d5-121">Visual Basic Kompilator wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="4d8d5-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="4d8d5-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="4d8d5-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="4d8d5-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="4d8d5-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="4d8d5-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="4d8d5-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="4d8d5-125">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="4d8d5-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="4d8d5-126">Option Explicit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4d8d5-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="4d8d5-127">Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="4d8d5-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
