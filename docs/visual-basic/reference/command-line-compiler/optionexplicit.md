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
ms.openlocfilehash: b004acb0c1c7d145c59a1e3a88ef7f1d405a91c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400565"
---
# <a name="-optionexplicit"></a><span data-ttu-id="4ae47-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="4ae47-102">-optionexplicit</span></span>
<span data-ttu-id="4ae47-103">Powoduje, że kompilator zgłasza błędy, jeśli zmienne nie są deklarowane przed ich użyciem.</span><span class="sxs-lookup"><span data-stu-id="4ae47-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ae47-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ae47-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4ae47-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4ae47-105">Arguments</span></span>  
 <span data-ttu-id="4ae47-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="4ae47-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="4ae47-107">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4ae47-107">Optional.</span></span> <span data-ttu-id="4ae47-108">Określ `-optionexplicit+` , aby wymagać jawnej deklaracji zmiennych.</span><span class="sxs-lookup"><span data-stu-id="4ae47-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="4ae47-109">`-optionexplicit+`Opcja jest wartością domyślną i jest taka sama jak `-optionexplicit` .</span><span class="sxs-lookup"><span data-stu-id="4ae47-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="4ae47-110">`-optionexplicit-`Opcja włącza niejawną deklarację zmiennych.</span><span class="sxs-lookup"><span data-stu-id="4ae47-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ae47-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ae47-111">Remarks</span></span>  
 <span data-ttu-id="4ae47-112">Jeśli plik kodu źródłowego zawiera [instrukcję Option Explicit](../../language-reference/statements/option-explicit-statement.md), instrukcja zastępuje `-optionexplicit` ustawienie kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4ae47-112">If the source code file contains an [Option Explicit statement](../../language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="4ae47-113">Aby ustawić-optionexplicit w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4ae47-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="4ae47-114">Zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="4ae47-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4ae47-115">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="4ae47-115">On the **Project** menu, click **Properties**.</span></span>
  
2. <span data-ttu-id="4ae47-116">Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="4ae47-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="4ae47-117">Zmodyfikuj wartość w polu **opcja Explicit** .</span><span class="sxs-lookup"><span data-stu-id="4ae47-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ae47-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ae47-118">Example</span></span>  
 <span data-ttu-id="4ae47-119">Poniższy kod kompiluje, kiedy `-optionexplicit-` jest używany.</span><span class="sxs-lookup"><span data-stu-id="4ae47-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="4ae47-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ae47-120">See also</span></span>

- [<span data-ttu-id="4ae47-121">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4ae47-121">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="4ae47-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="4ae47-122">-optioncompare</span></span>](optioncompare.md)
- [<span data-ttu-id="4ae47-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="4ae47-123">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="4ae47-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="4ae47-124">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="4ae47-125">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="4ae47-125">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="4ae47-126">Option Explicit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4ae47-126">Option Explicit Statement</span></span>](../../language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="4ae47-127">Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="4ae47-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
