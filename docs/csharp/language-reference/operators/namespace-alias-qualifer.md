---
title: ':: Operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 2e456be075f3487676228244e0119ff46ed9a538
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243481"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="03b3c-102">:: Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="03b3c-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="03b3c-103">Kwalifikator aliasu przestrzeni nazw (`::`) jest używany do wyszukiwania identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="03b3c-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="03b3c-104">Zawsze znajduje się między dwoma identyfikatorami — jak w przykładzie poniżej:</span><span class="sxs-lookup"><span data-stu-id="03b3c-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  

<span data-ttu-id="03b3c-105">`::` Operator może również służyć za pomocą *użycie dyrektywy alias*:</span><span class="sxs-lookup"><span data-stu-id="03b3c-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="03b3c-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03b3c-106">Remarks</span></span>  
 <span data-ttu-id="03b3c-107">Kwalifikator aliasu przestrzeni nazw może mieć wartość `global`.</span><span class="sxs-lookup"><span data-stu-id="03b3c-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="03b3c-108">Wywołuje to wyszukiwanie w globalnej przestrzeni nazw, a nie w przestrzeni nazw z aliasem.</span><span class="sxs-lookup"><span data-stu-id="03b3c-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="03b3c-109">Aby uzyskać więcej informacji</span><span class="sxs-lookup"><span data-stu-id="03b3c-109">For More Information</span></span>  
 <span data-ttu-id="03b3c-110">Aby zobaczyć przykład użycia operatora `::`, odwiedź sekcję poniżej:</span><span class="sxs-lookup"><span data-stu-id="03b3c-110">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="03b3c-111">Instrukcje: Użycie globalnych aliasów Namespace</span><span class="sxs-lookup"><span data-stu-id="03b3c-111">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="03b3c-112">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="03b3c-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="03b3c-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03b3c-113">See Also</span></span>

- [<span data-ttu-id="03b3c-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="03b3c-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="03b3c-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="03b3c-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="03b3c-116">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="03b3c-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="03b3c-117">Słowa kluczowe przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="03b3c-117">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="03b3c-118">. operator</span><span class="sxs-lookup"><span data-stu-id="03b3c-118">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
- [<span data-ttu-id="03b3c-119">extern alias</span><span class="sxs-lookup"><span data-stu-id="03b3c-119">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
