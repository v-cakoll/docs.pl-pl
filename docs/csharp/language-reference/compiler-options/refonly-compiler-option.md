---
title: -refonly (Opcje kompilatora C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 856b65d3b2217dbe5d53ecda00723b47247d80a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72773853"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="85383-102">-refonly (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="85383-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="85383-103">Opcja **-refonly** wskazuje, że zestaw odniesienia powinien być wyjściowy zamiast zestawu implementacji, jako dane wyjściowe podstawowe.</span><span class="sxs-lookup"><span data-stu-id="85383-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="85383-104">Parametr `-refonly` dyskretnie wyłącza wyjmowanie pdb, ponieważ nie można wykonać zestawów odwołań.</span><span class="sxs-lookup"><span data-stu-id="85383-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="85383-105">Ta opcja odpowiada właściwości projektu [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) firmy MSBuild.</span><span class="sxs-lookup"><span data-stu-id="85383-105">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="85383-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="85383-106">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="85383-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85383-107">Remarks</span></span>

<span data-ttu-id="85383-108">Zestawy odwołań są specjalnym typem zestawu, który zawiera tylko minimalną ilość metadanych wymaganych do reprezentowania publicznej powierzchni interfejsu API biblioteki.</span><span class="sxs-lookup"><span data-stu-id="85383-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="85383-109">Obejmują one deklaracje dla wszystkich elementów członkowskich, które są istotne podczas odwoływania się do zestawu w narzędziakompilacji, ale wykluczają wszystkie implementacje elementów członkowskich i deklaracje prywatnych elementów członkowskich, które nie mają zauważalnego wpływu na ich kontrakt interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="85383-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="85383-110">Aby uzyskać więcej informacji, zobacz [Zestawy odwołań](../../../standard/assembly/reference-assemblies.md) w przewodniku .NET.</span><span class="sxs-lookup"><span data-stu-id="85383-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="85383-111">Opcje `-refonly` [`-refout`](refout-compiler-option.md) i wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="85383-111">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="85383-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85383-112">See also</span></span>

- [<span data-ttu-id="85383-113">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="85383-113">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="85383-114">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="85383-114">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
