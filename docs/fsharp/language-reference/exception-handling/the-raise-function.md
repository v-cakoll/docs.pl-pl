---
title: 'Wyjątki: raise — Funkcja (F#)'
description: 'Dowiedz się, jak F # "raise" funkcja służy do wskazują, że wystąpił błąd lub wyjątkowych warunku.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.assetid: b00da469-4789-4cdd-9f77-7a2e29f28637
ms.openlocfilehash: 6bc62b13467b8cf4cfcb22f7d4a5f3464236f6d1
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="exceptions-the-raise-function"></a><span data-ttu-id="4e811-103">Wyjątki: raise — Funkcja</span><span class="sxs-lookup"><span data-stu-id="4e811-103">Exceptions: the raise Function</span></span>

<span data-ttu-id="4e811-104">`raise` Funkcja służy do wskazują, że wystąpił błąd lub wyjątkowych warunku.</span><span class="sxs-lookup"><span data-stu-id="4e811-104">The `raise` function is used to indicate that an error or exceptional condition has occurred.</span></span> <span data-ttu-id="4e811-105">Obiekt wyjątku jest przechwytywane informacje o tym błędzie.</span><span class="sxs-lookup"><span data-stu-id="4e811-105">Information about the error is captured in an exception object.</span></span>


## <a name="syntax"></a><span data-ttu-id="4e811-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e811-106">Syntax</span></span>

```fsharp
raise (expression)
```

## <a name="remarks"></a><span data-ttu-id="4e811-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e811-107">Remarks</span></span>
<span data-ttu-id="4e811-108">`raise` Funkcji generuje obiekt wyjątku i inicjuje proces odwijanie stosu.</span><span class="sxs-lookup"><span data-stu-id="4e811-108">The `raise` function generates an exception object and initiates a stack unwinding process.</span></span> <span data-ttu-id="4e811-109">Proces odwijaniem stosu jest zarządzana przez środowisko uruchomieniowe języka wspólnego (CLR), dlatego działanie tego procesu jest taka sama jak w dowolnym języku .NET.</span><span class="sxs-lookup"><span data-stu-id="4e811-109">The stack unwinding process is managed by the common language runtime (CLR), so the behavior of this process is the same as it is in any other .NET language.</span></span> <span data-ttu-id="4e811-110">Proces odwijaniem stosu jest wyszukiwania dla obsługi wyjątków odpowiadający wygenerowany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="4e811-110">The stack unwinding process is a search for an exception handler that matches the generated exception.</span></span> <span data-ttu-id="4e811-111">Wyszukiwanie rozpoczyna się w bieżącym `try...with` wyrażenia, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="4e811-111">The search starts in the current `try...with` expression, if there is one.</span></span> <span data-ttu-id="4e811-112">W każdym wzorca `with` bloku zaznaczono w kolejności.</span><span class="sxs-lookup"><span data-stu-id="4e811-112">Each pattern in the `with` block is checked, in order.</span></span> <span data-ttu-id="4e811-113">W przypadku odnalezienia pasującego obsługi wyjątków wyjątek jest uznawany za obsługiwany; w przeciwnym razie stos jest oddzielić i `with` bloki zapasowej łańcuch wywołań są zaznaczone, aż do znalezienia zgodnego programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="4e811-113">When a matching exception handler is found, the exception is considered handled; otherwise, the stack is unwound and `with` blocks up the call chain are checked until a matching handler is found.</span></span> <span data-ttu-id="4e811-114">Wszelkie `finally` bloków, które występują w łańcuchu wywołań także są wykonywane w kolejności jako cofa stosu.</span><span class="sxs-lookup"><span data-stu-id="4e811-114">Any `finally` blocks that are encountered in the call chain are also executed in sequence as the stack unwinds.</span></span>

<span data-ttu-id="4e811-115">`raise` Funkcji jest odpowiednikiem `throw` w języku C# lub języka C++.</span><span class="sxs-lookup"><span data-stu-id="4e811-115">The `raise` function is the equivalent of `throw` in C# or C++.</span></span> <span data-ttu-id="4e811-116">Użyj `reraise` w procedurze obsługi catch propagację ten sam wyjątek zapasowej łańcuch wywołań.</span><span class="sxs-lookup"><span data-stu-id="4e811-116">Use `reraise` in a catch handler to propagate the same exception up the call chain.</span></span>

<span data-ttu-id="4e811-117">Następujący przykładowy kod, przedstawiający zastosowanie `raise` funkcji do generowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="4e811-117">The following code examples illustrate the use of the `raise` function to generate an exception.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

<span data-ttu-id="4e811-118">`raise` Funkcji można również zgłaszać wyjątki .NET, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4e811-118">The `raise` function can also be used to raise .NET exceptions, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]
    
## <a name="see-also"></a><span data-ttu-id="4e811-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4e811-119">See Also</span></span>
[<span data-ttu-id="4e811-120">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="4e811-120">Exception Handling</span></span>](index.md)

[<span data-ttu-id="4e811-121">Typy wyjątków</span><span class="sxs-lookup"><span data-stu-id="4e811-121">Exception Types</span></span>](exception-types.md)

[<span data-ttu-id="4e811-122">Wyjątki: `try...with` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="4e811-122">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)

[<span data-ttu-id="4e811-123">Wyjątki: `try...finally` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="4e811-123">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)

[<span data-ttu-id="4e811-124">Wyjątki: `failwith` — funkcja</span><span class="sxs-lookup"><span data-stu-id="4e811-124">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)

[<span data-ttu-id="4e811-125">Wyjątki: `invalidArg` — funkcja</span><span class="sxs-lookup"><span data-stu-id="4e811-125">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)
