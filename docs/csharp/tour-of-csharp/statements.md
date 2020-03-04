---
title: C#Instrukcje — przewodnik po C# języku
description: Tworzenie akcji C# programu przy użyciu instrukcji
ms.date: 02/27/2020
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: ced13b1bfd17977acb98bf33c0a477161cf08a93
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159107"
---
# <a name="statements"></a><span data-ttu-id="46fc7-103">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="46fc7-103">Statements</span></span>

<span data-ttu-id="46fc7-104">Akcje programu są wyrażane przy użyciu *instrukcji*.</span><span class="sxs-lookup"><span data-stu-id="46fc7-104">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="46fc7-105">C#obsługuje kilka różnych rodzajów instrukcji, które są zdefiniowane w zakresie osadzonych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="46fc7-105">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="46fc7-106">*Blok* umożliwia zapisanie wielu instrukcji w kontekstach, w których Pojedyncza instrukcja jest dozwolona.</span><span class="sxs-lookup"><span data-stu-id="46fc7-106">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="46fc7-107">Blok składa się z listy instrukcji zapisanych między ogranicznikami `{` i `}`.</span><span class="sxs-lookup"><span data-stu-id="46fc7-107">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="46fc7-108">*Instrukcje deklaracji* są używane do deklarowania zmiennych lokalnych i stałych.</span><span class="sxs-lookup"><span data-stu-id="46fc7-108">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="46fc7-109">*Instrukcje wyrażeń* są używane do obliczania wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="46fc7-109">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="46fc7-110">Wyrażenia, które mogą być używane jako instrukcje, obejmują wywołania metod, alokacje obiektów za pomocą operatora `new`, przypisania przy użyciu `=` i operatory przypisania złożonego, operacje zwiększania i zmniejszania przy użyciu operatorów `++` i `--` oraz wyrażeń `await`.</span><span class="sxs-lookup"><span data-stu-id="46fc7-110">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="46fc7-111">*Instrukcje wyboru* są używane do wybierania jednej z wielu możliwych instrukcji do wykonania na podstawie wartości niektórych wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="46fc7-111">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="46fc7-112">Ta grupa zawiera instrukcje `if` i `switch`.</span><span class="sxs-lookup"><span data-stu-id="46fc7-112">This group contains the `if` and `switch` statements.</span></span>

<span data-ttu-id="46fc7-113">*Instrukcje iteracji* są używane do wielokrotnego wykonywania osadzonej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="46fc7-113">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="46fc7-114">Ta grupa zawiera instrukcje `while`, `do`, `for`i `foreach`.</span><span class="sxs-lookup"><span data-stu-id="46fc7-114">This group contains the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="46fc7-115">*Instrukcje skoku* są używane do transferowania kontroli.</span><span class="sxs-lookup"><span data-stu-id="46fc7-115">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="46fc7-116">Ta grupa zawiera instrukcje `break`, `continue`, `goto`, `throw`, `return`i `yield`.</span><span class="sxs-lookup"><span data-stu-id="46fc7-116">This group contains the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="46fc7-117">Instrukcja `try`...`catch` służy do przechwytywania wyjątków występujących podczas wykonywania bloku, a instrukcja `try`...`finally` służy do określania kodu finalizacji, który jest zawsze wykonywany, niezależnie od tego, czy wystąpił wyjątek, czy nie.</span><span class="sxs-lookup"><span data-stu-id="46fc7-117">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="46fc7-118">Instrukcje `checked` i `unchecked` są używane do kontrolowania kontekstu sprawdzania przepełnienia dla operacji arytmetycznych typu całkowitego i konwersji.</span><span class="sxs-lookup"><span data-stu-id="46fc7-118">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="46fc7-119">Instrukcja `lock` służy do uzyskiwania blokady wzajemnego wykluczania dla danego obiektu, wykonywania instrukcji i zwalniania blokady.</span><span class="sxs-lookup"><span data-stu-id="46fc7-119">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="46fc7-120">Instrukcja `using` służy do uzyskiwania zasobu, wykonywania instrukcji i usuwania tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="46fc7-120">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="46fc7-121">Poniżej wymieniono rodzaje instrukcji, które mogą być używane, i przedstawiono przykład dla każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="46fc7-121">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="46fc7-122">Deklaracja zmiennej lokalnej:</span><span class="sxs-lookup"><span data-stu-id="46fc7-122">Local variable declaration:</span></span>

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* <span data-ttu-id="46fc7-123">Lokalna deklaracja stała:</span><span class="sxs-lookup"><span data-stu-id="46fc7-123">Local constant declaration:</span></span>

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* <span data-ttu-id="46fc7-124">Instrukcja wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="46fc7-124">Expression statement:</span></span>

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* <span data-ttu-id="46fc7-125">Instrukcja `if`:</span><span class="sxs-lookup"><span data-stu-id="46fc7-125">`if` statement:</span></span>

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* <span data-ttu-id="46fc7-126">Instrukcja `switch`:</span><span class="sxs-lookup"><span data-stu-id="46fc7-126">`switch` statement:</span></span>

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* <span data-ttu-id="46fc7-127">Instrukcja `while`:</span><span class="sxs-lookup"><span data-stu-id="46fc7-127">`while` statement:</span></span>

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* <span data-ttu-id="46fc7-128">Instrukcja `do`:</span><span class="sxs-lookup"><span data-stu-id="46fc7-128">`do` statement:</span></span>

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* <span data-ttu-id="46fc7-129">Instrukcja `for`:</span><span class="sxs-lookup"><span data-stu-id="46fc7-129">`for` statement:</span></span>

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* <span data-ttu-id="46fc7-130">Instrukcja `foreach`:</span><span class="sxs-lookup"><span data-stu-id="46fc7-130">`foreach` statement:</span></span>

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* <span data-ttu-id="46fc7-131">Instrukcja `break`:</span><span class="sxs-lookup"><span data-stu-id="46fc7-131">`break` statement:</span></span>

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* <span data-ttu-id="46fc7-132">Instrukcja `continue`:</span><span class="sxs-lookup"><span data-stu-id="46fc7-132">`continue` statement:</span></span>

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* <span data-ttu-id="46fc7-133">Instrukcja `goto`:</span><span class="sxs-lookup"><span data-stu-id="46fc7-133">`goto` statement:</span></span>

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* <span data-ttu-id="46fc7-134">Instrukcja `return`:</span><span class="sxs-lookup"><span data-stu-id="46fc7-134">`return` statement:</span></span>

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* <span data-ttu-id="46fc7-135">Instrukcja `yield`:</span><span class="sxs-lookup"><span data-stu-id="46fc7-135">`yield` statement:</span></span>

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* <span data-ttu-id="46fc7-136">instrukcje `throw` i instrukcje `try`:</span><span class="sxs-lookup"><span data-stu-id="46fc7-136">`throw` statements and `try` statements:</span></span>

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* <span data-ttu-id="46fc7-137">instrukcje `checked` i `unchecked`:</span><span class="sxs-lookup"><span data-stu-id="46fc7-137">`checked` and `unchecked` statements:</span></span>

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* <span data-ttu-id="46fc7-138">Instrukcja `lock`:</span><span class="sxs-lookup"><span data-stu-id="46fc7-138">`lock` statement:</span></span>

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* <span data-ttu-id="46fc7-139">Instrukcja `using`:</span><span class="sxs-lookup"><span data-stu-id="46fc7-139">`using` statement:</span></span>

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
><span data-ttu-id="46fc7-140">[Poprzednie](expressions.md)
>[dalej](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="46fc7-140">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>
