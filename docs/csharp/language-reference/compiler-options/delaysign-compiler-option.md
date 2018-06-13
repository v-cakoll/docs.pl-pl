---
title: -delaysign (opcje kompilatora C#)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 72dcba3b506dae42f67f0421ba92efee18274c37
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472649"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="0c116-102">-delaysign (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="0c116-102">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="0c116-103">Ta opcja powoduje, że kompilator zarezerwowanego miejsca w pliku wyjściowym, tak aby później można dodać podpisu cyfrowego.</span><span class="sxs-lookup"><span data-stu-id="0c116-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="0c116-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c116-104">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="0c116-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0c116-105">Arguments</span></span>

<span data-ttu-id="0c116-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="0c116-106">`+` &#124; `-`</span></span>

<span data-ttu-id="0c116-107">Użyj **- delaysign —** Jeśli chcesz całkowicie podpisane zestawu.</span><span class="sxs-lookup"><span data-stu-id="0c116-107">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="0c116-108">Użyj **- delaysign +** Jeśli chcesz umieścić klucz publiczny w zestawie.</span><span class="sxs-lookup"><span data-stu-id="0c116-108">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="0c116-109">Wartość domyślna to **- delaysign —**.</span><span class="sxs-lookup"><span data-stu-id="0c116-109">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c116-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c116-110">Remarks</span></span>

<span data-ttu-id="0c116-111">**- Delaysign** opcja nie ma znaczenia, chyba że używana z [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) lub [- keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="0c116-111">The **-delaysign** option has no effect unless used with [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) or [-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="0c116-112">**- Delaysign** i **- publicsign** wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="0c116-112">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="0c116-113">Gdy użytkownik żąda zestawem całkowicie podpisane, kompilator tworzy skrót pliku, który zawiera manifest (metadanych zestawu) i podpisuje ten skrót z kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="0c116-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="0c116-114">Tej operacji tworzy podpis cyfrowy, który jest przechowywany w pliku, który zawiera manifest.</span><span class="sxs-lookup"><span data-stu-id="0c116-114">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="0c116-115">Jeśli zestaw jest podpisywany z opóźnieniem, kompilator nie obliczania i przechowywania podpisu, ale rezerw miejsca w pliku, aby później można dodać podpisu.</span><span class="sxs-lookup"><span data-stu-id="0c116-115">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="0c116-116">Na przykład za pomocą **- delaysign +** umożliwia tester do umieszczenia zestawu w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="0c116-116">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="0c116-117">Po zakończeniu testowania, możesz się zalogować zestawu pełni przez umieszczenie w zestawie przy użyciu klucza prywatnego [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="0c116-117">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="0c116-118">Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) i [opóźnione podpisywanie zestawu](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="0c116-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="0c116-119">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0c116-119">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="0c116-120">Otwórz **właściwości** strony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="0c116-120">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="0c116-121">Modyfikowanie **opóźnienie tylko znak** właściwości.</span><span class="sxs-lookup"><span data-stu-id="0c116-121">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="0c116-122">Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="0c116-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c116-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c116-123">See Also</span></span>

 [<span data-ttu-id="0c116-124">Opcja - publicsign C#</span><span class="sxs-lookup"><span data-stu-id="0c116-124">C# -publicsign option</span></span>](publicsign-compiler-option.md)  
 [<span data-ttu-id="0c116-125">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="0c116-125">C# Compiler Options</span></span>](index.md)  
 [<span data-ttu-id="0c116-126">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="0c116-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
