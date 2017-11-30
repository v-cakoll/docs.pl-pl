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
ms.openlocfilehash: 4e765f0007eea8e196b1a1b3b55b969c5b074b52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="removeintchecks"></a><span data-ttu-id="0fe46-102">/removeintchecks</span><span class="sxs-lookup"><span data-stu-id="0fe46-102">/removeintchecks</span></span>
<span data-ttu-id="0fe46-103">Włącza sprawdzanie operacji liczby całkowitej lub wyłącz błąd przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="0fe46-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fe46-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0fe46-104">Syntax</span></span>  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0fe46-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0fe46-105">Arguments</span></span>  
  
|<span data-ttu-id="0fe46-106">Termin</span><span class="sxs-lookup"><span data-stu-id="0fe46-106">Term</span></span>|<span data-ttu-id="0fe46-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="0fe46-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="0fe46-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="0fe46-108">`+` &#124; `-`</span></span>|<span data-ttu-id="0fe46-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0fe46-109">Optional.</span></span> <span data-ttu-id="0fe46-110">`/removeintchecks-` Opcja powoduje, że kompilator, aby sprawdzić wszystkie obliczenia całkowitą błędy przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="0fe46-110">The `/removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="0fe46-111">Wartość domyślna to `/removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="0fe46-111">The default is `/removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="0fe46-112">Określanie `/removeintchecks` lub `/removeintchecks+` uniemożliwia sprawdzanie błędów i może wykonywać szybsze obliczenia liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="0fe46-112">Specifying `/removeintchecks` or `/removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="0fe46-113">Jednak bez sprawdzania błędów, i jeśli są przepełnienie danych typu pojemności, niepoprawne wyniki mogą być przechowywane bez zgłaszania błędu.</span><span class="sxs-lookup"><span data-stu-id="0fe46-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="0fe46-114">Aby ustawić/removeintchecks w programie Visual Studio zintegrowane środowisko deweloperskie</span><span class="sxs-lookup"><span data-stu-id="0fe46-114">To set /removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="0fe46-115">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="0fe46-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0fe46-116">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="0fe46-116">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="0fe46-117">Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="0fe46-117">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="0fe46-118">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="0fe46-118">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="0fe46-119">3.  Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="0fe46-119">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="0fe46-120">4.  Zmodyfikuj wartość **Wyłącz sprawdzanie przepełnienia całkowitych** pole.</span><span class="sxs-lookup"><span data-stu-id="0fe46-120">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0fe46-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="0fe46-121">Example</span></span>  
 <span data-ttu-id="0fe46-122">Poniższy kod kompiluje `Test.vb` i wyłącza sprawdzanie błąd przepełnienia liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="0fe46-122">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fe46-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0fe46-123">See Also</span></span>  
 [<span data-ttu-id="0fe46-124">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0fe46-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="0fe46-125">Kompilacja przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="0fe46-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
