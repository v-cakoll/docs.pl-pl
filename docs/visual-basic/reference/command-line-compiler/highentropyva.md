---
title: -highentropyva
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 9501ea46eb13baa171208e20d0c9645d118c4301
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408624"
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="43c91-102">-HIGHENTROPYVA (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43c91-102">-highentropyva (Visual Basic)</span></span>
<span data-ttu-id="43c91-103">Wskazuje, czy 64-bitowy plik wykonywalny lub plik wykonywalny, który jest oznaczony przez [-platformą: anycpu](platform.md) , opcja kompilatora o wysokiej entropii (ASLR).</span><span class="sxs-lookup"><span data-stu-id="43c91-103">Indicates whether a 64-bit executable or an executable that's marked by the [-platform:anycpu](platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43c91-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43c91-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="43c91-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="43c91-105">Arguments</span></span>  
 <span data-ttu-id="43c91-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="43c91-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="43c91-107">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="43c91-107">Optional.</span></span> <span data-ttu-id="43c91-108">Opcja jest domyślnie wyłączona lub jeśli określono `-highentropyva-` .</span><span class="sxs-lookup"><span data-stu-id="43c91-108">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="43c91-109">Opcja jest włączona, jeśli określono `-highentropyva` lub `-highentropyva+` .</span><span class="sxs-lookup"><span data-stu-id="43c91-109">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43c91-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43c91-110">Remarks</span></span>  
 <span data-ttu-id="43c91-111">W przypadku wybrania tej opcji zgodne wersje jądra systemu Windows mogą używać wyższych stopni entropii, gdy jądro losowo rozmieszczenie przestrzeni adresowej procesu w ramach ASLR.</span><span class="sxs-lookup"><span data-stu-id="43c91-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="43c91-112">Jeśli jądro używa wyższych stopni entropii, można przydzielać większą liczbę adresów do regionów pamięci, takich jak stosy i sterty.</span><span class="sxs-lookup"><span data-stu-id="43c91-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="43c91-113">W związku z tym trudniejsze jest odpuszczenie lokalizacji określonego obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="43c91-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="43c91-114">Gdy opcja jest włączona, docelowy plik wykonywalny i wszystkie moduły, od których zależy, muszą być w stanie obsłużyć wartości wskaźników, które są większe niż 4 gigabajty (GB), gdy te moduły działają jako procesy 64-bitowe.</span><span class="sxs-lookup"><span data-stu-id="43c91-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43c91-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43c91-115">See also</span></span>

- [<span data-ttu-id="43c91-116">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43c91-116">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="43c91-117">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="43c91-117">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
