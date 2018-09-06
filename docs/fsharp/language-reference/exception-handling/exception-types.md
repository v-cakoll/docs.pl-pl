---
title: Typy wyjątków (F#)
description: 'Dowiedz się, jak definiowanie i korzystanie z wyjątkiem typów F #.'
ms.date: 05/16/2016
ms.openlocfilehash: b8d648a3649153a3604856deb61ce41db8c40bf2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858824"
---
# <a name="exception-types"></a><span data-ttu-id="4a17a-103">Typy wyjątków</span><span class="sxs-lookup"><span data-stu-id="4a17a-103">Exception Types</span></span>

<span data-ttu-id="4a17a-104">Istnieją dwie kategorie wyjątków w języku F #: typy wyjątków .NET i typy wyjątków F #.</span><span class="sxs-lookup"><span data-stu-id="4a17a-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="4a17a-105">W tym temacie opisano sposób definiowania i używania typów wyjątków F #.</span><span class="sxs-lookup"><span data-stu-id="4a17a-105">This topic describes how to define and use F# exception types.</span></span>

## <a name="syntax"></a><span data-ttu-id="4a17a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a17a-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="4a17a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a17a-107">Remarks</span></span>

<span data-ttu-id="4a17a-108">W poprzedniej składni *typ wyjątku* nazywa się nowych typów języka F # wyjątek, i *typ argumentu* reprezentuje typ argumentu, który może być podany zgłosić wyjątek tego typu.</span><span class="sxs-lookup"><span data-stu-id="4a17a-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="4a17a-109">Można określić wiele argumentów za pomocą typu krotki *typ argumentu*.</span><span class="sxs-lookup"><span data-stu-id="4a17a-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="4a17a-110">Typowe definicji, dla wyjątku F # jest podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="4a17a-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="4a17a-111">Wyjątek tego typu można wygenerować za pomocą `raise` funkcji w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="4a17a-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="4a17a-112">Typ wyjątku F # można użyć bezpośrednio w filtry w `try...with` wyrażenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4a17a-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="4a17a-113">Typ wyjątku, który zdefiniujesz z `exception` — słowo kluczowe w języku F # to nowy typ, który dziedziczy z `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="4a17a-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a17a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a17a-114">See also</span></span>

- [<span data-ttu-id="4a17a-115">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="4a17a-115">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="4a17a-116">Wyjątki: `raise` — funkcja</span><span class="sxs-lookup"><span data-stu-id="4a17a-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)
- [<span data-ttu-id="4a17a-117">Hierarchia wyjątków</span><span class="sxs-lookup"><span data-stu-id="4a17a-117">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
