---
title: 'Wyjątki: Wyrażenie try...with'
description: Dowiedz się, F# jak używać metody "try... z wyrażeniem "Expression for Exception obsługi.
ms.date: 05/16/2016
ms.openlocfilehash: e4d615086a93e26b76cca460e797659ca13792b5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630248"
---
# <a name="exceptions-the-trywith-expression"></a><span data-ttu-id="3e9c7-103">Wyjątki: Wyrażenie try...with</span><span class="sxs-lookup"><span data-stu-id="3e9c7-103">Exceptions: The try...with Expression</span></span>

<span data-ttu-id="3e9c7-104">W tym temacie opisano `try...with` wyrażenie, wyrażenie, które jest używane do obsługi wyjątków w F# języku.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-104">This topic describes the `try...with` expression, the expression that is used for exception handling in the F# language.</span></span>

## <a name="syntax"></a><span data-ttu-id="3e9c7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e9c7-105">Syntax</span></span>

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a><span data-ttu-id="3e9c7-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e9c7-106">Remarks</span></span>

<span data-ttu-id="3e9c7-107">Wyrażenie służy do obsługi wyjątków w F# `try...with`</span><span class="sxs-lookup"><span data-stu-id="3e9c7-107">The `try...with` expression is used to handle exceptions in F#.</span></span> <span data-ttu-id="3e9c7-108">Jest podobna do `try...catch` instrukcji w C#temacie.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-108">It is similar to the `try...catch` statement in C#.</span></span> <span data-ttu-id="3e9c7-109">W powyższej składni kod w elemencie *wyrażenie1* może generować wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-109">In the preceding syntax, the code in *expression1* might generate an exception.</span></span> <span data-ttu-id="3e9c7-110">`try...with` Wyrażenie zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-110">The `try...with` expression returns a value.</span></span> <span data-ttu-id="3e9c7-111">Jeśli żaden wyjątek nie zostanie zgłoszony, całe wyrażenie zwróci wartość *wyrażenie1*.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-111">If no exception is thrown, the whole expression returns the value of *expression1*.</span></span> <span data-ttu-id="3e9c7-112">Jeśli wystąpi wyjątek, każdy *wzorzec* jest porównywany z wyjątkiem, a dla pierwszego pasującego wzorca, odpowiednie *wyrażenie*, znane jako *procedura obsługi wyjątków*, dla tej gałęzi jest wykonywane i wyrażenie ogólne Zwraca wartość wyrażenia w tej procedurze obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-112">If an exception is thrown, each *pattern* is compared in turn with the exception, and for the first matching pattern, the corresponding *expression*, known as the *exception handler*, for that branch is executed, and the overall expression returns the value of the expression in that exception handler.</span></span> <span data-ttu-id="3e9c7-113">Jeśli żaden wzorzec nie jest zgodny, wyjątek propaguje stos wywołań do momentu znalezienia zgodnej procedury obsługi.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-113">If no pattern matches, the exception propagates up the call stack until a matching handler is found.</span></span> <span data-ttu-id="3e9c7-114">Typy wartości zwracane z każdego wyrażenia w obsłudze wyjątków muszą być zgodne z typem zwracanym z wyrażenia w `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-114">The types of the values returned from each expression in the exception handlers must match the type returned from the expression in the `try` block.</span></span>

<span data-ttu-id="3e9c7-115">Często fakt, że wystąpił błąd, oznacza również, że nie ma prawidłowej wartości, którą można zwrócić z wyrażeń w ramach każdego programu obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-115">Frequently, the fact that an error occurred also means that there is no valid value that can be returned from the expressions in each exception handler.</span></span> <span data-ttu-id="3e9c7-116">Częstym wzorcem jest posiadanie typu wyrażenia jako typu opcji.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-116">A frequent pattern is to have the type of the expression be an option type.</span></span> <span data-ttu-id="3e9c7-117">Poniższy przykład kodu ilustruje ten wzorzec.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-117">The following code example illustrates this pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

<span data-ttu-id="3e9c7-118">Wyjątki mogą być wyjątkami platformy .NET lub mogą być F# wyjątkami.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-118">Exceptions can be .NET exceptions, or they can be F# exceptions.</span></span> <span data-ttu-id="3e9c7-119">Wyjątki można definiować F# za pomocą `exception` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-119">You can define F# exceptions by using the `exception` keyword.</span></span>

<span data-ttu-id="3e9c7-120">Można użyć różnych wzorców do filtrowania według typu wyjątku i innych warunków; opcje są podsumowane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-120">You can use a variety of patterns to filter on the exception type and other conditions; the options are summarized in the following table.</span></span>

