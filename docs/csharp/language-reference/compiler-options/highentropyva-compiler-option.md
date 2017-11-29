---
title: -highentropyva (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5746caed8c1bf61038c97a49987c4c168eef9f3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="highentropyva-c-compiler-options"></a><span data-ttu-id="dbedc-102">/highentropyva (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="dbedc-102">/highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="dbedc-103">**/Highentropyva** — opcja kompilatora informuje jądra systemu Windows, czy określonego pliku wykonywalnego obsługuje wysokiej entropii losowe generowanie układu przestrzeni adresów (ASLR).</span><span class="sxs-lookup"><span data-stu-id="dbedc-103">The **/highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbedc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dbedc-104">Syntax</span></span>  
  
```console  
/highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="dbedc-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="dbedc-105">Arguments</span></span>  
 <span data-ttu-id="dbedc-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="dbedc-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="dbedc-107">Ta opcja określa, że 64-bitowy wykonywalny lub plik wykonywalny, który został oznaczony przez [/platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) — opcja kompilatora obsługuje wysokiej entropii wirtualnej przestrzeni adresowej.</span><span class="sxs-lookup"><span data-stu-id="dbedc-107">This option specifies that a 64-bit executable or an executable that is marked by the [/platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="dbedc-108">Opcja jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="dbedc-108">The option is disabled by default.</span></span> <span data-ttu-id="dbedc-109">Użyj **/highentropyva+** lub **/highentropyva** ją włączyć.</span><span class="sxs-lookup"><span data-stu-id="dbedc-109">Use **/highentropyva+** or **/highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbedc-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dbedc-110">Remarks</span></span>  
 <span data-ttu-id="dbedc-111">**/Highentropyva** opcja umożliwia zgodne wersje jądra systemu Windows, aby użyć wyższy stopień entropii podczas losowego generowania układu przestrzeni adresów procesu jako część ASLR.</span><span class="sxs-lookup"><span data-stu-id="dbedc-111">The **/highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="dbedc-112">Użycie wyższy stopień entropii oznacza, że większej liczby adresy mogą być przydzielone do regiony pamięci, takich jak stosy i stosów.</span><span class="sxs-lookup"><span data-stu-id="dbedc-112">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="dbedc-113">W związku z tym jest trudniej odgadnąć lokalizacji obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="dbedc-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="dbedc-114">Gdy **/highentropyva** określono opcję kompilatora, element docelowy pliku wykonywalnego i wszelkich modułów, których zależy musi mieć możliwość obsługi wartości wskaźnika, które są większe niż 4 gigabajty (GB), gdy są na nich uruchomione jako proces 64-bitowy.</span><span class="sxs-lookup"><span data-stu-id="dbedc-114">When the **/highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
