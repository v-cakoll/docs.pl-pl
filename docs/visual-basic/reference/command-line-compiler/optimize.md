---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: e8daf4a49123623b6470bc3c6281869f1b9b3d0f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005372"
---
# <a name="-optimize"></a><span data-ttu-id="3066b-102">-optimize</span><span class="sxs-lookup"><span data-stu-id="3066b-102">-optimize</span></span>
<span data-ttu-id="3066b-103">Włącza lub wyłącza optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="3066b-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3066b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3066b-104">Syntax</span></span>  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3066b-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3066b-105">Arguments</span></span>  
  
|<span data-ttu-id="3066b-106">Termin</span><span class="sxs-lookup"><span data-stu-id="3066b-106">Term</span></span>|<span data-ttu-id="3066b-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="3066b-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="3066b-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="3066b-108">`+` &#124; `-`</span></span>|<span data-ttu-id="3066b-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3066b-109">Optional.</span></span> <span data-ttu-id="3066b-110">Opcja `-optimize-` wyłącza optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="3066b-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="3066b-111">Opcja `-optimize+` umożliwia optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="3066b-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="3066b-112">Optymalizacje są domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="3066b-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3066b-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3066b-113">Remarks</span></span>  
 <span data-ttu-id="3066b-114">Optymalizacje kompilatora sprawiają, że plik wyjściowy jest mniejszy, szybszy i bardziej wydajny.</span><span class="sxs-lookup"><span data-stu-id="3066b-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="3066b-115">Jednakże, ponieważ optymalizacje powodują zmianę układu kodu w pliku wyjściowym, `-optimize+` może utrudniać debugowanie.</span><span class="sxs-lookup"><span data-stu-id="3066b-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="3066b-116">Wszystkie moduły wygenerowane z `-target:module` dla zestawu muszą używać tych samych ustawień `-optimize` jako zestawu.</span><span class="sxs-lookup"><span data-stu-id="3066b-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="3066b-117">Aby uzyskać więcej informacji, zobacz [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="3066b-117">For more information, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="3066b-118">Można połączyć opcje `-optimize` i `-debug`.</span><span class="sxs-lookup"><span data-stu-id="3066b-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="3066b-119">Aby ustawić-optymalizować w zintegrowanym środowisku programistycznym programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3066b-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="3066b-120">1. zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="3066b-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="3066b-121">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="3066b-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="3066b-122">2. Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="3066b-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="3066b-123">3. kliknij przycisk **Zaawansowane** .</span><span class="sxs-lookup"><span data-stu-id="3066b-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="3066b-124">4. Zmodyfikuj pole wyboru **Włącz optymalizacje** .</span><span class="sxs-lookup"><span data-stu-id="3066b-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3066b-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="3066b-125">Example</span></span>  
 <span data-ttu-id="3066b-126">Poniższy kod kompiluje `T2.vb` i włącza optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="3066b-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="3066b-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3066b-127">See also</span></span>

- [<span data-ttu-id="3066b-128">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3066b-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="3066b-129">-Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3066b-129">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)
- [<span data-ttu-id="3066b-130">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="3066b-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="3066b-131">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3066b-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
