---
title: C#Wyrażenia — Przewodnik po przykładzie C# języka
description: bloki konstrukcyjne są wyrażenia, argumenty operacji i operatory C# języka
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 4ffe947a4cb8c36a5925a4b3846486e44a9d8ec4
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480758"
---
# <a name="expressions"></a><span data-ttu-id="cb966-103">Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="cb966-103">Expressions</span></span>

<span data-ttu-id="cb966-104">*Wyrażenia* są konstruowane na podstawie *operandów* i *operatorów*.</span><span class="sxs-lookup"><span data-stu-id="cb966-104">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="cb966-105">Operatory wyrażenia wskazują operacje do zastosowania dla operandów.</span><span class="sxs-lookup"><span data-stu-id="cb966-105">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="cb966-106">Przykłady operatorów to `+`, `-`, `*`, `/`i `new`.</span><span class="sxs-lookup"><span data-stu-id="cb966-106">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="cb966-107">Przykładami operandów są literały, pola, zmienne lokalne i wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="cb966-107">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="cb966-108">Gdy wyrażenie zawiera wiele operatorów *pierwszeństwo* operatorów określa kolejność, w jakiej są oceniane poszczególne operatory.</span><span class="sxs-lookup"><span data-stu-id="cb966-108">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="cb966-109">Na przykład, wyrażenie `x + y * z` jest oceniane jako `x + (y * z)`, ponieważ operator `*` ma wyższy priorytet niż operator `+`.</span><span class="sxs-lookup"><span data-stu-id="cb966-109">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="cb966-110">Gdy operand występuje między dwoma operatorami o tym samym priorytecie *asocjacyjność* operatorów określa kolejność, w której są wykonywane operacje:</span><span class="sxs-lookup"><span data-stu-id="cb966-110">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

* <span data-ttu-id="cb966-111">Z wyjątkiem operatorów przypisania wszystkie operatory dwuargumentowe są *lewostronne*, co oznacza, że operacje są wykonywane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="cb966-111">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="cb966-112">Na przykład `x + y + z` jest oceniane jako `(x + y) + z`.</span><span class="sxs-lookup"><span data-stu-id="cb966-112">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
* <span data-ttu-id="cb966-113">Operatory przypisania i operator warunkowy (`?:`) są *prawostronne*, co oznacza, że operacje są wykonywane od prawej do lewej.</span><span class="sxs-lookup"><span data-stu-id="cb966-113">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="cb966-114">Na przykład `x = y = z` jest oceniane jako `x = (y = z)`.</span><span class="sxs-lookup"><span data-stu-id="cb966-114">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="cb966-115">Pierwszeństwo i asocjacyjność mogą być kontrolowane za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="cb966-115">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="cb966-116">Na przykład `x + y * z` najpierw mnoży `y` przez `z` , a następnie dodaje wynik do `x`, ale `(x + y) * z` najpierw dodaje `x` i `y` i następnie wynik mnoży przez `z`.</span><span class="sxs-lookup"><span data-stu-id="cb966-116">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="cb966-117">Większość operatorów może być *przeciążona*.</span><span class="sxs-lookup"><span data-stu-id="cb966-117">Most operators can be *overloaded*.</span></span> <span data-ttu-id="cb966-118">Przeciążanie operatora umożliwia określanie definiowanych przez użytkownika implementacji operatorów dla operacji, w których jeden lub oba operandy mają typ struktury lub klasy zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cb966-118">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="cb966-119">Poniżej znajduje się podsumowanie operatorów języka C#. Kategorie operatorów wypisane są w kolejności pierwszeństwa od najwyższego do najniższego.</span><span class="sxs-lookup"><span data-stu-id="cb966-119">The following summarizes C#’s operators, listing the operator categories in order of precedence from highest to lowest.</span></span> <span data-ttu-id="cb966-120">Operatory w tej samej kategorii mają takie samo pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="cb966-120">Operators in the same category have equal precedence.</span></span> <span data-ttu-id="cb966-121">Pod każdą z kategorii znajduje się lista wyrażeń znajdujących się w niej, wraz z opisem danego typu wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="cb966-121">Under each category is a list of expressions in that category along with the description of that expression type.</span></span>

