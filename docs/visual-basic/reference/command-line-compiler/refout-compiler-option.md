---
title: -refout
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 3649a24a52cc6a448ea7cf4d850915adf02147fb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348654"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="cca4e-102">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cca4e-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="cca4e-103">The **-refout** option specifies a file path where the reference assembly should be output.</span><span class="sxs-lookup"><span data-stu-id="cca4e-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="cca4e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cca4e-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="cca4e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cca4e-105">Arguments</span></span>

`filepath`  
<span data-ttu-id="cca4e-106">The path and filename of the reference assembly.</span><span class="sxs-lookup"><span data-stu-id="cca4e-106">The path and filename of the reference assembly.</span></span> <span data-ttu-id="cca4e-107">It should generally be in a sub-folder of the primary assembly.</span><span class="sxs-lookup"><span data-stu-id="cca4e-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="cca4e-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span><span class="sxs-lookup"><span data-stu-id="cca4e-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="cca4e-109">All folders in `filepath` must exist; the compiler does not create them.</span><span class="sxs-lookup"><span data-stu-id="cca4e-109">All folders in `filepath` must exist; the compiler does not create them.</span></span>

## <a name="remarks"></a><span data-ttu-id="cca4e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cca4e-110">Remarks</span></span>

<span data-ttu-id="cca4e-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span><span class="sxs-lookup"><span data-stu-id="cca4e-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="cca4e-112">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span><span class="sxs-lookup"><span data-stu-id="cca4e-112">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="cca4e-113">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span><span class="sxs-lookup"><span data-stu-id="cca4e-113">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="cca4e-114">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span><span class="sxs-lookup"><span data-stu-id="cca4e-114">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="cca4e-115">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span><span class="sxs-lookup"><span data-stu-id="cca4e-115">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="cca4e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cca4e-116">See also</span></span>

- [<span data-ttu-id="cca4e-117">-refonly</span><span class="sxs-lookup"><span data-stu-id="cca4e-117">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="cca4e-118">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="cca4e-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="cca4e-119">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="cca4e-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
