---
title: /optimize
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dead17435cd147bdcdf91bdc5b8e0aa651e9e9fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="optimize"></a><span data-ttu-id="0e3fa-102">/optimize</span><span class="sxs-lookup"><span data-stu-id="0e3fa-102">/optimize</span></span>
<span data-ttu-id="0e3fa-103">Włącza lub wyłącza optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="0e3fa-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e3fa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e3fa-104">Syntax</span></span>  
  
```  
/optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0e3fa-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0e3fa-105">Arguments</span></span>  
  
|<span data-ttu-id="0e3fa-106">Termin</span><span class="sxs-lookup"><span data-stu-id="0e3fa-106">Term</span></span>|<span data-ttu-id="0e3fa-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="0e3fa-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="0e3fa-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="0e3fa-108">`+` &#124; `-`</span></span>|<span data-ttu-id="0e3fa-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="0e3fa-109">Optional.</span></span> <span data-ttu-id="0e3fa-110">`/optimize-` Opcja wyłącza optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="0e3fa-110">The `/optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="0e3fa-111">`/optimize+` Opcja włącza optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="0e3fa-111">The `/optimize+` option enables optimizations.</span></span> <span data-ttu-id="0e3fa-112">Optymalizacje są domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="0e3fa-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e3fa-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e3fa-113">Remarks</span></span>  
 <span data-ttu-id="0e3fa-114">Mniejszy, szybszy i bardziej wydajne, plik wyjściowy był optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="0e3fa-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="0e3fa-115">Jednakże, ponieważ optymalizacje powoduje modyfikacji kodu w pliku wyjściowym `/optimize+` może utrudnić debugowania.</span><span class="sxs-lookup"><span data-stu-id="0e3fa-115">However, because optimizations result in code rearrangement in the output file, `/optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="0e3fa-116">Wszystkie moduły wygenerowane z `/target:module` dla zestawu musi używać tego samego `/optimize` ustawienia jako zestaw.</span><span class="sxs-lookup"><span data-stu-id="0e3fa-116">All modules generated with `/target:module` for an assembly must use the same `/optimize` settings as the assembly.</span></span> <span data-ttu-id="0e3fa-117">Aby uzyskać więcej informacji, zobacz [/TARGET (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="0e3fa-117">For more information, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="0e3fa-118">Możesz połączyć ze sobą `/optimize` i `/debug` opcje.</span><span class="sxs-lookup"><span data-stu-id="0e3fa-118">You can combine the `/optimize` and `/debug` options.</span></span>  
  
|<span data-ttu-id="0e3fa-119">Aby ustawić / optimize w programie Visual Studio zintegrowane środowisko deweloperskie</span><span class="sxs-lookup"><span data-stu-id="0e3fa-119">To set /optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="0e3fa-120">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="0e3fa-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0e3fa-121">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="0e3fa-121">On the **Project** menu, click **Properties**.</span></span><br />     <span data-ttu-id="0e3fa-122">Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="0e3fa-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="0e3fa-123">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="0e3fa-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="0e3fa-124">3.  Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="0e3fa-124">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="0e3fa-125">4.  Modyfikowanie **Włącz optymalizacje** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="0e3fa-125">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0e3fa-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="0e3fa-126">Example</span></span>  
 <span data-ttu-id="0e3fa-127">Poniższy kod kompiluje `T2.vb` i włącza optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="0e3fa-127">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```  
vbc t2.vb /optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e3fa-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e3fa-128">See Also</span></span>  
 [<span data-ttu-id="0e3fa-129">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0e3fa-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="0e3fa-130">/ Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e3fa-130">/debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="0e3fa-131">Kompilacja przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="0e3fa-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="0e3fa-132">/ TARGET (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e3fa-132">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
