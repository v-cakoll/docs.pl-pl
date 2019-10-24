---
title: -refonly (C# opcje kompilatora)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 856b65d3b2217dbe5d53ecda00723b47247d80a4
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773853"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="83285-102">-refonly (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="83285-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="83285-103">Opcja **-refonly** wskazuje, że zestaw odwołania powinien być wyjściem, a nie zestawem implementacji, jako podstawowy wynik.</span><span class="sxs-lookup"><span data-stu-id="83285-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="83285-104">Parametr `-refonly` dyskretnie wyłącza umieszczanie plików PDB, ponieważ nie można wykonać zestawów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="83285-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="83285-105">Ta opcja odnosi się do właściwości Project [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="83285-105">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="83285-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="83285-106">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="83285-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83285-107">Remarks</span></span>

<span data-ttu-id="83285-108">Zestawy referencyjne są specjalnym typem zestawu, który zawiera tylko minimalną ilość metadanych wymaganą do reprezentowania publicznej powierzchni interfejsu API biblioteki.</span><span class="sxs-lookup"><span data-stu-id="83285-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="83285-109">Obejmują one deklaracje dla wszystkich elementów członkowskich, które są istotne w przypadku odwoływania się do zestawu w narzędziach kompilacji, ale wyklucza wszystkie implementacje składowych i deklaracje prywatnych członków, którzy nie mają zauważalnego wpływu na ich kontrakt interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="83285-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="83285-110">Aby uzyskać więcej informacji, zobacz [zestawy referencyjne](../../../standard/assembly/reference-assemblies.md) w przewodniku .NET.</span><span class="sxs-lookup"><span data-stu-id="83285-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="83285-111">Opcje `-refonly` i [`-refout`](refout-compiler-option.md) wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="83285-111">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="83285-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83285-112">See also</span></span>

- [<span data-ttu-id="83285-113">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="83285-113">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="83285-114">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="83285-114">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
