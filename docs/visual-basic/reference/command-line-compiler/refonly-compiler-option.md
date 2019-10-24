---
title: -refonly (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: 8e64989ac1410b51991027ffcb33e8dae0c0284b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775566"
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="ae9d0-102">-refonly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae9d0-102">-refonly (Visual Basic)</span></span>

<span data-ttu-id="ae9d0-103">Opcja **-refonly** wskazuje, że podstawowe dane wyjściowe kompilacji powinny być zestawem referencyjnym, a nie zestawem implementacji.</span><span class="sxs-lookup"><span data-stu-id="ae9d0-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="ae9d0-104">Parametr `-refonly` dyskretnie wyłącza umieszczanie plików PDB, ponieważ nie można wykonać zestawów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="ae9d0-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="ae9d0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae9d0-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="ae9d0-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae9d0-106">Remarks</span></span>

<span data-ttu-id="ae9d0-107">Visual Basic obsługuje przełącznik `-refonly`, zaczynając od wersji 15,3.</span><span class="sxs-lookup"><span data-stu-id="ae9d0-107">Visual Basic supports the `-refonly` switch starting with version 15.3.</span></span>

<span data-ttu-id="ae9d0-108">Zestawy referencyjne są specjalnym typem zestawu, który zawiera tylko minimalną ilość metadanych wymaganą do reprezentowania publicznej powierzchni interfejsu API biblioteki.</span><span class="sxs-lookup"><span data-stu-id="ae9d0-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="ae9d0-109">Obejmują one deklaracje dla wszystkich elementów członkowskich, które są istotne w przypadku odwoływania się do zestawu w narzędziach kompilacji, ale wyklucza wszystkie implementacje składowych i deklaracje prywatnych członków, którzy nie mają zauważalnego wpływu na ich kontrakt interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="ae9d0-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="ae9d0-110">Aby uzyskać więcej informacji, zobacz [zestawy referencyjne](../../../standard/assembly/reference-assemblies.md) w przewodniku .NET.</span><span class="sxs-lookup"><span data-stu-id="ae9d0-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="ae9d0-111">Opcje `-refonly` i [`-refout`](refout-compiler-option.md) wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="ae9d0-111">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae9d0-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae9d0-112">See also</span></span>

- [<span data-ttu-id="ae9d0-113">-refout</span><span class="sxs-lookup"><span data-stu-id="ae9d0-113">-refout</span></span>](refout-compiler-option.md)
- [<span data-ttu-id="ae9d0-114">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae9d0-114">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="ae9d0-115">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="ae9d0-115">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
