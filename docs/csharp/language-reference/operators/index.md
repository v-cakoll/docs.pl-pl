---
title: Operatory języka C#
ms.date: 04/30/2019
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
ms.openlocfilehash: 07ef96862c04b8245d8365c3d3b419d227e824c4
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876950"
---
# <a name="c-operators"></a><span data-ttu-id="48fdb-102">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="48fdb-102">C# operators</span></span>

<span data-ttu-id="48fdb-103">C#zawiera szereg wstępnie zdefiniowanych operatory obsługiwane przez typy wbudowane.</span><span class="sxs-lookup"><span data-stu-id="48fdb-103">C# provides a number of predefined operators supported by the built-in types.</span></span> <span data-ttu-id="48fdb-104">Na przykład [operatorów arytmetycznych](arithmetic-operators.md) wykonywać operacji arytmetycznych na wartościach operandy wbudowanych typów liczbowych i [logiczna operatorów logicznych](boolean-logical-operators.md) wykonywać operacje logiczne z [bool ](../keywords/bool.md) argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="48fdb-104">For example, [arithmetic operators](arithmetic-operators.md) perform arithmetic operations with operands of built-in numeric types and [Boolean logical operators](boolean-logical-operators.md) perform logical operations with the [bool](../keywords/bool.md) operands.</span></span>

<span data-ttu-id="48fdb-105">Typ zdefiniowany przez użytkownika może doprowadzić do przeciążenia operatorów, aby zdefiniować odpowiednie zachowanie w przypadku argumentów operacji typu.</span><span class="sxs-lookup"><span data-stu-id="48fdb-105">A user-defined type can overload certain operators to define the corresponding behavior for the operands of that type.</span></span> <span data-ttu-id="48fdb-106">Aby uzyskać więcej informacji, zobacz [operator](../keywords/operator.md) artykułu — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="48fdb-106">For more information, see the [operator](../keywords/operator.md) keyword article.</span></span>

<span data-ttu-id="48fdb-107">Na poniższej liście sekcje C# operatorów, począwszy od najniższej najwyższy priorytet.</span><span class="sxs-lookup"><span data-stu-id="48fdb-107">The following sections list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="48fdb-108">Operatory w każdej sekcji udostępniać na tym samym poziomie pierwszeństwa.</span><span class="sxs-lookup"><span data-stu-id="48fdb-108">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="48fdb-109">Operatory podstawowe</span><span class="sxs-lookup"><span data-stu-id="48fdb-109">Primary operators</span></span>

<span data-ttu-id="48fdb-110">Są to najwyższy pierwszeństwo operatorów.</span><span class="sxs-lookup"><span data-stu-id="48fdb-110">These are the highest precedence operators.</span></span>

