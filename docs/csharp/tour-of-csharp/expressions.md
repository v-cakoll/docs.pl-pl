---
title: C#Wyrażenia — Przewodnik po przykładzie C# języka
description: bloki konstrukcyjne są wyrażenia, argumenty operacji i operatory C# języka
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 28e1d6952975c6932dc9ae40af28c7201d61d778
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154937"
---
# <a name="expressions"></a><span data-ttu-id="ce2b2-103">Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="ce2b2-103">Expressions</span></span>

<span data-ttu-id="ce2b2-104">*Wyrażenia* są konstruowane na podstawie *operandy* i *operatory*.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-104">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="ce2b2-105">Operatory wyrażenie wskazuje operacji do zastosowania do operandów.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-105">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="ce2b2-106">Przykłady operatorów `+`, `-`, `*`, `/`, i `new`.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-106">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="ce2b2-107">Przykładami operandy są literały, pola, zmienne lokalne i wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-107">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="ce2b2-108">Gdy wyrażenie zawiera wiele operatorów *pierwszeństwo* operatorów określa kolejność, w jakiej są oceniane poszczególnych operatorach.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-108">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="ce2b2-109">Na przykład, wyrażenie `x + y * z` jest oceniane jako `x + (y * z)` ponieważ `*` operator ma wyższy priorytet niż `+` operatora.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-109">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="ce2b2-110">Gdy argument odbywa się między dwa operatory o tym samym priorytecie *kojarzenie* operatorów określa kolejność, w której są wykonywane operacje:</span><span class="sxs-lookup"><span data-stu-id="ce2b2-110">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

*   <span data-ttu-id="ce2b2-111">Z wyjątkiem operatorów przypisania wszystkie operatory dwuargumentowe to *lewostronne*, co oznacza, że operacje są wykonywane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-111">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="ce2b2-112">Na przykład `x + y + z` jest oceniane jako `(x + y) + z`.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-112">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
*   <span data-ttu-id="ce2b2-113">Operatory przypisania i operator warunkowy (`?:`) są *zespolony z prawej*, co oznacza, że operacje są wykonywane od prawej do lewej.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-113">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="ce2b2-114">Na przykład `x = y = z` jest oceniane jako `x = (y = z)`.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-114">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="ce2b2-115">Pierwszeństwo i kojarzenie mogą być kontrolowane za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-115">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="ce2b2-116">Na przykład `x + y * z` najpierw mnoży `y` przez `z` , a następnie dodaje wynik do `x`, ale `(x + y) * z` najpierw dodaje `x` i `y` i następnie mnoży wynik przez `z`.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-116">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="ce2b2-117">Większość operatorów może być *przeciążone*.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-117">Most operators can be *overloaded*.</span></span> <span data-ttu-id="ce2b2-118">Przeciążanie operatora zezwala na implementacjami operatorów zdefiniowanych przez użytkownika, może być określony dla operacji, gdzie jeden lub oba operandy są typu klasy lub struktury zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-118">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="ce2b2-119">Poniżej znajduje się podsumowanie C#firmy operatorów, najniższą listę kategorii operatora w kolejności od najwyższego do.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-119">The following summarizes C#’s operators, listing the operator categories in order of precedence from highest to lowest.</span></span> <span data-ttu-id="ce2b2-120">Operatory w tej samej kategorii mają równy priorytet.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-120">Operators in the same category have equal precedence.</span></span> <span data-ttu-id="ce2b2-121">W każdej z nich znajduje się lista wyrażeń w danej kategorii, oraz opis tego typu wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="ce2b2-121">Under each category is a list of expressions in that category along with the description of that expression type.</span></span>

