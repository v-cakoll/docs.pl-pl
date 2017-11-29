---
title: "Typy wyjątków (F#)"
description: "Dowiedz się, jak zdefiniować i użyć typów wyjątków F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e850205a-b8da-459e-8f6d-cb3510f8f173
ms.openlocfilehash: a0864218841396c0ebdf26c7585e0e5bb778f83e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="exception-types"></a><span data-ttu-id="1b49d-104">Typy wyjątków</span><span class="sxs-lookup"><span data-stu-id="1b49d-104">Exception Types</span></span>

<span data-ttu-id="1b49d-105">Istnieją dwie kategorie wyjątków w języku F #: typy wyjątków .NET i typów wyjątków F #.</span><span class="sxs-lookup"><span data-stu-id="1b49d-105">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="1b49d-106">W tym temacie opisano sposób definiowania i użyć typów wyjątków F #.</span><span class="sxs-lookup"><span data-stu-id="1b49d-106">This topic describes how to define and use F# exception types.</span></span>


## <a name="syntax"></a><span data-ttu-id="1b49d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b49d-107">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="1b49d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b49d-108">Remarks</span></span>
<span data-ttu-id="1b49d-109">W poprzednich składni *typu wyjątku* jest nazwą nowego F # wyjątek typu, i *typ argumentu* reprezentuje typ argumentu, który może zostać podane w przypadku zgłaszał wyjątku tego typu.</span><span class="sxs-lookup"><span data-stu-id="1b49d-109">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="1b49d-110">Można określić wiele argumentów, za pomocą typ krotki dla *typ argumentu*.</span><span class="sxs-lookup"><span data-stu-id="1b49d-110">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="1b49d-111">Typowy definicji wyjątku języka F # podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="1b49d-111">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="1b49d-112">Wystąpił wyjątek tego typu można wygenerować za pomocą `raise` działają w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="1b49d-112">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="1b49d-113">Typ wyjątku języka F # można użyć bezpośrednio w filtrów w `try...with` wyrażenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1b49d-113">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="1b49d-114">Typ wyjątku, który definiuje z `exception` słów kluczowych w języku F # jest nowym typem, który dziedziczy z `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="1b49d-114">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>


## <a name="see-also"></a><span data-ttu-id="1b49d-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b49d-115">See Also</span></span>
[<span data-ttu-id="1b49d-116">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="1b49d-116">Exception Handling</span></span>](index.md)

[<span data-ttu-id="1b49d-117">Wyjątki: `raise` — funkcja</span><span class="sxs-lookup"><span data-stu-id="1b49d-117">Exceptions: the `raise` Function</span></span>](the-raise-function.md)

[<span data-ttu-id="1b49d-118">Hierarchia wyjątków</span><span class="sxs-lookup"><span data-stu-id="1b49d-118">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
