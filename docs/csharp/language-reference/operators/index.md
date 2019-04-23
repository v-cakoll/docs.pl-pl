---
title: Operatory języka C#
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
ms.openlocfilehash: f4267caeb6301950b9f6a8b9545a47b9f48e7920
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977382"
---
# <a name="c-operators"></a><span data-ttu-id="1e502-102">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="1e502-102">C# operators</span></span>

<span data-ttu-id="1e502-103">C# zawiera wiele operatorów, które są symbolami określającymi operacje (matematycznych, indeksowanie, wywołanie funkcji itp.) do wykonania w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="1e502-103">C# provides many operators, which are symbols that specify which operations (math, indexing, function call, etc.) to perform in an expression.</span></span> <span data-ttu-id="1e502-104">Możesz [przeciążenia](../../programming-guide/statements-expressions-operators/overloadable-operators.md) wiele operatorów, aby zmienić ich znaczenia w przypadku zastosowania do typu zdefiniowanego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1e502-104">You can [overload](../../programming-guide/statements-expressions-operators/overloadable-operators.md) many operators to change their meaning when applied to a user-defined type.</span></span>

<span data-ttu-id="1e502-105">Operacje na typach całkowitoliczbowych (takie jak `==`, `!=`, `<`, `>`, `&`, `|`) są ogólnie dozwolone w wyliczeniu (`enum`) typy.</span><span class="sxs-lookup"><span data-stu-id="1e502-105">Operations on integral types (such as `==`, `!=`, `<`, `>`, `&`, `|`) are generally allowed on enumeration (`enum`) types.</span></span>

<span data-ttu-id="1e502-106">Poniższe rozdziały zawierają listę operatorów języka C# od o najwyższym priorytecie do najniższego.</span><span class="sxs-lookup"><span data-stu-id="1e502-106">The sections below list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="1e502-107">Operatory w każdej sekcji udostępniać na tym samym poziomie pierwszeństwa.</span><span class="sxs-lookup"><span data-stu-id="1e502-107">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="1e502-108">Operatory podstawowe</span><span class="sxs-lookup"><span data-stu-id="1e502-108">Primary operators</span></span>

<span data-ttu-id="1e502-109">Są to najwyższy pierwszeństwo operatorów.</span><span class="sxs-lookup"><span data-stu-id="1e502-109">These are the highest precedence operators.</span></span>

<span data-ttu-id="1e502-110">[x.y](member-access-operator.md) — dostęp do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1e502-110">[x.y](member-access-operator.md) – member access.</span></span>

<span data-ttu-id="1e502-111">[x? y](null-conditional-operators.md) — wartość null, dostęp warunkowy elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1e502-111">[x?.y](null-conditional-operators.md) – null conditional member access.</span></span> <span data-ttu-id="1e502-112">Zwraca `null` Jeśli po lewej stronie operand ma wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="1e502-112">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="1e502-113">[x? [t] ](null-conditional-operators.md) — wartość null, dostęp warunkowy indeksu.</span><span class="sxs-lookup"><span data-stu-id="1e502-113">[x?[y]](null-conditional-operators.md) - null conditional index access.</span></span> <span data-ttu-id="1e502-114">Zwraca `null` Jeśli po lewej stronie operand ma wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="1e502-114">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="1e502-115">[f(x)](invocation-operator.md) — wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="1e502-115">[f(x)](invocation-operator.md) – function invocation.</span></span>

