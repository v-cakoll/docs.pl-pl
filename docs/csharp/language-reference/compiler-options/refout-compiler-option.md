---
title: -refout (Opcje kompilatora C#)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: f48316a1e6f657e3bd0190d269dfe0e875a833d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72771759"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="17fcd-102">-refout (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="17fcd-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="17fcd-103">Opcja **-refout** określa ścieżkę pliku, w której powinien być wyjściowy zestaw odniesienia.</span><span class="sxs-lookup"><span data-stu-id="17fcd-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="17fcd-104">Przekłada się `metadataPeStream` to na interfejs API emituj.</span><span class="sxs-lookup"><span data-stu-id="17fcd-104">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="17fcd-105">Ta opcja odpowiada właściwości projektu [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) msbuild.</span><span class="sxs-lookup"><span data-stu-id="17fcd-105">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="17fcd-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="17fcd-106">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="17fcd-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="17fcd-107">Arguments</span></span>

 <span data-ttu-id="17fcd-108">`filepath`Ścieżka pliku dla zestawu odniesienia.</span><span class="sxs-lookup"><span data-stu-id="17fcd-108">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="17fcd-109">Ogólnie powinien odpowiadać zestawu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="17fcd-109">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="17fcd-110">Zalecaną konwencją (używaną przez MSBuild) jest umieszczenie zestawu odniesienia w podfolderze "ref/" względem zestawu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="17fcd-110">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="17fcd-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17fcd-111">Remarks</span></span>

<span data-ttu-id="17fcd-112">Zestawy odwołań są specjalnym typem zestawu, który zawiera tylko minimalną ilość metadanych wymaganych do reprezentowania publicznej powierzchni interfejsu API biblioteki.</span><span class="sxs-lookup"><span data-stu-id="17fcd-112">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="17fcd-113">Obejmują one deklaracje dla wszystkich elementów członkowskich, które są istotne podczas odwoływania się do zestawu w narzędziakompilacji, ale wykluczają wszystkie implementacje elementów członkowskich i deklaracje prywatnych elementów członkowskich, które nie mają zauważalnego wpływu na ich kontrakt interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="17fcd-113">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="17fcd-114">Aby uzyskać więcej informacji, zobacz [Zestawy odwołań](../../../standard/assembly/reference-assemblies.md) w przewodniku .NET.</span><span class="sxs-lookup"><span data-stu-id="17fcd-114">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="17fcd-115">Opcje `-refout` [`-refonly`](refonly-compiler-option.md) i wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="17fcd-115">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="17fcd-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17fcd-116">See also</span></span>

- [<span data-ttu-id="17fcd-117">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="17fcd-117">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="17fcd-118">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="17fcd-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
