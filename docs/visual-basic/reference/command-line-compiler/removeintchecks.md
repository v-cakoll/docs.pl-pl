---
title: -removeintchecks
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- -removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25a14ffaca6e61c6e3306f8ff58de441e2ba2ade
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-removeintchecks"></a><span data-ttu-id="afb72-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="afb72-102">-removeintchecks</span></span>
<span data-ttu-id="afb72-103">Włącza sprawdzanie operacji liczby całkowitej lub wyłącz błąd przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="afb72-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afb72-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="afb72-104">Syntax</span></span>  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="afb72-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="afb72-105">Arguments</span></span>  
  
|<span data-ttu-id="afb72-106">Termin</span><span class="sxs-lookup"><span data-stu-id="afb72-106">Term</span></span>|<span data-ttu-id="afb72-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="afb72-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="afb72-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="afb72-108">`+` &#124; `-`</span></span>|<span data-ttu-id="afb72-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="afb72-109">Optional.</span></span> <span data-ttu-id="afb72-110">`-removeintchecks-` Opcja powoduje, że kompilator, aby sprawdzić wszystkie obliczenia całkowitą błędy przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="afb72-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="afb72-111">Wartość domyślna to `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="afb72-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="afb72-112">Określanie `-removeintchecks` lub `-removeintchecks+` uniemożliwia sprawdzanie błędów i może wykonywać szybsze obliczenia liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="afb72-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="afb72-113">Jednak bez sprawdzania błędów, i jeśli są przepełnienie danych typu pojemności, niepoprawne wyniki mogą być przechowywane bez zgłaszania błędu.</span><span class="sxs-lookup"><span data-stu-id="afb72-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="afb72-114">Aby ustawić - removeintchecks w programie Visual Studio zintegrowane środowisko deweloperskie</span><span class="sxs-lookup"><span data-stu-id="afb72-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="afb72-115">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="afb72-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="afb72-116">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="afb72-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="afb72-117">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="afb72-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="afb72-118">3.  Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="afb72-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="afb72-119">4.  Zmodyfikuj wartość **Wyłącz sprawdzanie przepełnienia całkowitych** pole.</span><span class="sxs-lookup"><span data-stu-id="afb72-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="afb72-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="afb72-120">Example</span></span>  
 <span data-ttu-id="afb72-121">Poniższy kod kompiluje `Test.vb` i wyłącza sprawdzanie błąd przepełnienia liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="afb72-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="afb72-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afb72-122">See Also</span></span>  
 [<span data-ttu-id="afb72-123">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="afb72-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="afb72-124">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="afb72-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
