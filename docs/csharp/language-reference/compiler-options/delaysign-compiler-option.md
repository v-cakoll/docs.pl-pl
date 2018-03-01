---
title: -delaysign (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a931dccb2aebd2c898b55f0a007d9fac8da42f2e
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2018
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="a2606-102">-delaysign (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="a2606-102">-delaysign (C# Compiler Options)</span></span>
<span data-ttu-id="a2606-103">Ta opcja powoduje, że kompilator zarezerwowanego miejsca w pliku wyjściowym, tak aby później można dodać podpisu cyfrowego.</span><span class="sxs-lookup"><span data-stu-id="a2606-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2606-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2606-104">Syntax</span></span>  
  
```console  
-delaysign[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a2606-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a2606-105">Arguments</span></span>  
 <span data-ttu-id="a2606-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="a2606-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="a2606-107">Użyj **- delaysign —** Jeśli chcesz całkowicie podpisane zestawu.</span><span class="sxs-lookup"><span data-stu-id="a2606-107">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="a2606-108">Użyj **- delaysign +** Jeśli chcesz umieścić klucz publiczny w zestawie.</span><span class="sxs-lookup"><span data-stu-id="a2606-108">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="a2606-109">Wartość domyślna to **- delaysign —**.</span><span class="sxs-lookup"><span data-stu-id="a2606-109">The default is **-delaysign-**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2606-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2606-110">Remarks</span></span>  
 <span data-ttu-id="a2606-111">**- Delaysign** opcja nie ma znaczenia, chyba że używana z [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) lub [- keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="a2606-111">The **-delaysign** option has no effect unless used with [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) or [-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span></span>  
  
 <span data-ttu-id="a2606-112">Gdy użytkownik żąda zestawem całkowicie podpisane, kompilator tworzy skrót pliku, który zawiera manifest (metadanych zestawu) i podpisuje ten skrót z kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="a2606-112">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="a2606-113">Wynikowy podpis cyfrowy jest przechowywany w pliku, który zawiera manifest.</span><span class="sxs-lookup"><span data-stu-id="a2606-113">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="a2606-114">Jeśli zestaw jest podpisywany z opóźnieniem, kompilator nie obliczania i przechowywania podpisu, ale rezerw miejsca w pliku, aby później można dodać podpisu.</span><span class="sxs-lookup"><span data-stu-id="a2606-114">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="a2606-115">Na przykład za pomocą **- delaysign +** umożliwia tester do umieszczenia zestawu w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a2606-115">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="a2606-116">Po zakończeniu testowania, możesz się zalogować zestawu pełni przez umieszczenie w zestawie przy użyciu klucza prywatnego [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="a2606-116">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>  
  
 <span data-ttu-id="a2606-117">Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) i [opóźnione podpisywanie zestawu](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="a2606-117">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a2606-118">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a2606-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="a2606-119">Otwórz **właściwości** strony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="a2606-119">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="a2606-120">Modyfikowanie **opóźnienie tylko znak** właściwości.</span><span class="sxs-lookup"><span data-stu-id="a2606-120">Modify the **Delay sign only** property.</span></span>  
  
 <span data-ttu-id="a2606-121">Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2606-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2606-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2606-122">See Also</span></span>  
 [<span data-ttu-id="a2606-123">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="a2606-123">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="a2606-124">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a2606-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
