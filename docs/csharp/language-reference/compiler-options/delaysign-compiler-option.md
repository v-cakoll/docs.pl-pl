---
title: -delaysign (Opcje kompilatora C#)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 9fdc02c22d9d8c8a709155e43a17ebf0d86dfd69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970447"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="b3f5e-102">-delaysign (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="b3f5e-102">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="b3f5e-103">Ta opcja powoduje, że kompilator rezerwuje miejsce w pliku wyjściowym, dzięki czemu podpis cyfrowy można dodać później.</span><span class="sxs-lookup"><span data-stu-id="b3f5e-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="b3f5e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3f5e-104">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="b3f5e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b3f5e-105">Arguments</span></span>

<span data-ttu-id="b3f5e-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="b3f5e-106">`+` &#124; `-`</span></span>

<span data-ttu-id="b3f5e-107">Użyj **-delaysign-** jeśli chcesz mieć w pełni podpisany zestaw.</span><span class="sxs-lookup"><span data-stu-id="b3f5e-107">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="b3f5e-108">Użyj **-delaysign+,** jeśli chcesz umieścić tylko klucz publiczny w zestawie.</span><span class="sxs-lookup"><span data-stu-id="b3f5e-108">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="b3f5e-109">Wartością domyślną jest **-delaysign-**.</span><span class="sxs-lookup"><span data-stu-id="b3f5e-109">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="b3f5e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b3f5e-110">Remarks</span></span>

<span data-ttu-id="b3f5e-111">Opcja **-delaysign** nie ma wpływu, chyba że jest używana z [-keyfile](./keyfile-compiler-option.md) lub [-keycontainer](./keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="b3f5e-111">The **-delaysign** option has no effect unless used with [-keyfile](./keyfile-compiler-option.md) or [-keycontainer](./keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="b3f5e-112">Opcje **-delaysign** i **-publicsign** wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="b3f5e-112">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="b3f5e-113">Gdy zażądasz w pełni podpisanego zestawu, kompilator poszumowa plik zawierający manifest (metadane zestawu) i znaki, które hash z kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="b3f5e-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="b3f5e-114">Ta operacja tworzy podpis cyfrowy, który jest przechowywany w pliku, który zawiera manifest.</span><span class="sxs-lookup"><span data-stu-id="b3f5e-114">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="b3f5e-115">Gdy zestaw jest podpisany opóźnienie, kompilator nie oblicza i przechowywania podpisu, ale rezerwuje miejsce w pliku, więc podpis można dodać później.</span><span class="sxs-lookup"><span data-stu-id="b3f5e-115">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="b3f5e-116">Na przykład za pomocą **-delaysign+** umożliwia tester umieścić zestaw w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="b3f5e-116">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="b3f5e-117">Po przetestowaniu można w pełni podpisać zestaw, umieszczając klucz prywatny w zestawie za pomocą narzędzia [Łącze zestawu.](../../../framework/tools/al-exe-assembly-linker.md)</span><span class="sxs-lookup"><span data-stu-id="b3f5e-117">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="b3f5e-118">Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnych nazwach](../../../standard/assembly/create-use-strong-named.md) i [Opóźnianie podpisywania zestawu](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="b3f5e-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="b3f5e-119">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b3f5e-119">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="b3f5e-120">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="b3f5e-120">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="b3f5e-121">Zmodyfikuj **tylko znak opóźnienia.**</span><span class="sxs-lookup"><span data-stu-id="b3f5e-121">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="b3f5e-122">Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="b3f5e-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3f5e-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3f5e-123">See also</span></span>

- [<span data-ttu-id="b3f5e-124">C# -opcja publicsign</span><span class="sxs-lookup"><span data-stu-id="b3f5e-124">C# -publicsign option</span></span>](publicsign-compiler-option.md)
- [<span data-ttu-id="b3f5e-125">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="b3f5e-125">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="b3f5e-126">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="b3f5e-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
