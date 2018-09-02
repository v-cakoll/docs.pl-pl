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
ms.openlocfilehash: 105f564d40799c1c006caf8b59d6199dbd8e9318
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400199"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="de421-102">-delaysign (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="de421-102">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="de421-103">Ta opcja powoduje, że kompilator, aby zarezerwować miejsce, w pliku wyjściowym, tak aby później można dodać podpisu cyfrowego.</span><span class="sxs-lookup"><span data-stu-id="de421-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="de421-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="de421-104">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="de421-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="de421-105">Arguments</span></span>

<span data-ttu-id="de421-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="de421-106">`+` &#124; `-`</span></span>

<span data-ttu-id="de421-107">Użyj **- delaysign —** Jeśli chcesz, aby podpisać zestaw całkowicie.</span><span class="sxs-lookup"><span data-stu-id="de421-107">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="de421-108">Użyj **- delaysign +** Jeśli chcesz tylko umieścić klucz publiczny w zestawie.</span><span class="sxs-lookup"><span data-stu-id="de421-108">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="de421-109">Wartość domyślna to **- delaysign —**.</span><span class="sxs-lookup"><span data-stu-id="de421-109">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="de421-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de421-110">Remarks</span></span>

<span data-ttu-id="de421-111">**- Delaysign** opcja nie ma wpływu, chyba że używana z [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) lub [- keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="de421-111">The **-delaysign** option has no effect unless used with [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) or [-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="de421-112">**- Delaysign** i **- publicsign** opcje wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="de421-112">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="de421-113">W przypadku żądania całkowicie podpisanego zestawu, kompilator tworzy skrót pliku który zawiera manifest (metadane zestawu) i podpisuje skrót przy użyciu klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="de421-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="de421-114">Ta operacja tworzy podpis cyfrowy, który jest przechowywany w pliku, który zawiera manifest.</span><span class="sxs-lookup"><span data-stu-id="de421-114">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="de421-115">Gdy zestaw jest podpisany z opóźnieniem, kompilator nie obliczeniowe i przechowuj podpisu, ale rezerwuje miejsce w pliku, aby podpis mógł zostać dodany później.</span><span class="sxs-lookup"><span data-stu-id="de421-115">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="de421-116">Na przykład za pomocą **- delaysign +** umożliwia testerowi umieszczenie zestawu w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="de421-116">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="de421-117">Po zakończeniu testowania można całkowicie podpisać zestaw, umieszczając klucza prywatnego w zestawie przy użyciu [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="de421-117">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="de421-118">Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) i [opóźnienie podpisywania zestawu](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="de421-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="de421-119">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="de421-119">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="de421-120">Otwórz **właściwości** strony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="de421-120">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="de421-121">Modyfikowanie **opóźnienie logowania tylko** właściwości.</span><span class="sxs-lookup"><span data-stu-id="de421-121">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="de421-122">Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="de421-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="de421-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="de421-123">See Also</span></span>

- [<span data-ttu-id="de421-124">Opcja - publicsign C#</span><span class="sxs-lookup"><span data-stu-id="de421-124">C# -publicsign option</span></span>](publicsign-compiler-option.md)  
- [<span data-ttu-id="de421-125">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="de421-125">C# Compiler Options</span></span>](index.md)  
- [<span data-ttu-id="de421-126">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="de421-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