* <span data-ttu-id="ce2b2-122">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="ce2b2-122">Primary</span></span>
    - <span data-ttu-id="ce2b2-123">`x.m`: Dostęp do elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="ce2b2-123">`x.m`: Member access</span></span>
    - <span data-ttu-id="ce2b2-124">`x(...)`: Wywołanie metody i delegata</span><span class="sxs-lookup"><span data-stu-id="ce2b2-124">`x(...)`: Method and delegate invocation</span></span>
    - <span data-ttu-id="ce2b2-125">`x[...]`: Dostęp do tablicy i indeksatora</span><span class="sxs-lookup"><span data-stu-id="ce2b2-125">`x[...]`: Array and indexer access</span></span>
    - <span data-ttu-id="ce2b2-126">`x++`: Postinkrementacja</span><span class="sxs-lookup"><span data-stu-id="ce2b2-126">`x++`: Post-increment</span></span>
    - <span data-ttu-id="ce2b2-127">`x--`: Postdekrementacja</span><span class="sxs-lookup"><span data-stu-id="ce2b2-127">`x--`: Post-decrement</span></span>
    - <span data-ttu-id="ce2b2-128">`new T(...)`: Utworzenie obiektu i delegata</span><span class="sxs-lookup"><span data-stu-id="ce2b2-128">`new T(...)`: Object and delegate creation</span></span>
    - <span data-ttu-id="ce2b2-129">`new T(...){...}`: Utworzenie obiektu za pomocą inicjatora</span><span class="sxs-lookup"><span data-stu-id="ce2b2-129">`new T(...){...}`: Object creation with initializer</span></span>
    - <span data-ttu-id="ce2b2-130">`new {...}`:  Inicjator obiektu anonimowego</span><span class="sxs-lookup"><span data-stu-id="ce2b2-130">`new {...}`:  Anonymous object initializer</span></span>
    - <span data-ttu-id="ce2b2-131">`new T[...]`: Do utworzenia tablicy</span><span class="sxs-lookup"><span data-stu-id="ce2b2-131">`new T[...]`: Array creation</span></span>
    - <span data-ttu-id="ce2b2-132">`typeof(T)`: Uzyskaj <xref:System.Type> dla obiektu `T`</span><span class="sxs-lookup"><span data-stu-id="ce2b2-132">`typeof(T)`: Obtain <xref:System.Type> object for `T`</span></span>
    - <span data-ttu-id="ce2b2-133">`checked(x)`: Obliczenie wyrażenia w kontekście sprawdzanym</span><span class="sxs-lookup"><span data-stu-id="ce2b2-133">`checked(x)`: Evaluate expression in checked context</span></span>
    - <span data-ttu-id="ce2b2-134">`unchecked(x)`: Obliczenie wyrażenia w kontekście niesprawdzanym</span><span class="sxs-lookup"><span data-stu-id="ce2b2-134">`unchecked(x)`: Evaluate expression in unchecked context</span></span>
    - <span data-ttu-id="ce2b2-135">`default(T)`: Uzyskanie wartości domyślnej typu `T`</span><span class="sxs-lookup"><span data-stu-id="ce2b2-135">`default(T)`: Obtain default value of type `T`</span></span>
    - <span data-ttu-id="ce2b2-136">`delegate {...}`: Funkcja anonimowa (metoda anonimowa)</span><span class="sxs-lookup"><span data-stu-id="ce2b2-136">`delegate {...}`: Anonymous function (anonymous method)</span></span>
* <span data-ttu-id="ce2b2-137">Jednoargumentowy</span><span class="sxs-lookup"><span data-stu-id="ce2b2-137">Unary</span></span>
    - <span data-ttu-id="ce2b2-138">`+x`: Tożsamość</span><span class="sxs-lookup"><span data-stu-id="ce2b2-138">`+x`: Identity</span></span>
    - <span data-ttu-id="ce2b2-139">`-x`: Negacja</span><span class="sxs-lookup"><span data-stu-id="ce2b2-139">`-x`: Negation</span></span>
    - <span data-ttu-id="ce2b2-140">`!x`: Negacja logiczna</span><span class="sxs-lookup"><span data-stu-id="ce2b2-140">`!x`: Logical negation</span></span>
    - <span data-ttu-id="ce2b2-141">`~x`: Negacja bitowa</span><span class="sxs-lookup"><span data-stu-id="ce2b2-141">`~x`: Bitwise negation</span></span>
    - <span data-ttu-id="ce2b2-142">`++x`: Preinkrementacja</span><span class="sxs-lookup"><span data-stu-id="ce2b2-142">`++x`: Pre-increment</span></span>
    - <span data-ttu-id="ce2b2-143">`--x`: Predekrementacja</span><span class="sxs-lookup"><span data-stu-id="ce2b2-143">`--x`: Pre-decrement</span></span>
    - <span data-ttu-id="ce2b2-144">`(T)x`: Jawnie przekonwertować `x` na typ `T`</span><span class="sxs-lookup"><span data-stu-id="ce2b2-144">`(T)x`: Explicitly convert `x` to type `T`</span></span>
    - <span data-ttu-id="ce2b2-145">`await x`: Asynchronicznie poczekaj, aż `x` do ukończenia</span><span class="sxs-lookup"><span data-stu-id="ce2b2-145">`await x`: Asynchronously wait for `x` to complete</span></span>
