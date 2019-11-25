---
title: -refonly
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: b906178abf8d159083d95e41448596d512e857de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348575"
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="9607e-102">-refonly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9607e-102">-refonly (Visual Basic)</span></span>

<span data-ttu-id="9607e-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span><span class="sxs-lookup"><span data-stu-id="9607e-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="9607e-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span><span class="sxs-lookup"><span data-stu-id="9607e-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="9607e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9607e-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="9607e-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9607e-106">Remarks</span></span>

<span data-ttu-id="9607e-107">Visual Basic supports the `-refonly` switch starting with version 15.3.</span><span class="sxs-lookup"><span data-stu-id="9607e-107">Visual Basic supports the `-refonly` switch starting with version 15.3.</span></span>

<span data-ttu-id="9607e-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span><span class="sxs-lookup"><span data-stu-id="9607e-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="9607e-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span><span class="sxs-lookup"><span data-stu-id="9607e-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="9607e-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span><span class="sxs-lookup"><span data-stu-id="9607e-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="9607e-111">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span><span class="sxs-lookup"><span data-stu-id="9607e-111">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="9607e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9607e-112">See also</span></span>

- [<span data-ttu-id="9607e-113">-refout</span><span class="sxs-lookup"><span data-stu-id="9607e-113">-refout</span></span>](refout-compiler-option.md)
- [<span data-ttu-id="9607e-114">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="9607e-114">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="9607e-115">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="9607e-115">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
