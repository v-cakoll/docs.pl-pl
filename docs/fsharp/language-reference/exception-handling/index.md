---
title: Obsługa wyjątków (F#)
description: 'Poznaj podstawy obsługi wyjątków w F # i łącza do obsługi wyrażeń i funkcji wyjątków.'
keywords: 'Visual f #, f #, funkcjonalności programowania'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ad475c4a-d94e-47d9-b27b-3ff000b65f8e
ms.openlocfilehash: b61af66e0a70fdf9b86df37418c0284957d1f99e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="exception-handling"></a><span data-ttu-id="77878-104">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="77878-104">Exception Handling</span></span>

<span data-ttu-id="77878-105">Ta sekcja zawiera informacje o pomocy technicznej w języku F # obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="77878-105">This section contains information about exception handling support in the F# language.</span></span>


## <a name="exception-handling-basics"></a><span data-ttu-id="77878-106">Podstawowe informacje dotyczące obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="77878-106">Exception Handling Basics</span></span>
<span data-ttu-id="77878-107">Obsługa wyjątków jest standardowym sposobem obsługi błędów w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="77878-107">Exception handling is the standard way of handling error conditions in the .NET Framework.</span></span> <span data-ttu-id="77878-108">W związku z tym dowolnego języka .NET musi obsługiwać ten mechanizm, w tym F #.</span><span class="sxs-lookup"><span data-stu-id="77878-108">Thus, any .NET language must support this mechanism, including F#.</span></span> <span data-ttu-id="77878-109">*Wyjątek* jest obiekt hermetyzujący informacje o błędzie.</span><span class="sxs-lookup"><span data-stu-id="77878-109">An *exception* is an object that encapsulates information about an error.</span></span> <span data-ttu-id="77878-110">Jeśli wystąpią błędy, wyjątki są zatrzymuje wykonywanie zostaje zgłoszone, a regularne.</span><span class="sxs-lookup"><span data-stu-id="77878-110">When errors occur, exceptions are raised and regular execution stops.</span></span> <span data-ttu-id="77878-111">Zamiast tego środowiska uruchomieniowego wyszukuje odpowiednią obsługę wyjątku.</span><span class="sxs-lookup"><span data-stu-id="77878-111">Instead, the runtime searches for an appropriate handler for the exception.</span></span> <span data-ttu-id="77878-112">Wyszukiwanie rozpoczyna się bieżącą funkcję i będzie kontynuowana górę stosu za pośrednictwem warstw obiektów wywołujących, aż do znalezienia zgodnego programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="77878-112">The search starts in the current function, and proceeds up the stack through the layers of callers until a matching handler is found.</span></span> <span data-ttu-id="77878-113">Następnie program obsługi jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="77878-113">Then the handler is executed.</span></span>

<span data-ttu-id="77878-114">Ponadto, ponieważ stos jest oddzielić, środowiska uruchomieniowego wykonuje żadnego kodu w `finally` bloków, aby zagwarantować, że obiekty są czyszczone poprawnie podczas procesu odwijaniem.</span><span class="sxs-lookup"><span data-stu-id="77878-114">In addition, as the stack is unwound, the runtime executes any code in `finally` blocks, to guarantee that objects are cleaned up correctly during the unwinding process.</span></span>


## <a name="related-topics"></a><span data-ttu-id="77878-115">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="77878-115">Related Topics</span></span>

|<span data-ttu-id="77878-116">Tytuł</span><span class="sxs-lookup"><span data-stu-id="77878-116">Title</span></span>|<span data-ttu-id="77878-117">Opis</span><span class="sxs-lookup"><span data-stu-id="77878-117">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="77878-118">Typy wyjątków</span><span class="sxs-lookup"><span data-stu-id="77878-118">Exception Types</span></span>](exception-types.md)|<span data-ttu-id="77878-119">Opisuje sposób zadeklarować typ wyjątku.</span><span class="sxs-lookup"><span data-stu-id="77878-119">Describes how to declare an exception type.</span></span>|
|[<span data-ttu-id="77878-120">Wyjątki: `try...with` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="77878-120">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)|<span data-ttu-id="77878-121">W tym artykule opisano konstrukcji języka, który obsługuje obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="77878-121">Describes the language construct that supports exception handling.</span></span>|
|[<span data-ttu-id="77878-122">Wyjątki: `try...finally` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="77878-122">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)|<span data-ttu-id="77878-123">W tym artykule opisano konstrukcji języka, który pozwala na wykonywanie czyszczenia kodu cofa stosu, gdy jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="77878-123">Describes the language construct that enables you to execute clean-up code as the stack unwinds when an exception is thrown.</span></span>|
|[<span data-ttu-id="77878-124">Wyjątki: `raise` — funkcja</span><span class="sxs-lookup"><span data-stu-id="77878-124">Exceptions: the `raise` Function</span></span>](the-raise-Function.md)|<span data-ttu-id="77878-125">Opisuje sposób throw obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="77878-125">Describes how to throw an exception object.</span></span>|
|[<span data-ttu-id="77878-126">Wyjątki: `failwith` — funkcja</span><span class="sxs-lookup"><span data-stu-id="77878-126">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)|<span data-ttu-id="77878-127">Opisuje sposób generowania ogólny wyjątek F #.</span><span class="sxs-lookup"><span data-stu-id="77878-127">Describes how to generate a general F# exception.</span></span>|
|[<span data-ttu-id="77878-128">Wyjątki: `invalidArg` — funkcja</span><span class="sxs-lookup"><span data-stu-id="77878-128">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)|<span data-ttu-id="77878-129">Opisuje sposób generowania wyjątek nieprawidłowego argumentu.</span><span class="sxs-lookup"><span data-stu-id="77878-129">Describes how to generate an invalid argument exception.</span></span>|
