---
title: -highentropyva (C# Compiler Options)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: 2ff63ddc48a4f5c4287fe1badb092a1db93f68dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662858"
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="bd13e-102">-highentropyva (C# Compiler Options)</span><span class="sxs-lookup"><span data-stu-id="bd13e-102">-highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="bd13e-103">**- Highentropyva** jądra Windows informuje o — opcja kompilatora czy określonego pliku wykonywalnego obsługuje o wysokiej entropii adres miejsca układ losowe (ASLR).</span><span class="sxs-lookup"><span data-stu-id="bd13e-103">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd13e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd13e-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="bd13e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="bd13e-105">Arguments</span></span>  
 <span data-ttu-id="bd13e-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="bd13e-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="bd13e-107">Ta opcja określa, że 64-bitowy plik wykonywalny lub plik wykonywalny, który jest oznaczony za [— platforma: anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) — opcja kompilatora obsługuje przestrzeni adresów wirtualnych o wysokiej entropii.</span><span class="sxs-lookup"><span data-stu-id="bd13e-107">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="bd13e-108">Opcja jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="bd13e-108">The option is disabled by default.</span></span> <span data-ttu-id="bd13e-109">Użyj **- highentropyva +** lub **- highentropyva** ją włączyć.</span><span class="sxs-lookup"><span data-stu-id="bd13e-109">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd13e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd13e-110">Remarks</span></span>  
 <span data-ttu-id="bd13e-111">**- Highentropyva** opcja umożliwia zgodne wersje jądra Windows do użycia wyższy stopień entropii podczas losowego generowania układu przestrzeni adresów procesu jako część ASLR.</span><span class="sxs-lookup"><span data-stu-id="bd13e-111">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="bd13e-112">Użycie wyższy stopień entropii oznacza, że większa liczba adresów może być przydzielona do regiony pamięci, takie jak stosy i stosów.</span><span class="sxs-lookup"><span data-stu-id="bd13e-112">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="bd13e-113">W rezultacie jego trudniej jest intruzowi zgadnąć lokalizację konkretnego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="bd13e-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="bd13e-114">Gdy **- highentropyva** — opcja kompilatora jest określony, obiektu docelowego pliku wykonywalnego i wszystkie moduły, od których zależy musi być w stanie obsłużyć wartości wskaźnika, które są większe niż 4 gigabajty (GB), uruchamianego jako procesu 64-bitowego.</span><span class="sxs-lookup"><span data-stu-id="bd13e-114">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
