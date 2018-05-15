---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: 2f066835c5f864538f281d4c58772e0e60c132f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-optimize"></a><span data-ttu-id="1091f-102">-optimize</span><span class="sxs-lookup"><span data-stu-id="1091f-102">-optimize</span></span>
<span data-ttu-id="1091f-103">Włącza lub wyłącza optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="1091f-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1091f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1091f-104">Syntax</span></span>  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1091f-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1091f-105">Arguments</span></span>  
  
|<span data-ttu-id="1091f-106">Termin</span><span class="sxs-lookup"><span data-stu-id="1091f-106">Term</span></span>|<span data-ttu-id="1091f-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="1091f-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="1091f-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="1091f-108">`+` &#124; `-`</span></span>|<span data-ttu-id="1091f-109">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1091f-109">Optional.</span></span> <span data-ttu-id="1091f-110">`-optimize-` Opcja wyłącza optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="1091f-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="1091f-111">`-optimize+` Opcja włącza optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="1091f-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="1091f-112">Optymalizacje są domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="1091f-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1091f-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1091f-113">Remarks</span></span>  
 <span data-ttu-id="1091f-114">Mniejszy, szybszy i bardziej wydajne, plik wyjściowy był optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="1091f-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="1091f-115">Jednakże, ponieważ optymalizacje powoduje modyfikacji kodu w pliku wyjściowym `-optimize+` może utrudnić debugowania.</span><span class="sxs-lookup"><span data-stu-id="1091f-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="1091f-116">Wszystkie moduły wygenerowane z `-target:module` dla zestawu musi używać tego samego `-optimize` ustawienia jako zestaw.</span><span class="sxs-lookup"><span data-stu-id="1091f-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="1091f-117">Aby uzyskać więcej informacji, zobacz [-docelowego (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="1091f-117">For more information, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="1091f-118">Możesz połączyć ze sobą `-optimize` i `-debug` opcje.</span><span class="sxs-lookup"><span data-stu-id="1091f-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="1091f-119">Aby ustawić - optymalizowania w Visual Studio zintegrowane środowisko programistyczne</span><span class="sxs-lookup"><span data-stu-id="1091f-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="1091f-120">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="1091f-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1091f-121">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="1091f-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="1091f-122">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="1091f-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="1091f-123">3.  Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="1091f-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="1091f-124">4.  Modyfikowanie **Włącz optymalizacje** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="1091f-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1091f-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="1091f-125">Example</span></span>  
 <span data-ttu-id="1091f-126">Poniższy kod kompiluje `T2.vb` i włącza optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="1091f-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="1091f-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1091f-127">See Also</span></span>  
 [<span data-ttu-id="1091f-128">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1091f-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1091f-129">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1091f-129">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="1091f-130">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="1091f-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="1091f-131">-docelowego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1091f-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
