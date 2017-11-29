---
title: '#<a name="externalsource-directive"></a>ExternalSource-dyrektywa'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "160"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f90b838e50b65b8652cd9cf6f6ee084e9552f025
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="externalsource-directive"></a><span data-ttu-id="93c36-102">#ExternalSource — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="93c36-102">#ExternalSource Directive</span></span>
<span data-ttu-id="93c36-103">Wskazuje mapowanie między określonych wierszy kodu źródłowego i tekst do źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="93c36-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93c36-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="93c36-104">Syntax</span></span>  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="93c36-105">Części</span><span class="sxs-lookup"><span data-stu-id="93c36-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="93c36-106">Ścieżka do źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="93c36-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="93c36-107">Numer wiersza w pierwszej linii źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="93c36-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="93c36-108">Wiersz, w którym występuje błąd z zewnętrznego źródła.</span><span class="sxs-lookup"><span data-stu-id="93c36-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="93c36-109">Kończy `#ExternalSource` bloku.</span><span class="sxs-lookup"><span data-stu-id="93c36-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93c36-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93c36-110">Remarks</span></span>  
 <span data-ttu-id="93c36-111">Ta dyrektywa jest używany tylko przez kompilator i debuger.</span><span class="sxs-lookup"><span data-stu-id="93c36-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="93c36-112">Plik źródłowy może zawierać dyrektyw źródła zewnętrznego, wskazujące mapowanie między określonych wierszy kodu w pliku źródłowym i tekst zewnętrznych do źródła, takich jak plik .aspx.</span><span class="sxs-lookup"><span data-stu-id="93c36-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="93c36-113">Jeśli podczas kompilacji w kodzie źródłowym wyznaczonych zostaną napotkane błędy, są one zidentyfikowane jako pochodzące ze źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="93c36-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="93c36-114">Dyrektywy źródła zewnętrznego nie mają wpływu na kompilacji i nie mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="93c36-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="93c36-115">Są one przeznaczone do użytku wewnętrznego przez aplikację tylko.</span><span class="sxs-lookup"><span data-stu-id="93c36-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93c36-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93c36-116">See Also</span></span>  
 [<span data-ttu-id="93c36-117">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="93c36-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
