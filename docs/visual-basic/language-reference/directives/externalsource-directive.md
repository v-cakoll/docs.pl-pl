---
title: '#ExternalSource-dyrektywa'
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
ms.openlocfilehash: 146ab41d74b45acc4063e2463baca26c7caa4652
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586594"
---
# <a name="externalsource-directive"></a><span data-ttu-id="79651-102">#ExternalSource — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="79651-102">#ExternalSource Directive</span></span>
<span data-ttu-id="79651-103">Wskazuje mapowanie między określonych wierszy kodu źródłowego i tekst do źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="79651-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79651-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="79651-104">Syntax</span></span>  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="79651-105">Części</span><span class="sxs-lookup"><span data-stu-id="79651-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="79651-106">Ścieżka do źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="79651-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="79651-107">Numer wiersza w pierwszej linii źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="79651-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="79651-108">Wiersz, w którym występuje błąd z zewnętrznego źródła.</span><span class="sxs-lookup"><span data-stu-id="79651-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="79651-109">Kończy blok `#ExternalSource`.</span><span class="sxs-lookup"><span data-stu-id="79651-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79651-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79651-110">Remarks</span></span>  
 <span data-ttu-id="79651-111">Ta dyrektywa jest używany tylko przez kompilator i debuger.</span><span class="sxs-lookup"><span data-stu-id="79651-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="79651-112">Plik źródłowy może zawierać dyrektyw źródła zewnętrznego, wskazujące mapowanie między określonych wierszy kodu w pliku źródłowym i tekst zewnętrznych do źródła, takich jak plik .aspx.</span><span class="sxs-lookup"><span data-stu-id="79651-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="79651-113">Jeśli podczas kompilacji w kodzie źródłowym wyznaczonych zostaną napotkane błędy, są one zidentyfikowane jako pochodzące ze źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="79651-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="79651-114">Dyrektywy źródła zewnętrznego nie mają wpływu na kompilacji i nie mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="79651-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="79651-115">Są one przeznaczone do użytku wewnętrznego przez aplikację tylko.</span><span class="sxs-lookup"><span data-stu-id="79651-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79651-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79651-116">See Also</span></span>  
 [<span data-ttu-id="79651-117">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="79651-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