|<span data-ttu-id="3e9c7-121">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="3e9c7-121">Pattern</span></span>|<span data-ttu-id="3e9c7-122">Opis</span><span class="sxs-lookup"><span data-stu-id="3e9c7-122">Description</span></span>|
|-------|-----------|
|<span data-ttu-id="3e9c7-123">:?</span><span class="sxs-lookup"><span data-stu-id="3e9c7-123">:?</span></span> <span data-ttu-id="3e9c7-124">*Typ wyjątku*</span><span class="sxs-lookup"><span data-stu-id="3e9c7-124">*exception-type*</span></span>|<span data-ttu-id="3e9c7-125">Dopasowuje określony typ wyjątku platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-125">Matches the specified .NET exception type.</span></span>|
|<span data-ttu-id="3e9c7-126">:?</span><span class="sxs-lookup"><span data-stu-id="3e9c7-126">:?</span></span> <span data-ttu-id="3e9c7-127">*Typ wyjątku* jako *Identyfikator*</span><span class="sxs-lookup"><span data-stu-id="3e9c7-127">*exception-type* as *identifier*</span></span>|<span data-ttu-id="3e9c7-128">Dopasowuje określony typ wyjątku .NET, ale daje wyjątek nazwaną wartość.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-128">Matches the specified .NET exception type, but gives the exception a named value.</span></span>|
|<span data-ttu-id="3e9c7-129">*Nazwa wyjątku* (*argumenty*)</span><span class="sxs-lookup"><span data-stu-id="3e9c7-129">*exception-name*(*arguments*)</span></span>|<span data-ttu-id="3e9c7-130">Dopasowuje F# typ wyjątku i wiąże argumenty.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-130">Matches an F# exception type and binds the arguments.</span></span>|
|<span data-ttu-id="3e9c7-131">*identyfikatora*</span><span class="sxs-lookup"><span data-stu-id="3e9c7-131">*identifier*</span></span>|<span data-ttu-id="3e9c7-132">Dopasowuje dowolny wyjątek i wiąże nazwę z obiektem Exception.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-132">Matches any exception and binds the name to the exception object.</span></span> <span data-ttu-id="3e9c7-133">**Równoważne:? System. Exception jako**_Identyfikator_</span><span class="sxs-lookup"><span data-stu-id="3e9c7-133">Equivalent to **:? System.Exception as**_identifier_</span></span>|
|<span data-ttu-id="3e9c7-134">*Identyfikator* , gdy *warunek*</span><span class="sxs-lookup"><span data-stu-id="3e9c7-134">*identifier* when *condition*</span></span>|<span data-ttu-id="3e9c7-135">Dopasowuje dowolny wyjątek, jeśli warunek ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-135">Matches any exception if the condition is true.</span></span>|

## <a name="examples"></a><span data-ttu-id="3e9c7-136">Przykłady</span><span class="sxs-lookup"><span data-stu-id="3e9c7-136">Examples</span></span>

<span data-ttu-id="3e9c7-137">Poniższe przykłady kodu ilustrują użycie różnych wzorców obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-137">The following code examples illustrate the use of the various exception handler patterns.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> <span data-ttu-id="3e9c7-138">Konstrukcja jest osobnym wyrażeniem `try...finally` z wyrażenia. `try...with`</span><span class="sxs-lookup"><span data-stu-id="3e9c7-138">The `try...with` construct is a separate expression from the `try...finally` expression.</span></span> <span data-ttu-id="3e9c7-139">W związku z tym, jeśli kod wymaga `with` zarówno bloku, `finally` jak i bloku, należy zagnieździć te dwa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-139">Therefore, if your code requires both a `with` block and a `finally` block, you will have to nest the two expressions.</span></span>

> [!NOTE]
> <span data-ttu-id="3e9c7-140">Można używać `try...with` w asynchronicznych przepływach pracy i innych wyrażeniach obliczeniowych, w tym przypadku używana `try...with` jest dostosowana wersja wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="3e9c7-140">You can use `try...with` in asynchronous workflows and other computation expressions, in which case a customized version of the `try...with` expression is used.</span></span> <span data-ttu-id="3e9c7-141">Aby uzyskać więcej informacji, zobacz [asynchroniczne przepływy pracy](../asynchronous-workflows.md)i [wyrażenia obliczeń](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="3e9c7-141">For more information, see [Asynchronous Workflows](../asynchronous-workflows.md), and [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3e9c7-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e9c7-142">See also</span></span>

- [<span data-ttu-id="3e9c7-143">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="3e9c7-143">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="3e9c7-144">Typy wyjątków</span><span class="sxs-lookup"><span data-stu-id="3e9c7-144">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="3e9c7-145">Wyjątki: `try...finally` Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="3e9c7-145">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
