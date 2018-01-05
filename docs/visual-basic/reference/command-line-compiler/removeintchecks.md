---
title: /removeintchecks
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- /removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 917977d8e5e12c231370ab3c956aca9d96e8a8a8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="removeintchecks"></a><span data-ttu-id="ebf0b-102">/removeintchecks</span><span class="sxs-lookup"><span data-stu-id="ebf0b-102">/removeintchecks</span></span>
<span data-ttu-id="ebf0b-103">Włącza sprawdzanie operacji liczby całkowitej lub wyłącz błąd przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="ebf0b-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebf0b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ebf0b-104">Syntax</span></span>  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ebf0b-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ebf0b-105">Arguments</span></span>  
  
|<span data-ttu-id="ebf0b-106">Termin</span><span class="sxs-lookup"><span data-stu-id="ebf0b-106">Term</span></span>|<span data-ttu-id="ebf0b-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="ebf0b-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="ebf0b-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="ebf0b-108">`+` &#124; `-`</span></span>|<span data-ttu-id="ebf0b-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ebf0b-109">Optional.</span></span> <span data-ttu-id="ebf0b-110">`/removeintchecks-` Opcja powoduje, że kompilator, aby sprawdzić wszystkie obliczenia całkowitą błędy przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="ebf0b-110">The `/removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="ebf0b-111">Wartość domyślna to `/removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="ebf0b-111">The default is `/removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="ebf0b-112">Określanie `/removeintchecks` lub `/removeintchecks+` uniemożliwia sprawdzanie błędów i może wykonywać szybsze obliczenia liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="ebf0b-112">Specifying `/removeintchecks` or `/removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="ebf0b-113">Jednak bez sprawdzania błędów, i jeśli są przepełnienie danych typu pojemności, niepoprawne wyniki mogą być przechowywane bez zgłaszania błędu.</span><span class="sxs-lookup"><span data-stu-id="ebf0b-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="ebf0b-114">Aby ustawić/removeintchecks w programie Visual Studio zintegrowane środowisko deweloperskie</span><span class="sxs-lookup"><span data-stu-id="ebf0b-114">To set /removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="ebf0b-115">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="ebf0b-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ebf0b-116">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ebf0b-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="ebf0b-117">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="ebf0b-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="ebf0b-118">3.  Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ebf0b-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="ebf0b-119">4.  Zmodyfikuj wartość **Wyłącz sprawdzanie przepełnienia całkowitych** pole.</span><span class="sxs-lookup"><span data-stu-id="ebf0b-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ebf0b-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="ebf0b-120">Example</span></span>  
 <span data-ttu-id="ebf0b-121">Poniższy kod kompiluje `Test.vb` i wyłącza sprawdzanie błąd przepełnienia liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="ebf0b-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ebf0b-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebf0b-122">See Also</span></span>  
 [<span data-ttu-id="ebf0b-123">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ebf0b-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ebf0b-124">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="ebf0b-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
