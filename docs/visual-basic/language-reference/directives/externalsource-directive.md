---
title: '#ExternalSource — dyrektywa (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: ac7096e998dd8d2a416dc739e1d7625e1abff7a6
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696821"
---
# <a name="externalsource-directive"></a><span data-ttu-id="0ec07-102">#ExternalSource — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="0ec07-102">#ExternalSource Directive</span></span>
<span data-ttu-id="0ec07-103">Wskazuje mapowanie między określonymi wierszami kodu źródłowego a tekstem zewnętrznym do źródła.</span><span class="sxs-lookup"><span data-stu-id="0ec07-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ec07-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ec07-104">Syntax</span></span>  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="0ec07-105">Części</span><span class="sxs-lookup"><span data-stu-id="0ec07-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="0ec07-106">Ścieżka do zewnętrznego źródła.</span><span class="sxs-lookup"><span data-stu-id="0ec07-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="0ec07-107">Numer wiersza pierwszego wiersza zewnętrznego źródła.</span><span class="sxs-lookup"><span data-stu-id="0ec07-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="0ec07-108">Wiersz, w którym wystąpił błąd w zewnętrznym źródle.</span><span class="sxs-lookup"><span data-stu-id="0ec07-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="0ec07-109">Kończy blok `#ExternalSource`.</span><span class="sxs-lookup"><span data-stu-id="0ec07-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ec07-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ec07-110">Remarks</span></span>  
 <span data-ttu-id="0ec07-111">Ta dyrektywa jest używana tylko przez kompilator i debuger.</span><span class="sxs-lookup"><span data-stu-id="0ec07-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="0ec07-112">Plik źródłowy może zawierać dyrektywy zewnętrznego źródła, które wskazują mapowanie między określonymi wierszami kodu w pliku źródłowym a tekstem zewnętrznym ze źródłem, takim jak plik. aspx.</span><span class="sxs-lookup"><span data-stu-id="0ec07-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="0ec07-113">Jeśli w wyznaczonym kodzie źródłowym wystąpią błędy podczas kompilacji, są one identyfikowane jako pochodzące ze źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="0ec07-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="0ec07-114">Dyrektywy źródła zewnętrznego nie mają wpływu na kompilację i nie mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="0ec07-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="0ec07-115">Są one przeznaczone do użytku wewnętrznego tylko przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="0ec07-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ec07-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ec07-116">See also</span></span>

- [<span data-ttu-id="0ec07-117">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="0ec07-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
