---
title: 'Wyjątki: Try... with — wyrażenie (F#)'
description: Dowiedz się, jak używać F# "try... with —" wyrażenia dla obsługi wyjątków.
ms.date: 05/16/2016
ms.openlocfilehash: 946cf56f7abc4bd5e3a9f9acc52b868bd6c7f84a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127410"
---
# <a name="exceptions-the-trywith-expression"></a><span data-ttu-id="5af82-103">Wyjątki: Try... with — wyrażenie</span><span class="sxs-lookup"><span data-stu-id="5af82-103">Exceptions: The try...with Expression</span></span>

<span data-ttu-id="5af82-104">W tym temacie opisano `try...with` wyrażenia, wyrażenie, które służy do obsługi wyjątków w F# języka.</span><span class="sxs-lookup"><span data-stu-id="5af82-104">This topic describes the `try...with` expression, the expression that is used for exception handling in the F# language.</span></span>

## <a name="syntax"></a><span data-ttu-id="5af82-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5af82-105">Syntax</span></span>

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a><span data-ttu-id="5af82-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5af82-106">Remarks</span></span>

<span data-ttu-id="5af82-107">`try...with` Wyrażenie jest używane do obsługi wyjątków w F#.</span><span class="sxs-lookup"><span data-stu-id="5af82-107">The `try...with` expression is used to handle exceptions in F#.</span></span> <span data-ttu-id="5af82-108">Jest on podobny do `try...catch` instrukcji w języku C#.</span><span class="sxs-lookup"><span data-stu-id="5af82-108">It is similar to the `try...catch` statement in C#.</span></span> <span data-ttu-id="5af82-109">W poprzedniej składni kodu w *wyrażenie1* może generować wyjątek.</span><span class="sxs-lookup"><span data-stu-id="5af82-109">In the preceding syntax, the code in *expression1* might generate an exception.</span></span> <span data-ttu-id="5af82-110">`try...with` Wyrażenie zwróci wartość.</span><span class="sxs-lookup"><span data-stu-id="5af82-110">The `try...with` expression returns a value.</span></span> <span data-ttu-id="5af82-111">Jeśli jest zgłaszany żaden wyjątek, całe wyrażenie zwraca wartość *wyrażenie1*.</span><span class="sxs-lookup"><span data-stu-id="5af82-111">If no exception is thrown, the whole expression returns the value of *expression1*.</span></span> <span data-ttu-id="5af82-112">Jeśli wyjątek jest zgłaszany, każdy *wzorzec* jest porównywany z kolei, z wyjątkiem i dopasowywania wzorca pierwszego odpowiedniego *wyrażenie*, znaną jako *obsługi wyjątków*dla tej gałęzi jest wykonywany i ogólną wyrażenie zwraca wartość wyrażenia w tym obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="5af82-112">If an exception is thrown, each *pattern* is compared in turn with the exception, and for the first matching pattern, the corresponding *expression*, known as the *exception handler*, for that branch is executed, and the overall expression returns the value of the expression in that exception handler.</span></span> <span data-ttu-id="5af82-113">Jeśli wzorzec nie jest zgodny, wyjątek propaguje górę stosu wywołań, dopóki nie znaleziono pasującej klauzuli obsługi.</span><span class="sxs-lookup"><span data-stu-id="5af82-113">If no pattern matches, the exception propagates up the call stack until a matching handler is found.</span></span> <span data-ttu-id="5af82-114">Typy wartości zwracanych z każde wyrażenie w obsługi wyjątków musi odpowiadać typ zwracany z wyrażenia w `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="5af82-114">The types of the values returned from each expression in the exception handlers must match the type returned from the expression in the `try` block.</span></span>

<span data-ttu-id="5af82-115">Nie ma prawidłowej wartości, które mogą być zwrócone z wyrażeń w każdy program obsługi wyjątków oznacza często fakt również wystąpił błąd.</span><span class="sxs-lookup"><span data-stu-id="5af82-115">Frequently, the fact that an error occurred also means that there is no valid value that can be returned from the expressions in each exception handler.</span></span> <span data-ttu-id="5af82-116">Częsty wzór jest typ wyrażenia jest typem opcji.</span><span class="sxs-lookup"><span data-stu-id="5af82-116">A frequent pattern is to have the type of the expression be an option type.</span></span> <span data-ttu-id="5af82-117">Poniższy przykład kodu ilustruje ten wzorzec.</span><span class="sxs-lookup"><span data-stu-id="5af82-117">The following code example illustrates this pattern.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

<span data-ttu-id="5af82-118">Wyjątki mogą być wyjątki platformy .NET lub mogą być F# wyjątków.</span><span class="sxs-lookup"><span data-stu-id="5af82-118">Exceptions can be .NET exceptions, or they can be F# exceptions.</span></span> <span data-ttu-id="5af82-119">Można zdefiniować F# wyjątków za pomocą `exception` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="5af82-119">You can define F# exceptions by using the `exception` keyword.</span></span>

