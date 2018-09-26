---
title: ++ — Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: a52f614ce1bbfb8e9d9be686b277c1e69f6f9d35
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47202254"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="28959-102">++ — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="28959-102">++ Operator (C# Reference)</span></span>
<span data-ttu-id="28959-103">Operator inkrementacji (`++`) zwiększa wartość argumentu operacji o 1.</span><span class="sxs-lookup"><span data-stu-id="28959-103">The increment operator (`++`) increments its operand by 1.</span></span> <span data-ttu-id="28959-104">Operator inkrementacji może występować przed argumentem operacji lub po nim: `++variable` i `variable++`.</span><span class="sxs-lookup"><span data-stu-id="28959-104">The increment operator can appear before or after its operand: `++variable` and `variable++`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28959-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28959-105">Remarks</span></span>  
 <span data-ttu-id="28959-106">Pierwsza forma to inkrementacja prefiksowa.</span><span class="sxs-lookup"><span data-stu-id="28959-106">The first form is a prefix increment operation.</span></span> <span data-ttu-id="28959-107">Wynikiem tej operacji jest wartość argumentu po zwiększeniu.</span><span class="sxs-lookup"><span data-stu-id="28959-107">The result of the operation is the value of the operand after it has been incremented.</span></span>  
  
 <span data-ttu-id="28959-108">Druga forma to inkrementacja odwrotna.</span><span class="sxs-lookup"><span data-stu-id="28959-108">The second form is a postfix increment operation.</span></span> <span data-ttu-id="28959-109">Wynikiem tej operacji jest wartość argumentu przed zwiększeniem.</span><span class="sxs-lookup"><span data-stu-id="28959-109">The result of the operation is the value of the operand before it has been incremented.</span></span>  
  
 <span data-ttu-id="28959-110">Typy numeryczne i wyliczenia mają wstępnie zdefiniowane operatory inkrementacji.</span><span class="sxs-lookup"><span data-stu-id="28959-110">Numeric and enumeration types have predefined increment operators.</span></span> <span data-ttu-id="28959-111">W typach definiowanych przez użytkownika można przeciążać operator `++`.</span><span class="sxs-lookup"><span data-stu-id="28959-111">User-defined types can overload the `++` operator.</span></span> <span data-ttu-id="28959-112">Operacje na typach całkowitych w wyliczeniach są zazwyczaj dozwolone.</span><span class="sxs-lookup"><span data-stu-id="28959-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28959-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="28959-113">Example</span></span>  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="28959-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28959-114">See Also</span></span>

- [<span data-ttu-id="28959-115">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="28959-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="28959-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="28959-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="28959-117">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="28959-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