* <span data-ttu-id="ce2b2-146">Mnożenia</span><span class="sxs-lookup"><span data-stu-id="ce2b2-146">Multiplicative</span></span>
    - <span data-ttu-id="ce2b2-147">`x * y`: Mnożenie</span><span class="sxs-lookup"><span data-stu-id="ce2b2-147">`x * y`: Multiplication</span></span>
    - <span data-ttu-id="ce2b2-148">`x / y`: Dzielenie</span><span class="sxs-lookup"><span data-stu-id="ce2b2-148">`x / y`: Division</span></span>
    - <span data-ttu-id="ce2b2-149">`x % y`: Reszta</span><span class="sxs-lookup"><span data-stu-id="ce2b2-149">`x % y`: Remainder</span></span>
* <span data-ttu-id="ce2b2-150">Dodatku</span><span class="sxs-lookup"><span data-stu-id="ce2b2-150">Additive</span></span>
    - <span data-ttu-id="ce2b2-151">`x + y`: Dodawanie, łączenie ciągów, łączenie delegatów</span><span class="sxs-lookup"><span data-stu-id="ce2b2-151">`x + y`: Addition, string concatenation, delegate combination</span></span>
    - <span data-ttu-id="ce2b2-152">`x – y`: Odejmowanie, usuwanie delegata</span><span class="sxs-lookup"><span data-stu-id="ce2b2-152">`x – y`: Subtraction, delegate removal</span></span>
* <span data-ttu-id="ce2b2-153">Shift</span><span class="sxs-lookup"><span data-stu-id="ce2b2-153">Shift</span></span>
    - <span data-ttu-id="ce2b2-154">`x << y`: Przesunięcie w lewo</span><span class="sxs-lookup"><span data-stu-id="ce2b2-154">`x << y`: Shift left</span></span>
    - <span data-ttu-id="ce2b2-155">`x >> y`: Przesunięcie w prawo</span><span class="sxs-lookup"><span data-stu-id="ce2b2-155">`x >> y`: Shift right</span></span>
* <span data-ttu-id="ce2b2-156">Relacyjne i badania typu</span><span class="sxs-lookup"><span data-stu-id="ce2b2-156">Relational and type testing</span></span>
    - <span data-ttu-id="ce2b2-157">`x < y`: Mniejsze niż</span><span class="sxs-lookup"><span data-stu-id="ce2b2-157">`x < y`: Less than</span></span>
    - <span data-ttu-id="ce2b2-158">`x > y`: Większe niż</span><span class="sxs-lookup"><span data-stu-id="ce2b2-158">`x > y`: Greater than</span></span>
    - <span data-ttu-id="ce2b2-159">`x <= y`: Mniejsze niż lub równe</span><span class="sxs-lookup"><span data-stu-id="ce2b2-159">`x <= y`: Less than or equal</span></span>
    - <span data-ttu-id="ce2b2-160">`x >= y`: Większe niż lub równe</span><span class="sxs-lookup"><span data-stu-id="ce2b2-160">`x >= y`: Greater than or equal</span></span>
    - <span data-ttu-id="ce2b2-161">`x is T`: Zwróć `true` Jeśli `x` jest `T`, `false` inaczej</span><span class="sxs-lookup"><span data-stu-id="ce2b2-161">`x is T`: Return `true` if `x` is a `T`, `false` otherwise</span></span>
    - <span data-ttu-id="ce2b2-162">`x as T`: Zwróć `x` wpisanych w formie `T`, lub `null` Jeśli `x` nie jest `T`</span><span class="sxs-lookup"><span data-stu-id="ce2b2-162">`x as T`: Return `x` typed as `T`, or `null` if `x` is not a `T`</span></span>
* <span data-ttu-id="ce2b2-163">Równość</span><span class="sxs-lookup"><span data-stu-id="ce2b2-163">Equality</span></span>
    - <span data-ttu-id="ce2b2-164">`x == y`: Równa się</span><span class="sxs-lookup"><span data-stu-id="ce2b2-164">`x == y`: Equal</span></span>
    - <span data-ttu-id="ce2b2-165">`x != y`: Nie równa się</span><span class="sxs-lookup"><span data-stu-id="ce2b2-165">`x != y`: Not equal</span></span>
