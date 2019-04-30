---
title: ':: operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 2618131f27271e7c06cb6d425fc22b5bd9750c49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688855"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="7206c-102">:: — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="7206c-102">:: operator (C# Reference)</span></span>

<span data-ttu-id="7206c-103">Kwalifikator aliasu przestrzeni nazw (`::`) jest używany do wyszukiwania identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="7206c-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="7206c-104">Zawsze znajduje się między dwoma identyfikatorami — jak w przykładzie poniżej:</span><span class="sxs-lookup"><span data-stu-id="7206c-104">It is always positioned between two identifiers, as in this example:</span></span>

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

<span data-ttu-id="7206c-105">`::` Operator może również służyć za pomocą *użycie dyrektywy alias*:</span><span class="sxs-lookup"><span data-stu-id="7206c-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="7206c-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7206c-106">Remarks</span></span>

<span data-ttu-id="7206c-107">Kwalifikator aliasu przestrzeni nazw może mieć wartość `global`.</span><span class="sxs-lookup"><span data-stu-id="7206c-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="7206c-108">Wywołuje to wyszukiwanie w globalnej przestrzeni nazw, a nie w przestrzeni nazw z aliasem.</span><span class="sxs-lookup"><span data-stu-id="7206c-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="7206c-109">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="7206c-109">For more information</span></span>

<span data-ttu-id="7206c-110">Aby zobaczyć przykład użycia operatora `::`, odwiedź sekcję poniżej:</span><span class="sxs-lookup"><span data-stu-id="7206c-110">For an example of how to use the `::` operator, see the following section:</span></span>

- [<span data-ttu-id="7206c-111">Instrukcje: Użycie globalnych aliasów Namespace</span><span class="sxs-lookup"><span data-stu-id="7206c-111">How to: Use the Global Namespace Alias</span></span>](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a><span data-ttu-id="7206c-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7206c-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7206c-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7206c-113">See also</span></span>

- [<span data-ttu-id="7206c-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7206c-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7206c-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7206c-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7206c-116">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="7206c-116">C# operators</span></span>](index.md)
- [<span data-ttu-id="7206c-117">Słowa kluczowe przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="7206c-117">Namespace Keywords</span></span>](../keywords/namespace-keywords.md)
- [<span data-ttu-id="7206c-118">. operator</span><span class="sxs-lookup"><span data-stu-id="7206c-118">. operator</span></span>](member-access-operator.md)
- [<span data-ttu-id="7206c-119">extern alias</span><span class="sxs-lookup"><span data-stu-id="7206c-119">extern alias</span></span>](../keywords/extern-alias.md)