---
title: -highentropyva (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 5d948817d4bc71aa31c5890f6740248f4c309588
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181504"
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="1ebfa-102">-highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ebfa-102">-highentropyva (Visual Basic)</span></span>
<span data-ttu-id="1ebfa-103">Wskazuje, czy 64-bitowy plik wykonywalny lub plik wykonywalny, który jest oznaczony za [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) — opcja kompilatora obsługuje o wysokiej entropii adres miejsca układ losowe (ASLR).</span><span class="sxs-lookup"><span data-stu-id="1ebfa-103">Indicates whether a 64-bit executable or an executable that's marked by the [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ebfa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ebfa-104">Syntax</span></span>  
  
```  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1ebfa-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1ebfa-105">Arguments</span></span>  
 <span data-ttu-id="1ebfa-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="1ebfa-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="1ebfa-107">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1ebfa-107">Optional.</span></span> <span data-ttu-id="1ebfa-108">Opcja jest domyślnie wyłączona, lub jeśli określisz `-highentropyva-`.</span><span class="sxs-lookup"><span data-stu-id="1ebfa-108">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="1ebfa-109">Opcja jest włączona, jeśli określisz `-highentropyva` lub `-highentropyva+`.</span><span class="sxs-lookup"><span data-stu-id="1ebfa-109">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ebfa-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ebfa-110">Remarks</span></span>  
 <span data-ttu-id="1ebfa-111">Jeśli ta opcja jest określona, zgodne wersje jądra Windows użyć wyższy stopień entropii jądra wybiera losowo układ przestrzeni adresów procesu jako część ASLR.</span><span class="sxs-lookup"><span data-stu-id="1ebfa-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="1ebfa-112">Jeśli jądro używa wyższy stopień entropii, większej liczby adresów można przydzielić do regionów pamięci, takich jak stosy i stosów.</span><span class="sxs-lookup"><span data-stu-id="1ebfa-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="1ebfa-113">W rezultacie jego trudniej jest intruzowi zgadnąć lokalizację konkretnego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="1ebfa-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="1ebfa-114">Gdy opcja jest na docelowego pliku wykonywalnego i moduły, w której jest to uzależnione należy obsługi wartości wskaźnika, które są większe niż 4 gigabajty (GB), gdy te moduły są uruchomione jako procesy 64-bitowe.</span><span class="sxs-lookup"><span data-stu-id="1ebfa-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ebfa-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ebfa-115">See Also</span></span>  
 [<span data-ttu-id="1ebfa-116">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ebfa-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1ebfa-117">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="1ebfa-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
