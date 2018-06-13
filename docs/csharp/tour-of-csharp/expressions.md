---
title: C# wyrażeń — samouczek języka C#
description: wyrażenia, argumentów i operatory są blokami konstrukcyjnymi języka C#
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 8fa1c5d0464644b26eb457bca8ecaf007c288f42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352306"
---
# <a name="expressions"></a><span data-ttu-id="812c4-103">Wyrażenia</span><span class="sxs-lookup"><span data-stu-id="812c4-103">Expressions</span></span>

<span data-ttu-id="812c4-104">*Wyrażenia* są tworzone na podstawie *operandy* i *operatory*.</span><span class="sxs-lookup"><span data-stu-id="812c4-104">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="812c4-105">Operatory wyrażenia wskazują, jakie operacje, aby zastosować do argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="812c4-105">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="812c4-106">Przykłady operatory `+`, `-`, `*`, `/`, i `new`.</span><span class="sxs-lookup"><span data-stu-id="812c4-106">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="812c4-107">Przykładami operandy literały, pola, zmienne lokalne i wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="812c4-107">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="812c4-108">Jeśli wyrażenie zawiera wiele operatorów *pierwszeństwo* operatorów decyduje o kolejności, w jakiej są oceniane poszczególne operatory.</span><span class="sxs-lookup"><span data-stu-id="812c4-108">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="812c4-109">Na przykład, wyrażenie `x + y * z` jest szacowana jako `x + (y * z)` ponieważ `*` operator ma wyższy priorytet niż `+` operatora.</span><span class="sxs-lookup"><span data-stu-id="812c4-109">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="812c4-110">Po wystąpieniu operand między dwa operatory o tym samym priorytecie *kojarzenie* operatorów decyduje o kolejności, w którym wykonywane są operacje:</span><span class="sxs-lookup"><span data-stu-id="812c4-110">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

*   <span data-ttu-id="812c4-111">Z wyjątkiem operatory przypisania są wszystkie operatory binarne *lewostronne*, co oznacza, że operacje są wykonywane od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="812c4-111">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="812c4-112">Na przykład `x + y + z` jest szacowana jako `(x + y) + z`.</span><span class="sxs-lookup"><span data-stu-id="812c4-112">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
*   <span data-ttu-id="812c4-113">Operatory przypisania i operator warunkowy (`?:`) są *łączny prawo*, co oznacza, że operacje są wykonywane od prawej do lewej.</span><span class="sxs-lookup"><span data-stu-id="812c4-113">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="812c4-114">Na przykład `x = y = z` jest szacowana jako `x = (y = z)`.</span><span class="sxs-lookup"><span data-stu-id="812c4-114">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="812c4-115">Priorytet i łączność można sterować za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="812c4-115">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="812c4-116">Na przykład `x + y * z` najpierw mnoży `y` przez `z` , a następnie dodaje wynik do `x`, ale `(x + y) * z` najpierw dodaje `x` i `y` , a następnie mnoży wynik przez `z`.</span><span class="sxs-lookup"><span data-stu-id="812c4-116">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="812c4-117">Większość operatorów może być *przeciążony*.</span><span class="sxs-lookup"><span data-stu-id="812c4-117">Most operators can be *overloaded*.</span></span> <span data-ttu-id="812c4-118">Przeładowanie operatora pozwala implementacje zdefiniowany przez użytkownika operator może być określony dla operacji skutkującej jeden lub oba argumenty operacji typu klasy lub struktury zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="812c4-118">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="812c4-119">Poniżej przedstawiono podsumowanie C# dla operatorów, wyświetlanie kategorii operatora w kolejności od najwyższego malejąco.</span><span class="sxs-lookup"><span data-stu-id="812c4-119">The following summarizes C#’s operators, listing the operator categories in order of precedence from highest to lowest.</span></span> <span data-ttu-id="812c4-120">Operatory w tej samej kategorii mają taki sam priorytet.</span><span class="sxs-lookup"><span data-stu-id="812c4-120">Operators in the same category have equal precedence.</span></span> <span data-ttu-id="812c4-121">W każdej z nich znajduje się lista wyrażeń w tej kategorii, oraz opis tego typu wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="812c4-121">Under each category is a list of expressions in that category along with the description of that expression type.</span></span>

