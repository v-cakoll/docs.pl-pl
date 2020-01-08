---
title: Funkcje zdefiniowane przez użytkownika
ms.date: 12/13/2019
description: Dowiedz się, jak tworzyć zdefiniowane przez użytkownika funkcje skalarne i agregujące.
ms.openlocfilehash: 9ee3fbac73215353c8dc82199203b0d25e580cdb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447175"
---
# <a name="user-defined-functions"></a><span data-ttu-id="98f44-103">Funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="98f44-103">User-defined functions</span></span>

<span data-ttu-id="98f44-104">Większość baz danych ma dialekt proceduralny dotyczący języka SQL, którego można użyć do zdefiniowania własnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="98f44-104">Most databases have a procedural dialect of SQL that you can use to define your own functions.</span></span> <span data-ttu-id="98f44-105">Jednak program SQLite działa w procesie z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="98f44-105">SQLite however, runs in-process with your app.</span></span> <span data-ttu-id="98f44-106">Zamiast uczyć się nowego dialektu SQL, można po prostu użyć języka programowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="98f44-106">Instead of having to learn a new dialect of SQL, you can just use the programming language of your app.</span></span>

## <a name="scalar-functions"></a><span data-ttu-id="98f44-107">Funkcje skalarne</span><span class="sxs-lookup"><span data-stu-id="98f44-107">Scalar functions</span></span>

<span data-ttu-id="98f44-108">Funkcje skalarne zwracają pojedynczą wartość skalarną dla każdego wiersza w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="98f44-108">Scalar functions return a single, scalar value for each row in a query.</span></span> <span data-ttu-id="98f44-109">Zdefiniuj nowe funkcje skalarne i zastąp wbudowane dla nich przy użyciu <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateFunction%2A>.</span><span class="sxs-lookup"><span data-stu-id="98f44-109">Define new scalar functions and override the built-in ones using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateFunction%2A>.</span></span>

<span data-ttu-id="98f44-110">Zobacz [typy danych](types.md) , aby uzyskać listę obsługiwanych parametrów i zwracanych typów dla argumentu `func`.</span><span class="sxs-lookup"><span data-stu-id="98f44-110">See [Data types](types.md) for a list of supported parameter and return types for the `func` argument.</span></span>

<span data-ttu-id="98f44-111">Określenie argumentu `state` przekaże tę wartość do każdego wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="98f44-111">Specifying the `state` argument will pass that value into every invocation of the function.</span></span> <span data-ttu-id="98f44-112">Użyj tego, aby uniknąć zamykania.</span><span class="sxs-lookup"><span data-stu-id="98f44-112">Use this to avoid closures.</span></span>

<span data-ttu-id="98f44-113">Określ `isDeterministic`, jeśli funkcja jest deterministyczna, aby umożliwić firmie SQLite Używanie dodatkowych optymalizacji podczas kompilowania zapytań.</span><span class="sxs-lookup"><span data-stu-id="98f44-113">Specify `isDeterministic` if your function is deterministic to allow SQLite to use additional optimizations when compiling queries.</span></span>

<span data-ttu-id="98f44-114">Poniższy przykład pokazuje, jak dodać funkcję skalarną, aby obliczyć promień cylindra.</span><span class="sxs-lookup"><span data-stu-id="98f44-114">The following example shows how to add a scalar function to calculate the radius of a cylinder.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ScalarFunctionSample/Program.cs?name=snippet_CreateFunction)]

## <a name="operators"></a><span data-ttu-id="98f44-115">Operatory</span><span class="sxs-lookup"><span data-stu-id="98f44-115">Operators</span></span>

<span data-ttu-id="98f44-116">Następujące operatory programu SQLite są implementowane przez odpowiednie funkcje skalarne.</span><span class="sxs-lookup"><span data-stu-id="98f44-116">The following SQLite operators are implemented by corresponding scalar functions.</span></span> <span data-ttu-id="98f44-117">Zdefiniowanie tych funkcji skalarnych w aplikacji spowoduje przesłonięcie zachowania tych operatorów.</span><span class="sxs-lookup"><span data-stu-id="98f44-117">Defining these scalar functions in your app will override the behavior of these operators.</span></span>

