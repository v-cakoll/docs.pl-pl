---
title: -delaysign (C# opcje kompilatora)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: ae309a8de6c4691f0009e5beb8ac2adc8772805b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603029"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="51acd-102">-delaysign (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="51acd-102">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="51acd-103">Ta opcja powoduje, że kompilator rezerwuje miejsce w pliku wyjściowym, aby można było później dodać podpis cyfrowy.</span><span class="sxs-lookup"><span data-stu-id="51acd-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="51acd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="51acd-104">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="51acd-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="51acd-105">Arguments</span></span>

<span data-ttu-id="51acd-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="51acd-106">`+` &#124; `-`</span></span>

<span data-ttu-id="51acd-107">Użyj **-delaysign —** Jeśli chcesz użyć w pełni podpisanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="51acd-107">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="51acd-108">Użyj **-delaysign +** , jeśli chcesz umieścić klucz publiczny w zestawie.</span><span class="sxs-lookup"><span data-stu-id="51acd-108">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="51acd-109">Wartość domyślna to **-delaysign-** .</span><span class="sxs-lookup"><span data-stu-id="51acd-109">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="51acd-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="51acd-110">Remarks</span></span>

<span data-ttu-id="51acd-111">Opcja **-delaysign** nie ma żadnego efektu, chyba że jest używana z atrybutem [-KeyFile](./keyfile-compiler-option.md) lub [-Container](./keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="51acd-111">The **-delaysign** option has no effect unless used with [-keyfile](./keyfile-compiler-option.md) or [-keycontainer](./keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="51acd-112">Opcje **-delaysign** i **-publicsign** wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="51acd-112">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="51acd-113">Po zażądaniu w pełni podpisanego zestawu, kompilator skrótów pliku, który zawiera manifest (metadane zestawu) i podpisuje ten skrót z kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="51acd-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="51acd-114">Ta operacja tworzy podpis cyfrowy, który jest przechowywany w pliku, który zawiera manifest.</span><span class="sxs-lookup"><span data-stu-id="51acd-114">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="51acd-115">Gdy zestaw jest podpisany z opóźnieniem, kompilator nie oblicza i nie przechowuje podpisu, ale rezerwuje miejsce w pliku, aby podpis mógł zostać dodany później.</span><span class="sxs-lookup"><span data-stu-id="51acd-115">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="51acd-116">Na przykład przy użyciu polecenia **-delaysign +** umożliwia testerowi umieszczenie zestawu w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="51acd-116">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="51acd-117">Po przetestowaniu można w pełni podpisać zestaw, umieszczając klucz prywatny w zestawie przy użyciu narzędzia [konsolidatora zestawu](../../../framework/tools/al-exe-assembly-linker.md) .</span><span class="sxs-lookup"><span data-stu-id="51acd-117">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="51acd-118">Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnych nazwach](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) oraz [opóźnienie podpisywania zestawu](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="51acd-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="51acd-119">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="51acd-119">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="51acd-120">Otwórz stronę **Właściwości** dla projektu.</span><span class="sxs-lookup"><span data-stu-id="51acd-120">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="51acd-121">Zmodyfikuj właściwość **opóźnienia tylko do podpisywania** .</span><span class="sxs-lookup"><span data-stu-id="51acd-121">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="51acd-122">Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>tę opcję kompilatora, zobacz.</span><span class="sxs-lookup"><span data-stu-id="51acd-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="51acd-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51acd-123">See also</span></span>

- [<span data-ttu-id="51acd-124">C#-publicsign — opcja</span><span class="sxs-lookup"><span data-stu-id="51acd-124">C# -publicsign option</span></span>](publicsign-compiler-option.md)
- [<span data-ttu-id="51acd-125">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="51acd-125">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="51acd-126">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="51acd-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
