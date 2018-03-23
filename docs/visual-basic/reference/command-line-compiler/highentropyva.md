---
title: -highentropyva (Visual Basic)
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12d40e5acda73786ee88d16bacd9bc5f69400be8
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="a6c36-102">-highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6c36-102">-highentropyva (Visual Basic)</span></span>
<span data-ttu-id="a6c36-103">Wskazuje, czy 64-bitowy wykonywalny lub plik wykonywalny, który został oznaczony przez [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) — opcja kompilatora obsługuje wysokiej entropii losowe generowanie układu przestrzeni adresów (ASLR).</span><span class="sxs-lookup"><span data-stu-id="a6c36-103">Indicates whether a 64-bit executable or an executable that's marked by the [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6c36-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6c36-104">Syntax</span></span>  
  
```  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a6c36-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a6c36-105">Arguments</span></span>  
 <span data-ttu-id="a6c36-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="a6c36-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="a6c36-107">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a6c36-107">Optional.</span></span> <span data-ttu-id="a6c36-108">Opcja jest domyślnie wyłączona lub jeśli określisz `-highentropyva-`.</span><span class="sxs-lookup"><span data-stu-id="a6c36-108">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="a6c36-109">Opcja jest włączona, jeśli można określić `-highentropyva` lub `-highentropyva+`.</span><span class="sxs-lookup"><span data-stu-id="a6c36-109">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6c36-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6c36-110">Remarks</span></span>  
 <span data-ttu-id="a6c36-111">Jeśli określisz tej opcji, zgodne wersje jądra systemu Windows można użyć wyższy stopień entropii podczas jądra wybrać losowo układ przestrzeni adresów procesu jako część ASLR.</span><span class="sxs-lookup"><span data-stu-id="a6c36-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="a6c36-112">Jeśli jądra używa wyższy stopień entropii, większa liczba adresów mogą przydzielone do regiony pamięci, takich jak stosy i stosów.</span><span class="sxs-lookup"><span data-stu-id="a6c36-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="a6c36-113">W związku z tym jest trudniej odgadnąć lokalizacji obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="a6c36-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="a6c36-114">Gdy opcja znajduje się w docelowym pliku wykonywalnego i wszelkich modułów na jego zależności musi mieć możliwość obsługi wartości wskaźnika, które są większe niż 4 gigabajty (GB), gdy te moduły są uruchomione jako procesów 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="a6c36-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6c36-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6c36-115">See Also</span></span>  
 [<span data-ttu-id="a6c36-116">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a6c36-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="a6c36-117">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="a6c36-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
