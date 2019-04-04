---
title: C#Operatory
ms.date: 04/04/2018
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 7666918cbff7a395a93a274629fe574ff20e170c
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545692"
---
# <a name="c-operators"></a><span data-ttu-id="23178-102">C#Operatory</span><span class="sxs-lookup"><span data-stu-id="23178-102">C# operators</span></span>

<span data-ttu-id="23178-103">C# zawiera wiele operatorów, które są symbolami określającymi operacje (matematycznych, indeksowanie, wywołanie funkcji itp.) do wykonania w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="23178-103">C# provides many operators, which are symbols that specify which operations (math, indexing, function call, etc.) to perform in an expression.</span></span> <span data-ttu-id="23178-104">Możesz [przeciążenia](../../programming-guide/statements-expressions-operators/overloadable-operators.md) wiele operatorów, aby zmienić ich znaczenia w przypadku zastosowania do typu zdefiniowanego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="23178-104">You can [overload](../../programming-guide/statements-expressions-operators/overloadable-operators.md) many operators to change their meaning when applied to a user-defined type.</span></span>

<span data-ttu-id="23178-105">Operacje na typach całkowitoliczbowych (takie jak `==`, `!=`, `<`, `>`, `&`, `|`) są ogólnie dozwolone w wyliczeniu (`enum`) typy.</span><span class="sxs-lookup"><span data-stu-id="23178-105">Operations on integral types (such as `==`, `!=`, `<`, `>`, `&`, `|`) are generally allowed on enumeration (`enum`) types.</span></span>

<span data-ttu-id="23178-106">Poniższe rozdziały zawierają listę operatorów języka C# od o najwyższym priorytecie do najniższego.</span><span class="sxs-lookup"><span data-stu-id="23178-106">The sections below list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="23178-107">Operatory w każdej sekcji udostępniać na tym samym poziomie pierwszeństwa.</span><span class="sxs-lookup"><span data-stu-id="23178-107">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="23178-108">Operatory podstawowe</span><span class="sxs-lookup"><span data-stu-id="23178-108">Primary operators</span></span>

<span data-ttu-id="23178-109">Są to najwyższy pierwszeństwo operatorów.</span><span class="sxs-lookup"><span data-stu-id="23178-109">These are the highest precedence operators.</span></span>

<span data-ttu-id="23178-110">[x.y](member-access-operator.md) — dostęp do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="23178-110">[x.y](member-access-operator.md) – member access.</span></span>

<span data-ttu-id="23178-111">[x? y](null-conditional-operators.md) — wartość null, dostęp warunkowy elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="23178-111">[x?.y](null-conditional-operators.md) – null conditional member access.</span></span> <span data-ttu-id="23178-112">Zwraca `null` Jeśli po lewej stronie operand ma wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="23178-112">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="23178-113">[x? [t] ](null-conditional-operators.md) — wartość null, dostęp warunkowy indeksu.</span><span class="sxs-lookup"><span data-stu-id="23178-113">[x?[y]](null-conditional-operators.md) - null conditional index access.</span></span> <span data-ttu-id="23178-114">Zwraca `null` Jeśli po lewej stronie operand ma wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="23178-114">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="23178-115">[f(x)](invocation-operator.md) — wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="23178-115">[f(x)](invocation-operator.md) – function invocation.</span></span>