* <span data-ttu-id="cb966-122">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="cb966-122">Primary</span></span>
  - `x.m`<span data-ttu-id="cb966-123">: Dostęp do elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="cb966-123">: Member access</span></span>
  - `x(...)`<span data-ttu-id="cb966-124">: Wywołanie metody i delegata</span><span class="sxs-lookup"><span data-stu-id="cb966-124">: Method and delegate invocation</span></span>
  - `x[...]`<span data-ttu-id="cb966-125">: Dostęp do tablicy i indeksatora</span><span class="sxs-lookup"><span data-stu-id="cb966-125">: Array and indexer access</span></span>
  - `x++`<span data-ttu-id="cb966-126">: Postinkrementacja</span><span class="sxs-lookup"><span data-stu-id="cb966-126">: Post-increment</span></span>
  - `x--`<span data-ttu-id="cb966-127">: Postdekrementacja</span><span class="sxs-lookup"><span data-stu-id="cb966-127">: Post-decrement</span></span>
  - `new T(...)`<span data-ttu-id="cb966-128">: Utworzenie obiektu i delegata</span><span class="sxs-lookup"><span data-stu-id="cb966-128">: Object and delegate creation</span></span>
  - `new T(...){...}`<span data-ttu-id="cb966-129">: Utworzenie obiektu za pomocą inicjatora</span><span class="sxs-lookup"><span data-stu-id="cb966-129">: Object creation with initializer</span></span>
  - `new {...}`<span data-ttu-id="cb966-130">:  Inicjator obiektu anonimowego</span><span class="sxs-lookup"><span data-stu-id="cb966-130">:  Anonymous object initializer</span></span>
  - `new T[...]`<span data-ttu-id="cb966-131">: Do utworzenia tablicy</span><span class="sxs-lookup"><span data-stu-id="cb966-131">: Array creation</span></span>
  - `typeof(T)`<span data-ttu-id="cb966-132">: Uzyskaj <xref:System.Type> dla obiektu</span><span class="sxs-lookup"><span data-stu-id="cb966-132">: Obtain <xref:System.Type> object for</span></span> `T`
  - `checked(x)`<span data-ttu-id="cb966-133">: Obliczenie wyrażenia w kontekście sprawdzanym</span><span class="sxs-lookup"><span data-stu-id="cb966-133">: Evaluate expression in checked context</span></span>
  - `unchecked(x)`<span data-ttu-id="cb966-134">: Obliczenie wyrażenia w kontekście niesprawdzanym</span><span class="sxs-lookup"><span data-stu-id="cb966-134">: Evaluate expression in unchecked context</span></span>
  - `default(T)`<span data-ttu-id="cb966-135">: Uzyskanie wartości domyślnej typu</span><span class="sxs-lookup"><span data-stu-id="cb966-135">: Obtain default value of type</span></span> `T`
  - `delegate {...}`<span data-ttu-id="cb966-136">: Funkcja anonimowa (metoda anonimowa)</span><span class="sxs-lookup"><span data-stu-id="cb966-136">: Anonymous function (anonymous method)</span></span>
* <span data-ttu-id="cb966-137">Jednoargumentowy</span><span class="sxs-lookup"><span data-stu-id="cb966-137">Unary</span></span>
  - `+x`<span data-ttu-id="cb966-138">: Tożsamość</span><span class="sxs-lookup"><span data-stu-id="cb966-138">: Identity</span></span>
  - `-x`<span data-ttu-id="cb966-139">: Negacja</span><span class="sxs-lookup"><span data-stu-id="cb966-139">: Negation</span></span>
  - `!x`<span data-ttu-id="cb966-140">: Negacja logiczna</span><span class="sxs-lookup"><span data-stu-id="cb966-140">: Logical negation</span></span>
  - `~x`<span data-ttu-id="cb966-141">: Negacja bitowa</span><span class="sxs-lookup"><span data-stu-id="cb966-141">: Bitwise negation</span></span>
  - `++x`<span data-ttu-id="cb966-142">: Preinkrementacja</span><span class="sxs-lookup"><span data-stu-id="cb966-142">: Pre-increment</span></span>
  - `--x`<span data-ttu-id="cb966-143">: Predekrementacja</span><span class="sxs-lookup"><span data-stu-id="cb966-143">: Pre-decrement</span></span>
  - `(T)x`<span data-ttu-id="cb966-144">: Jawnie przekonwertować `x` na typ</span><span class="sxs-lookup"><span data-stu-id="cb966-144">: Explicitly convert `x` to type</span></span> `T`
  - `await x`<span data-ttu-id="cb966-145">: Asynchronicznie poczekaj na ukończenie `x`</span><span class="sxs-lookup"><span data-stu-id="cb966-145">: Asynchronously wait for `x` to complete</span></span>