<span data-ttu-id="5af82-120">Można użyć różnych wzorców do filtrowania typ wyjątku i innych warunków; opcje są podsumowane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="5af82-120">You can use a variety of patterns to filter on the exception type and other conditions; the options are summarized in the following table.</span></span>

|<span data-ttu-id="5af82-121">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="5af82-121">Pattern</span></span>|<span data-ttu-id="5af82-122">Opis</span><span class="sxs-lookup"><span data-stu-id="5af82-122">Description</span></span>|
|-------|-----------|
|<span data-ttu-id="5af82-123">:?</span><span class="sxs-lookup"><span data-stu-id="5af82-123">:?</span></span> <span data-ttu-id="5af82-124">*Typ wyjątku*</span><span class="sxs-lookup"><span data-stu-id="5af82-124">*exception-type*</span></span>|<span data-ttu-id="5af82-125">Jest zgodny z określonym typem wyjątku .NET.</span><span class="sxs-lookup"><span data-stu-id="5af82-125">Matches the specified .NET exception type.</span></span>|
|<span data-ttu-id="5af82-126">:?</span><span class="sxs-lookup"><span data-stu-id="5af82-126">:?</span></span> <span data-ttu-id="5af82-127">*Typ wyjątku* jako *identyfikator*</span><span class="sxs-lookup"><span data-stu-id="5af82-127">*exception-type* as *identifier*</span></span>|<span data-ttu-id="5af82-128">Jest zgodny z określonym typem wyjątku .NET, ale zapewnia wyjątek nazwanej wartości.</span><span class="sxs-lookup"><span data-stu-id="5af82-128">Matches the specified .NET exception type, but gives the exception a named value.</span></span>|
|<span data-ttu-id="5af82-129">*nazwa wyjątku*(*argumenty*)</span><span class="sxs-lookup"><span data-stu-id="5af82-129">*exception-name*(*arguments*)</span></span>|<span data-ttu-id="5af82-130">Dopasowuje F# typ wyjątku i powiązań argumenty.</span><span class="sxs-lookup"><span data-stu-id="5af82-130">Matches an F# exception type and binds the arguments.</span></span>|
|<span data-ttu-id="5af82-131">*Identyfikator*</span><span class="sxs-lookup"><span data-stu-id="5af82-131">*identifier*</span></span>|<span data-ttu-id="5af82-132">Dopasowuje dowolny wyjątek i wiąże nazwę obiektu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="5af82-132">Matches any exception and binds the name to the exception object.</span></span> <span data-ttu-id="5af82-133">Odpowiednikiem **:? System.Exception jako**_identyfikator_</span><span class="sxs-lookup"><span data-stu-id="5af82-133">Equivalent to **:? System.Exception as**_identifier_</span></span>|
|<span data-ttu-id="5af82-134">*Identyfikator* podczas *warunku*</span><span class="sxs-lookup"><span data-stu-id="5af82-134">*identifier* when *condition*</span></span>|<span data-ttu-id="5af82-135">Dopasowuje każdy wyjątek, jeśli warunek jest prawdziwy.</span><span class="sxs-lookup"><span data-stu-id="5af82-135">Matches any exception if the condition is true.</span></span>|

## <a name="examples"></a><span data-ttu-id="5af82-136">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5af82-136">Examples</span></span>

<span data-ttu-id="5af82-137">Poniższe przykłady kodu ilustrują używanie różnych wzorców obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="5af82-137">The following code examples illustrate the use of the various exception handler patterns.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> <span data-ttu-id="5af82-138">`try...with` Konstrukcja jest wyrażeniem osobnych z `try...finally` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5af82-138">The `try...with` construct is a separate expression from the `try...finally` expression.</span></span> <span data-ttu-id="5af82-139">W związku z tym jeśli kod wymaga zarówno `with` bloku i `finally` bloku, należy zagnieździć dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="5af82-139">Therefore, if your code requires both a `with` block and a `finally` block, you will have to nest the two expressions.</span></span>

> [!NOTE]
> <span data-ttu-id="5af82-140">Możesz użyć `try...with` w Asynchroniczne przepływy pracy i inne wyrażenia obliczeń, w którym zamierzone, Zapisz dostosowaną wersję `try...with` wyrażenie jest używane.</span><span class="sxs-lookup"><span data-stu-id="5af82-140">You can use `try...with` in asynchronous workflows and other computation expressions, in which case a customized version of the `try...with` expression is used.</span></span> <span data-ttu-id="5af82-141">Aby uzyskać więcej informacji, zobacz [Asynchroniczne przepływy pracy](../asynchronous-workflows.md), i [wyrażenia obliczeń](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="5af82-141">For more information, see [Asynchronous Workflows](../asynchronous-workflows.md), and [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5af82-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5af82-142">See also</span></span>

- [<span data-ttu-id="5af82-143">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="5af82-143">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="5af82-144">Typy wyjątków</span><span class="sxs-lookup"><span data-stu-id="5af82-144">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="5af82-145">Wyjątki: `try...finally` Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="5af82-145">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
