---
title: C# Instrukcje — przewodnik po języku Języka C#
description: Akcje programu C# można tworzyć przy użyciu instrukcji
ms.date: 02/27/2020
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: ced13b1bfd17977acb98bf33c0a477161cf08a93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159107"
---
# <a name="statements"></a><span data-ttu-id="0fead-103">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="0fead-103">Statements</span></span>

<span data-ttu-id="0fead-104">Akcje programu są wyrażane za pomocą *instrukcji*.</span><span class="sxs-lookup"><span data-stu-id="0fead-104">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="0fead-105">C# obsługuje kilka różnych rodzajów instrukcji, z których wiele jest zdefiniowanych w kategoriach osadzonych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0fead-105">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="0fead-106">*Blok* zezwala na wiele instrukcji do zapisu w kontekstach, w których pojedyncza instrukcja jest dozwolona.</span><span class="sxs-lookup"><span data-stu-id="0fead-106">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="0fead-107">Blok składa się z listy instrukcji napisanych `{` `}`między ogranicznikami i .</span><span class="sxs-lookup"><span data-stu-id="0fead-107">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="0fead-108">*Instrukcje deklaracji* są używane do deklarowania zmiennych lokalnych i stałych.</span><span class="sxs-lookup"><span data-stu-id="0fead-108">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="0fead-109">*Instrukcje wyrażenia* są używane do oceny wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="0fead-109">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="0fead-110">Wyrażenia, które mogą być używane jako instrukcje obejmują wywołania `new` metody, alokacje obiektów przy użyciu operatora, przypisania `=` przy `++` `--` użyciu `await` i operatorów przypisania złożonego, operacje przyrostu i zmniejszania przy użyciu i operatorów i wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="0fead-110">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="0fead-111">*Instrukcje wyboru* są używane do wybierania jednej z wielu możliwych instrukcji do wykonania na podstawie wartości niektórych wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="0fead-111">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="0fead-112">Ta grupa `if` zawiera `switch` i instrukcje.</span><span class="sxs-lookup"><span data-stu-id="0fead-112">This group contains the `if` and `switch` statements.</span></span>

<span data-ttu-id="0fead-113">*Instrukcje iteracji* są używane do wykonywania wielokrotnie osadzone instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0fead-113">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="0fead-114">Ta grupa `while`zawiera `do` `for`, `foreach` , i instrukcje.</span><span class="sxs-lookup"><span data-stu-id="0fead-114">This group contains the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="0fead-115">*Instrukcje skoku* są używane do przenoszenia kontroli.</span><span class="sxs-lookup"><span data-stu-id="0fead-115">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="0fead-116">Ta grupa `break`zawiera `continue` `goto`, `throw` `return`, `yield` , , i instrukcje.</span><span class="sxs-lookup"><span data-stu-id="0fead-116">This group contains the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="0fead-117">W `try`... `catch` instrukcja służy do wychwytywania wyjątków, które występują podczas wykonywania bloku, a `try`... `finally` instrukcja służy do określania kodu finalizacji, który jest zawsze wykonywany, niezależnie od tego, czy wystąpił wyjątek, czy nie.</span><span class="sxs-lookup"><span data-stu-id="0fead-117">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="0fead-118">I `checked` `unchecked` instrukcje są używane do kontrolowania kontekstu sprawdzania przepełnienia dla operacji arytmetycznych typu integralnego i konwersji.</span><span class="sxs-lookup"><span data-stu-id="0fead-118">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="0fead-119">Instrukcja `lock` jest używana do uzyskania blokady wzajemnego wykluczenia dla danego obiektu, wykonać instrukcję, a następnie zwolnić blokadę.</span><span class="sxs-lookup"><span data-stu-id="0fead-119">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="0fead-120">Instrukcja `using` jest używana do uzyskania zasobu, wykonania instrukcji, a następnie usunięcia tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="0fead-120">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="0fead-121">Poniżej wymieniono rodzaje instrukcji, które mogą być używane i stanowi przykład dla każdego.</span><span class="sxs-lookup"><span data-stu-id="0fead-121">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="0fead-122">Deklaracja zmiennej lokalnej:</span><span class="sxs-lookup"><span data-stu-id="0fead-122">Local variable declaration:</span></span>

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* <span data-ttu-id="0fead-123">Stała deklaracja lokalna:</span><span class="sxs-lookup"><span data-stu-id="0fead-123">Local constant declaration:</span></span>

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* <span data-ttu-id="0fead-124">Instrukcja wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="0fead-124">Expression statement:</span></span>

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* <span data-ttu-id="0fead-125">`if`Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="0fead-125">`if` statement:</span></span>

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* <span data-ttu-id="0fead-126">`switch`Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="0fead-126">`switch` statement:</span></span>

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* <span data-ttu-id="0fead-127">`while`Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="0fead-127">`while` statement:</span></span>

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* <span data-ttu-id="0fead-128">`do`Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="0fead-128">`do` statement:</span></span>

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* <span data-ttu-id="0fead-129">`for`Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="0fead-129">`for` statement:</span></span>

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* <span data-ttu-id="0fead-130">`foreach`Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="0fead-130">`foreach` statement:</span></span>

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* <span data-ttu-id="0fead-131">`break`Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="0fead-131">`break` statement:</span></span>

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* <span data-ttu-id="0fead-132">`continue`Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="0fead-132">`continue` statement:</span></span>

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* <span data-ttu-id="0fead-133">`goto`Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="0fead-133">`goto` statement:</span></span>

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* <span data-ttu-id="0fead-134">`return`Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="0fead-134">`return` statement:</span></span>

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* <span data-ttu-id="0fead-135">`yield`Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="0fead-135">`yield` statement:</span></span>

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* <span data-ttu-id="0fead-136">`throw`oświadczenia `try` i oświadczenia:</span><span class="sxs-lookup"><span data-stu-id="0fead-136">`throw` statements and `try` statements:</span></span>

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* <span data-ttu-id="0fead-137">`checked`i `unchecked` oświadczenia:</span><span class="sxs-lookup"><span data-stu-id="0fead-137">`checked` and `unchecked` statements:</span></span>

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* <span data-ttu-id="0fead-138">`lock`Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="0fead-138">`lock` statement:</span></span>

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* <span data-ttu-id="0fead-139">`using`Instrukcja:</span><span class="sxs-lookup"><span data-stu-id="0fead-139">`using` statement:</span></span>

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
><span data-ttu-id="0fead-140">[Poprzedni](expressions.md)
>[następny](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="0fead-140">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>
