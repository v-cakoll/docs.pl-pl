---
title: C#Instrukcje — Przewodnik po przykładzie C# języka
description: Utwórz akcje C# program za pomocą instrukcji
ms.date: 11/06/2016
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: 75f6c7bb29af7f9c809c5278c97d21683166a8e5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154297"
---
# <a name="statements"></a><span data-ttu-id="c67bf-103">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="c67bf-103">Statements</span></span>

<span data-ttu-id="c67bf-104">Akcje programu są wyrażone za pomocą *instrukcji*.</span><span class="sxs-lookup"><span data-stu-id="c67bf-104">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="c67bf-105">C# obsługuje wiele rodzajów instrukcji, z których są definiowane zgodnie z osadzonych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c67bf-105">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="c67bf-106">A *bloku* zezwala na wiele instrukcji, które ma zostać zapisany w kontekstach, których jest dozwolone pojedynczej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c67bf-106">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="c67bf-107">Blok zawiera listę instrukcji, zapisywane między ogranicznikami `{` i `}`.</span><span class="sxs-lookup"><span data-stu-id="c67bf-107">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="c67bf-108">*Instrukcje deklaracji* są używane do deklarowania stałe i zmienne lokalne.</span><span class="sxs-lookup"><span data-stu-id="c67bf-108">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="c67bf-109">*Instrukcje wyrażeń* są używane do oceny wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c67bf-109">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="c67bf-110">Wyrażenia, które mogą służyć jako stwierdzenia obejmują wywołań metod obiektu alokacje za pomocą `new` operator, za pomocą przypisań `=` i operatorów przypisania złożonego, operacje inkrementacji i dekrementacji przy użyciu `++`i `--` operatorów i `await` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c67bf-110">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="c67bf-111">*Instrukcje wyboru* są używane, aby wybrać jeden z wielu możliwych instrukcji do wykonania na podstawie wartości w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="c67bf-111">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="c67bf-112">W tej grupie są `if` i `switch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c67bf-112">In this group are the `if` and `switch` statements.</span></span>

<span data-ttu-id="c67bf-113">*Instrukcje iteracji* są używane do wykonywania wielokrotnie osadzona instrukcja.</span><span class="sxs-lookup"><span data-stu-id="c67bf-113">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="c67bf-114">W tej grupie są `while`, `do`, `for`, i `foreach` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c67bf-114">In this group are the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="c67bf-115">*Instrukcje skoku* służą do przekazywania kontroli.</span><span class="sxs-lookup"><span data-stu-id="c67bf-115">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="c67bf-116">W tej grupie są `break`, `continue`, `goto`, `throw`, `return`, i `yield` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c67bf-116">In this group are the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="c67bf-117">`try`... `catch` instrukcja jest używane do przechwytywania wyjątków, które występują podczas wykonywania blok, a `try`... `finally` instrukcja jest używane do określenia kod finalizacji, który jest zawsze wykonywana, czy wystąpił wyjątek, czy nie.</span><span class="sxs-lookup"><span data-stu-id="c67bf-117">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="c67bf-118">`checked` i `unchecked` instrukcje są używane do kontrolowania kontekstu sprawdzającego przepełnienie typu całkowitego operacje arytmetyczne i konwersje.</span><span class="sxs-lookup"><span data-stu-id="c67bf-118">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="c67bf-119">`lock` Instrukcja jest używane do uzyskania blokadę wykluczania wzajemnego dla danego obiektu, wykonania instrukcji i następnie zwalnia blokadę.</span><span class="sxs-lookup"><span data-stu-id="c67bf-119">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="c67bf-120">`using` Instrukcja jest używane do uzyskania zasobu, należy wykonać instrukcję, a następnie usunąć tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="c67bf-120">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="c67bf-121">Poniżej wymieniono rodzaje instrukcji, które mogą być używane i przedstawiono przykład dla każdego.</span><span class="sxs-lookup"><span data-stu-id="c67bf-121">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="c67bf-122">Deklaracji zmiennej lokalnej:</span><span class="sxs-lookup"><span data-stu-id="c67bf-122">Local variable declaration:</span></span>

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* <span data-ttu-id="c67bf-123">Deklaracji stałej lokalnej:</span><span class="sxs-lookup"><span data-stu-id="c67bf-123">Local constant declaration:</span></span>

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* <span data-ttu-id="c67bf-124">Instrukcja wyrażeń:</span><span class="sxs-lookup"><span data-stu-id="c67bf-124">Expression statement:</span></span>

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* <span data-ttu-id="c67bf-125">`if` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="c67bf-125">`if` statement:</span></span>

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* <span data-ttu-id="c67bf-126">`switch` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="c67bf-126">`switch` statement:</span></span>

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* <span data-ttu-id="c67bf-127">`while` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="c67bf-127">`while` statement:</span></span>

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* <span data-ttu-id="c67bf-128">`do` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="c67bf-128">`do` statement:</span></span>

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* <span data-ttu-id="c67bf-129">`for` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="c67bf-129">`for` statement:</span></span>

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* <span data-ttu-id="c67bf-130">`foreach` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="c67bf-130">`foreach` statement:</span></span>

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* <span data-ttu-id="c67bf-131">`break` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="c67bf-131">`break` statement:</span></span>

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* <span data-ttu-id="c67bf-132">`continue` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="c67bf-132">`continue` statement:</span></span>

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* <span data-ttu-id="c67bf-133">`goto` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="c67bf-133">`goto` statement:</span></span>

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* <span data-ttu-id="c67bf-134">`return` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="c67bf-134">`return` statement:</span></span>

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* <span data-ttu-id="c67bf-135">`yield` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="c67bf-135">`yield` statement:</span></span>

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* <span data-ttu-id="c67bf-136">`throw` instrukcje i `try` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="c67bf-136">`throw` statements and `try` statements:</span></span>

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* <span data-ttu-id="c67bf-137">`checked` i `unchecked` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="c67bf-137">`checked` and `unchecked` statements:</span></span>

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* <span data-ttu-id="c67bf-138">`lock` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="c67bf-138">`lock` statement:</span></span>

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* <span data-ttu-id="c67bf-139">`using` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="c67bf-139">`using` statement:</span></span>

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
><span data-ttu-id="c67bf-140">[Poprzednie](expressions.md)
>[dalej](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="c67bf-140">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>