* <span data-ttu-id="cb966-146">Mnożeniowy</span><span class="sxs-lookup"><span data-stu-id="cb966-146">Multiplicative</span></span>
  - `x * y`<span data-ttu-id="cb966-147">: Mnożenie</span><span class="sxs-lookup"><span data-stu-id="cb966-147">: Multiplication</span></span>
  - `x / y`<span data-ttu-id="cb966-148">: Dzielenie</span><span class="sxs-lookup"><span data-stu-id="cb966-148">: Division</span></span>
  - `x % y`<span data-ttu-id="cb966-149">: Reszta</span><span class="sxs-lookup"><span data-stu-id="cb966-149">: Remainder</span></span>
* <span data-ttu-id="cb966-150">Dodatku</span><span class="sxs-lookup"><span data-stu-id="cb966-150">Additive</span></span>
  - `x + y`<span data-ttu-id="cb966-151">: Dodawanie, łączenie ciągów, łączenie delegatów</span><span class="sxs-lookup"><span data-stu-id="cb966-151">: Addition, string concatenation, delegate combination</span></span>
  - `x – y`<span data-ttu-id="cb966-152">: Odejmowanie, usuwanie delegata</span><span class="sxs-lookup"><span data-stu-id="cb966-152">: Subtraction, delegate removal</span></span>
* <span data-ttu-id="cb966-153">Shift</span><span class="sxs-lookup"><span data-stu-id="cb966-153">Shift</span></span>
  - `x << y`<span data-ttu-id="cb966-154">: Przesunięcie w lewo</span><span class="sxs-lookup"><span data-stu-id="cb966-154">: Shift left</span></span>
  - `x >> y`<span data-ttu-id="cb966-155">: Przesunięcie w prawo</span><span class="sxs-lookup"><span data-stu-id="cb966-155">: Shift right</span></span>
* <span data-ttu-id="cb966-156">Relacyjne i badania typu</span><span class="sxs-lookup"><span data-stu-id="cb966-156">Relational and type testing</span></span>
  - `x < y`<span data-ttu-id="cb966-157">: Mniejsze niż</span><span class="sxs-lookup"><span data-stu-id="cb966-157">: Less than</span></span>
  - `x > y`<span data-ttu-id="cb966-158">: Większe niż</span><span class="sxs-lookup"><span data-stu-id="cb966-158">: Greater than</span></span>
  - `x <= y`<span data-ttu-id="cb966-159">: Mniejsze niż lub równe</span><span class="sxs-lookup"><span data-stu-id="cb966-159">: Less than or equal</span></span>
  - `x >= y`<span data-ttu-id="cb966-160">: Większe niż lub równe</span><span class="sxs-lookup"><span data-stu-id="cb966-160">: Greater than or equal</span></span>
  - `x is T`<span data-ttu-id="cb966-161">: Zwróć `true` Jeśli `x` jest `T`, `false` inaczej</span><span class="sxs-lookup"><span data-stu-id="cb966-161">: Return `true` if `x` is a `T`, `false` otherwise</span></span>
  - `x as T`<span data-ttu-id="cb966-162">: Zwróć `x` wpisanych w formie `T`, lub `null` Jeśli `x` nie jest</span><span class="sxs-lookup"><span data-stu-id="cb966-162">: Return `x` typed as `T`, or `null` if `x` is not a</span></span> `T`
* <span data-ttu-id="cb966-163">Równości</span><span class="sxs-lookup"><span data-stu-id="cb966-163">Equality</span></span>
  - `x == y`<span data-ttu-id="cb966-164">: Równa się</span><span class="sxs-lookup"><span data-stu-id="cb966-164">: Equal</span></span>
  - `x != y`<span data-ttu-id="cb966-165">: Nie równa się</span><span class="sxs-lookup"><span data-stu-id="cb966-165">: Not equal</span></span>
