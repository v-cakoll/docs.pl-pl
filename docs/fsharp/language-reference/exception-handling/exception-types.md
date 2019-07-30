---
title: Typy wyjątków
description: Dowiedz się, jak definiować F# typy wyjątków i korzystać z nich.
ms.date: 05/16/2016
ms.openlocfilehash: 8545fab50ff6338d1f1621710a838a200f9ac705
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630311"
---
# <a name="exception-types"></a><span data-ttu-id="cfed6-103">Typy wyjątków</span><span class="sxs-lookup"><span data-stu-id="cfed6-103">Exception Types</span></span>

<span data-ttu-id="cfed6-104">Istnieją dwie kategorie wyjątków w programie F#: typy wyjątków .NET i F# typy wyjątków.</span><span class="sxs-lookup"><span data-stu-id="cfed6-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="cfed6-105">W tym temacie opisano sposób definiowania typów wyjątków F# i ich używania.</span><span class="sxs-lookup"><span data-stu-id="cfed6-105">This topic describes how to define and use F# exception types.</span></span>

## <a name="syntax"></a><span data-ttu-id="cfed6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="cfed6-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="cfed6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cfed6-107">Remarks</span></span>

<span data-ttu-id="cfed6-108">W poprzedniej składni *Typ wyjątku* jest nazwą nowego F# typu wyjątku, a *argument-type* reprezentuje typ argumentu, który może być dostarczony podczas zgłaszania wyjątku tego typu.</span><span class="sxs-lookup"><span data-stu-id="cfed6-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="cfed6-109">Można określić wiele argumentów za pomocą typu krotki dla *typu argumentu*.</span><span class="sxs-lookup"><span data-stu-id="cfed6-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="cfed6-110">Typowa definicja F# wyjątku jest podobna do następującej.</span><span class="sxs-lookup"><span data-stu-id="cfed6-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="cfed6-111">Wyjątek tego typu można wygenerować przy użyciu `raise` funkcji w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="cfed6-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="cfed6-112">Możesz użyć typu F# wyjątku bezpośrednio w filtrach w `try...with` wyrażeniu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cfed6-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="cfed6-113">Typ wyjątku zdefiniowany za pomocą `exception` słowa kluczowego w F# jest nowym typem, który dziedziczy z `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="cfed6-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>

## <a name="see-also"></a><span data-ttu-id="cfed6-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cfed6-114">See also</span></span>

- [<span data-ttu-id="cfed6-115">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="cfed6-115">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="cfed6-116">Wyjątki: `raise` funkcja</span><span class="sxs-lookup"><span data-stu-id="cfed6-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)
- [<span data-ttu-id="cfed6-117">Hierarchia wyjątków</span><span class="sxs-lookup"><span data-stu-id="cfed6-117">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
