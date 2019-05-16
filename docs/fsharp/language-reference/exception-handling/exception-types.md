---
title: Typy wyjątków
description: Dowiedz się, jak zdefiniować i zastosować F# typów wyjątków.
ms.date: 05/16/2016
ms.openlocfilehash: b7203dc042c7207bca95cfd0372790bfe52e0226
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645569"
---
# <a name="exception-types"></a><span data-ttu-id="5679d-103">Typy wyjątków</span><span class="sxs-lookup"><span data-stu-id="5679d-103">Exception Types</span></span>

<span data-ttu-id="5679d-104">Istnieją dwie kategorie wyjątków w F#: typy wyjątków .NET i F# typów wyjątków.</span><span class="sxs-lookup"><span data-stu-id="5679d-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="5679d-105">W tym temacie opisano sposób definiowania i używania F# typów wyjątków.</span><span class="sxs-lookup"><span data-stu-id="5679d-105">This topic describes how to define and use F# exception types.</span></span>

## <a name="syntax"></a><span data-ttu-id="5679d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="5679d-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="5679d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5679d-107">Remarks</span></span>

<span data-ttu-id="5679d-108">W poprzedniej składni *typ wyjątku* jest nazwą nowego F# typ wyjątku i *typ argumentu* reprezentuje typ argumentu, który może być podany zgłosić wyjątek tego typu.</span><span class="sxs-lookup"><span data-stu-id="5679d-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="5679d-109">Można określić wiele argumentów za pomocą typu krotki *typ argumentu*.</span><span class="sxs-lookup"><span data-stu-id="5679d-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="5679d-110">Definicję typowej F# wyjątek jest podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="5679d-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="5679d-111">Wyjątek tego typu można wygenerować za pomocą `raise` funkcji w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="5679d-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="5679d-112">Możesz użyć F# typ wyjątku, bezpośrednio z filtrami, które w `try...with` wyrażenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5679d-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="5679d-113">Typ wyjątku, który zdefiniujesz z `exception` — słowo kluczowe w F# to nowy typ, który dziedziczy z `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="5679d-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>

## <a name="see-also"></a><span data-ttu-id="5679d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5679d-114">See also</span></span>

- [<span data-ttu-id="5679d-115">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="5679d-115">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="5679d-116">Wyjątki: `raise` — funkcja</span><span class="sxs-lookup"><span data-stu-id="5679d-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)
- [<span data-ttu-id="5679d-117">Hierarchia wyjątków</span><span class="sxs-lookup"><span data-stu-id="5679d-117">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