* <span data-ttu-id="812c4-122">podstawowy</span><span class="sxs-lookup"><span data-stu-id="812c4-122">Primary</span></span>
    - <span data-ttu-id="812c4-123">`x.m`: Dostęp do elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="812c4-123">`x.m`: Member access</span></span>
    - <span data-ttu-id="812c4-124">`x(...)`: Wywołanie metody a obiektem delegowanym</span><span class="sxs-lookup"><span data-stu-id="812c4-124">`x(...)`: Method and delegate invocation</span></span>
    - <span data-ttu-id="812c4-125">`x[...]`: Tablica i dostęp indeksatora</span><span class="sxs-lookup"><span data-stu-id="812c4-125">`x[...]`: Array and indexer access</span></span>
    - <span data-ttu-id="812c4-126">`x++`: Przyrost po</span><span class="sxs-lookup"><span data-stu-id="812c4-126">`x++`: Post-increment</span></span>
    - <span data-ttu-id="812c4-127">`x--`: Zmniejszenie po</span><span class="sxs-lookup"><span data-stu-id="812c4-127">`x--`: Post-decrement</span></span>
    - <span data-ttu-id="812c4-128">`new T(...)`: Obiekt, a następnie delegatem tworzenia</span><span class="sxs-lookup"><span data-stu-id="812c4-128">`new T(...)`: Object and delegate creation</span></span>
    - <span data-ttu-id="812c4-129">`new T(...){...}`: Tworzenie obiektów za pomocą inicjatora</span><span class="sxs-lookup"><span data-stu-id="812c4-129">`new T(...){...}`: Object creation with initializer</span></span>
    - <span data-ttu-id="812c4-130">`new {...}`: Inicjator obiektu anonimowe</span><span class="sxs-lookup"><span data-stu-id="812c4-130">`new {...}`:  Anonymous object initializer</span></span>
    - <span data-ttu-id="812c4-131">`new T[...]`: Do utworzenia tablicy</span><span class="sxs-lookup"><span data-stu-id="812c4-131">`new T[...]`: Array creation</span></span>
    - <span data-ttu-id="812c4-132">`typeof(T)`: Uzyskanie <xref:System.Type> obiekt do `T`</span><span class="sxs-lookup"><span data-stu-id="812c4-132">`typeof(T)`: Obtain <xref:System.Type> object for `T`</span></span>
    - <span data-ttu-id="812c4-133">`checked(x)`: Obliczyć wyrażenia w kontekście zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="812c4-133">`checked(x)`: Evaluate expression in checked context</span></span>
    - <span data-ttu-id="812c4-134">`unchecked(x)`: Obliczyć wyrażenia w kontekście unchecked</span><span class="sxs-lookup"><span data-stu-id="812c4-134">`unchecked(x)`: Evaluate expression in unchecked context</span></span>
    - <span data-ttu-id="812c4-135">`default(T)`: Wartość domyślna typu uzyskać `T`</span><span class="sxs-lookup"><span data-stu-id="812c4-135">`default(T)`: Obtain default value of type `T`</span></span>
    - <span data-ttu-id="812c4-136">`delegate {...}`: Anonimowy — funkcja (metody anonimowej)</span><span class="sxs-lookup"><span data-stu-id="812c4-136">`delegate {...}`: Anonymous function (anonymous method)</span></span>
* <span data-ttu-id="812c4-137">Jednoargumentowe</span><span class="sxs-lookup"><span data-stu-id="812c4-137">Unary</span></span>
    - <span data-ttu-id="812c4-138">`+x`: Tożsamości</span><span class="sxs-lookup"><span data-stu-id="812c4-138">`+x`: Identity</span></span>
    - <span data-ttu-id="812c4-139">`-x`: Negacji</span><span class="sxs-lookup"><span data-stu-id="812c4-139">`-x`: Negation</span></span>
    - <span data-ttu-id="812c4-140">`!x`: Logiczna Negacja</span><span class="sxs-lookup"><span data-stu-id="812c4-140">`!x`: Logical negation</span></span>
    - <span data-ttu-id="812c4-141">`~x`: Bitową negację</span><span class="sxs-lookup"><span data-stu-id="812c4-141">`~x`: Bitwise negation</span></span>
    - <span data-ttu-id="812c4-142">`++x`: Przyrost wstępnego</span><span class="sxs-lookup"><span data-stu-id="812c4-142">`++x`: Pre-increment</span></span>
    - <span data-ttu-id="812c4-143">`--x`: Zmniejszenie wstępnego</span><span class="sxs-lookup"><span data-stu-id="812c4-143">`--x`: Pre-decrement</span></span>
    - <span data-ttu-id="812c4-144">`(T)x`: Jawnie przekonwertować `x` na typ `T`</span><span class="sxs-lookup"><span data-stu-id="812c4-144">`(T)x`: Explicitly convert `x` to type `T`</span></span>
    - <span data-ttu-id="812c4-145">`await x`: Poczekaj asynchronicznie `x` do ukończenia</span><span class="sxs-lookup"><span data-stu-id="812c4-145">`await x`: Asynchronously wait for `x` to complete</span></span>
