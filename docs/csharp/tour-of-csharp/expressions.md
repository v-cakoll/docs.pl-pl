---
title: C#Wyrażenia — Przewodnik po przykładzie C# języka
description: bloki konstrukcyjne są wyrażenia, argumenty operacji i operatory C# języka
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 682f98d51bf4eb3c1641297972afb86956e06d3e
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212095"
---
# <a name="expressions"></a><span data-ttu-id="bac28-103">Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="bac28-103">Expressions</span></span>

<span data-ttu-id="bac28-104">*Wyrażenia* są konstruowane na podstawie *operandów* i *operatorów*.</span><span class="sxs-lookup"><span data-stu-id="bac28-104">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="bac28-105">Operatory wyrażenia wskazują operacje do zastosowania dla operandów.</span><span class="sxs-lookup"><span data-stu-id="bac28-105">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="bac28-106">Przykłady operatorów to `+`, `-`, `*`, `/`i `new`.</span><span class="sxs-lookup"><span data-stu-id="bac28-106">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="bac28-107">Przykładami operandów są literały, pola, zmienne lokalne i wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="bac28-107">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="bac28-108">Gdy wyrażenie zawiera wiele operatorów *pierwszeństwo* operatorów określa kolejność, w jakiej są oceniane poszczególne operatory.</span><span class="sxs-lookup"><span data-stu-id="bac28-108">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="bac28-109">Na przykład, wyrażenie `x + y * z` jest oceniane jako `x + (y * z)`, ponieważ operator `*` ma wyższy priorytet niż operator `+`.</span><span class="sxs-lookup"><span data-stu-id="bac28-109">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="bac28-110">Gdy operand występuje między dwoma operatorami o tym samym priorytecie *asocjacyjność* operatorów określa kolejność, w której są wykonywane operacje:</span><span class="sxs-lookup"><span data-stu-id="bac28-110">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

*   <span data-ttu-id="bac28-111">Z wyjątkiem operatorów przypisania wszystkie operatory dwuargumentowe są *lewostronne*, co oznacza, że operacje są wykonywane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="bac28-111">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="bac28-112">Na przykład `x + y + z` jest oceniane jako `(x + y) + z`.</span><span class="sxs-lookup"><span data-stu-id="bac28-112">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
*   <span data-ttu-id="bac28-113">Operatory przypisania i operator warunkowy (`?:`) są *prawostronne*, co oznacza, że operacje są wykonywane od prawej do lewej.</span><span class="sxs-lookup"><span data-stu-id="bac28-113">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="bac28-114">Na przykład `x = y = z` jest oceniane jako `x = (y = z)`.</span><span class="sxs-lookup"><span data-stu-id="bac28-114">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="bac28-115">Pierwszeństwo i asocjacyjność mogą być kontrolowane za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="bac28-115">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="bac28-116">Na przykład `x + y * z` najpierw mnoży `y` przez `z` , a następnie dodaje wynik do `x`, ale `(x + y) * z` najpierw dodaje `x` i `y` i następnie wynik mnoży przez `z`.</span><span class="sxs-lookup"><span data-stu-id="bac28-116">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="bac28-117">Większość operatorów może być *przeciążona*.</span><span class="sxs-lookup"><span data-stu-id="bac28-117">Most operators can be *overloaded*.</span></span> <span data-ttu-id="bac28-118">Przeciążanie operatora umożliwia określanie definiowanych przez użytkownika implementacji operatorów dla operacji, w których jeden lub oba operandy mają typ struktury lub klasy zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bac28-118">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="bac28-119">Poniżej znajduje się podsumowanie operatorów języka C#. Kategorie operatorów wypisane są w kolejności pierwszeństwa od najwyższego do najniższego.</span><span class="sxs-lookup"><span data-stu-id="bac28-119">The following summarizes C#’s operators, listing the operator categories in order of precedence from highest to lowest.</span></span> <span data-ttu-id="bac28-120">Operatory w tej samej kategorii mają takie samo pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="bac28-120">Operators in the same category have equal precedence.</span></span> <span data-ttu-id="bac28-121">Pod każdą z kategorii znajduje się lista wyrażeń znajdujących się w niej, wraz z opisem danego typu wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="bac28-121">Under each category is a list of expressions in that category along with the description of that expression type.</span></span>