<span data-ttu-id="1e502-116">[&#91;x&#93; ](index-operator.md) — indeksowanie obiektu agregacji.</span><span class="sxs-lookup"><span data-stu-id="1e502-116">[a&#91;x&#93;](index-operator.md) – aggregate object indexing.</span></span>

<span data-ttu-id="1e502-117">[x ++](arithmetic-operators.md#increment-operator-) — zwiększenie przyrostkowe.</span><span class="sxs-lookup"><span data-stu-id="1e502-117">[x++](arithmetic-operators.md#increment-operator-) – postfix increment.</span></span> <span data-ttu-id="1e502-118">Zwraca wartość x, a następnie aktualizuje lokalizację przechowywania z wartością x, która jest większa o jeden (zazwyczaj dodaje liczbę całkowitą 1).</span><span class="sxs-lookup"><span data-stu-id="1e502-118">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="1e502-119">[x —](arithmetic-operators.md#decrement-operator---) — zmniejszenie przyrostkowe.</span><span class="sxs-lookup"><span data-stu-id="1e502-119">[x--](arithmetic-operators.md#decrement-operator---) –  postfix decrement.</span></span> <span data-ttu-id="1e502-120">Zwraca wartość x, a następnie aktualizuje lokalizację przechowywania z wartością x, która jest mniejsza (zazwyczaj odejmuje liczbę całkowitą 1).</span><span class="sxs-lookup"><span data-stu-id="1e502-120">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="1e502-121">[nowe](../keywords/new-operator.md) — podczas tworzenia wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="1e502-121">[new](../keywords/new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="1e502-122">[TypeOf](../keywords/typeof.md) — zwraca <xref:System.Type> obiekt reprezentujący argument.</span><span class="sxs-lookup"><span data-stu-id="1e502-122">[typeof](../keywords/typeof.md) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="1e502-123">[zaznaczone](../keywords/checked.md) — umożliwia przepełnienie sprawdzania pod kątem operacji liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="1e502-123">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="1e502-124">[unchecked](../keywords/unchecked.md) — wyłącza przepełnienie sprawdzania pod kątem operacji liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="1e502-124">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="1e502-125">Jest to domyślne zachowanie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="1e502-125">This is the default compiler behavior.</span></span>

<span data-ttu-id="1e502-126">[wartość Default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) — tworzy domyślną wartość typu T.</span><span class="sxs-lookup"><span data-stu-id="1e502-126">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produces the default value of type T.</span></span>

<span data-ttu-id="1e502-127">[Delegowanie](../../programming-guide/statements-expressions-operators/anonymous-methods.md) — deklaruje i zwraca wystąpienie delegata.</span><span class="sxs-lookup"><span data-stu-id="1e502-127">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="1e502-128">[Operator sizeof](../keywords/sizeof.md) — zwraca rozmiar w bajtach argument typu.</span><span class="sxs-lookup"><span data-stu-id="1e502-128">[sizeof](../keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="1e502-129">[->](dereference-operator.md) — wyłuskanie wskaźnika w połączeniu z dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1e502-129">[->](dereference-operator.md) – pointer dereferencing combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="1e502-130">Operatory jednoargumentowe</span><span class="sxs-lookup"><span data-stu-id="1e502-130">Unary operators</span></span>

<span data-ttu-id="1e502-131">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1e502-131">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1e502-132">[+ x](addition-operator.md) — zwraca wartość x.</span><span class="sxs-lookup"><span data-stu-id="1e502-132">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="1e502-133">[-x](subtraction-operator.md) — negacji liczbowych.</span><span class="sxs-lookup"><span data-stu-id="1e502-133">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="1e502-134">[\!x](boolean-logical-operators.md#logical-negation-operator-) — negacji logicznej.</span><span class="sxs-lookup"><span data-stu-id="1e502-134">[\!x](boolean-logical-operators.md#logical-negation-operator-) – logical negation.</span></span>

<span data-ttu-id="1e502-135">[~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-) — uzupełnienie bitowe.</span><span class="sxs-lookup"><span data-stu-id="1e502-135">[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bitwise complement.</span></span>

<span data-ttu-id="1e502-136">[++ x](arithmetic-operators.md#increment-operator-) — przedrostkowe.</span><span class="sxs-lookup"><span data-stu-id="1e502-136">[++x](arithmetic-operators.md#increment-operator-) – prefix increment.</span></span> <span data-ttu-id="1e502-137">Zwraca wartość x po zaktualizowaniu lokalizacji magazynu z wartością x, który jest jednym większą (zazwyczaj dodaje liczbę całkowitą 1).</span><span class="sxs-lookup"><span data-stu-id="1e502-137">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="1e502-138">[--x](arithmetic-operators.md#decrement-operator---) — przedrostkowe.</span><span class="sxs-lookup"><span data-stu-id="1e502-138">[--x](arithmetic-operators.md#decrement-operator---) – prefix decrement.</span></span> <span data-ttu-id="1e502-139">Zwraca wartość x po zaktualizowaniu lokalizacji magazynu o wartości x, która jest mniejsza (zazwyczaj odejmuje liczbę całkowitą 1).</span><span class="sxs-lookup"><span data-stu-id="1e502-139">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="1e502-140">[(T) x](invocation-operator.md) — typ rzutowania.</span><span class="sxs-lookup"><span data-stu-id="1e502-140">[(T)x](invocation-operator.md) – type casting.</span></span>

<span data-ttu-id="1e502-141">[await](../keywords/await.md) — czeka `Task`.</span><span class="sxs-lookup"><span data-stu-id="1e502-141">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="1e502-142">[& x](and-operator.md) — adres.</span><span class="sxs-lookup"><span data-stu-id="1e502-142">[&x](and-operator.md) – address of.</span></span>

<span data-ttu-id="1e502-143">[\* x](multiplication-operator.md) — dereferencji.</span><span class="sxs-lookup"><span data-stu-id="1e502-143">[\*x](multiplication-operator.md) – dereferencing.</span></span>

<span data-ttu-id="1e502-144">[TRUE — operator](../keywords/true-false-operators.md) — zwraca [bool](../keywords/bool.md) wartość `true` do wskazania, że argument jest zdecydowanie true.</span><span class="sxs-lookup"><span data-stu-id="1e502-144">[true operator](../keywords/true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely true.</span></span>

<span data-ttu-id="1e502-145">[FALSE — operator](../keywords/true-false-operators.md) — zwraca [bool](../keywords/bool.md) wartość `true` do wskazania, że argument jest zdecydowanie false.</span><span class="sxs-lookup"><span data-stu-id="1e502-145">[false operator](../keywords/true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely false.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="1e502-146">Operatory multiplikatywne</span><span class="sxs-lookup"><span data-stu-id="1e502-146">Multiplicative operators</span></span>

<span data-ttu-id="1e502-147">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1e502-147">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1e502-148">[x \* y](arithmetic-operators.md#multiplication-operator-) — mnożenia.</span><span class="sxs-lookup"><span data-stu-id="1e502-148">[x \* y](arithmetic-operators.md#multiplication-operator-) – multiplication.</span></span>

<span data-ttu-id="1e502-149">[x / y](arithmetic-operators.md#division-operator-) — dzielenia.</span><span class="sxs-lookup"><span data-stu-id="1e502-149">[x / y](arithmetic-operators.md#division-operator-) – division.</span></span> <span data-ttu-id="1e502-150">Jeśli argumenty są liczbami całkowitymi, wynik jest liczbą całkowitą obcięte w kierunku zera (na przykład `-7 / 2 is -3`).</span><span class="sxs-lookup"><span data-stu-id="1e502-150">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="1e502-151">[x, % y](arithmetic-operators.md#remainder-operator-) — resztę.</span><span class="sxs-lookup"><span data-stu-id="1e502-151">[x % y](arithmetic-operators.md#remainder-operator-) – remainder.</span></span> <span data-ttu-id="1e502-152">Jeśli argumenty są liczbami całkowitymi, to zwraca resztę z dzielenia podziału x, y.</span><span class="sxs-lookup"><span data-stu-id="1e502-152">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="1e502-153">Jeśli `q = x / y` i `r = x % y`, następnie `x = q * y + r`.</span><span class="sxs-lookup"><span data-stu-id="1e502-153">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="1e502-154">Operatory addytywne</span><span class="sxs-lookup"><span data-stu-id="1e502-154">Additive operators</span></span>

<span data-ttu-id="1e502-155">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1e502-155">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1e502-156">[x + y](arithmetic-operators.md#addition-operator-) — Dodawanie.</span><span class="sxs-lookup"><span data-stu-id="1e502-156">[x + y](arithmetic-operators.md#addition-operator-) – addition.</span></span>

<span data-ttu-id="1e502-157">[x – y](arithmetic-operators.md#subtraction-operator--) — odejmowania.</span><span class="sxs-lookup"><span data-stu-id="1e502-157">[x – y](arithmetic-operators.md#subtraction-operator--) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="1e502-158">Operatory przesunięcia</span><span class="sxs-lookup"><span data-stu-id="1e502-158">Shift operators</span></span>

<span data-ttu-id="1e502-159">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1e502-159">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1e502-160">[x <\< y](bitwise-and-shift-operators.md#left-shift-operator-) — przesunięcia bitów w lewo i wypełnić zero po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="1e502-160">[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="1e502-161">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) — shift bits po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="1e502-161">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – shift bits right.</span></span> <span data-ttu-id="1e502-162">Jeśli Lewy argument operacji jest `int` lub `long`, a następnie po lewej stronie bity są wypełnione bitu znaku.</span><span class="sxs-lookup"><span data-stu-id="1e502-162">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="1e502-163">Jeśli Lewy argument operacji jest `uint` lub `ulong`, a następnie po lewej stronie bity są wypełnione zero.</span><span class="sxs-lookup"><span data-stu-id="1e502-163">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="1e502-164">Operatory relacyjne i badania typu</span><span class="sxs-lookup"><span data-stu-id="1e502-164">Relational and type-testing operators</span></span>

<span data-ttu-id="1e502-165">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1e502-165">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1e502-166">[x \< y](less-than-operator.md) — mniejsze niż (wartość true, jeśli x jest mniejsza niż y).</span><span class="sxs-lookup"><span data-stu-id="1e502-166">[x \< y](less-than-operator.md) – less than (true if x is less than y).</span></span>

<span data-ttu-id="1e502-167">[x > y](greater-than-operator.md) — większa (wartość true, jeśli x jest większa niż y).</span><span class="sxs-lookup"><span data-stu-id="1e502-167">[x > y](greater-than-operator.md) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="1e502-168">[x \<= y](less-than-equal-operator.md) — mniejsze niż lub równe.</span><span class="sxs-lookup"><span data-stu-id="1e502-168">[x \<= y](less-than-equal-operator.md) – less than or equal to.</span></span>

<span data-ttu-id="1e502-169">[x > = y](greater-than-equal-operator.md) — większa lub równa.</span><span class="sxs-lookup"><span data-stu-id="1e502-169">[x >= y](greater-than-equal-operator.md) – greater than or equal to.</span></span>

<span data-ttu-id="1e502-170">[jest](../keywords/is.md) — wpisz zgodności.</span><span class="sxs-lookup"><span data-stu-id="1e502-170">[is](../keywords/is.md) – type compatibility.</span></span> <span data-ttu-id="1e502-171">Zwraca wartość PRAWDA, jeśli ocenianą lewy operand mogą być rzutowane na typ określony w prawy operand (typu statycznego).</span><span class="sxs-lookup"><span data-stu-id="1e502-171">Returns true if the evaluated left operand can be cast to the type specified in the right operand (a static type).</span></span>

<span data-ttu-id="1e502-172">[jako](../keywords/as.md) — konwersja typu.</span><span class="sxs-lookup"><span data-stu-id="1e502-172">[as](../keywords/as.md) – type conversion.</span></span> <span data-ttu-id="1e502-173">Zwraca lewy operand rzutowany na typ określony przez prawy operand (typ statycznej), ale `as` zwraca `null` gdzie `(T)x` spowoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="1e502-173">Returns the left operand cast to the type specified by the right operand (a static type), but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="1e502-174">Operatory równości</span><span class="sxs-lookup"><span data-stu-id="1e502-174">Equality operators</span></span>

<span data-ttu-id="1e502-175">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1e502-175">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1e502-176">[x == y](equality-operators.md#equality-operator-) — równości.</span><span class="sxs-lookup"><span data-stu-id="1e502-176">[x == y](equality-operators.md#equality-operator-) – equality.</span></span> <span data-ttu-id="1e502-177">Domyślnie dla odwołania do typów innych niż `string`ten zwraca odwołania równości (test tożsamości).</span><span class="sxs-lookup"><span data-stu-id="1e502-177">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="1e502-178">Jednak typów może doprowadzić do przeciążenia `==`, więc jeśli zgodne z zamiarami użytkownika jest, aby sprawdzić tożsamość, najlepiej użyć `ReferenceEquals` metody `object`.</span><span class="sxs-lookup"><span data-stu-id="1e502-178">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="1e502-179">[x! = y](equality-operators.md#inequality-operator-) — są nierówne.</span><span class="sxs-lookup"><span data-stu-id="1e502-179">[x != y](equality-operators.md#inequality-operator-) – not equal.</span></span> <span data-ttu-id="1e502-180">Zobacz komentarz dotyczący `==`.</span><span class="sxs-lookup"><span data-stu-id="1e502-180">See comment for `==`.</span></span> <span data-ttu-id="1e502-181">Jeśli typem przeciążenia `==`, a następnie przeciąża musi `!=`.</span><span class="sxs-lookup"><span data-stu-id="1e502-181">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="1e502-182">Operator logiczny AND</span><span class="sxs-lookup"><span data-stu-id="1e502-182">Logical AND operator</span></span>

<span data-ttu-id="1e502-183">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1e502-183">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1e502-184">`x & y` — [operator logiczny oraz](boolean-logical-operators.md#logical-and-operator-) dla `bool` operandy lub [iloczynu bitowego AND logiczne](bitwise-and-shift-operators.md#logical-and-operator-) przypadku argumentów operacji typu całkowitoliczbowego.</span><span class="sxs-lookup"><span data-stu-id="1e502-184">`x & y` – [logical AND](boolean-logical-operators.md#logical-and-operator-) for the `bool` operands or [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) for the operands of the integral types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="1e502-185">Operatora logicznego XOR</span><span class="sxs-lookup"><span data-stu-id="1e502-185">Logical XOR operator</span></span>

<span data-ttu-id="1e502-186">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1e502-186">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1e502-187">`x ^ y` — [XOR logiczne](boolean-logical-operators.md#logical-exclusive-or-operator-) dla `bool` operandy lub [iloczynu bitowego XOR logiczne](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) przypadku argumentów operacji typu całkowitoliczbowego.</span><span class="sxs-lookup"><span data-stu-id="1e502-187">`x ^ y` – [logical XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) for the `bool` operands or [bitwise logical XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) for the operands of the integral types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="1e502-188">Operator logiczny OR</span><span class="sxs-lookup"><span data-stu-id="1e502-188">Logical OR operator</span></span>

<span data-ttu-id="1e502-189">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1e502-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1e502-190">`x | y` — [logiczne OR](boolean-logical-operators.md#logical-or-operator-) dla `bool` operandy lub [bitowe OR logiczne](bitwise-and-shift-operators.md#logical-or-operator-) przypadku argumentów operacji typu całkowitoliczbowego.</span><span class="sxs-lookup"><span data-stu-id="1e502-190">`x | y` – [logical OR](boolean-logical-operators.md#logical-or-operator-) for the `bool` operands or [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) for the operands of the integral types.</span></span>

## <a name="conditional-and-operator"></a><span data-ttu-id="1e502-191">Operator warunkowy AND</span><span class="sxs-lookup"><span data-stu-id="1e502-191">Conditional AND operator</span></span>

<span data-ttu-id="1e502-192">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1e502-192">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1e502-193">[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) — operatora logicznego AND.</span><span class="sxs-lookup"><span data-stu-id="1e502-193">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – logical AND.</span></span> <span data-ttu-id="1e502-194">Jeśli pierwszy operand zwróci wartość false, następnie C# nie może oszacować drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="1e502-194">If the first operand evaluates to false, then C# does not evaluate the second operand.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="1e502-195">Operator warunkowy OR</span><span class="sxs-lookup"><span data-stu-id="1e502-195">Conditional OR operator</span></span>

<span data-ttu-id="1e502-196">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1e502-196">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1e502-197">[x &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) — operator logiczny lub.</span><span class="sxs-lookup"><span data-stu-id="1e502-197">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logical OR.</span></span> <span data-ttu-id="1e502-198">Jeśli pierwszy argument zwraca wartość true, następnie C# nie może oszacować drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="1e502-198">If the first operand evaluates to true, then C# does not evaluate the second operand.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="1e502-199">Operatorem łączenia wartości null</span><span class="sxs-lookup"><span data-stu-id="1e502-199">Null-coalescing operator</span></span>

<span data-ttu-id="1e502-200">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1e502-200">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1e502-201">[x? y](null-coalescing-operator.md) — zwraca `x` jeśli je ma wartość inną niż`null`; w przeciwnym razie zwraca `y`.</span><span class="sxs-lookup"><span data-stu-id="1e502-201">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="1e502-202">Operator warunkowy</span><span class="sxs-lookup"><span data-stu-id="1e502-202">Conditional operator</span></span>

<span data-ttu-id="1e502-203">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1e502-203">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1e502-204">[t? x: y](conditional-operator.md) — w przypadku testowania `t` daje w wyniku wartość true, a następnie oceniana i zwracana `x`; w przeciwnym razie oceniana i zwracana `y`.</span><span class="sxs-lookup"><span data-stu-id="1e502-204">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="1e502-205">Operatory przypisania i Lambda</span><span class="sxs-lookup"><span data-stu-id="1e502-205">Assignment and Lambda operators</span></span>

<span data-ttu-id="1e502-206">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1e502-206">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="1e502-207">[x = y](assignment-operator.md) — przypisania.</span><span class="sxs-lookup"><span data-stu-id="1e502-207">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="1e502-208">[x += y](addition-assignment-operator.md) — przyrostu.</span><span class="sxs-lookup"><span data-stu-id="1e502-208">[x += y](addition-assignment-operator.md) – increment.</span></span> <span data-ttu-id="1e502-209">Dodaj wartość `y` wartość `x`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="1e502-209">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="1e502-210">Jeśli `x` wyznacza `event`, następnie `y` musi mieć odpowiednią funkcję, dodającego C# jako program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1e502-210">If `x` designates an `event`, then `y` must be an appropriate function that C# adds as an event handler.</span></span>

<span data-ttu-id="1e502-211">[x-= y](subtraction-assignment-operator.md) — zmniejszanie.</span><span class="sxs-lookup"><span data-stu-id="1e502-211">[x -= y](subtraction-assignment-operator.md) – decrement.</span></span> <span data-ttu-id="1e502-212">Odejmuje wartość `y` od wartości `x`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="1e502-212">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="1e502-213">Jeśli `x` wyznacza `event`, następnie `y` musi mieć odpowiednią funkcję C# usuwa jako program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1e502-213">If `x` designates an `event`, then `y` must be an appropriate function that C# removes as an event handler.</span></span>

<span data-ttu-id="1e502-214">[x \* = y](arithmetic-operators.md#compound-assignment) — mnożenie i przypisanie.</span><span class="sxs-lookup"><span data-stu-id="1e502-214">[x \*= y](arithmetic-operators.md#compound-assignment) – multiplication assignment.</span></span> <span data-ttu-id="1e502-215">Mnoży wartość `y` wartość `x`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="1e502-215">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1e502-216">[x / = y](arithmetic-operators.md#compound-assignment) — dzielenie i przypisanie.</span><span class="sxs-lookup"><span data-stu-id="1e502-216">[x /= y](arithmetic-operators.md#compound-assignment) – division assignment.</span></span> <span data-ttu-id="1e502-217">Dzieli wartość `x` przez wartość `y`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="1e502-217">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1e502-218">[x % = y](arithmetic-operators.md#compound-assignment) — remainder przypisania.</span><span class="sxs-lookup"><span data-stu-id="1e502-218">[x %= y](arithmetic-operators.md#compound-assignment) – remainder assignment.</span></span> <span data-ttu-id="1e502-219">Dzieli wartość `x` przez wartość `y`, przechowywać resztę w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="1e502-219">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="1e502-220">[x & = y](boolean-logical-operators.md#compound-assignment) — i przypisanie.</span><span class="sxs-lookup"><span data-stu-id="1e502-220">[x &= y](boolean-logical-operators.md#compound-assignment) – AND assignment.</span></span> <span data-ttu-id="1e502-221">I wartość `y` z wartością `x`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="1e502-221">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1e502-222">[x &#124;= y](boolean-logical-operators.md#compound-assignment) — i przypisanie.</span><span class="sxs-lookup"><span data-stu-id="1e502-222">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – OR assignment.</span></span> <span data-ttu-id="1e502-223">LUB wartość `y` z wartością `x`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="1e502-223">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1e502-224">[x ^ = y](boolean-logical-operators.md#compound-assignment) — przypisanie XOR.</span><span class="sxs-lookup"><span data-stu-id="1e502-224">[x ^= y](boolean-logical-operators.md#compound-assignment) – XOR assignment.</span></span> <span data-ttu-id="1e502-225">XOR wartość z `y` z wartością `x`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="1e502-225">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1e502-226">[x << = y](bitwise-and-shift-operators.md#compound-assignment) — przypisania przesunięcia w lewo.</span><span class="sxs-lookup"><span data-stu-id="1e502-226">[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – left-shift assignment.</span></span> <span data-ttu-id="1e502-227">Przesuwa wartość `x` po lewej stronie, `y` miejscach, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="1e502-227">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1e502-228">[x >> = y](bitwise-and-shift-operators.md#compound-assignment) — przypisania przesunięcia w prawo.</span><span class="sxs-lookup"><span data-stu-id="1e502-228">[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – right-shift assignment.</span></span> <span data-ttu-id="1e502-229">Przesuwa wartość `x` bezpośrednio przez `y` miejscach, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="1e502-229">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="1e502-230">[=>](lambda-operator.md) — deklaracji lambda.</span><span class="sxs-lookup"><span data-stu-id="1e502-230">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e502-231">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e502-231">See also</span></span>

- [<span data-ttu-id="1e502-232">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1e502-232">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1e502-233">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1e502-233">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1e502-234">C#</span><span class="sxs-lookup"><span data-stu-id="1e502-234">C#</span></span>](../../index.md)
- [<span data-ttu-id="1e502-235">Operatory z możliwością przeciążenia</span><span class="sxs-lookup"><span data-stu-id="1e502-235">Overloadable operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="1e502-236">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="1e502-236">C# Keywords</span></span>](../keywords/index.md)
