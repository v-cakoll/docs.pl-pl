---
title: Typy wyjątków (F#)
description: 'Dowiedz się, jak zdefiniować i użyć typów wyjątków F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 6aaa5cd1b94f829b98d5aed5dcf6e30472a8b751
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="exception-types"></a><span data-ttu-id="2f900-103">Typy wyjątków</span><span class="sxs-lookup"><span data-stu-id="2f900-103">Exception Types</span></span>

<span data-ttu-id="2f900-104">Istnieją dwie kategorie wyjątków w języku F #: typy wyjątków .NET i typów wyjątków F #.</span><span class="sxs-lookup"><span data-stu-id="2f900-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="2f900-105">W tym temacie opisano sposób definiowania i użyć typów wyjątków F #.</span><span class="sxs-lookup"><span data-stu-id="2f900-105">This topic describes how to define and use F# exception types.</span></span>


## <a name="syntax"></a><span data-ttu-id="2f900-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f900-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="2f900-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f900-107">Remarks</span></span>
<span data-ttu-id="2f900-108">W poprzednich składni *typu wyjątku* jest nazwą nowego F # wyjątek typu, i *typ argumentu* reprezentuje typ argumentu, który może zostać podane w przypadku zgłaszał wyjątku tego typu.</span><span class="sxs-lookup"><span data-stu-id="2f900-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="2f900-109">Można określić wiele argumentów, za pomocą typ krotki dla *typ argumentu*.</span><span class="sxs-lookup"><span data-stu-id="2f900-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="2f900-110">Typowy definicji wyjątku języka F # podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="2f900-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="2f900-111">Wystąpił wyjątek tego typu można wygenerować za pomocą `raise` działają w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="2f900-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="2f900-112">Typ wyjątku języka F # można użyć bezpośrednio w filtrów w `try...with` wyrażenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2f900-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="2f900-113">Typ wyjątku, który definiuje z `exception` słów kluczowych w języku F # jest nowym typem, który dziedziczy z `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="2f900-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>


## <a name="see-also"></a><span data-ttu-id="2f900-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f900-114">See Also</span></span>
[<span data-ttu-id="2f900-115">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="2f900-115">Exception Handling</span></span>](index.md)

[<span data-ttu-id="2f900-116">Wyjątki: `raise` — funkcja</span><span class="sxs-lookup"><span data-stu-id="2f900-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)

[<span data-ttu-id="2f900-117">Hierarchia wyjątków</span><span class="sxs-lookup"><span data-stu-id="2f900-117">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
