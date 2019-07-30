---
title: ':: operator- C# odwołanie'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: c494e8dbb18f44ce5520b21800a21d3feb03da59
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631135"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0a8f9-102">:: — operatorC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="0a8f9-102">:: operator (C# reference)</span></span>

<span data-ttu-id="0a8f9-103">Kwalifikator aliasu przestrzeni nazw (`::`) jest używany do wyszukiwania identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="0a8f9-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="0a8f9-104">Zawsze znajduje się między dwoma identyfikatorami — jak w przykładzie poniżej:</span><span class="sxs-lookup"><span data-stu-id="0a8f9-104">It is always positioned between two identifiers, as in this example:</span></span>

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

<span data-ttu-id="0a8f9-105">Operatora można również używać z *dyrektywą aliasu using:* `::`</span><span class="sxs-lookup"><span data-stu-id="0a8f9-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="0a8f9-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0a8f9-106">Remarks</span></span>

<span data-ttu-id="0a8f9-107">Kwalifikator aliasu przestrzeni nazw może mieć wartość `global`.</span><span class="sxs-lookup"><span data-stu-id="0a8f9-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="0a8f9-108">Wywołuje to wyszukiwanie w globalnej przestrzeni nazw, a nie w przestrzeni nazw z aliasem.</span><span class="sxs-lookup"><span data-stu-id="0a8f9-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="0a8f9-109">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="0a8f9-109">For more information</span></span>

<span data-ttu-id="0a8f9-110">Aby zobaczyć przykład użycia operatora `::`, odwiedź sekcję poniżej:</span><span class="sxs-lookup"><span data-stu-id="0a8f9-110">For an example of how to use the `::` operator, see the following section:</span></span>

- [<span data-ttu-id="0a8f9-111">Instrukcje: Użyj globalnego aliasu przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="0a8f9-111">How to: Use the Global Namespace Alias</span></span>](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a><span data-ttu-id="0a8f9-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0a8f9-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0a8f9-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a8f9-113">See also</span></span>

- [<span data-ttu-id="0a8f9-114">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="0a8f9-114">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0a8f9-115">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="0a8f9-115">C# operators</span></span>](index.md)
- [<span data-ttu-id="0a8f9-116">. zakład</span><span class="sxs-lookup"><span data-stu-id="0a8f9-116">. operator</span></span>](member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="0a8f9-117">extern alias</span><span class="sxs-lookup"><span data-stu-id="0a8f9-117">extern alias</span></span>](../keywords/extern-alias.md)