* <span data-ttu-id="bac28-122">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="bac28-122">Primary</span></span>
    - <span data-ttu-id="bac28-123">`x.m`: Dostęp do elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="bac28-123">`x.m`: Member access</span></span>
    - <span data-ttu-id="bac28-124">`x(...)`: Wywołanie metody i delegata</span><span class="sxs-lookup"><span data-stu-id="bac28-124">`x(...)`: Method and delegate invocation</span></span>
    - <span data-ttu-id="bac28-125">`x[...]`: Dostęp do tablicy i indeksatora</span><span class="sxs-lookup"><span data-stu-id="bac28-125">`x[...]`: Array and indexer access</span></span>
    - <span data-ttu-id="bac28-126">`x++`: Postinkrementacja</span><span class="sxs-lookup"><span data-stu-id="bac28-126">`x++`: Post-increment</span></span>
    - <span data-ttu-id="bac28-127">`x--`: Postdekrementacja</span><span class="sxs-lookup"><span data-stu-id="bac28-127">`x--`: Post-decrement</span></span>
    - <span data-ttu-id="bac28-128">`new T(...)`: Utworzenie obiektu i delegata</span><span class="sxs-lookup"><span data-stu-id="bac28-128">`new T(...)`: Object and delegate creation</span></span>
    - <span data-ttu-id="bac28-129">`new T(...){...}`: Utworzenie obiektu za pomocą inicjatora</span><span class="sxs-lookup"><span data-stu-id="bac28-129">`new T(...){...}`: Object creation with initializer</span></span>
    - <span data-ttu-id="bac28-130">`new {...}`:  Inicjator obiektu anonimowego</span><span class="sxs-lookup"><span data-stu-id="bac28-130">`new {...}`:  Anonymous object initializer</span></span>
    - <span data-ttu-id="bac28-131">`new T[...]`: Do utworzenia tablicy</span><span class="sxs-lookup"><span data-stu-id="bac28-131">`new T[...]`: Array creation</span></span>
    - <span data-ttu-id="bac28-132">`typeof(T)`: Uzyskaj <xref:System.Type> dla obiektu `T`</span><span class="sxs-lookup"><span data-stu-id="bac28-132">`typeof(T)`: Obtain <xref:System.Type> object for `T`</span></span>
    - <span data-ttu-id="bac28-133">`checked(x)`: Obliczenie wyrażenia w kontekście sprawdzanym</span><span class="sxs-lookup"><span data-stu-id="bac28-133">`checked(x)`: Evaluate expression in checked context</span></span>
    - <span data-ttu-id="bac28-134">`unchecked(x)`: Obliczenie wyrażenia w kontekście niesprawdzanym</span><span class="sxs-lookup"><span data-stu-id="bac28-134">`unchecked(x)`: Evaluate expression in unchecked context</span></span>
    - <span data-ttu-id="bac28-135">`default(T)`: Uzyskanie wartości domyślnej typu `T`</span><span class="sxs-lookup"><span data-stu-id="bac28-135">`default(T)`: Obtain default value of type `T`</span></span>
    - <span data-ttu-id="bac28-136">`delegate {...}`: Funkcja anonimowa (metoda anonimowa)</span><span class="sxs-lookup"><span data-stu-id="bac28-136">`delegate {...}`: Anonymous function (anonymous method)</span></span>
* <span data-ttu-id="bac28-137">Jednoargumentowy</span><span class="sxs-lookup"><span data-stu-id="bac28-137">Unary</span></span>
    - <span data-ttu-id="bac28-138">`+x`: Tożsamość</span><span class="sxs-lookup"><span data-stu-id="bac28-138">`+x`: Identity</span></span>
    - <span data-ttu-id="bac28-139">`-x`: Negacja</span><span class="sxs-lookup"><span data-stu-id="bac28-139">`-x`: Negation</span></span>
    - <span data-ttu-id="bac28-140">`!x`: Negacja logiczna</span><span class="sxs-lookup"><span data-stu-id="bac28-140">`!x`: Logical negation</span></span>
    - <span data-ttu-id="bac28-141">`~x`: Negacja bitowa</span><span class="sxs-lookup"><span data-stu-id="bac28-141">`~x`: Bitwise negation</span></span>
    - <span data-ttu-id="bac28-142">`++x`: Preinkrementacja</span><span class="sxs-lookup"><span data-stu-id="bac28-142">`++x`: Pre-increment</span></span>
    - <span data-ttu-id="bac28-143">`--x`: Predekrementacja</span><span class="sxs-lookup"><span data-stu-id="bac28-143">`--x`: Pre-decrement</span></span>
    - <span data-ttu-id="bac28-144">`(T)x`: Jawna konwersja `x` na typ `T`</span><span class="sxs-lookup"><span data-stu-id="bac28-144">`(T)x`: Explicitly convert `x` to type `T`</span></span>
    - <span data-ttu-id="bac28-145">`await x`: Asynchronicznie poczekaj na ukończenie `x`</span><span class="sxs-lookup"><span data-stu-id="bac28-145">`await x`: Asynchronously wait for `x` to complete</span></span>
