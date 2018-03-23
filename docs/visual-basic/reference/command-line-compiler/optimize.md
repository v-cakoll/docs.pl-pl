---
title: -optimize
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7df1c873c166def9fde1bedc139470263e3e4437
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-optimize"></a><span data-ttu-id="029f8-102">-optimize</span><span class="sxs-lookup"><span data-stu-id="029f8-102">-optimize</span></span>
<span data-ttu-id="029f8-103">Włącza lub wyłącza optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="029f8-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="029f8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="029f8-104">Syntax</span></span>  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="029f8-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="029f8-105">Arguments</span></span>  
  
|<span data-ttu-id="029f8-106">Termin</span><span class="sxs-lookup"><span data-stu-id="029f8-106">Term</span></span>|<span data-ttu-id="029f8-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="029f8-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="029f8-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="029f8-108">`+` &#124; `-`</span></span>|<span data-ttu-id="029f8-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="029f8-109">Optional.</span></span> <span data-ttu-id="029f8-110">`-optimize-` Opcja wyłącza optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="029f8-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="029f8-111">`-optimize+` Opcja włącza optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="029f8-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="029f8-112">Optymalizacje są domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="029f8-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="029f8-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="029f8-113">Remarks</span></span>  
 <span data-ttu-id="029f8-114">Mniejszy, szybszy i bardziej wydajne, plik wyjściowy był optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="029f8-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="029f8-115">Jednakże, ponieważ optymalizacje powoduje modyfikacji kodu w pliku wyjściowym `-optimize+` może utrudnić debugowania.</span><span class="sxs-lookup"><span data-stu-id="029f8-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="029f8-116">Wszystkie moduły wygenerowane z `-target:module` dla zestawu musi używać tego samego `-optimize` ustawienia jako zestaw.</span><span class="sxs-lookup"><span data-stu-id="029f8-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="029f8-117">Aby uzyskać więcej informacji, zobacz [-docelowego (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="029f8-117">For more information, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="029f8-118">Możesz połączyć ze sobą `-optimize` i `-debug` opcje.</span><span class="sxs-lookup"><span data-stu-id="029f8-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="029f8-119">Aby ustawić - optymalizowania w Visual Studio zintegrowane środowisko programistyczne</span><span class="sxs-lookup"><span data-stu-id="029f8-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="029f8-120">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="029f8-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="029f8-121">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="029f8-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="029f8-122">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="029f8-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="029f8-123">3.  Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="029f8-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="029f8-124">4.  Modyfikowanie **Włącz optymalizacje** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="029f8-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="029f8-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="029f8-125">Example</span></span>  
 <span data-ttu-id="029f8-126">Poniższy kod kompiluje `T2.vb` i włącza optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="029f8-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="029f8-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="029f8-127">See Also</span></span>  
 [<span data-ttu-id="029f8-128">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="029f8-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="029f8-129">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="029f8-129">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="029f8-130">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="029f8-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="029f8-131">-docelowego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="029f8-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
