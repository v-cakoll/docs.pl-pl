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
ms.openlocfilehash: 077d5835b372897cbe797385271effc5d00bf6e3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43473976"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="450a0-102">Operator :: (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="450a0-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="450a0-103">Kwalifikator aliasu przestrzeni nazw (`::`) jest używany do wyszukiwania identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="450a0-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="450a0-104">Zawsze znajduje się między dwoma identyfikatorami — jak w przykładzie poniżej:</span><span class="sxs-lookup"><span data-stu-id="450a0-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  

<span data-ttu-id="450a0-105">`::` Operator może również służyć za pomocą *użycie dyrektywy alias*:</span><span class="sxs-lookup"><span data-stu-id="450a0-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="450a0-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="450a0-106">Remarks</span></span>  
 <span data-ttu-id="450a0-107">Kwalifikator aliasu przestrzeni nazw może mieć wartość `global`.</span><span class="sxs-lookup"><span data-stu-id="450a0-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="450a0-108">Wywołuje to wyszukiwanie w globalnej przestrzeni nazw, a nie w przestrzeni nazw z aliasem.</span><span class="sxs-lookup"><span data-stu-id="450a0-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="450a0-109">Aby uzyskać więcej informacji</span><span class="sxs-lookup"><span data-stu-id="450a0-109">For More Information</span></span>  
 <span data-ttu-id="450a0-110">Aby zobaczyć przykład użycia operatora `::`, odwiedź sekcję poniżej:</span><span class="sxs-lookup"><span data-stu-id="450a0-110">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="450a0-111">Instrukcje: użycie globalnych aliasów przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="450a0-111">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="450a0-112">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="450a0-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="450a0-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="450a0-113">See Also</span></span>

- [<span data-ttu-id="450a0-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="450a0-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="450a0-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="450a0-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="450a0-116">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="450a0-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="450a0-117">Słowa kluczowe przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="450a0-117">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="450a0-118">. operator</span><span class="sxs-lookup"><span data-stu-id="450a0-118">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
- [<span data-ttu-id="450a0-119">extern alias</span><span class="sxs-lookup"><span data-stu-id="450a0-119">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