| <span data-ttu-id="98f44-118">Operator</span><span class="sxs-lookup"><span data-stu-id="98f44-118">Operator</span></span>          | <span data-ttu-id="98f44-119">Funkcja</span><span class="sxs-lookup"><span data-stu-id="98f44-119">Function</span></span>      |
| ----------------- | ------------- |
| <span data-ttu-id="98f44-120">X GLOBALIZOWANIA Y</span><span class="sxs-lookup"><span data-stu-id="98f44-120">X GLOB Y</span></span>          | <span data-ttu-id="98f44-121">globalizowania (Y, X)</span><span class="sxs-lookup"><span data-stu-id="98f44-121">glob(Y, X)</span></span>    |
| <span data-ttu-id="98f44-122">X PODOBNE DO Y</span><span class="sxs-lookup"><span data-stu-id="98f44-122">X LIKE Y</span></span>          | <span data-ttu-id="98f44-123">like (Y, X)</span><span class="sxs-lookup"><span data-stu-id="98f44-123">like(Y, X)</span></span>    |
| <span data-ttu-id="98f44-124">X LIKE Y UCIECZKI Z</span><span class="sxs-lookup"><span data-stu-id="98f44-124">X LIKE Y ESCAPE Z</span></span> | <span data-ttu-id="98f44-125">like (Y, X, Z)</span><span class="sxs-lookup"><span data-stu-id="98f44-125">like(Y, X, Z)</span></span> |
| <span data-ttu-id="98f44-126">X DOPASOWANIA Y</span><span class="sxs-lookup"><span data-stu-id="98f44-126">X MATCH Y</span></span>         | <span data-ttu-id="98f44-127">dopasowanie (Y, X)</span><span class="sxs-lookup"><span data-stu-id="98f44-127">match(Y, X)</span></span>   |
| <span data-ttu-id="98f44-128">X REGEXP Y</span><span class="sxs-lookup"><span data-stu-id="98f44-128">X REGEXP Y</span></span>        | <span data-ttu-id="98f44-129">RegExp (Y, X)</span><span class="sxs-lookup"><span data-stu-id="98f44-129">regexp(Y, X)</span></span>  |

<span data-ttu-id="98f44-130">Poniższy przykład pokazuje, jak zdefiniować funkcję RegExp w celu włączenia odpowiadającego jej operatora.</span><span class="sxs-lookup"><span data-stu-id="98f44-130">The following example shows how to define the regexp function to enable its corresponding operator.</span></span> <span data-ttu-id="98f44-131">Technologia SQLite nie zawiera domyślnej implementacji funkcji RegExp.</span><span class="sxs-lookup"><span data-stu-id="98f44-131">SQLite doesn't include a default implementation of the regexp function.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/RegularExpressionSample/Program.cs?name=snippet_Regex)]

## <a name="aggregate-functions"></a><span data-ttu-id="98f44-132">Funkcje agregujące</span><span class="sxs-lookup"><span data-stu-id="98f44-132">Aggregate functions</span></span>

<span data-ttu-id="98f44-133">Funkcje agregujące zwracają pojedynczą, zagregowaną wartość dla wszystkich wierszy w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="98f44-133">Aggregate functions return a single, aggregated value for all the rows in a query.</span></span> <span data-ttu-id="98f44-134">Zdefiniuj i Zastąp funkcje agregujące przy użyciu <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateAggregate%2A>.</span><span class="sxs-lookup"><span data-stu-id="98f44-134">Define and override aggregate functions using <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateAggregate%2A>.</span></span>

<span data-ttu-id="98f44-135">Argument `seed` określa początkowy stan kontekstu.</span><span class="sxs-lookup"><span data-stu-id="98f44-135">The `seed` argument specifies the initial state of the context.</span></span> <span data-ttu-id="98f44-136">Użyj tego, aby uniknąć również zamknięć.</span><span class="sxs-lookup"><span data-stu-id="98f44-136">Use this to avoid closures also.</span></span>

<span data-ttu-id="98f44-137">`func` argument jest wywoływany raz w każdym wierszu.</span><span class="sxs-lookup"><span data-stu-id="98f44-137">The `func` argument is invoked once per row.</span></span> <span data-ttu-id="98f44-138">Użyj kontekstu, aby zbierać wynik końcowy.</span><span class="sxs-lookup"><span data-stu-id="98f44-138">Use the context to accumulate a final result.</span></span> <span data-ttu-id="98f44-139">Zwróć kontekst.</span><span class="sxs-lookup"><span data-stu-id="98f44-139">Return the context.</span></span> <span data-ttu-id="98f44-140">Ten wzorzec zezwala na kontekst jako typ wartości lub niezmienny.</span><span class="sxs-lookup"><span data-stu-id="98f44-140">This pattern allows the context to be a value type or immutable.</span></span>

<span data-ttu-id="98f44-141">Jeśli żadna `resultSelector` nie jest określona, końcowym stanem kontekstu jest używany jako wynik.</span><span class="sxs-lookup"><span data-stu-id="98f44-141">If no `resultSelector` is specified, the final state of the context is used as the result.</span></span> <span data-ttu-id="98f44-142">Może to uprościć definicje funkcji, takich jak sum i Count, które wymagają zwiększenia liczby tylko każdego wiersza i zwrócenia go.</span><span class="sxs-lookup"><span data-stu-id="98f44-142">This can simplify the definition of functions like sum and count that only need to increment a number each row and return it.</span></span>

<span data-ttu-id="98f44-143">Określ `resultSelector`, aby obliczyć końcowy wynik z kontekstu po przeprowadzeniu iteracji we wszystkich wierszach.</span><span class="sxs-lookup"><span data-stu-id="98f44-143">Specify `resultSelector` to calculate the final result from the context after iterating through all the rows.</span></span>