* <span data-ttu-id="bac28-146">Mnożeniowy</span><span class="sxs-lookup"><span data-stu-id="bac28-146">Multiplicative</span></span>
    - <span data-ttu-id="bac28-147">`x * y`: Mnożenie</span><span class="sxs-lookup"><span data-stu-id="bac28-147">`x * y`: Multiplication</span></span>
    - <span data-ttu-id="bac28-148">`x / y`: Dzielenie</span><span class="sxs-lookup"><span data-stu-id="bac28-148">`x / y`: Division</span></span>
    - <span data-ttu-id="bac28-149">`x % y`: Reszta</span><span class="sxs-lookup"><span data-stu-id="bac28-149">`x % y`: Remainder</span></span>
* <span data-ttu-id="bac28-150">Dodatku</span><span class="sxs-lookup"><span data-stu-id="bac28-150">Additive</span></span>
    - <span data-ttu-id="bac28-151">`x + y`: Dodawanie, łączenie ciągów, łączenie delegatów</span><span class="sxs-lookup"><span data-stu-id="bac28-151">`x + y`: Addition, string concatenation, delegate combination</span></span>
    - <span data-ttu-id="bac28-152">`x – y`: Odejmowanie, usuwanie delegata</span><span class="sxs-lookup"><span data-stu-id="bac28-152">`x – y`: Subtraction, delegate removal</span></span>
* <span data-ttu-id="bac28-153">Shift</span><span class="sxs-lookup"><span data-stu-id="bac28-153">Shift</span></span>
    - <span data-ttu-id="bac28-154">`x << y`: Przesunięcie w lewo</span><span class="sxs-lookup"><span data-stu-id="bac28-154">`x << y`: Shift left</span></span>
    - <span data-ttu-id="bac28-155">`x >> y`: Przesunięcie w prawo</span><span class="sxs-lookup"><span data-stu-id="bac28-155">`x >> y`: Shift right</span></span>
* <span data-ttu-id="bac28-156">Relacyjne i badania typu</span><span class="sxs-lookup"><span data-stu-id="bac28-156">Relational and type testing</span></span>
    - <span data-ttu-id="bac28-157">`x < y`: Mniejsze niż</span><span class="sxs-lookup"><span data-stu-id="bac28-157">`x < y`: Less than</span></span>
    - <span data-ttu-id="bac28-158">`x > y`: Większe niż</span><span class="sxs-lookup"><span data-stu-id="bac28-158">`x > y`: Greater than</span></span>
    - <span data-ttu-id="bac28-159">`x <= y`: Mniejsze niż lub równe</span><span class="sxs-lookup"><span data-stu-id="bac28-159">`x <= y`: Less than or equal</span></span>
    - <span data-ttu-id="bac28-160">`x >= y`: Większe niż lub równe</span><span class="sxs-lookup"><span data-stu-id="bac28-160">`x >= y`: Greater than or equal</span></span>
    - <span data-ttu-id="bac28-161">`x is T`: Zwróć `true` Jeśli `x` jest `T`, `false` inaczej</span><span class="sxs-lookup"><span data-stu-id="bac28-161">`x is T`: Return `true` if `x` is a `T`, `false` otherwise</span></span>
    - <span data-ttu-id="bac28-162">`x as T`: Zwróć `x` wpisanych w formie `T`, lub `null` Jeśli `x` nie jest `T`</span><span class="sxs-lookup"><span data-stu-id="bac28-162">`x as T`: Return `x` typed as `T`, or `null` if `x` is not a `T`</span></span>
* <span data-ttu-id="bac28-163">Równości</span><span class="sxs-lookup"><span data-stu-id="bac28-163">Equality</span></span>
    - <span data-ttu-id="bac28-164">`x == y`: Równa się</span><span class="sxs-lookup"><span data-stu-id="bac28-164">`x == y`: Equal</span></span>
    - <span data-ttu-id="bac28-165">`x != y`: Nie równa się</span><span class="sxs-lookup"><span data-stu-id="bac28-165">`x != y`: Not equal</span></span>
