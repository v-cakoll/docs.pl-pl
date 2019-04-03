---
title: '#ExternalSource-dyrektywa (Visual Basic)'
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
ms.openlocfilehash: 39e6963c97340daab3f0ab7ad6860695f1f6c135
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823431"
---
# <a name="externalsource-directive"></a><span data-ttu-id="dcc28-102">#ExternalSource — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="dcc28-102">#ExternalSource Directive</span></span>
<span data-ttu-id="dcc28-103">Wskazuje mapowanie między poszczególne wiersze kodu źródłowego, a tekstem zewnętrznym do źródła.</span><span class="sxs-lookup"><span data-stu-id="dcc28-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcc28-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dcc28-104">Syntax</span></span>  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="dcc28-105">Części</span><span class="sxs-lookup"><span data-stu-id="dcc28-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="dcc28-106">Ścieżka do źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="dcc28-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="dcc28-107">Numer wiersza w pierwszej linii źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="dcc28-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="dcc28-108">Wiersz, w którym występuje błąd ze źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="dcc28-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="dcc28-109">Kończy blok `#ExternalSource`.</span><span class="sxs-lookup"><span data-stu-id="dcc28-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcc28-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dcc28-110">Remarks</span></span>  
 <span data-ttu-id="dcc28-111">Ta dyrektywa jest używany tylko przez kompilator i debugera.</span><span class="sxs-lookup"><span data-stu-id="dcc28-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="dcc28-112">Plik źródłowy może zawierać dyrektyw zewnętrznego źródła, które wskazują mapowanie między poszczególne wiersze kodu w pliku źródłowym i tekstem zewnętrznym do źródła, takich jak plik .aspx.</span><span class="sxs-lookup"><span data-stu-id="dcc28-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="dcc28-113">Jeśli wystąpią błędy w kodzie źródłowym wyznaczonej podczas kompilacji, są one zidentyfikowane jako pochodzące z zewnętrznego źródła.</span><span class="sxs-lookup"><span data-stu-id="dcc28-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="dcc28-114">Dyrektywy zewnętrznego źródła, nie mają wpływu na kompilację i nie mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="dcc28-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="dcc28-115">Są one przeznaczone do użytku wewnętrznego przez aplikację tylko.</span><span class="sxs-lookup"><span data-stu-id="dcc28-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcc28-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dcc28-116">See also</span></span>

- [<span data-ttu-id="dcc28-117">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="dcc28-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