* <span data-ttu-id="812c4-146">Mnożenia</span><span class="sxs-lookup"><span data-stu-id="812c4-146">Multiplicative</span></span>
    - <span data-ttu-id="812c4-147">`x * y`: Mnożenia</span><span class="sxs-lookup"><span data-stu-id="812c4-147">`x * y`: Multiplication</span></span>
    - <span data-ttu-id="812c4-148">`x / y`: Dzielenie</span><span class="sxs-lookup"><span data-stu-id="812c4-148">`x / y`: Division</span></span>
    - <span data-ttu-id="812c4-149">`x % y`: Pozostałe</span><span class="sxs-lookup"><span data-stu-id="812c4-149">`x % y`: Remainder</span></span>
* <span data-ttu-id="812c4-150">Dodatku</span><span class="sxs-lookup"><span data-stu-id="812c4-150">Additive</span></span>
    - <span data-ttu-id="812c4-151">`x + y`: Dodawanie, ciągów, kombinacja delegata</span><span class="sxs-lookup"><span data-stu-id="812c4-151">`x + y`: Addition, string concatenation, delegate combination</span></span>
    - <span data-ttu-id="812c4-152">`x – y`: Odejmowania, usunięcie delegata</span><span class="sxs-lookup"><span data-stu-id="812c4-152">`x – y`: Subtraction, delegate removal</span></span>
* <span data-ttu-id="812c4-153">SHIFT</span><span class="sxs-lookup"><span data-stu-id="812c4-153">Shift</span></span>
    - <span data-ttu-id="812c4-154">`x << y`: Przesunięcia w lewo</span><span class="sxs-lookup"><span data-stu-id="812c4-154">`x << y`: Shift left</span></span>
    - <span data-ttu-id="812c4-155">`x >> y`: Przesuń w prawo</span><span class="sxs-lookup"><span data-stu-id="812c4-155">`x >> y`: Shift right</span></span>
* <span data-ttu-id="812c4-156">Relacyjna i testowania typu</span><span class="sxs-lookup"><span data-stu-id="812c4-156">Relational and type testing</span></span>
    - <span data-ttu-id="812c4-157">`x < y`: Mniejsza niż</span><span class="sxs-lookup"><span data-stu-id="812c4-157">`x < y`: Less than</span></span>
    - <span data-ttu-id="812c4-158">`x > y`: Większa niż</span><span class="sxs-lookup"><span data-stu-id="812c4-158">`x > y`: Greater than</span></span>
    - <span data-ttu-id="812c4-159">`x <= y`: Mniejsza niż lub równe</span><span class="sxs-lookup"><span data-stu-id="812c4-159">`x <= y`: Less than or equal</span></span>
    - <span data-ttu-id="812c4-160">`x >= y`: Większe lub równe</span><span class="sxs-lookup"><span data-stu-id="812c4-160">`x >= y`: Greater than or equal</span></span>
    - <span data-ttu-id="812c4-161">`x is T`: Zwracany `true` Jeśli `x` jest `T`, `false` inaczej</span><span class="sxs-lookup"><span data-stu-id="812c4-161">`x is T`: Return `true` if `x` is a `T`, `false` otherwise</span></span>
    - <span data-ttu-id="812c4-162">`x as T`: Zwracany `x` typu `T`, lub `null` Jeśli `x` nie jest `T`</span><span class="sxs-lookup"><span data-stu-id="812c4-162">`x as T`: Return `x` typed as `T`, or `null` if `x` is not a `T`</span></span>
* <span data-ttu-id="812c4-163">Równość</span><span class="sxs-lookup"><span data-stu-id="812c4-163">Equality</span></span>
    - <span data-ttu-id="812c4-164">`x == y`: Równe</span><span class="sxs-lookup"><span data-stu-id="812c4-164">`x == y`: Equal</span></span>
    - <span data-ttu-id="812c4-165">`x != y`: Nie jest równy</span><span class="sxs-lookup"><span data-stu-id="812c4-165">`x != y`: Not equal</span></span>