* <span data-ttu-id="bac28-166">Logicznego AND</span><span class="sxs-lookup"><span data-stu-id="bac28-166">Logical AND</span></span>
    - <span data-ttu-id="bac28-167">`x & y`: Liczba całkowita bitowe i logicznych logiczne AND</span><span class="sxs-lookup"><span data-stu-id="bac28-167">`x & y`: Integer bitwise AND, boolean logical AND</span></span>
* <span data-ttu-id="bac28-168">Logicznego XOR</span><span class="sxs-lookup"><span data-stu-id="bac28-168">Logical XOR</span></span>
    - <span data-ttu-id="bac28-169">`x ^ y`: Bitowe XOR dla wartości całkowitych, logiczne XOR dla wartości binarnych</span><span class="sxs-lookup"><span data-stu-id="bac28-169">`x ^ y`: Integer bitwise XOR, boolean logical XOR</span></span>
* <span data-ttu-id="bac28-170">Logicznego OR</span><span class="sxs-lookup"><span data-stu-id="bac28-170">Logical OR</span></span>
    - <span data-ttu-id="bac28-171">`x | y`: Bitowe OR dla wartości całkowitych, logiczne OR dla wartości binarnych</span><span class="sxs-lookup"><span data-stu-id="bac28-171">`x | y`: Integer bitwise OR, boolean logical OR</span></span>
* <span data-ttu-id="bac28-172">Warunkowego AND</span><span class="sxs-lookup"><span data-stu-id="bac28-172">Conditional AND</span></span>
    - <span data-ttu-id="bac28-173">`x && y`: Ocenia `y` tylko wtedy, gdy `x` nie jest `false`</span><span class="sxs-lookup"><span data-stu-id="bac28-173">`x && y`: Evaluates `y` only if `x` is not `false`</span></span>
* <span data-ttu-id="bac28-174">Warunkowego OR</span><span class="sxs-lookup"><span data-stu-id="bac28-174">Conditional OR</span></span>
    - <span data-ttu-id="bac28-175">`x || y`: Ocenia `y` tylko wtedy, gdy `x` nie jest `true`</span><span class="sxs-lookup"><span data-stu-id="bac28-175">`x || y`: Evaluates `y` only if `x` is not `true`</span></span>
* <span data-ttu-id="bac28-176">Łączenia wartości null</span><span class="sxs-lookup"><span data-stu-id="bac28-176">Null coalescing</span></span>
    - <span data-ttu-id="bac28-177">`x ?? y`: Daje w wyniku `y` Jeśli `x` ma wartość null, aby `x` inaczej</span><span class="sxs-lookup"><span data-stu-id="bac28-177">`x ?? y`: Evaluates to `y` if `x` is null, to `x` otherwise</span></span>
* <span data-ttu-id="bac28-178">Warunkowe</span><span class="sxs-lookup"><span data-stu-id="bac28-178">Conditional</span></span>
    - <span data-ttu-id="bac28-179">`x ? y : z`: Ocenia `y` Jeśli `x` jest `true`, `z` Jeśli `x` jest `false`</span><span class="sxs-lookup"><span data-stu-id="bac28-179">`x ? y : z`: Evaluates `y` if `x` is `true`, `z` if `x` is `false`</span></span>
* <span data-ttu-id="bac28-180">Przypisania lub funkcji anonimowej</span><span class="sxs-lookup"><span data-stu-id="bac28-180">Assignment or anonymous function</span></span>
    - <span data-ttu-id="bac28-181">`x = y`: Przypisanie</span><span class="sxs-lookup"><span data-stu-id="bac28-181">`x = y`: Assignment</span></span>
    - <span data-ttu-id="bac28-182">`x op= y`: Złożone przypisanie; obsługiwane operatory to</span><span class="sxs-lookup"><span data-stu-id="bac28-182">`x op= y`: Compound assignment; supported operators are</span></span>
        - <span data-ttu-id="bac28-183">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span><span class="sxs-lookup"><span data-stu-id="bac28-183">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span></span>
    - <span data-ttu-id="bac28-184">`(T x) => y`: Funkcja anonimowa (wyrażenie lambda)</span><span class="sxs-lookup"><span data-stu-id="bac28-184">`(T x) => y`: Anonymous function (lambda expression)</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="bac28-185">[Poprzednie](types-and-variables.md)
> [dalej](statements.md)</span><span class="sxs-lookup"><span data-stu-id="bac28-185">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>