* <span data-ttu-id="ce2b2-166">AND logiczne</span><span class="sxs-lookup"><span data-stu-id="ce2b2-166">Logical AND</span></span>
    - <span data-ttu-id="ce2b2-167">`x & y`: Liczba całkowita bitowe i logicznych logiczne AND</span><span class="sxs-lookup"><span data-stu-id="ce2b2-167">`x & y`: Integer bitwise AND, boolean logical AND</span></span>
* <span data-ttu-id="ce2b2-168">XOR logiczne</span><span class="sxs-lookup"><span data-stu-id="ce2b2-168">Logical XOR</span></span>
    - <span data-ttu-id="ce2b2-169">`x ^ y`: Bitowe XOR dla wartości całkowitych, logiczne XOR dla wartości binarnych</span><span class="sxs-lookup"><span data-stu-id="ce2b2-169">`x ^ y`: Integer bitwise XOR, boolean logical XOR</span></span>
* <span data-ttu-id="ce2b2-170">OR logiczne</span><span class="sxs-lookup"><span data-stu-id="ce2b2-170">Logical OR</span></span>
    - <span data-ttu-id="ce2b2-171">`x | y`: Bitowe OR dla wartości całkowitych, logiczne OR dla wartości binarnych</span><span class="sxs-lookup"><span data-stu-id="ce2b2-171">`x | y`: Integer bitwise OR, boolean logical OR</span></span>
* <span data-ttu-id="ce2b2-172">AND warunkowe</span><span class="sxs-lookup"><span data-stu-id="ce2b2-172">Conditional AND</span></span>
    - <span data-ttu-id="ce2b2-173">`x && y`: Ocenia `y` tylko wtedy, gdy `x` nie jest `false`</span><span class="sxs-lookup"><span data-stu-id="ce2b2-173">`x && y`: Evaluates `y` only if `x` is not `false`</span></span>
* <span data-ttu-id="ce2b2-174">OR warunkowe</span><span class="sxs-lookup"><span data-stu-id="ce2b2-174">Conditional OR</span></span>
    - <span data-ttu-id="ce2b2-175">`x || y`: Ocenia `y` tylko wtedy, gdy `x` nie jest `true`</span><span class="sxs-lookup"><span data-stu-id="ce2b2-175">`x || y`: Evaluates `y` only if `x` is not `true`</span></span>
* <span data-ttu-id="ce2b2-176">Łączenie wartości null</span><span class="sxs-lookup"><span data-stu-id="ce2b2-176">Null coalescing</span></span>
    - <span data-ttu-id="ce2b2-177">`x ?? y`: Daje w wyniku `y` Jeśli `x` ma wartość null, aby `x` inaczej</span><span class="sxs-lookup"><span data-stu-id="ce2b2-177">`x ?? y`: Evaluates to `y` if `x` is null, to `x` otherwise</span></span>
* <span data-ttu-id="ce2b2-178">Warunkowe</span><span class="sxs-lookup"><span data-stu-id="ce2b2-178">Conditional</span></span>
    - <span data-ttu-id="ce2b2-179">`x ? y : z`: Ocenia `y` Jeśli `x` jest `true`, `z` Jeśli `x` jest `false`</span><span class="sxs-lookup"><span data-stu-id="ce2b2-179">`x ? y : z`: Evaluates `y` if `x` is `true`, `z` if `x` is `false`</span></span>
* <span data-ttu-id="ce2b2-180">Przypisania lub funkcja anonimowa</span><span class="sxs-lookup"><span data-stu-id="ce2b2-180">Assignment or anonymous function</span></span>
    - <span data-ttu-id="ce2b2-181">`x = y`: Przypisanie</span><span class="sxs-lookup"><span data-stu-id="ce2b2-181">`x = y`: Assignment</span></span>
    - <span data-ttu-id="ce2b2-182">`x op= y`: Przydział złożony; obsługiwane operatory to</span><span class="sxs-lookup"><span data-stu-id="ce2b2-182">`x op= y`: Compound assignment; supported operators are</span></span>
        - <span data-ttu-id="ce2b2-183">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span><span class="sxs-lookup"><span data-stu-id="ce2b2-183">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span></span>
    - <span data-ttu-id="ce2b2-184">`(T x) => y`: Funkcja anonimowa (wyrażenie lambda)</span><span class="sxs-lookup"><span data-stu-id="ce2b2-184">`(T x) => y`: Anonymous function (lambda expression)</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ce2b2-185">[Poprzednie](types-and-variables.md)
>[dalej](statements.md)</span><span class="sxs-lookup"><span data-stu-id="ce2b2-185">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>