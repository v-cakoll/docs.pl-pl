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
ms.openlocfilehash: e157fb0e1fcdb3899440eed02a42b16f75541989
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="optimize"></a><span data-ttu-id="23b45-102">/optimize</span><span class="sxs-lookup"><span data-stu-id="23b45-102">/optimize</span></span>
<span data-ttu-id="23b45-103">Włącza lub wyłącza optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="23b45-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23b45-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="23b45-104">Syntax</span></span>  
  
```  
/optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="23b45-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="23b45-105">Arguments</span></span>  
  
|<span data-ttu-id="23b45-106">Termin</span><span class="sxs-lookup"><span data-stu-id="23b45-106">Term</span></span>|<span data-ttu-id="23b45-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="23b45-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="23b45-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="23b45-108">`+` &#124; `-`</span></span>|<span data-ttu-id="23b45-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="23b45-109">Optional.</span></span> <span data-ttu-id="23b45-110">`/optimize-` Opcja wyłącza optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="23b45-110">The `/optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="23b45-111">`/optimize+` Opcja włącza optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="23b45-111">The `/optimize+` option enables optimizations.</span></span> <span data-ttu-id="23b45-112">Optymalizacje są domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="23b45-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23b45-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="23b45-113">Remarks</span></span>  
 <span data-ttu-id="23b45-114">Mniejszy, szybszy i bardziej wydajne, plik wyjściowy był optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="23b45-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="23b45-115">Jednakże, ponieważ optymalizacje powoduje modyfikacji kodu w pliku wyjściowym `/optimize+` może utrudnić debugowania.</span><span class="sxs-lookup"><span data-stu-id="23b45-115">However, because optimizations result in code rearrangement in the output file, `/optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="23b45-116">Wszystkie moduły wygenerowane z `/target:module` dla zestawu musi używać tego samego `/optimize` ustawienia jako zestaw.</span><span class="sxs-lookup"><span data-stu-id="23b45-116">All modules generated with `/target:module` for an assembly must use the same `/optimize` settings as the assembly.</span></span> <span data-ttu-id="23b45-117">Aby uzyskać więcej informacji, zobacz [/TARGET (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="23b45-117">For more information, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="23b45-118">Możesz połączyć ze sobą `/optimize` i `/debug` opcje.</span><span class="sxs-lookup"><span data-stu-id="23b45-118">You can combine the `/optimize` and `/debug` options.</span></span>  
  
|<span data-ttu-id="23b45-119">Aby ustawić / optimize w programie Visual Studio zintegrowane środowisko deweloperskie</span><span class="sxs-lookup"><span data-stu-id="23b45-119">To set /optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="23b45-120">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="23b45-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="23b45-121">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="23b45-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="23b45-122">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="23b45-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="23b45-123">3.  Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="23b45-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="23b45-124">4.  Modyfikowanie **Włącz optymalizacje** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="23b45-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="23b45-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="23b45-125">Example</span></span>  
 <span data-ttu-id="23b45-126">Poniższy kod kompiluje `T2.vb` i włącza optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="23b45-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```  
vbc t2.vb /optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="23b45-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23b45-127">See Also</span></span>  
 [<span data-ttu-id="23b45-128">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="23b45-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="23b45-129">/ Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23b45-129">/debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="23b45-130">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="23b45-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="23b45-131">/ TARGET (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23b45-131">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
