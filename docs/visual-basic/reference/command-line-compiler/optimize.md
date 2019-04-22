---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: eb84e0a7038e7ff8cb399ac7222b6ac1661b5bc1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842164"
---
# <a name="-optimize"></a><span data-ttu-id="ad7bb-102">-optimize</span><span class="sxs-lookup"><span data-stu-id="ad7bb-102">-optimize</span></span>
<span data-ttu-id="ad7bb-103">Włącza lub wyłącza optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad7bb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad7bb-104">Syntax</span></span>  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ad7bb-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ad7bb-105">Arguments</span></span>  
  
|<span data-ttu-id="ad7bb-106">Termin</span><span class="sxs-lookup"><span data-stu-id="ad7bb-106">Term</span></span>|<span data-ttu-id="ad7bb-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="ad7bb-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="ad7bb-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="ad7bb-108">`+` &#124; `-`</span></span>|<span data-ttu-id="ad7bb-109">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-109">Optional.</span></span> <span data-ttu-id="ad7bb-110">`-optimize-` Opcja wyłącza optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="ad7bb-111">`-optimize+` Opcja włącza optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="ad7bb-112">Domyślnie są wyłączone optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad7bb-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad7bb-113">Remarks</span></span>  
 <span data-ttu-id="ad7bb-114">Plik wyjściowy był optymalizacje kompilatora, mniejszy, szybszy i bardziej wydajne.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="ad7bb-115">Jednakże, ponieważ optymalizacje powoduje modyfikacji kodu w pliku wyjściowym `-optimize+` może utrudnić debugowanie.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="ad7bb-116">Wszystkie moduły, wygenerowane za pomocą `-target:module` dla zestawu musi używać tego samego `-optimize` ustawienia zgodnie z zestawu.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="ad7bb-117">Aby uzyskać więcej informacji, zobacz [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="ad7bb-117">For more information, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="ad7bb-118">Można połączyć `-optimize` i `-debug` opcje.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="ad7bb-119">Aby ustawić - optymalizacji w programie Visual Studio zintegrowanego środowiska programistycznego</span><span class="sxs-lookup"><span data-stu-id="ad7bb-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="ad7bb-120">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ad7bb-121">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="ad7bb-122">2.  Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="ad7bb-123">3.  Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="ad7bb-124">4.  Modyfikowanie **Włącz optymalizacje** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ad7bb-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad7bb-125">Example</span></span>  
 <span data-ttu-id="ad7bb-126">Poniższy kod kompiluje `T2.vb` i umożliwia optymalizacje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="ad7bb-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad7bb-127">See also</span></span>

- [<span data-ttu-id="ad7bb-128">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ad7bb-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="ad7bb-129">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad7bb-129">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)
- [<span data-ttu-id="ad7bb-130">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="ad7bb-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="ad7bb-131">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad7bb-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