<span data-ttu-id="98f44-144">Zobacz [typy danych](types.md) , aby uzyskać listę obsługiwanych typów parametrów dla argumentu `func` i typów zwracanych dla `resultSelector`.</span><span class="sxs-lookup"><span data-stu-id="98f44-144">See [Data types](types.md) for a list of supported parameter types for the `func` argument and return types for `resultSelector`.</span></span>

<span data-ttu-id="98f44-145">Jeśli funkcja jest deterministyczna, określ `isDeterministic`, aby umożliwić firmie SQLite Używanie dodatkowych optymalizacji podczas kompilowania zapytań.</span><span class="sxs-lookup"><span data-stu-id="98f44-145">If your function is deterministic, specify `isDeterministic` to allow SQLite to use additional optimizations when compiling queries.</span></span>

<span data-ttu-id="98f44-146">W poniższym przykładzie zdefiniowano funkcję agregującą, aby obliczyć odchylenie standardowe kolumny.</span><span class="sxs-lookup"><span data-stu-id="98f44-146">The following example defines an aggregate function to calculate the standard deviation of a column.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AggregateFunctionSample/Program.cs?name=snippet_CreateAggregate)]

## <a name="errors"></a><span data-ttu-id="98f44-147">błędy</span><span class="sxs-lookup"><span data-stu-id="98f44-147">Errors</span></span>

<span data-ttu-id="98f44-148">Jeśli funkcja zdefiniowana przez użytkownika zgłosi wyjątek, komunikat jest zwracany do oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="98f44-148">If a user-defined function throws an exception, the message is returned to SQLite.</span></span> <span data-ttu-id="98f44-149">Oprogramowanie SQLite zgłosi błąd, a firma Microsoft. Data. sqlite zgłosi wyjątek Sqliteexception.</span><span class="sxs-lookup"><span data-stu-id="98f44-149">SQLite will then raise an error and Microsoft.Data.Sqlite will throw a SqliteException.</span></span> <span data-ttu-id="98f44-150">Aby uzyskać więcej informacji, zobacz [Błędy bazy danych](database-errors.md).</span><span class="sxs-lookup"><span data-stu-id="98f44-150">For more information, see [Database errors](database-errors.md).</span></span>

<span data-ttu-id="98f44-151">Domyślnie kod błędu programu SQLite zostanie zwrócony SQLITE_ERROR (lub 1).</span><span class="sxs-lookup"><span data-stu-id="98f44-151">By default, the error SQLite error code will be SQLITE_ERROR (or 1).</span></span> <span data-ttu-id="98f44-152">Można jednak go zmienić, zgłaszając <xref:Microsoft.Data.Sqlite.SqliteException> w funkcji o żądanym <xref:Microsoft.Data.Sqlite.SqliteException.SqliteErrorCode> określonym.</span><span class="sxs-lookup"><span data-stu-id="98f44-152">You can, however, change it by throwing a <xref:Microsoft.Data.Sqlite.SqliteException> in your function with the desired <xref:Microsoft.Data.Sqlite.SqliteException.SqliteErrorCode> specified.</span></span>

## <a name="debugging"></a><span data-ttu-id="98f44-153">debugowanie</span><span class="sxs-lookup"><span data-stu-id="98f44-153">Debugging</span></span>

<span data-ttu-id="98f44-154">Technologia SQLite bezpośrednio wywołuje Twoją implementację.</span><span class="sxs-lookup"><span data-stu-id="98f44-154">SQLite calls your implementation directly.</span></span> <span data-ttu-id="98f44-155">Dzięki temu można dodawać punkty przerwania wyzwalane podczas oceniania przez program SQLite zapytań.</span><span class="sxs-lookup"><span data-stu-id="98f44-155">This lets you add breakpoints that trigger while SQLite is evaluating queries.</span></span> <span data-ttu-id="98f44-156">Dostępne jest pełne środowisko debugowania .NET, które ułatwia tworzenie funkcji zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="98f44-156">The full .NET debugging experience is available to help you create your user-defined functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="98f44-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98f44-157">See also</span></span>

* [<span data-ttu-id="98f44-158">Typy danych</span><span class="sxs-lookup"><span data-stu-id="98f44-158">Data types</span></span>](types.md)
* [<span data-ttu-id="98f44-159">Podstawowe funkcje oprogramowania SQLite</span><span class="sxs-lookup"><span data-stu-id="98f44-159">SQLite Core functions</span></span>](https://www.sqlite.org/lang_corefunc.html)
* [<span data-ttu-id="98f44-160">Funkcje agregujące oprogramowania SQLite</span><span class="sxs-lookup"><span data-stu-id="98f44-160">SQLite Aggregate Functions</span></span>](https://www.sqlite.org/lang_aggfunc.html)