<span data-ttu-id="23178-116">[&#91;x&#93; ](index-operator.md) — indeksowanie obiektu agregacji.</span><span class="sxs-lookup"><span data-stu-id="23178-116">[a&#91;x&#93;](index-operator.md) – aggregate object indexing.</span></span>

<span data-ttu-id="23178-117">[x ++](arithmetic-operators.md#increment-operator-) — zwiększenie przyrostkowe.</span><span class="sxs-lookup"><span data-stu-id="23178-117">[x++](arithmetic-operators.md#increment-operator-) – postfix increment.</span></span> <span data-ttu-id="23178-118">Zwraca wartość x, a następnie aktualizuje lokalizację przechowywania z wartością x, która jest większa o jeden (zazwyczaj dodaje liczbę całkowitą 1).</span><span class="sxs-lookup"><span data-stu-id="23178-118">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="23178-119">[x —](arithmetic-operators.md#decrement-operator---) — zmniejszenie przyrostkowe.</span><span class="sxs-lookup"><span data-stu-id="23178-119">[x--](arithmetic-operators.md#decrement-operator---) –  postfix decrement.</span></span> <span data-ttu-id="23178-120">Zwraca wartość x, a następnie aktualizuje lokalizację przechowywania z wartością x, która jest mniejsza (zazwyczaj odejmuje liczbę całkowitą 1).</span><span class="sxs-lookup"><span data-stu-id="23178-120">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="23178-121">[nowe](../keywords/new-operator.md) — podczas tworzenia wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="23178-121">[new](../keywords/new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="23178-122">[TypeOf](../keywords/typeof.md) — zwraca <xref:System.Type> obiekt reprezentujący argument.</span><span class="sxs-lookup"><span data-stu-id="23178-122">[typeof](../keywords/typeof.md) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="23178-123">[zaznaczone](../keywords/checked.md) — umożliwia przepełnienie sprawdzania pod kątem operacji liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="23178-123">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="23178-124">[unchecked](../keywords/unchecked.md) — wyłącza przepełnienie sprawdzania pod kątem operacji liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="23178-124">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="23178-125">Jest to domyślne zachowanie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="23178-125">This is the default compiler behavior.</span></span>

<span data-ttu-id="23178-126">[wartość Default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) — tworzy domyślną wartość typu T.</span><span class="sxs-lookup"><span data-stu-id="23178-126">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produces the default value of type T.</span></span>

<span data-ttu-id="23178-127">[Delegowanie](../../programming-guide/statements-expressions-operators/anonymous-methods.md) — deklaruje i zwraca wystąpienie delegata.</span><span class="sxs-lookup"><span data-stu-id="23178-127">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="23178-128">[Operator sizeof](../keywords/sizeof.md) — zwraca rozmiar w bajtach argument typu.</span><span class="sxs-lookup"><span data-stu-id="23178-128">[sizeof](../keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="23178-129">[->](dereference-operator.md) — wyłuskanie wskaźnika w połączeniu z dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="23178-129">[->](dereference-operator.md) – pointer dereferencing combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="23178-130">Operatory jednoargumentowe</span><span class="sxs-lookup"><span data-stu-id="23178-130">Unary operators</span></span>

<span data-ttu-id="23178-131">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="23178-131">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="23178-132">[+ x](addition-operator.md) — zwraca wartość x.</span><span class="sxs-lookup"><span data-stu-id="23178-132">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="23178-133">[-x](subtraction-operator.md) — negacji liczbowych.</span><span class="sxs-lookup"><span data-stu-id="23178-133">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="23178-134">[\!x](logical-negation-operator.md) — negacji logicznej.</span><span class="sxs-lookup"><span data-stu-id="23178-134">[\!x](logical-negation-operator.md) – logical negation.</span></span>

<span data-ttu-id="23178-135">[~ x](bitwise-complement-operator.md) — uzupełnienie bitowe.</span><span class="sxs-lookup"><span data-stu-id="23178-135">[~x](bitwise-complement-operator.md) – bitwise complement.</span></span>

<span data-ttu-id="23178-136">[++ x](arithmetic-operators.md#increment-operator-) — przedrostkowe.</span><span class="sxs-lookup"><span data-stu-id="23178-136">[++x](arithmetic-operators.md#increment-operator-) – prefix increment.</span></span> <span data-ttu-id="23178-137">Zwraca wartość x po zaktualizowaniu lokalizacji magazynu z wartością x, który jest jednym większą (zazwyczaj dodaje liczbę całkowitą 1).</span><span class="sxs-lookup"><span data-stu-id="23178-137">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="23178-138">[--x](arithmetic-operators.md#decrement-operator---) — przedrostkowe.</span><span class="sxs-lookup"><span data-stu-id="23178-138">[--x](arithmetic-operators.md#decrement-operator---) – prefix decrement.</span></span> <span data-ttu-id="23178-139">Zwraca wartość x po zaktualizowaniu lokalizacji magazynu o wartości x, która jest mniejsza (zazwyczaj odejmuje liczbę całkowitą 1).</span><span class="sxs-lookup"><span data-stu-id="23178-139">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="23178-140">[(T) x](invocation-operator.md) — typ rzutowania.</span><span class="sxs-lookup"><span data-stu-id="23178-140">[(T)x](invocation-operator.md) – type casting.</span></span>

<span data-ttu-id="23178-141">[await](../keywords/await.md) — czeka `Task`.</span><span class="sxs-lookup"><span data-stu-id="23178-141">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="23178-142">[& x](and-operator.md) — adres.</span><span class="sxs-lookup"><span data-stu-id="23178-142">[&x](and-operator.md) – address of.</span></span>

<span data-ttu-id="23178-143">[\* x](multiplication-operator.md) — dereferencji.</span><span class="sxs-lookup"><span data-stu-id="23178-143">[\*x](multiplication-operator.md) – dereferencing.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="23178-144">Operatory multiplikatywne</span><span class="sxs-lookup"><span data-stu-id="23178-144">Multiplicative operators</span></span>

<span data-ttu-id="23178-145">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="23178-145">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="23178-146">[x \* y](arithmetic-operators.md#multiplication-operator-) — mnożenia.</span><span class="sxs-lookup"><span data-stu-id="23178-146">[x \* y](arithmetic-operators.md#multiplication-operator-) – multiplication.</span></span>

<span data-ttu-id="23178-147">[x / y](arithmetic-operators.md#division-operator-) — dzielenia.</span><span class="sxs-lookup"><span data-stu-id="23178-147">[x / y](arithmetic-operators.md#division-operator-) – division.</span></span> <span data-ttu-id="23178-148">Jeśli argumenty są liczbami całkowitymi, wynik jest liczbą całkowitą obcięte w kierunku zera (na przykład `-7 / 2 is -3`).</span><span class="sxs-lookup"><span data-stu-id="23178-148">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="23178-149">[x, % y](arithmetic-operators.md#remainder-operator-) — resztę.</span><span class="sxs-lookup"><span data-stu-id="23178-149">[x % y](arithmetic-operators.md#remainder-operator-) – remainder.</span></span> <span data-ttu-id="23178-150">Jeśli argumenty są liczbami całkowitymi, to zwraca resztę z dzielenia podziału x, y.</span><span class="sxs-lookup"><span data-stu-id="23178-150">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="23178-151">Jeśli `q = x / y` i `r = x % y`, następnie `x = q * y + r`.</span><span class="sxs-lookup"><span data-stu-id="23178-151">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="23178-152">Operatory addytywne</span><span class="sxs-lookup"><span data-stu-id="23178-152">Additive operators</span></span>

<span data-ttu-id="23178-153">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="23178-153">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="23178-154">[x + y](arithmetic-operators.md#addition-operator-) — Dodawanie.</span><span class="sxs-lookup"><span data-stu-id="23178-154">[x + y](arithmetic-operators.md#addition-operator-) – addition.</span></span>

<span data-ttu-id="23178-155">[x – y](arithmetic-operators.md#subtraction-operator--) — odejmowania.</span><span class="sxs-lookup"><span data-stu-id="23178-155">[x – y](arithmetic-operators.md#subtraction-operator--) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="23178-156">Operatory przesunięcia</span><span class="sxs-lookup"><span data-stu-id="23178-156">Shift operators</span></span>

<span data-ttu-id="23178-157">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="23178-157">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="23178-158">[x <\< y](left-shift-operator.md) — przesunięcia bitów w lewo i wypełnić zero po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="23178-158">[x <\<  y](left-shift-operator.md) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="23178-159">[x >> y](right-shift-operator.md) — shift bits po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="23178-159">[x >> y](right-shift-operator.md) – shift bits right.</span></span> <span data-ttu-id="23178-160">Jeśli Lewy argument operacji jest `int` lub `long`, a następnie po lewej stronie bity są wypełnione bitu znaku.</span><span class="sxs-lookup"><span data-stu-id="23178-160">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="23178-161">Jeśli Lewy argument operacji jest `uint` lub `ulong`, a następnie po lewej stronie bity są wypełnione zero.</span><span class="sxs-lookup"><span data-stu-id="23178-161">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="23178-162">Operatory relacyjne i badania typu</span><span class="sxs-lookup"><span data-stu-id="23178-162">Relational and type-testing operators</span></span>

<span data-ttu-id="23178-163">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="23178-163">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="23178-164">[x \< y](less-than-operator.md) — mniejsze niż (wartość true, jeśli x jest mniejsza niż y).</span><span class="sxs-lookup"><span data-stu-id="23178-164">[x \< y](less-than-operator.md) – less than (true if x is less than y).</span></span>

<span data-ttu-id="23178-165">[x > y](greater-than-operator.md) — większa (wartość true, jeśli x jest większa niż y).</span><span class="sxs-lookup"><span data-stu-id="23178-165">[x > y](greater-than-operator.md) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="23178-166">[x \<= y](less-than-equal-operator.md) — mniejsze niż lub równe.</span><span class="sxs-lookup"><span data-stu-id="23178-166">[x \<= y](less-than-equal-operator.md) – less than or equal to.</span></span>

<span data-ttu-id="23178-167">[x > = y](greater-than-equal-operator.md) — większa lub równa.</span><span class="sxs-lookup"><span data-stu-id="23178-167">[x >= y](greater-than-equal-operator.md) – greater than or equal to.</span></span>

<span data-ttu-id="23178-168">[jest](../keywords/is.md) — wpisz zgodności.</span><span class="sxs-lookup"><span data-stu-id="23178-168">[is](../keywords/is.md) – type compatibility.</span></span> <span data-ttu-id="23178-169">Zwraca wartość PRAWDA, jeśli ocenianą lewy operand mogą być rzutowane na typ określony w prawy operand (typu statycznego).</span><span class="sxs-lookup"><span data-stu-id="23178-169">Returns true if the evaluated left operand can be cast to the type specified in the right operand (a static type).</span></span>

<span data-ttu-id="23178-170">[jako](../keywords/as.md) — konwersja typu.</span><span class="sxs-lookup"><span data-stu-id="23178-170">[as](../keywords/as.md) – type conversion.</span></span> <span data-ttu-id="23178-171">Zwraca lewy operand rzutowany na typ określony przez prawy operand (typ statycznej), ale `as` zwraca `null` gdzie `(T)x` spowoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="23178-171">Returns the left operand cast to the type specified by the right operand (a static type), but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="23178-172">Operatory równości</span><span class="sxs-lookup"><span data-stu-id="23178-172">Equality operators</span></span>

<span data-ttu-id="23178-173">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="23178-173">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="23178-174">[x == y](equality-operators.md#equality-operator-) — równości.</span><span class="sxs-lookup"><span data-stu-id="23178-174">[x == y](equality-operators.md#equality-operator-) – equality.</span></span> <span data-ttu-id="23178-175">Domyślnie dla odwołania do typów innych niż `string`ten zwraca odwołania równości (test tożsamości).</span><span class="sxs-lookup"><span data-stu-id="23178-175">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="23178-176">Jednak typów może doprowadzić do przeciążenia `==`, więc jeśli zgodne z zamiarami użytkownika jest, aby sprawdzić tożsamość, najlepiej użyć `ReferenceEquals` metody `object`.</span><span class="sxs-lookup"><span data-stu-id="23178-176">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="23178-177">[x! = y](equality-operators.md#inequality-operator-) — są nierówne.</span><span class="sxs-lookup"><span data-stu-id="23178-177">[x != y](equality-operators.md#inequality-operator-) – not equal.</span></span> <span data-ttu-id="23178-178">Zobacz komentarz dotyczący `==`.</span><span class="sxs-lookup"><span data-stu-id="23178-178">See comment for `==`.</span></span> <span data-ttu-id="23178-179">Jeśli typem przeciążenia `==`, a następnie przeciąża musi `!=`.</span><span class="sxs-lookup"><span data-stu-id="23178-179">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="23178-180">Operator logiczny AND</span><span class="sxs-lookup"><span data-stu-id="23178-180">Logical AND operator</span></span>

<span data-ttu-id="23178-181">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="23178-181">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="23178-182">[x i y](and-operator.md) — operatora logicznego lub bitowego AND.</span><span class="sxs-lookup"><span data-stu-id="23178-182">[x & y](and-operator.md) – logical or bitwise AND.</span></span> <span data-ttu-id="23178-183">Zazwyczaj można użyć tego z typami całkowitymi i `enum` typów.</span><span class="sxs-lookup"><span data-stu-id="23178-183">You can generally use this with integer types and `enum` types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="23178-184">Operatora logicznego XOR</span><span class="sxs-lookup"><span data-stu-id="23178-184">Logical XOR operator</span></span>

<span data-ttu-id="23178-185">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="23178-185">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="23178-186">[x ^ y](xor-operator.md) — logicznych lub bitowe XOR.</span><span class="sxs-lookup"><span data-stu-id="23178-186">[x ^ y](xor-operator.md) – logical or bitwise XOR.</span></span> <span data-ttu-id="23178-187">Zazwyczaj można użyć tego z typami całkowitymi i `enum` typów.</span><span class="sxs-lookup"><span data-stu-id="23178-187">You can generally use this with integer types and `enum` types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="23178-188">Operator logiczny OR</span><span class="sxs-lookup"><span data-stu-id="23178-188">Logical OR operator</span></span>

<span data-ttu-id="23178-189">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="23178-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="23178-190">[x &#124; y](or-operator.md) — logicznych lub bitowe OR.</span><span class="sxs-lookup"><span data-stu-id="23178-190">[x &#124; y](or-operator.md) – logical or bitwise OR.</span></span> <span data-ttu-id="23178-191">Zazwyczaj można użyć tego z typami całkowitymi i `enum` typów.</span><span class="sxs-lookup"><span data-stu-id="23178-191">You can generally use this with integer types and `enum` types.</span></span>

## <a name="conditional-and-operator"></a><span data-ttu-id="23178-192">Operator warunkowy AND</span><span class="sxs-lookup"><span data-stu-id="23178-192">Conditional AND operator</span></span>

<span data-ttu-id="23178-193">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="23178-193">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="23178-194">[x & & y](conditional-and-operator.md) — operatora logicznego AND.</span><span class="sxs-lookup"><span data-stu-id="23178-194">[x && y](conditional-and-operator.md) – logical AND.</span></span> <span data-ttu-id="23178-195">Jeśli pierwszy operand zwróci wartość false, następnie C# nie może oszacować drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="23178-195">If the first operand evaluates to false, then C# does not evaluate the second operand.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="23178-196">Operator warunkowy OR</span><span class="sxs-lookup"><span data-stu-id="23178-196">Conditional OR operator</span></span>

<span data-ttu-id="23178-197">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="23178-197">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="23178-198">[x &#124; &#124; y](conditional-or-operator.md) — operator logiczny lub.</span><span class="sxs-lookup"><span data-stu-id="23178-198">[x &#124;&#124; y](conditional-or-operator.md) – logical OR.</span></span> <span data-ttu-id="23178-199">Jeśli pierwszy argument zwraca wartość true, następnie C# nie może oszacować drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="23178-199">If the first operand evaluates to true, then C# does not evaluate the second operand.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="23178-200">Operatorem łączenia wartości null</span><span class="sxs-lookup"><span data-stu-id="23178-200">Null-coalescing operator</span></span>

<span data-ttu-id="23178-201">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="23178-201">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="23178-202">[x? y](null-coalescing-operator.md) — zwraca `x` jeśli je ma wartość inną niż`null`; w przeciwnym razie zwraca `y`.</span><span class="sxs-lookup"><span data-stu-id="23178-202">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="23178-203">Operator warunkowy</span><span class="sxs-lookup"><span data-stu-id="23178-203">Conditional operator</span></span>

<span data-ttu-id="23178-204">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="23178-204">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="23178-205">[t? x: y](conditional-operator.md) — w przypadku testowania `t` daje w wyniku wartość true, a następnie oceniana i zwracana `x`; w przeciwnym razie oceniana i zwracana `y`.</span><span class="sxs-lookup"><span data-stu-id="23178-205">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="23178-206">Operatory przypisania i Lambda</span><span class="sxs-lookup"><span data-stu-id="23178-206">Assignment and Lambda operators</span></span>

<span data-ttu-id="23178-207">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="23178-207">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="23178-208">[x = y](assignment-operator.md) — przypisania.</span><span class="sxs-lookup"><span data-stu-id="23178-208">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="23178-209">[x += y](addition-assignment-operator.md) — przyrostu.</span><span class="sxs-lookup"><span data-stu-id="23178-209">[x += y](addition-assignment-operator.md) – increment.</span></span> <span data-ttu-id="23178-210">Dodaj wartość `y` wartość `x`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="23178-210">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="23178-211">Jeśli `x` wyznacza `event`, następnie `y` musi mieć odpowiednią funkcję, dodającego C# jako program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="23178-211">If `x` designates an `event`, then `y` must be an appropriate function that C# adds as an event handler.</span></span>

<span data-ttu-id="23178-212">[x-= y](subtraction-assignment-operator.md) — zmniejszanie.</span><span class="sxs-lookup"><span data-stu-id="23178-212">[x -= y](subtraction-assignment-operator.md) – decrement.</span></span> <span data-ttu-id="23178-213">Odejmuje wartość `y` od wartości `x`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="23178-213">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="23178-214">Jeśli `x` wyznacza `event`, następnie `y` musi mieć odpowiednią funkcję, który C# usuwa jako program obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="23178-214">If `x` designates an `event`, then `y` must be an appropriate function that C# removes as an event handler</span></span>

<span data-ttu-id="23178-215">[x \* = y](multiplication-assignment-operator.md) — mnożenie i przypisanie.</span><span class="sxs-lookup"><span data-stu-id="23178-215">[x \*= y](multiplication-assignment-operator.md) – multiplication assignment.</span></span> <span data-ttu-id="23178-216">Mnoży wartość `y` wartość `x`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="23178-216">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="23178-217">[x / = y](arithmetic-operators.md#compound-assignment) — dzielenie i przypisanie.</span><span class="sxs-lookup"><span data-stu-id="23178-217">[x /= y](arithmetic-operators.md#compound-assignment) – division assignment.</span></span> <span data-ttu-id="23178-218">Dzieli wartość `x` przez wartość `y`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="23178-218">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="23178-219">[x % = y](arithmetic-operators.md#compound-assignment) — remainder przypisania.</span><span class="sxs-lookup"><span data-stu-id="23178-219">[x %= y](arithmetic-operators.md#compound-assignment) – remainder assignment.</span></span> <span data-ttu-id="23178-220">Dzieli wartość `x` przez wartość `y`, przechowywać resztę w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="23178-220">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="23178-221">[x & = y](and-assignment-operator.md) — i przypisanie.</span><span class="sxs-lookup"><span data-stu-id="23178-221">[x &= y](and-assignment-operator.md) – AND assignment.</span></span> <span data-ttu-id="23178-222">I wartość `y` z wartością `x`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="23178-222">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="23178-223">[x &#124;= y](or-assignment-operator.md) — i przypisanie.</span><span class="sxs-lookup"><span data-stu-id="23178-223">[x &#124;= y](or-assignment-operator.md) – OR assignment.</span></span> <span data-ttu-id="23178-224">LUB wartość `y` z wartością `x`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="23178-224">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="23178-225">[x ^ = y](xor-assignment-operator.md) — przypisanie XOR.</span><span class="sxs-lookup"><span data-stu-id="23178-225">[x ^= y](xor-assignment-operator.md) – XOR assignment.</span></span> <span data-ttu-id="23178-226">XOR wartość z `y` z wartością `x`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="23178-226">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="23178-227">[x << = y](left-shift-assignment-operator.md) — przypisania przesunięcia w lewo.</span><span class="sxs-lookup"><span data-stu-id="23178-227">[x <<= y](left-shift-assignment-operator.md) – left-shift assignment.</span></span> <span data-ttu-id="23178-228">Przesuwa wartość `x` po lewej stronie, `y` miejscach, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="23178-228">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="23178-229">[x >> = y](right-shift-assignment-operator.md) — przypisania przesunięcia w prawo.</span><span class="sxs-lookup"><span data-stu-id="23178-229">[x >>= y](right-shift-assignment-operator.md) – right-shift assignment.</span></span> <span data-ttu-id="23178-230">Przesuwa wartość `x` bezpośrednio przez `y` miejscach, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="23178-230">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="23178-231">[=>](lambda-operator.md) — deklaracji lambda.</span><span class="sxs-lookup"><span data-stu-id="23178-231">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="23178-232">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23178-232">See also</span></span>

- [<span data-ttu-id="23178-233">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="23178-233">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="23178-234">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="23178-234">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="23178-235">C#</span><span class="sxs-lookup"><span data-stu-id="23178-235">C#</span></span>](../../index.md)
- [<span data-ttu-id="23178-236">Operatory z możliwością przeciążenia</span><span class="sxs-lookup"><span data-stu-id="23178-236">Overloadable Operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="23178-237">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="23178-237">C# Keywords</span></span>](../keywords/index.md)