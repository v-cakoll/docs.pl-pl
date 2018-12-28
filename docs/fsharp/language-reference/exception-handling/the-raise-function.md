---
title: 'Wyjątki: raise — Funkcja'
description: Dowiedz się, jak F# "raise" funkcja służy do wskazania, że wystąpił błąd lub wyjątkowy warunek.
ms.date: 05/16/2016
ms.openlocfilehash: 87773ead7773c62a325c7e7ff105c729e10dd69c
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610154"
---
# <a name="exceptions-the-raise-function"></a><span data-ttu-id="42e68-103">Wyjątki: raise — Funkcja</span><span class="sxs-lookup"><span data-stu-id="42e68-103">Exceptions: the raise Function</span></span>

<span data-ttu-id="42e68-104">`raise` Funkcji jest używany do wskazania, że wystąpił błąd lub wyjątkowy warunek.</span><span class="sxs-lookup"><span data-stu-id="42e68-104">The `raise` function is used to indicate that an error or exceptional condition has occurred.</span></span> <span data-ttu-id="42e68-105">Informacje o błędzie są przechwytywane w obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="42e68-105">Information about the error is captured in an exception object.</span></span>

## <a name="syntax"></a><span data-ttu-id="42e68-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="42e68-106">Syntax</span></span>

```fsharp
raise (expression)
```

## <a name="remarks"></a><span data-ttu-id="42e68-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="42e68-107">Remarks</span></span>

<span data-ttu-id="42e68-108">`raise` Funkcja generuje obiekt wyjątku i inicjuje proces odwijanie stosu.</span><span class="sxs-lookup"><span data-stu-id="42e68-108">The `raise` function generates an exception object and initiates a stack unwinding process.</span></span> <span data-ttu-id="42e68-109">Proces odwijania stosu jest zarządzany przez środowisko uruchomieniowe języka wspólnego (CLR), więc zachowanie tego procesu jest taka sama jak w dowolnym języku .NET.</span><span class="sxs-lookup"><span data-stu-id="42e68-109">The stack unwinding process is managed by the common language runtime (CLR), so the behavior of this process is the same as it is in any other .NET language.</span></span> <span data-ttu-id="42e68-110">Proces odwijania stosu jest wyszukiwanie do obsługi wyjątku, który odpowiada wygenerowany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="42e68-110">The stack unwinding process is a search for an exception handler that matches the generated exception.</span></span> <span data-ttu-id="42e68-111">Wyszukiwanie rozpoczyna się w bieżącym `try...with` wyrażenia, jeśli taka istnieje.</span><span class="sxs-lookup"><span data-stu-id="42e68-111">The search starts in the current `try...with` expression, if there is one.</span></span> <span data-ttu-id="42e68-112">Każdy wzorzec w `with` bloku jest zaznaczone, w kolejności.</span><span class="sxs-lookup"><span data-stu-id="42e68-112">Each pattern in the `with` block is checked, in order.</span></span> <span data-ttu-id="42e68-113">W przypadku odnalezienia pasującego obsługi wyjątków wyjątek jest uznawany za obsługiwany; w przeciwnym razie stos jest odwijany, i `with` bloki łańcuch wywołań są sprawdzane, dopóki nie znaleziono pasującej klauzuli obsługi.</span><span class="sxs-lookup"><span data-stu-id="42e68-113">When a matching exception handler is found, the exception is considered handled; otherwise, the stack is unwound and `with` blocks up the call chain are checked until a matching handler is found.</span></span> <span data-ttu-id="42e68-114">Wszelkie `finally` bloki, które wystąpią w łańcuchu wywołań także są wykonywane w kolejności, jak rozwija stos.</span><span class="sxs-lookup"><span data-stu-id="42e68-114">Any `finally` blocks that are encountered in the call chain are also executed in sequence as the stack unwinds.</span></span>

<span data-ttu-id="42e68-115">`raise` Funkcji jest odpowiednikiem `throw` w języku C# lub C++.</span><span class="sxs-lookup"><span data-stu-id="42e68-115">The `raise` function is the equivalent of `throw` in C# or C++.</span></span> <span data-ttu-id="42e68-116">Użyj `reraise` w obsługi catch do propagowania ten sam wyjątek łańcuch wywołań.</span><span class="sxs-lookup"><span data-stu-id="42e68-116">Use `reraise` in a catch handler to propagate the same exception up the call chain.</span></span>

<span data-ttu-id="42e68-117">Poniższe przykłady kodu ilustrują używanie `raise` funkcję, aby wygenerować wyjątek.</span><span class="sxs-lookup"><span data-stu-id="42e68-117">The following code examples illustrate the use of the `raise` function to generate an exception.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

<span data-ttu-id="42e68-118">`raise` Funkcji można również zgłaszać wyjątki .NET, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="42e68-118">The `raise` function can also be used to raise .NET exceptions, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a><span data-ttu-id="42e68-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42e68-119">See also</span></span>

- [<span data-ttu-id="42e68-120">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="42e68-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="42e68-121">Typy wyjątków</span><span class="sxs-lookup"><span data-stu-id="42e68-121">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="42e68-122">Wyjątki: `try...with` Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="42e68-122">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
- [<span data-ttu-id="42e68-123">Wyjątki: `try...finally` Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="42e68-123">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
- [<span data-ttu-id="42e68-124">Wyjątki: `failwith` — Funkcja</span><span class="sxs-lookup"><span data-stu-id="42e68-124">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)
- [<span data-ttu-id="42e68-125">Wyjątki: `invalidArg` — Funkcja</span><span class="sxs-lookup"><span data-stu-id="42e68-125">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)