---
title: -highentropyva (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: 2ff63ddc48a4f5c4287fe1badb092a1db93f68dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216681"
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="b2e9c-102">-highentropyva (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="b2e9c-102">-highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="b2e9c-103">**- Highentropyva** — opcja kompilatora informuje jądra systemu Windows, czy określonego pliku wykonywalnego obsługuje wysokiej entropii losowe generowanie układu przestrzeni adresów (ASLR).</span><span class="sxs-lookup"><span data-stu-id="b2e9c-103">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2e9c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2e9c-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="b2e9c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b2e9c-105">Arguments</span></span>  
 <span data-ttu-id="b2e9c-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="b2e9c-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="b2e9c-107">Ta opcja określa, że 64-bitowy wykonywalny lub plik wykonywalny, który został oznaczony przez [-platformy: anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) — opcja kompilatora obsługuje wysokiej entropii wirtualnej przestrzeni adresowej.</span><span class="sxs-lookup"><span data-stu-id="b2e9c-107">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="b2e9c-108">Opcja jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="b2e9c-108">The option is disabled by default.</span></span> <span data-ttu-id="b2e9c-109">Użyj **- highentropyva +** lub **- highentropyva** ją włączyć.</span><span class="sxs-lookup"><span data-stu-id="b2e9c-109">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2e9c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2e9c-110">Remarks</span></span>  
 <span data-ttu-id="b2e9c-111">**- Highentropyva** opcja umożliwia zgodne wersje jądra systemu Windows, aby użyć wyższy stopień entropii podczas losowego generowania układu przestrzeni adresów procesu jako część ASLR.</span><span class="sxs-lookup"><span data-stu-id="b2e9c-111">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="b2e9c-112">Użycie wyższy stopień entropii oznacza, że większej liczby adresy mogą być przydzielone do regiony pamięci, takich jak stosy i stosów.</span><span class="sxs-lookup"><span data-stu-id="b2e9c-112">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="b2e9c-113">W związku z tym jest trudniej odgadnąć lokalizacji obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="b2e9c-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="b2e9c-114">Gdy **- highentropyva** określono opcję kompilatora, element docelowy pliku wykonywalnego i wszelkich modułów, których zależy musi mieć możliwość obsługi wartości wskaźnika, które są większe niż 4 gigabajty (GB), gdy są na nich uruchomione jako proces 64-bitowy.</span><span class="sxs-lookup"><span data-stu-id="b2e9c-114">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