<span data-ttu-id="48fdb-111">[x.y](member-access-operators.md#member-access-operator-) — dostęp do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="48fdb-111">[x.y](member-access-operators.md#member-access-operator-) – member access.</span></span>

<span data-ttu-id="48fdb-112">[x? y](member-access-operators.md#null-conditional-operators--and-) — wartość null, dostęp warunkowy elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="48fdb-112">[x?.y](member-access-operators.md#null-conditional-operators--and-) – null conditional member access.</span></span> <span data-ttu-id="48fdb-113">Zwraca `null` Jeśli po lewej stronie operand ma wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="48fdb-113">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="48fdb-114">[x? [t] ](member-access-operators.md#null-conditional-operators--and-) — wartość null elementu tablicy warunkowego lub wpisz dostęp indeksatora.</span><span class="sxs-lookup"><span data-stu-id="48fdb-114">[x?[y]](member-access-operators.md#null-conditional-operators--and-) - null conditional array element or type indexer access.</span></span> <span data-ttu-id="48fdb-115">Zwraca `null` Jeśli po lewej stronie operand ma wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="48fdb-115">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="48fdb-116">[f(x)](member-access-operators.md#invocation-operator-) — metody wywołania lub delegować wywołania.</span><span class="sxs-lookup"><span data-stu-id="48fdb-116">[f(x)](member-access-operators.md#invocation-operator-) – method call or delegate invocation.</span></span>

<span data-ttu-id="48fdb-117">[&#91;x&#93; ](member-access-operators.md#indexer-operator-) — element w tablicy, lub wpisz dostęp indeksatora.</span><span class="sxs-lookup"><span data-stu-id="48fdb-117">[a&#91;x&#93;](member-access-operators.md#indexer-operator-) – array element or type indexer access.</span></span>

<span data-ttu-id="48fdb-118">[x ++](arithmetic-operators.md#increment-operator-) — zwiększenie przyrostkowe.</span><span class="sxs-lookup"><span data-stu-id="48fdb-118">[x++](arithmetic-operators.md#increment-operator-) – postfix increment.</span></span> <span data-ttu-id="48fdb-119">Zwraca wartość x, a następnie aktualizuje lokalizację przechowywania z wartością x, która jest większa o jeden (zazwyczaj dodaje liczbę całkowitą 1).</span><span class="sxs-lookup"><span data-stu-id="48fdb-119">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="48fdb-120">[x —](arithmetic-operators.md#decrement-operator---) — zmniejszenie przyrostkowe.</span><span class="sxs-lookup"><span data-stu-id="48fdb-120">[x--](arithmetic-operators.md#decrement-operator---) –  postfix decrement.</span></span> <span data-ttu-id="48fdb-121">Zwraca wartość x, a następnie aktualizuje lokalizację przechowywania z wartością x, która jest mniejsza (zazwyczaj odejmuje liczbę całkowitą 1).</span><span class="sxs-lookup"><span data-stu-id="48fdb-121">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="48fdb-122">[nowe](../keywords/new-operator.md) — podczas tworzenia wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="48fdb-122">[new](../keywords/new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="48fdb-123">[TypeOf](../keywords/typeof.md) — zwraca <xref:System.Type> obiekt reprezentujący argument.</span><span class="sxs-lookup"><span data-stu-id="48fdb-123">[typeof](../keywords/typeof.md) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="48fdb-124">[zaznaczone](../keywords/checked.md) — umożliwia przepełnienie sprawdzania pod kątem operacji liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="48fdb-124">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="48fdb-125">[unchecked](../keywords/unchecked.md) — wyłącza przepełnienie sprawdzania pod kątem operacji liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="48fdb-125">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="48fdb-126">Jest to domyślne zachowanie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="48fdb-126">This is the default compiler behavior.</span></span>

<span data-ttu-id="48fdb-127">[wartość Default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) — tworzy domyślną wartość typu T.</span><span class="sxs-lookup"><span data-stu-id="48fdb-127">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produces the default value of type T.</span></span>

<span data-ttu-id="48fdb-128">[nameof](../keywords/nameof.md) -uzyskuje proste (niekwalifikowanej) Nazwa zmiennej, typu lub składowej jako ciąg stałej.</span><span class="sxs-lookup"><span data-stu-id="48fdb-128">[nameof](../keywords/nameof.md) - obtains the simple (unqualified) name of a variable, type, or member as a constant string.</span></span>

<span data-ttu-id="48fdb-129">[Delegowanie](../../programming-guide/statements-expressions-operators/anonymous-methods.md) — deklaruje i zwraca wystąpienie delegata.</span><span class="sxs-lookup"><span data-stu-id="48fdb-129">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="48fdb-130">[Operator sizeof](../keywords/sizeof.md) — zwraca rozmiar w bajtach argument typu.</span><span class="sxs-lookup"><span data-stu-id="48fdb-130">[sizeof](../keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="48fdb-131">[stackalloc](../keywords/stackalloc.md) -przydziela blok pamięci na stosie.</span><span class="sxs-lookup"><span data-stu-id="48fdb-131">[stackalloc](../keywords/stackalloc.md) - allocates a block of memory on the stack.</span></span>

<span data-ttu-id="48fdb-132">[->](pointer-related-operators.md#pointer-member-access-operator--) — operację wskaźnika pośredniego w połączeniu z dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="48fdb-132">[->](pointer-related-operators.md#pointer-member-access-operator--) – pointer indirection combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="48fdb-133">Operatory jednoargumentowe</span><span class="sxs-lookup"><span data-stu-id="48fdb-133">Unary operators</span></span>

<span data-ttu-id="48fdb-134">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="48fdb-134">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="48fdb-135">[+ x](addition-operator.md) — zwraca wartość x.</span><span class="sxs-lookup"><span data-stu-id="48fdb-135">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="48fdb-136">[-x](subtraction-operator.md) — negacji liczbowych.</span><span class="sxs-lookup"><span data-stu-id="48fdb-136">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="48fdb-137">[\!x](boolean-logical-operators.md#logical-negation-operator-) — negacji logicznej.</span><span class="sxs-lookup"><span data-stu-id="48fdb-137">[\!x](boolean-logical-operators.md#logical-negation-operator-) – logical negation.</span></span>

<span data-ttu-id="48fdb-138">[~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-) — uzupełnienie bitowe.</span><span class="sxs-lookup"><span data-stu-id="48fdb-138">[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bitwise complement.</span></span>

<span data-ttu-id="48fdb-139">[++ x](arithmetic-operators.md#increment-operator-) — przedrostkowe.</span><span class="sxs-lookup"><span data-stu-id="48fdb-139">[++x](arithmetic-operators.md#increment-operator-) – prefix increment.</span></span> <span data-ttu-id="48fdb-140">Zwraca wartość x po zaktualizowaniu lokalizacji magazynu z wartością x, który jest jednym większą (zazwyczaj dodaje liczbę całkowitą 1).</span><span class="sxs-lookup"><span data-stu-id="48fdb-140">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="48fdb-141">[--x](arithmetic-operators.md#decrement-operator---) — przedrostkowe.</span><span class="sxs-lookup"><span data-stu-id="48fdb-141">[--x](arithmetic-operators.md#decrement-operator---) – prefix decrement.</span></span> <span data-ttu-id="48fdb-142">Zwraca wartość x po zaktualizowaniu lokalizacji magazynu o wartości x, która jest mniejsza (zazwyczaj odejmuje liczbę całkowitą 1).</span><span class="sxs-lookup"><span data-stu-id="48fdb-142">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="48fdb-143">[(T) x](invocation-operator.md) — typ rzutowania.</span><span class="sxs-lookup"><span data-stu-id="48fdb-143">[(T)x](invocation-operator.md) – type casting.</span></span>

<span data-ttu-id="48fdb-144">[await](../keywords/await.md) — czeka `Task`.</span><span class="sxs-lookup"><span data-stu-id="48fdb-144">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="48fdb-145">[& x](pointer-related-operators.md#address-of-operator-) — adres zmiennej.</span><span class="sxs-lookup"><span data-stu-id="48fdb-145">[&x](pointer-related-operators.md#address-of-operator-) – address of a variable.</span></span>

<span data-ttu-id="48fdb-146">[\* x](pointer-related-operators.md#pointer-indirection-operator-) — operację wskaźnika pośredniego lub wyłuskania.</span><span class="sxs-lookup"><span data-stu-id="48fdb-146">[\*x](pointer-related-operators.md#pointer-indirection-operator-) – pointer indirection, or dereference.</span></span>

<span data-ttu-id="48fdb-147">[TRUE — operator](../keywords/true-false-operators.md) — zwraca [bool](../keywords/bool.md) wartość `true` do wskazania, że argument jest zdecydowanie true.</span><span class="sxs-lookup"><span data-stu-id="48fdb-147">[true operator](../keywords/true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely true.</span></span>

<span data-ttu-id="48fdb-148">[FALSE — operator](../keywords/true-false-operators.md) — zwraca [bool](../keywords/bool.md) wartość `true` do wskazania, że argument jest zdecydowanie false.</span><span class="sxs-lookup"><span data-stu-id="48fdb-148">[false operator](../keywords/true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely false.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="48fdb-149">Operatory multiplikatywne</span><span class="sxs-lookup"><span data-stu-id="48fdb-149">Multiplicative operators</span></span>

<span data-ttu-id="48fdb-150">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="48fdb-150">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="48fdb-151">[x \* y](arithmetic-operators.md#multiplication-operator-) — mnożenia.</span><span class="sxs-lookup"><span data-stu-id="48fdb-151">[x \* y](arithmetic-operators.md#multiplication-operator-) – multiplication.</span></span>

<span data-ttu-id="48fdb-152">[x / y](arithmetic-operators.md#division-operator-) — dzielenia.</span><span class="sxs-lookup"><span data-stu-id="48fdb-152">[x / y](arithmetic-operators.md#division-operator-) – division.</span></span> <span data-ttu-id="48fdb-153">Jeśli argumenty są liczbami całkowitymi, wynik jest liczbą całkowitą obcięte w kierunku zera (na przykład `-7 / 2 is -3`).</span><span class="sxs-lookup"><span data-stu-id="48fdb-153">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="48fdb-154">[x, % y](arithmetic-operators.md#remainder-operator-) — resztę.</span><span class="sxs-lookup"><span data-stu-id="48fdb-154">[x % y](arithmetic-operators.md#remainder-operator-) – remainder.</span></span> <span data-ttu-id="48fdb-155">Jeśli argumenty są liczbami całkowitymi, to zwraca resztę z dzielenia podziału x, y.</span><span class="sxs-lookup"><span data-stu-id="48fdb-155">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="48fdb-156">Jeśli `q = x / y` i `r = x % y`, następnie `x = q * y + r`.</span><span class="sxs-lookup"><span data-stu-id="48fdb-156">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="48fdb-157">Operatory addytywne</span><span class="sxs-lookup"><span data-stu-id="48fdb-157">Additive operators</span></span>

<span data-ttu-id="48fdb-158">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="48fdb-158">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="48fdb-159">[x + y](arithmetic-operators.md#addition-operator-) — Dodawanie.</span><span class="sxs-lookup"><span data-stu-id="48fdb-159">[x + y](arithmetic-operators.md#addition-operator-) – addition.</span></span>

<span data-ttu-id="48fdb-160">[x – y](arithmetic-operators.md#subtraction-operator--) — odejmowania.</span><span class="sxs-lookup"><span data-stu-id="48fdb-160">[x – y](arithmetic-operators.md#subtraction-operator--) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="48fdb-161">Operatory przesunięcia</span><span class="sxs-lookup"><span data-stu-id="48fdb-161">Shift operators</span></span>

<span data-ttu-id="48fdb-162">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="48fdb-162">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="48fdb-163">[x <\< y](bitwise-and-shift-operators.md#left-shift-operator-) — przesunięcia bitów w lewo i wypełnić zero po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="48fdb-163">[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="48fdb-164">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) — shift bits po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="48fdb-164">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – shift bits right.</span></span> <span data-ttu-id="48fdb-165">Jeśli Lewy argument operacji jest `int` lub `long`, a następnie po lewej stronie bity są wypełnione bitu znaku.</span><span class="sxs-lookup"><span data-stu-id="48fdb-165">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="48fdb-166">Jeśli Lewy argument operacji jest `uint` lub `ulong`, a następnie po lewej stronie bity są wypełnione zero.</span><span class="sxs-lookup"><span data-stu-id="48fdb-166">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="48fdb-167">Operatory relacyjne i badania typu</span><span class="sxs-lookup"><span data-stu-id="48fdb-167">Relational and type-testing operators</span></span>

<span data-ttu-id="48fdb-168">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="48fdb-168">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="48fdb-169">[x \< y](comparison-operators.md#less-than-operator-) — mniejsze niż (wartość true, jeśli x jest mniejsza niż y).</span><span class="sxs-lookup"><span data-stu-id="48fdb-169">[x \< y](comparison-operators.md#less-than-operator-) – less than (true if x is less than y).</span></span>

<span data-ttu-id="48fdb-170">[x > y](comparison-operators.md#greater-than-operator-) — większa (wartość true, jeśli x jest większa niż y).</span><span class="sxs-lookup"><span data-stu-id="48fdb-170">[x > y](comparison-operators.md#greater-than-operator-) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="48fdb-171">[x \<= y](comparison-operators.md#less-than-or-equal-operator-) — mniejsze niż lub równe.</span><span class="sxs-lookup"><span data-stu-id="48fdb-171">[x \<= y](comparison-operators.md#less-than-or-equal-operator-) – less than or equal to.</span></span>

<span data-ttu-id="48fdb-172">[x > = y](comparison-operators.md#greater-than-or-equal-operator-) — większa lub równa.</span><span class="sxs-lookup"><span data-stu-id="48fdb-172">[x >= y](comparison-operators.md#greater-than-or-equal-operator-) – greater than or equal to.</span></span>

<span data-ttu-id="48fdb-173">[jest](../keywords/is.md) — wpisz zgodności.</span><span class="sxs-lookup"><span data-stu-id="48fdb-173">[is](../keywords/is.md) – type compatibility.</span></span> <span data-ttu-id="48fdb-174">Zwraca wartość PRAWDA, jeśli ocenianą lewy operand mogą być rzutowane na typ określony w prawy operand (typu statycznego).</span><span class="sxs-lookup"><span data-stu-id="48fdb-174">Returns true if the evaluated left operand can be cast to the type specified in the right operand (a static type).</span></span>

<span data-ttu-id="48fdb-175">[jako](../keywords/as.md) — konwersja typu.</span><span class="sxs-lookup"><span data-stu-id="48fdb-175">[as](../keywords/as.md) – type conversion.</span></span> <span data-ttu-id="48fdb-176">Zwraca lewy operand rzutowany na typ określony przez prawy operand (typ statycznej), ale `as` zwraca `null` gdzie `(T)x` spowoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="48fdb-176">Returns the left operand cast to the type specified by the right operand (a static type), but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="48fdb-177">Operatory równości</span><span class="sxs-lookup"><span data-stu-id="48fdb-177">Equality operators</span></span>

<span data-ttu-id="48fdb-178">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="48fdb-178">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="48fdb-179">[x == y](equality-operators.md#equality-operator-) — równości.</span><span class="sxs-lookup"><span data-stu-id="48fdb-179">[x == y](equality-operators.md#equality-operator-) – equality.</span></span> <span data-ttu-id="48fdb-180">Domyślnie dla odwołania do typów innych niż `string`ten zwraca odwołania równości (test tożsamości).</span><span class="sxs-lookup"><span data-stu-id="48fdb-180">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="48fdb-181">Jednak typów może doprowadzić do przeciążenia `==`, więc jeśli zgodne z zamiarami użytkownika jest, aby sprawdzić tożsamość, najlepiej użyć `ReferenceEquals` metody `object`.</span><span class="sxs-lookup"><span data-stu-id="48fdb-181">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="48fdb-182">[x! = y](equality-operators.md#inequality-operator-) — są nierówne.</span><span class="sxs-lookup"><span data-stu-id="48fdb-182">[x != y](equality-operators.md#inequality-operator-) – not equal.</span></span> <span data-ttu-id="48fdb-183">Zobacz komentarz dotyczący `==`.</span><span class="sxs-lookup"><span data-stu-id="48fdb-183">See comment for `==`.</span></span> <span data-ttu-id="48fdb-184">Jeśli typem przeciążenia `==`, a następnie przeciąża musi `!=`.</span><span class="sxs-lookup"><span data-stu-id="48fdb-184">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="48fdb-185">Operator logiczny AND</span><span class="sxs-lookup"><span data-stu-id="48fdb-185">Logical AND operator</span></span>

<span data-ttu-id="48fdb-186">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="48fdb-186">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="48fdb-187">`x & y` — [operator logiczny oraz](boolean-logical-operators.md#logical-and-operator-) dla `bool` operandy lub [iloczynu bitowego AND logiczne](bitwise-and-shift-operators.md#logical-and-operator-) przypadku argumentów operacji typu całkowitoliczbowego.</span><span class="sxs-lookup"><span data-stu-id="48fdb-187">`x & y` – [logical AND](boolean-logical-operators.md#logical-and-operator-) for the `bool` operands or [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) for the operands of the integral types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="48fdb-188">Operatora logicznego XOR</span><span class="sxs-lookup"><span data-stu-id="48fdb-188">Logical XOR operator</span></span>

<span data-ttu-id="48fdb-189">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="48fdb-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="48fdb-190">`x ^ y` — [XOR logiczne](boolean-logical-operators.md#logical-exclusive-or-operator-) dla `bool` operandy lub [iloczynu bitowego XOR logiczne](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) przypadku argumentów operacji typu całkowitoliczbowego.</span><span class="sxs-lookup"><span data-stu-id="48fdb-190">`x ^ y` – [logical XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) for the `bool` operands or [bitwise logical XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) for the operands of the integral types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="48fdb-191">Operator logiczny OR</span><span class="sxs-lookup"><span data-stu-id="48fdb-191">Logical OR operator</span></span>

<span data-ttu-id="48fdb-192">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="48fdb-192">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="48fdb-193">`x | y` — [logiczne OR](boolean-logical-operators.md#logical-or-operator-) dla `bool` operandy lub [bitowe OR logiczne](bitwise-and-shift-operators.md#logical-or-operator-) przypadku argumentów operacji typu całkowitoliczbowego.</span><span class="sxs-lookup"><span data-stu-id="48fdb-193">`x | y` – [logical OR](boolean-logical-operators.md#logical-or-operator-) for the `bool` operands or [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) for the operands of the integral types.</span></span>

## <a name="conditional-and-operator"></a><span data-ttu-id="48fdb-194">Operator warunkowy AND</span><span class="sxs-lookup"><span data-stu-id="48fdb-194">Conditional AND operator</span></span>

<span data-ttu-id="48fdb-195">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="48fdb-195">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="48fdb-196">[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) — operatora logicznego AND.</span><span class="sxs-lookup"><span data-stu-id="48fdb-196">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – logical AND.</span></span> <span data-ttu-id="48fdb-197">Jeśli pierwszy operand zwróci wartość false, następnie C# nie może oszacować drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="48fdb-197">If the first operand evaluates to false, then C# does not evaluate the second operand.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="48fdb-198">Operator warunkowy OR</span><span class="sxs-lookup"><span data-stu-id="48fdb-198">Conditional OR operator</span></span>

<span data-ttu-id="48fdb-199">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="48fdb-199">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="48fdb-200">[x &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) — operator logiczny lub.</span><span class="sxs-lookup"><span data-stu-id="48fdb-200">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logical OR.</span></span> <span data-ttu-id="48fdb-201">Jeśli pierwszy argument zwraca wartość true, następnie C# nie może oszacować drugiego operandu.</span><span class="sxs-lookup"><span data-stu-id="48fdb-201">If the first operand evaluates to true, then C# does not evaluate the second operand.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="48fdb-202">Operatorem łączenia wartości null</span><span class="sxs-lookup"><span data-stu-id="48fdb-202">Null-coalescing operator</span></span>

<span data-ttu-id="48fdb-203">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="48fdb-203">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="48fdb-204">[x? y](null-coalescing-operator.md) — zwraca `x` jeśli je ma wartość inną niż`null`; w przeciwnym razie zwraca `y`.</span><span class="sxs-lookup"><span data-stu-id="48fdb-204">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="48fdb-205">Operator warunkowy</span><span class="sxs-lookup"><span data-stu-id="48fdb-205">Conditional operator</span></span>

<span data-ttu-id="48fdb-206">Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="48fdb-206">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="48fdb-207">[t? x: y](conditional-operator.md) — w przypadku testowania `t` daje w wyniku wartość true, a następnie oceniana i zwracana `x`; w przeciwnym razie oceniana i zwracana `y`.</span><span class="sxs-lookup"><span data-stu-id="48fdb-207">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="48fdb-208">Operatory przypisania i lambda</span><span class="sxs-lookup"><span data-stu-id="48fdb-208">Assignment and lambda operators</span></span>

<span data-ttu-id="48fdb-209">Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="48fdb-209">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="48fdb-210">[x = y](assignment-operator.md) — przypisania.</span><span class="sxs-lookup"><span data-stu-id="48fdb-210">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="48fdb-211">[x += y](addition-assignment-operator.md) — przyrostu.</span><span class="sxs-lookup"><span data-stu-id="48fdb-211">[x += y](addition-assignment-operator.md) – increment.</span></span> <span data-ttu-id="48fdb-212">Dodaj wartość `y` wartość `x`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="48fdb-212">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="48fdb-213">Jeśli `x` wyznacza `event`, następnie `y` musi mieć odpowiednią funkcję, dodającego C# jako program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="48fdb-213">If `x` designates an `event`, then `y` must be an appropriate function that C# adds as an event handler.</span></span>

<span data-ttu-id="48fdb-214">[x-= y](subtraction-assignment-operator.md) — zmniejszanie.</span><span class="sxs-lookup"><span data-stu-id="48fdb-214">[x -= y](subtraction-assignment-operator.md) – decrement.</span></span> <span data-ttu-id="48fdb-215">Odejmuje wartość `y` od wartości `x`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="48fdb-215">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="48fdb-216">Jeśli `x` wyznacza `event`, następnie `y` musi mieć odpowiednią funkcję C# usuwa jako program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="48fdb-216">If `x` designates an `event`, then `y` must be an appropriate function that C# removes as an event handler.</span></span>

<span data-ttu-id="48fdb-217">[x \* = y](arithmetic-operators.md#compound-assignment) — mnożenie i przypisanie.</span><span class="sxs-lookup"><span data-stu-id="48fdb-217">[x \*= y](arithmetic-operators.md#compound-assignment) – multiplication assignment.</span></span> <span data-ttu-id="48fdb-218">Mnoży wartość `y` wartość `x`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="48fdb-218">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="48fdb-219">[x / = y](arithmetic-operators.md#compound-assignment) — dzielenie i przypisanie.</span><span class="sxs-lookup"><span data-stu-id="48fdb-219">[x /= y](arithmetic-operators.md#compound-assignment) – division assignment.</span></span> <span data-ttu-id="48fdb-220">Dzieli wartość `x` przez wartość `y`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="48fdb-220">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="48fdb-221">[x % = y](arithmetic-operators.md#compound-assignment) — remainder przypisania.</span><span class="sxs-lookup"><span data-stu-id="48fdb-221">[x %= y](arithmetic-operators.md#compound-assignment) – remainder assignment.</span></span> <span data-ttu-id="48fdb-222">Dzieli wartość `x` przez wartość `y`, przechowywać resztę w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="48fdb-222">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="48fdb-223">[x & = y](boolean-logical-operators.md#compound-assignment) — i przypisanie.</span><span class="sxs-lookup"><span data-stu-id="48fdb-223">[x &= y](boolean-logical-operators.md#compound-assignment) – AND assignment.</span></span> <span data-ttu-id="48fdb-224">I wartość `y` z wartością `x`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="48fdb-224">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="48fdb-225">[x &#124;= y](boolean-logical-operators.md#compound-assignment) — i przypisanie.</span><span class="sxs-lookup"><span data-stu-id="48fdb-225">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – OR assignment.</span></span> <span data-ttu-id="48fdb-226">LUB wartość `y` z wartością `x`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="48fdb-226">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="48fdb-227">[x ^ = y](boolean-logical-operators.md#compound-assignment) — przypisanie XOR.</span><span class="sxs-lookup"><span data-stu-id="48fdb-227">[x ^= y](boolean-logical-operators.md#compound-assignment) – XOR assignment.</span></span> <span data-ttu-id="48fdb-228">XOR wartość z `y` z wartością `x`, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="48fdb-228">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="48fdb-229">[x << = y](bitwise-and-shift-operators.md#compound-assignment) — przypisania przesunięcia w lewo.</span><span class="sxs-lookup"><span data-stu-id="48fdb-229">[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – left-shift assignment.</span></span> <span data-ttu-id="48fdb-230">Przesuwa wartość `x` po lewej stronie, `y` miejscach, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="48fdb-230">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="48fdb-231">[x >> = y](bitwise-and-shift-operators.md#compound-assignment) — przypisania przesunięcia w prawo.</span><span class="sxs-lookup"><span data-stu-id="48fdb-231">[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – right-shift assignment.</span></span> <span data-ttu-id="48fdb-232">Przesuwa wartość `x` bezpośrednio przez `y` miejscach, zapisują wynik w `x`i zwraca nową wartość.</span><span class="sxs-lookup"><span data-stu-id="48fdb-232">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="48fdb-233">[=>](lambda-operator.md) — deklaracji lambda.</span><span class="sxs-lookup"><span data-stu-id="48fdb-233">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="48fdb-234">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48fdb-234">See also</span></span>

- [<span data-ttu-id="48fdb-235">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="48fdb-235">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="48fdb-236">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="48fdb-236">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="48fdb-237">C#</span><span class="sxs-lookup"><span data-stu-id="48fdb-237">C#</span></span>](../../index.md)
- [<span data-ttu-id="48fdb-238">Operatory z możliwością przeciążenia</span><span class="sxs-lookup"><span data-stu-id="48fdb-238">Overloadable operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="48fdb-239">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="48fdb-239">C# Keywords</span></span>](../keywords/index.md)
