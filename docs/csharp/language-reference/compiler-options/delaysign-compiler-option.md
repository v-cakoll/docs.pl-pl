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
ms.openlocfilehash: 9fdc02c22d9d8c8a709155e43a17ebf0d86dfd69
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970447"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="a1c49-102">-delaysign (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="a1c49-102">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="a1c49-103">Ta opcja powoduje, że kompilator rezerwuje miejsce w pliku wyjściowym, aby można było później dodać podpis cyfrowy.</span><span class="sxs-lookup"><span data-stu-id="a1c49-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="a1c49-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1c49-104">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="a1c49-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a1c49-105">Arguments</span></span>

<span data-ttu-id="a1c49-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="a1c49-106">`+` &#124; `-`</span></span>

<span data-ttu-id="a1c49-107">Użyj **-delaysign —** Jeśli chcesz użyć w pełni podpisanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="a1c49-107">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="a1c49-108">Użyj **-delaysign +** , jeśli chcesz umieścić klucz publiczny w zestawie.</span><span class="sxs-lookup"><span data-stu-id="a1c49-108">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="a1c49-109">Wartość domyślna to **-delaysign-** .</span><span class="sxs-lookup"><span data-stu-id="a1c49-109">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="a1c49-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1c49-110">Remarks</span></span>

<span data-ttu-id="a1c49-111">Opcja **-delaysign** nie ma żadnego efektu, chyba że jest używana z atrybutem [-KeyFile](./keyfile-compiler-option.md) lub [-Container](./keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="a1c49-111">The **-delaysign** option has no effect unless used with [-keyfile](./keyfile-compiler-option.md) or [-keycontainer](./keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="a1c49-112">Opcje **-delaysign** i **-publicsign** wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="a1c49-112">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="a1c49-113">Po zażądaniu w pełni podpisanego zestawu, kompilator skrótów pliku, który zawiera manifest (metadane zestawu) i podpisuje ten skrót z kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="a1c49-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="a1c49-114">Ta operacja tworzy podpis cyfrowy, który jest przechowywany w pliku, który zawiera manifest.</span><span class="sxs-lookup"><span data-stu-id="a1c49-114">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="a1c49-115">Gdy zestaw jest podpisany z opóźnieniem, kompilator nie oblicza i nie przechowuje podpisu, ale rezerwuje miejsce w pliku, aby podpis mógł zostać dodany później.</span><span class="sxs-lookup"><span data-stu-id="a1c49-115">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="a1c49-116">Na przykład przy użyciu polecenia **-delaysign +** umożliwia testerowi umieszczenie zestawu w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a1c49-116">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="a1c49-117">Po przetestowaniu można w pełni podpisać zestaw, umieszczając klucz prywatny w zestawie przy użyciu narzędzia [konsolidatora zestawu](../../../framework/tools/al-exe-assembly-linker.md) .</span><span class="sxs-lookup"><span data-stu-id="a1c49-117">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="a1c49-118">Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnych nazwach](../../../standard/assembly/create-use-strong-named.md) oraz [opóźnienie podpisywania zestawu](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="a1c49-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a1c49-119">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a1c49-119">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="a1c49-120">Otwórz stronę **Właściwości** dla projektu.</span><span class="sxs-lookup"><span data-stu-id="a1c49-120">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="a1c49-121">Zmodyfikuj właściwość **opóźnienia tylko do podpisywania** .</span><span class="sxs-lookup"><span data-stu-id="a1c49-121">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="a1c49-122">Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>tę opcję kompilatora, zobacz.</span><span class="sxs-lookup"><span data-stu-id="a1c49-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1c49-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1c49-123">See also</span></span>

- [<span data-ttu-id="a1c49-124">C#-publicsign — opcja</span><span class="sxs-lookup"><span data-stu-id="a1c49-124">C# -publicsign option</span></span>](publicsign-compiler-option.md)
- [<span data-ttu-id="a1c49-125">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="a1c49-125">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="a1c49-126">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a1c49-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
