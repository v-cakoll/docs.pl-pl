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
ms.openlocfilehash: 0b456ed3ce9965ef389d8ce40167afa4ac33da18
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422523"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="450b8-102">:: — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="450b8-102">:: operator (C# Reference)</span></span>

<span data-ttu-id="450b8-103">Kwalifikator aliasu przestrzeni nazw (`::`) jest używany do wyszukiwania identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="450b8-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="450b8-104">Zawsze znajduje się między dwoma identyfikatorami — jak w przykładzie poniżej:</span><span class="sxs-lookup"><span data-stu-id="450b8-104">It is always positioned between two identifiers, as in this example:</span></span>

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

<span data-ttu-id="450b8-105">`::` Operator może również służyć za pomocą *użycie dyrektywy alias*:</span><span class="sxs-lookup"><span data-stu-id="450b8-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="450b8-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="450b8-106">Remarks</span></span>

<span data-ttu-id="450b8-107">Kwalifikator aliasu przestrzeni nazw może mieć wartość `global`.</span><span class="sxs-lookup"><span data-stu-id="450b8-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="450b8-108">Wywołuje to wyszukiwanie w globalnej przestrzeni nazw, a nie w przestrzeni nazw z aliasem.</span><span class="sxs-lookup"><span data-stu-id="450b8-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="450b8-109">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="450b8-109">For more information</span></span>

<span data-ttu-id="450b8-110">Aby zobaczyć przykład użycia operatora `::`, odwiedź sekcję poniżej:</span><span class="sxs-lookup"><span data-stu-id="450b8-110">For an example of how to use the `::` operator, see the following section:</span></span>

- [<span data-ttu-id="450b8-111">Instrukcje: Użycie globalnych aliasów Namespace</span><span class="sxs-lookup"><span data-stu-id="450b8-111">How to: Use the Global Namespace Alias</span></span>](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a><span data-ttu-id="450b8-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="450b8-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="450b8-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="450b8-113">See also</span></span>

- [<span data-ttu-id="450b8-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="450b8-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="450b8-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="450b8-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="450b8-116">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="450b8-116">C# operators</span></span>](index.md)
- [<span data-ttu-id="450b8-117">. operator</span><span class="sxs-lookup"><span data-stu-id="450b8-117">. operator</span></span>](member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="450b8-118">extern alias</span><span class="sxs-lookup"><span data-stu-id="450b8-118">extern alias</span></span>](../keywords/extern-alias.md)