* <span data-ttu-id="812c4-166">AND logiczne</span><span class="sxs-lookup"><span data-stu-id="812c4-166">Logical AND</span></span>
    - <span data-ttu-id="812c4-167">`x & y`: Liczba całkowita bitowe i logicznych logiczny AND</span><span class="sxs-lookup"><span data-stu-id="812c4-167">`x & y`: Integer bitwise AND, boolean logical AND</span></span>
* <span data-ttu-id="812c4-168">XOR logiczne</span><span class="sxs-lookup"><span data-stu-id="812c4-168">Logical XOR</span></span>
    - <span data-ttu-id="812c4-169">`x ^ y`: Liczba całkowita iloczynu bitowego XOR, logiczna XOR logiczne</span><span class="sxs-lookup"><span data-stu-id="812c4-169">`x ^ y`: Integer bitwise XOR, boolean logical XOR</span></span>
* <span data-ttu-id="812c4-170">OR logiczne</span><span class="sxs-lookup"><span data-stu-id="812c4-170">Logical OR</span></span>
    - <span data-ttu-id="812c4-171">`x | y`: Liczba całkowita bitowe lub logiczna operatora logicznego OR</span><span class="sxs-lookup"><span data-stu-id="812c4-171">`x | y`: Integer bitwise OR, boolean logical OR</span></span>
* <span data-ttu-id="812c4-172">AND warunkowe</span><span class="sxs-lookup"><span data-stu-id="812c4-172">Conditional AND</span></span>
    - <span data-ttu-id="812c4-173">`x && y`: Oblicza `y` tylko wtedy, gdy `x` nie jest `false`</span><span class="sxs-lookup"><span data-stu-id="812c4-173">`x && y`: Evaluates `y` only if `x` is not `false`</span></span>
* <span data-ttu-id="812c4-174">OR warunkowe</span><span class="sxs-lookup"><span data-stu-id="812c4-174">Conditional OR</span></span>
    - <span data-ttu-id="812c4-175">`x || y`: Oblicza `y` tylko wtedy, gdy `x` nie jest `true`</span><span class="sxs-lookup"><span data-stu-id="812c4-175">`x || y`: Evaluates `y` only if `x` is not `true`</span></span>
* <span data-ttu-id="812c4-176">Łączenie wartości null</span><span class="sxs-lookup"><span data-stu-id="812c4-176">Null coalescing</span></span>
    - <span data-ttu-id="812c4-177">`x ?? y`: Daje w wyniku `y` Jeśli `x` ma wartość null, aby `x` inaczej</span><span class="sxs-lookup"><span data-stu-id="812c4-177">`x ?? y`: Evaluates to `y` if `x` is null, to `x` otherwise</span></span>
* <span data-ttu-id="812c4-178">Warunkowe</span><span class="sxs-lookup"><span data-stu-id="812c4-178">Conditional</span></span>
    - <span data-ttu-id="812c4-179">`x ? y : z`: Oblicza `y` Jeśli `x` jest `true`, `z` Jeśli `x` jest `false`</span><span class="sxs-lookup"><span data-stu-id="812c4-179">`x ? y : z`: Evaluates `y` if `x` is `true`, `z` if `x` is `false`</span></span>
* <span data-ttu-id="812c4-180">Przypisanie ani funkcji anonimowej</span><span class="sxs-lookup"><span data-stu-id="812c4-180">Assignment or anonymous function</span></span>
    - <span data-ttu-id="812c4-181">`x = y`: Przypisania</span><span class="sxs-lookup"><span data-stu-id="812c4-181">`x = y`: Assignment</span></span>
    - <span data-ttu-id="812c4-182">`x op= y`: Przydział złożony; Operatory obsługiwane są</span><span class="sxs-lookup"><span data-stu-id="812c4-182">`x op= y`: Compound assignment; supported operators are</span></span>
        - <span data-ttu-id="812c4-183">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span><span class="sxs-lookup"><span data-stu-id="812c4-183">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span></span>
    - <span data-ttu-id="812c4-184">`(T x) => y`: Funkcja anonimowe (wyrażenia lambda)</span><span class="sxs-lookup"><span data-stu-id="812c4-184">`(T x) => y`: Anonymous function (lambda expression)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="812c4-185">[Poprzednie](types-and-variables.md)
[dalej](statements.md)</span><span class="sxs-lookup"><span data-stu-id="812c4-185">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>
