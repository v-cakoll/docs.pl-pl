---
title: -opcji refout (C# opcje kompilatora)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: f48316a1e6f657e3bd0190d269dfe0e875a833d9
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771759"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="a3b38-102">-opcji refout (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="a3b38-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="a3b38-103">Opcja **-opcji refout** określa ścieżkę pliku, w którym zestaw odniesienia powinien być wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="a3b38-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="a3b38-104">Spowoduje to przetłumaczenie na `metadataPeStream` w interfejsie API emisji.</span><span class="sxs-lookup"><span data-stu-id="a3b38-104">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="a3b38-105">Ta opcja odnosi się do właściwości Project [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="a3b38-105">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="a3b38-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3b38-106">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="a3b38-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a3b38-107">Arguments</span></span>

 <span data-ttu-id="a3b38-108">`filepath` ścieżka do zestawu referencyjnego.</span><span class="sxs-lookup"><span data-stu-id="a3b38-108">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="a3b38-109">Zwykle powinna być zgodna z zestawem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="a3b38-109">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="a3b38-110">Zalecaną konwencją (używaną przez program MSBuild) jest umieszczenie zestawu odwołania w podfolderze "ref/" względem podstawowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="a3b38-110">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="a3b38-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a3b38-111">Remarks</span></span>

<span data-ttu-id="a3b38-112">Zestawy referencyjne są specjalnym typem zestawu, który zawiera tylko minimalną ilość metadanych wymaganą do reprezentowania publicznej powierzchni interfejsu API biblioteki.</span><span class="sxs-lookup"><span data-stu-id="a3b38-112">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="a3b38-113">Obejmują one deklaracje dla wszystkich elementów członkowskich, które są istotne w przypadku odwoływania się do zestawu w narzędziach kompilacji, ale wyklucza wszystkie implementacje składowych i deklaracje prywatnych członków, którzy nie mają zauważalnego wpływu na ich kontrakt interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="a3b38-113">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="a3b38-114">Aby uzyskać więcej informacji, zobacz [zestawy referencyjne](../../../standard/assembly/reference-assemblies.md) w przewodniku .NET.</span><span class="sxs-lookup"><span data-stu-id="a3b38-114">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="a3b38-115">Opcje `-refout` i [`-refonly`](refonly-compiler-option.md) wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="a3b38-115">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3b38-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3b38-116">See also</span></span>

- [<span data-ttu-id="a3b38-117">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="a3b38-117">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="a3b38-118">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a3b38-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
