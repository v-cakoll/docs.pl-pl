---
title: -opcji refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 552e611f222bfcc3ce12520ecdb891fd7b8b21de
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775547"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="f8f77-102">-opcji refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8f77-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="f8f77-103">Opcja **-opcji refout** określa ścieżkę pliku, w którym zestaw odniesienia powinien być wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="f8f77-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="f8f77-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8f77-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="f8f77-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f8f77-105">Arguments</span></span>

`filepath`  
<span data-ttu-id="f8f77-106">Ścieżka i nazwa pliku zestawu odwołania.</span><span class="sxs-lookup"><span data-stu-id="f8f77-106">The path and filename of the reference assembly.</span></span> <span data-ttu-id="f8f77-107">Zwykle powinien znajdować się w podfolderze podstawowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f8f77-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="f8f77-108">Zalecaną konwencją (używaną przez program MSBuild) jest umieszczenie zestawu odwołania w podfolderze "ref/" względem podstawowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f8f77-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="f8f77-109">Wszystkie foldery w `filepath` muszą istnieć; Kompilator nie tworzy ich.</span><span class="sxs-lookup"><span data-stu-id="f8f77-109">All folders in `filepath` must exist; the compiler does not create them.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8f77-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8f77-110">Remarks</span></span>

<span data-ttu-id="f8f77-111">Visual Basic obsługuje przełącznik `-refout`, zaczynając od wersji 15,3.</span><span class="sxs-lookup"><span data-stu-id="f8f77-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="f8f77-112">Zestawy referencyjne są specjalnym typem zestawu, który zawiera tylko minimalną ilość metadanych wymaganą do reprezentowania publicznej powierzchni interfejsu API biblioteki.</span><span class="sxs-lookup"><span data-stu-id="f8f77-112">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="f8f77-113">Obejmują one deklaracje dla wszystkich elementów członkowskich, które są istotne w przypadku odwoływania się do zestawu w narzędziach kompilacji, ale wyklucza wszystkie implementacje składowych i deklaracje prywatnych członków, którzy nie mają zauważalnego wpływu na ich kontrakt interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="f8f77-113">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="f8f77-114">Aby uzyskać więcej informacji, zobacz [zestawy referencyjne](../../../standard/assembly/reference-assemblies.md) w przewodniku .NET.</span><span class="sxs-lookup"><span data-stu-id="f8f77-114">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="f8f77-115">Opcje `-refout` i [`-refonly`](refonly-compiler-option.md) wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="f8f77-115">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8f77-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8f77-116">See also</span></span>

- [<span data-ttu-id="f8f77-117">-refonly</span><span class="sxs-lookup"><span data-stu-id="f8f77-117">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="f8f77-118">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f8f77-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="f8f77-119">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="f8f77-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
