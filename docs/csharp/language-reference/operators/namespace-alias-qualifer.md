---
title: 'Operator :: (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 668799a2d846d0f0bf1b3743e202602250a57ae5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6e79e-102">Operator :: (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6e79e-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="6e79e-103">Kwalifikator aliasu przestrzeni nazw (`::`) jest używana do odszukania identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="6e79e-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="6e79e-104">Zawsze znajduje się między dwoma identyfikatorów, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="6e79e-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="6e79e-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6e79e-105">Remarks</span></span>  
 <span data-ttu-id="6e79e-106">Kwalifikator aliasu przestrzeni nazw może być `global`.</span><span class="sxs-lookup"><span data-stu-id="6e79e-106">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="6e79e-107">Wywołuje to wyszukiwanie w globalnej przestrzeni nazw, a nie do aliasu przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6e79e-107">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="6e79e-108">Aby uzyskać więcej informacji</span><span class="sxs-lookup"><span data-stu-id="6e79e-108">For More Information</span></span>  
 <span data-ttu-id="6e79e-109">Przykład sposobu użycia `::` operatora, zobacz sekcję poniżej:</span><span class="sxs-lookup"><span data-stu-id="6e79e-109">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="6e79e-110">Instrukcje: użycie globalnych aliasów przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="6e79e-110">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="6e79e-111">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6e79e-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6e79e-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e79e-112">See Also</span></span>  
 [<span data-ttu-id="6e79e-113">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="6e79e-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6e79e-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6e79e-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6e79e-115">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="6e79e-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="6e79e-116">Słowa kluczowe przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="6e79e-116">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="6e79e-117">. operator</span><span class="sxs-lookup"><span data-stu-id="6e79e-117">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
 [<span data-ttu-id="6e79e-118">extern alias</span><span class="sxs-lookup"><span data-stu-id="6e79e-118">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
