---
title: 'Wyjątki: raise — Funkcja'
description: Dowiedz się F# , jak funkcja "podnoszenie" służy do wskazywania, że wystąpił błąd lub wyjątkowy warunek.
ms.date: 05/16/2016
ms.openlocfilehash: e0cc8da8310203c537b8081af8a225671bd8c6a3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630289"
---
# <a name="exceptions-the-raise-function"></a><span data-ttu-id="2c524-103">Wyjątki: raise — Funkcja</span><span class="sxs-lookup"><span data-stu-id="2c524-103">Exceptions: the raise Function</span></span>

<span data-ttu-id="2c524-104">`raise` Funkcja służy do wskazywania, że wystąpił błąd lub wyjątkowy warunek.</span><span class="sxs-lookup"><span data-stu-id="2c524-104">The `raise` function is used to indicate that an error or exceptional condition has occurred.</span></span> <span data-ttu-id="2c524-105">Informacje o błędzie są przechwytywane w obiekcie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2c524-105">Information about the error is captured in an exception object.</span></span>

## <a name="syntax"></a><span data-ttu-id="2c524-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c524-106">Syntax</span></span>

```fsharp
raise (expression)
```

## <a name="remarks"></a><span data-ttu-id="2c524-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c524-107">Remarks</span></span>

<span data-ttu-id="2c524-108">`raise` Funkcja generuje obiekt wyjątku i inicjuje proces odwinięcia stosu.</span><span class="sxs-lookup"><span data-stu-id="2c524-108">The `raise` function generates an exception object and initiates a stack unwinding process.</span></span> <span data-ttu-id="2c524-109">Proces odwinięcia stosu jest zarządzany przez środowisko uruchomieniowe języka wspólnego (CLR), dzięki czemu zachowanie tego procesu jest takie samo, jak w przypadku dowolnego innego języka .NET.</span><span class="sxs-lookup"><span data-stu-id="2c524-109">The stack unwinding process is managed by the common language runtime (CLR), so the behavior of this process is the same as it is in any other .NET language.</span></span> <span data-ttu-id="2c524-110">Proces odwinięcia stosu jest wyszukiwaniem programu obsługi wyjątków, który pasuje do wygenerowanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2c524-110">The stack unwinding process is a search for an exception handler that matches the generated exception.</span></span> <span data-ttu-id="2c524-111">Wyszukiwanie rozpocznie się w bieżącym `try...with` wyrażeniu, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="2c524-111">The search starts in the current `try...with` expression, if there is one.</span></span> <span data-ttu-id="2c524-112">Każdy wzorzec w `with` bloku jest zaznaczony w kolejności.</span><span class="sxs-lookup"><span data-stu-id="2c524-112">Each pattern in the `with` block is checked, in order.</span></span> <span data-ttu-id="2c524-113">Po znalezieniu pasującej obsługi wyjątków wyjątek jest uznawany za obsłużony; w przeciwnym razie stos zostanie odtworzony i `with` zablokuje łańcuch wywołań, dopóki nie zostanie znaleziona zgodna procedura obsługi.</span><span class="sxs-lookup"><span data-stu-id="2c524-113">When a matching exception handler is found, the exception is considered handled; otherwise, the stack is unwound and `with` blocks up the call chain are checked until a matching handler is found.</span></span> <span data-ttu-id="2c524-114">Wszystkie `finally` bloki, które są napotkane w łańcuchu wywołań są również wykonywane sekwencyjnie jako rozwinięcia stosu.</span><span class="sxs-lookup"><span data-stu-id="2c524-114">Any `finally` blocks that are encountered in the call chain are also executed in sequence as the stack unwinds.</span></span>

<span data-ttu-id="2c524-115">Funkcja jest odpowiednikiem C# w lub C++ `throw` `raise`</span><span class="sxs-lookup"><span data-stu-id="2c524-115">The `raise` function is the equivalent of `throw` in C# or C++.</span></span> <span data-ttu-id="2c524-116">Użyj `reraise` w procedurze obsługi catch, aby propagować ten sam wyjątek w łańcuchu wywołań.</span><span class="sxs-lookup"><span data-stu-id="2c524-116">Use `reraise` in a catch handler to propagate the same exception up the call chain.</span></span>

<span data-ttu-id="2c524-117">Poniższy przykład kodu ilustruje użycie `raise` funkcji do wygenerowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2c524-117">The following code examples illustrate the use of the `raise` function to generate an exception.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

<span data-ttu-id="2c524-118">`raise` Funkcja może również służyć do wywoływania wyjątków platformy .NET, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2c524-118">The `raise` function can also be used to raise .NET exceptions, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a><span data-ttu-id="2c524-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c524-119">See also</span></span>

- [<span data-ttu-id="2c524-120">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="2c524-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="2c524-121">Typy wyjątków</span><span class="sxs-lookup"><span data-stu-id="2c524-121">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="2c524-122">Wyjątki: `try...with` Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="2c524-122">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
- [<span data-ttu-id="2c524-123">Wyjątki: `try...finally` Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="2c524-123">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
- [<span data-ttu-id="2c524-124">Wyjątki: `failwith` Funkcja</span><span class="sxs-lookup"><span data-stu-id="2c524-124">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)
- [<span data-ttu-id="2c524-125">Wyjątki: `invalidArg` Funkcja</span><span class="sxs-lookup"><span data-stu-id="2c524-125">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)
