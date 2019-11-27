---
title: '#ExternalSource, dyrektywa'
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
ms.openlocfilehash: fa0a40827c1b3865b90c7d796ea4dd364774e1c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343833"
---
# <a name="externalsource-directive"></a><span data-ttu-id="0cc3e-102">#ExternalSource — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="0cc3e-102">#ExternalSource Directive</span></span>

<span data-ttu-id="0cc3e-103">Wskazuje mapowanie między określonymi wierszami kodu źródłowego a tekstem zewnętrznym do źródła.</span><span class="sxs-lookup"><span data-stu-id="0cc3e-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cc3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0cc3e-104">Syntax</span></span>  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="0cc3e-105">Części</span><span class="sxs-lookup"><span data-stu-id="0cc3e-105">Parts</span></span>  

 `StringLiteral`  
 <span data-ttu-id="0cc3e-106">Ścieżka do zewnętrznego źródła.</span><span class="sxs-lookup"><span data-stu-id="0cc3e-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="0cc3e-107">Numer wiersza pierwszego wiersza zewnętrznego źródła.</span><span class="sxs-lookup"><span data-stu-id="0cc3e-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="0cc3e-108">Wiersz, w którym wystąpił błąd w zewnętrznym źródle.</span><span class="sxs-lookup"><span data-stu-id="0cc3e-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="0cc3e-109">Kończy blok `#ExternalSource`.</span><span class="sxs-lookup"><span data-stu-id="0cc3e-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cc3e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0cc3e-110">Remarks</span></span>  

 <span data-ttu-id="0cc3e-111">Ta dyrektywa jest używana tylko przez kompilator i debuger.</span><span class="sxs-lookup"><span data-stu-id="0cc3e-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="0cc3e-112">Plik źródłowy może zawierać dyrektywy zewnętrznego źródła, które wskazują mapowanie między określonymi wierszami kodu w pliku źródłowym a tekstem zewnętrznym ze źródłem, takim jak plik. aspx.</span><span class="sxs-lookup"><span data-stu-id="0cc3e-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="0cc3e-113">Jeśli w wyznaczonym kodzie źródłowym wystąpią błędy podczas kompilacji, są one identyfikowane jako pochodzące ze źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="0cc3e-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="0cc3e-114">Dyrektywy źródła zewnętrznego nie mają wpływu na kompilację i nie mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="0cc3e-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="0cc3e-115">Są one przeznaczone do użytku wewnętrznego tylko przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="0cc3e-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cc3e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0cc3e-116">See also</span></span>

- [<span data-ttu-id="0cc3e-117">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="0cc3e-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
