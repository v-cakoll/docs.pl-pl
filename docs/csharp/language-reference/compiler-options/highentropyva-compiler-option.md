---
title: -highentropyva (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: b710bb829f6a7591159d2f2e6bacc670d21c42d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606846"
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="4d884-102">-highentropyva (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="4d884-102">-highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="4d884-103">Opcja kompilatora **-highentropyva** informuje jądro systemu Windows, czy dany plik wykonywalny obsługuje randomizację układu przestrzeni adresowej (ASLR) o wysokiej entropii.</span><span class="sxs-lookup"><span data-stu-id="4d884-103">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d884-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d884-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4d884-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4d884-105">Arguments</span></span>  
 <span data-ttu-id="4d884-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="4d884-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="4d884-107">Ta opcja określa, że 64-bitowy plik wykonywalny lub plik wykonywalny oznaczony opcją kompilatora [-platform:anycpu](./platform-compiler-option.md) obsługuje wirtualną przestrzeń adresową o wysokiej entropii.</span><span class="sxs-lookup"><span data-stu-id="4d884-107">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](./platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="4d884-108">Opcja jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="4d884-108">The option is disabled by default.</span></span> <span data-ttu-id="4d884-109">Użyj **-highentropyva+** lub **-highentropyva,** aby go włączyć.</span><span class="sxs-lookup"><span data-stu-id="4d884-109">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d884-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d884-110">Remarks</span></span>  
 <span data-ttu-id="4d884-111">Opcja **-highentropyva** umożliwia zgodnym wersjom jądra systemu Windows użycie wyższych stopni entropii podczas losowania układu przestrzeni adresowej procesu jako części ASLR.</span><span class="sxs-lookup"><span data-stu-id="4d884-111">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="4d884-112">Przy użyciu wyższych stopni entropii oznacza, że większa liczba adresów mogą być przydzielane do regionów pamięci, takich jak stosy i sterty.</span><span class="sxs-lookup"><span data-stu-id="4d884-112">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="4d884-113">W rezultacie trudniej jest odgadnąć lokalizację określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="4d884-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="4d884-114">Po określeniu opcji kompilatora **-highentropyva** docelowy plik wykonywalny i wszystkie moduły, od których zależy, muszą być w stanie obsługiwać wartości wskaźnika, które są większe niż 4 gigabajty (GB), gdy są uruchomione jako proces 64-bitowy.</span><span class="sxs-lookup"><span data-stu-id="4d884-114">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