* <span data-ttu-id="cb966-166">Logicznego AND</span><span class="sxs-lookup"><span data-stu-id="cb966-166">Logical AND</span></span>
  - `x & y`<span data-ttu-id="cb966-167">: Liczba całkowita bitowe i logicznych logiczne AND</span><span class="sxs-lookup"><span data-stu-id="cb966-167">: Integer bitwise AND, boolean logical AND</span></span>
* <span data-ttu-id="cb966-168">Logicznego XOR</span><span class="sxs-lookup"><span data-stu-id="cb966-168">Logical XOR</span></span>
  - `x ^ y`<span data-ttu-id="cb966-169">: Bitowe XOR dla wartości całkowitych, logiczne XOR dla wartości binarnych</span><span class="sxs-lookup"><span data-stu-id="cb966-169">: Integer bitwise XOR, boolean logical XOR</span></span>
* <span data-ttu-id="cb966-170">Logicznego OR</span><span class="sxs-lookup"><span data-stu-id="cb966-170">Logical OR</span></span>
  - `x | y`<span data-ttu-id="cb966-171">: Bitowe OR dla wartości całkowitych, logiczne OR dla wartości binarnych</span><span class="sxs-lookup"><span data-stu-id="cb966-171">: Integer bitwise OR, boolean logical OR</span></span>
* <span data-ttu-id="cb966-172">Warunkowego AND</span><span class="sxs-lookup"><span data-stu-id="cb966-172">Conditional AND</span></span>
  - `x && y`<span data-ttu-id="cb966-173">: Ocenia `y` tylko wtedy, gdy `x` nie jest</span><span class="sxs-lookup"><span data-stu-id="cb966-173">: Evaluates `y` only if `x` is not</span></span> `false`
* <span data-ttu-id="cb966-174">Warunkowego OR</span><span class="sxs-lookup"><span data-stu-id="cb966-174">Conditional OR</span></span>
  - `x || y`<span data-ttu-id="cb966-175">: Ocenia `y` tylko wtedy, gdy `x` nie jest</span><span class="sxs-lookup"><span data-stu-id="cb966-175">: Evaluates `y` only if `x` is not</span></span> `true`
* <span data-ttu-id="cb966-176">Łączenia wartości null</span><span class="sxs-lookup"><span data-stu-id="cb966-176">Null coalescing</span></span>
  - `x ?? y`<span data-ttu-id="cb966-177">: Daje w wyniku `y` Jeśli `x` ma wartość null, aby `x` inaczej</span><span class="sxs-lookup"><span data-stu-id="cb966-177">: Evaluates to `y` if `x` is null, to `x` otherwise</span></span>
* <span data-ttu-id="cb966-178">Warunkowe</span><span class="sxs-lookup"><span data-stu-id="cb966-178">Conditional</span></span>
  - `x ? y : z`<span data-ttu-id="cb966-179">: Ocenia `y` Jeśli `x` jest `true`, `z` Jeśli `x` jest</span><span class="sxs-lookup"><span data-stu-id="cb966-179">: Evaluates `y` if `x` is `true`, `z` if `x` is</span></span> `false`
* <span data-ttu-id="cb966-180">Przypisania lub funkcji anonimowej</span><span class="sxs-lookup"><span data-stu-id="cb966-180">Assignment or anonymous function</span></span>
  - `x = y`<span data-ttu-id="cb966-181">: Przypisanie</span><span class="sxs-lookup"><span data-stu-id="cb966-181">: Assignment</span></span>
  - `x op= y`<span data-ttu-id="cb966-182">: Złożone przypisanie; obsługiwane operatory to</span><span class="sxs-lookup"><span data-stu-id="cb966-182">: Compound assignment; supported operators are</span></span>
    - `*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`
  - `(T x) => y`<span data-ttu-id="cb966-183">: Funkcja anonimowa (wyrażenie lambda)</span><span class="sxs-lookup"><span data-stu-id="cb966-183">: Anonymous function (lambda expression)</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="cb966-184">[Poprzednie](types-and-variables.md)
> [dalej](statements.md)</span><span class="sxs-lookup"><span data-stu-id="cb966-184">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>
