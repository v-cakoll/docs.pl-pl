---
title: 'Operator :: (odwołanie w C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6b4f1683e1250ed745e15ced88203ca942c75ff8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1d326-102">Operator :: (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1d326-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="1d326-103">Kwalifikator aliasu przestrzeni nazw (`::`) jest używana do odszukania identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="1d326-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="1d326-104">Zawsze znajduje się między dwoma identyfikatorów, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1d326-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="1d326-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d326-105">Remarks</span></span>  
 <span data-ttu-id="1d326-106">Kwalifikator aliasu przestrzeni nazw może być `global`.</span><span class="sxs-lookup"><span data-stu-id="1d326-106">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="1d326-107">Wywołuje to wyszukiwanie w globalnej przestrzeni nazw, a nie do aliasu przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1d326-107">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="1d326-108">Aby uzyskać więcej informacji</span><span class="sxs-lookup"><span data-stu-id="1d326-108">For More Information</span></span>  
 <span data-ttu-id="1d326-109">Przykład sposobu użycia `::` operatora, zobacz sekcję poniżej:</span><span class="sxs-lookup"><span data-stu-id="1d326-109">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="1d326-110">Porady: użycie globalnych aliasów Namespace</span><span class="sxs-lookup"><span data-stu-id="1d326-110">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="1d326-111">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1d326-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1d326-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d326-112">See Also</span></span>  
 [<span data-ttu-id="1d326-113">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="1d326-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1d326-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1d326-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1d326-115">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="1d326-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="1d326-116">Słowa kluczowe Namespace</span><span class="sxs-lookup"><span data-stu-id="1d326-116">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="1d326-117">. Operator</span><span class="sxs-lookup"><span data-stu-id="1d326-117">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
 [<span data-ttu-id="1d326-118">alias zewnętrzny</span><span class="sxs-lookup"><span data-stu-id="1d326-118">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
