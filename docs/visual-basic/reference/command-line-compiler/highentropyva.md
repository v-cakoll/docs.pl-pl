---
title: -HIGHENTROPYVA (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 58026ff84f1ff501bf767adebcfc01f7de5bf4a4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005583"
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="45424-102">-HIGHENTROPYVA (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45424-102">-highentropyva (Visual Basic)</span></span>
<span data-ttu-id="45424-103">Wskazuje, czy 64-bitowy plik wykonywalny lub plik wykonywalny, który jest oznaczony przez opcję kompilatora [/platform: anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) obsługuje generowanie losowe układu przestrzeni adresowej o wysokiej entropii (ASLR).</span><span class="sxs-lookup"><span data-stu-id="45424-103">Indicates whether a 64-bit executable or an executable that's marked by the [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45424-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="45424-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="45424-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="45424-105">Arguments</span></span>  
 <span data-ttu-id="45424-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="45424-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="45424-107">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="45424-107">Optional.</span></span> <span data-ttu-id="45424-108">Opcja jest domyślnie wyłączona lub jeśli określono `-highentropyva-`.</span><span class="sxs-lookup"><span data-stu-id="45424-108">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="45424-109">Opcja jest włączona, jeśli określono `-highentropyva` lub `-highentropyva+`.</span><span class="sxs-lookup"><span data-stu-id="45424-109">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45424-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="45424-110">Remarks</span></span>  
 <span data-ttu-id="45424-111">W przypadku wybrania tej opcji zgodne wersje jądra systemu Windows mogą używać wyższych stopni entropii, gdy jądro losowo rozmieszczenie przestrzeni adresowej procesu w ramach ASLR.</span><span class="sxs-lookup"><span data-stu-id="45424-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="45424-112">Jeśli jądro używa wyższych stopni entropii, można przydzielać większą liczbę adresów do regionów pamięci, takich jak stosy i sterty.</span><span class="sxs-lookup"><span data-stu-id="45424-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="45424-113">W związku z tym trudniejsze jest odpuszczenie lokalizacji określonego obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="45424-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="45424-114">Gdy opcja jest włączona, docelowy plik wykonywalny i wszystkie moduły, od których zależy, muszą być w stanie obsłużyć wartości wskaźników, które są większe niż 4 gigabajty (GB), gdy te moduły działają jako procesy 64-bitowe.</span><span class="sxs-lookup"><span data-stu-id="45424-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45424-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45424-115">See also</span></span>

- [<span data-ttu-id="45424-116">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="45424-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="45424-117">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="45424-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
