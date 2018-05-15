---
title: C# instrukcje — samouczek języka C#
description: Utwórz akcje programu C# przy użyciu instrukcji
ms.date: 11/06/2016
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: 2f25c07ccc0af27a503465b9414bf607c61d1b2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="statements"></a><span data-ttu-id="df3a8-103">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="df3a8-103">Statements</span></span>

<span data-ttu-id="df3a8-104">Akcje programu są wyrażane przy użyciu *instrukcje*.</span><span class="sxs-lookup"><span data-stu-id="df3a8-104">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="df3a8-105">C# obsługuje wiele rodzajów instrukcje liczba zdefiniowanych pod względem instrukcji osadzonych.</span><span class="sxs-lookup"><span data-stu-id="df3a8-105">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="df3a8-106">A *bloku* zezwala na użycie wielu instrukcji w kontekstach, których jednej instrukcji jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="df3a8-106">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="df3a8-107">Blok składa się z listy instrukcji zapisywane między ograniczniki `{` i `}`.</span><span class="sxs-lookup"><span data-stu-id="df3a8-107">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="df3a8-108">*Instrukcje deklaracji* są używane do deklarowania zmiennych lokalnych i stałe.</span><span class="sxs-lookup"><span data-stu-id="df3a8-108">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="df3a8-109">*Instrukcje wyrażeń* są używane do analizowania wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="df3a8-109">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="df3a8-110">Wyrażeń, które mogą być używane jako instrukcje obejmują wywołań metody opisywanego obiekt alokacji używających `new` operator, za pomocą przypisań `=` oraz złożone operatory przypisania, inkrementacja i dekrementacja operacje przy użyciu `++`i `--` operatory i `await` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="df3a8-110">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="df3a8-111">*Instrukcje wyboru* służą do wybierania jeden z wielu instrukcji możliwych do wykonania na podstawie wartości niektóre wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="df3a8-111">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="df3a8-112">W tej grupie są `if` i `switch` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="df3a8-112">In this group are the `if` and `switch` statements.</span></span>

<span data-ttu-id="df3a8-113">*Instrukcje iteracji* są używane wielokrotnie wykonać instrukcję osadzonych.</span><span class="sxs-lookup"><span data-stu-id="df3a8-113">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="df3a8-114">W tej grupie są `while`, `do`, `for`, i `foreach` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="df3a8-114">In this group are the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="df3a8-115">*Instrukcje skoku* są używane do przekazywania kontroli.</span><span class="sxs-lookup"><span data-stu-id="df3a8-115">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="df3a8-116">W tej grupie są `break`, `continue`, `goto`, `throw`, `return`, i `yield` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="df3a8-116">In this group are the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="df3a8-117">`try`... `catch` przechwytują wyjątki, jakie występują podczas wykonywania blok, używana jest instrukcja i `try`... `finally` instrukcji służy do określania finalizacji kod, który jest zawsze wykonywana, czy nie wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="df3a8-117">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="df3a8-118">`checked` i `unchecked` instrukcje są używane do kontrolowania kontekst sprawdzanie przepełnienia dla operacji arytmetycznych typem całkowitym i konwersji.</span><span class="sxs-lookup"><span data-stu-id="df3a8-118">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="df3a8-119">`lock` Instrukcji służy do uzyskania blokady wzajemnego wykluczeń dla danego obiektu, wykonania instrukcji, a następnie zwolnij blokady.</span><span class="sxs-lookup"><span data-stu-id="df3a8-119">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="df3a8-120">`using` Instrukcji jest używany do uzyskania zasobu, wykonania instrukcji i następnie usuwania tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="df3a8-120">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="df3a8-121">Poniżej wymieniono rodzaje instrukcji, które mogą być używane i zawiera przykład dla każdego.</span><span class="sxs-lookup"><span data-stu-id="df3a8-121">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="df3a8-122">Deklaracja zmiennej lokalnej:</span><span class="sxs-lookup"><span data-stu-id="df3a8-122">Local variable declaration:</span></span>

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* <span data-ttu-id="df3a8-123">Deklaracja stałej lokalna:</span><span class="sxs-lookup"><span data-stu-id="df3a8-123">Local constant declaration:</span></span>

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* <span data-ttu-id="df3a8-124">Instrukcja wyrażeń:</span><span class="sxs-lookup"><span data-stu-id="df3a8-124">Expression statement:</span></span>

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* <span data-ttu-id="df3a8-125">`if` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="df3a8-125">`if` statement:</span></span>

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* <span data-ttu-id="df3a8-126">`switch` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="df3a8-126">`switch` statement:</span></span>

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* <span data-ttu-id="df3a8-127">`while` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="df3a8-127">`while` statement:</span></span>

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* <span data-ttu-id="df3a8-128">`do` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="df3a8-128">`do` statement:</span></span>

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* <span data-ttu-id="df3a8-129">`for` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="df3a8-129">`for` statement:</span></span>

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* <span data-ttu-id="df3a8-130">`foreach` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="df3a8-130">`foreach` statement:</span></span>

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* <span data-ttu-id="df3a8-131">`break` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="df3a8-131">`break` statement:</span></span>

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* <span data-ttu-id="df3a8-132">`continue` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="df3a8-132">`continue` statement:</span></span>

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* <span data-ttu-id="df3a8-133">`goto` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="df3a8-133">`goto` statement:</span></span>

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* <span data-ttu-id="df3a8-134">`return` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="df3a8-134">`return` statement:</span></span>

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* <span data-ttu-id="df3a8-135">`yield` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="df3a8-135">`yield` statement:</span></span>

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* <span data-ttu-id="df3a8-136">`throw` instrukcje i `try` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="df3a8-136">`throw` statements and `try` statements:</span></span>

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* <span data-ttu-id="df3a8-137">`checked` i `unchecked` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="df3a8-137">`checked` and `unchecked` statements:</span></span>

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* <span data-ttu-id="df3a8-138">`lock` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="df3a8-138">`lock` statement:</span></span>

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* <span data-ttu-id="df3a8-139">`using` Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="df3a8-139">`using` statement:</span></span>

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
<span data-ttu-id="df3a8-140">[Poprzednie](expressions.md)
[dalej](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="df3a8-140">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>
