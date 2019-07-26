---
title: C#Operatory — C# odwołanie
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
ms.openlocfilehash: b6a1cc3ced3205037eb5b83ac3841efbfbd1b5b9
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331215"
---
# <a name="c-operators-c-reference"></a><span data-ttu-id="e9bda-102">C#Operatory (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="e9bda-102">C# operators (C# reference)</span></span>

<span data-ttu-id="e9bda-103">C#udostępnia wiele wstępnie zdefiniowanych operatorów obsługiwanych przez typy wbudowane.</span><span class="sxs-lookup"><span data-stu-id="e9bda-103">C# provides a number of predefined operators supported by the built-in types.</span></span> <span data-ttu-id="e9bda-104">Na przykład [Operatory arytmetyczne](arithmetic-operators.md) wykonują operacje arytmetyczne przy użyciu operandów wbudowanych typów liczbowych i logicznych [Operatory logiczne](boolean-logical-operators.md) wykonują operacje logiczne przy użyciu operandów [bool](../keywords/bool.md) .</span><span class="sxs-lookup"><span data-stu-id="e9bda-104">For example, [arithmetic operators](arithmetic-operators.md) perform arithmetic operations with operands of built-in numeric types and [Boolean logical operators](boolean-logical-operators.md) perform logical operations with the [bool](../keywords/bool.md) operands.</span></span>

<span data-ttu-id="e9bda-105">Typ zdefiniowany przez użytkownika może przeciążać pewne operatory, aby zdefiniować odpowiednie zachowanie dla operandów tego typu.</span><span class="sxs-lookup"><span data-stu-id="e9bda-105">A user-defined type can overload certain operators to define the corresponding behavior for the operands of that type.</span></span> <span data-ttu-id="e9bda-106">Aby uzyskać więcej informacji, zobacz przeciążanie [operatora](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="e9bda-106">For more information, see [Operator overloading](operator-overloading.md).</span></span>

<span data-ttu-id="e9bda-107">W poniższych sekcjach znajdują się C# operatory zaczynające się od najwyższego pierwszeństwa.</span><span class="sxs-lookup"><span data-stu-id="e9bda-107">The following sections list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="e9bda-108">Operatory w każdej sekcji mają ten sam poziom pierwszeństwa.</span><span class="sxs-lookup"><span data-stu-id="e9bda-108">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="e9bda-109">Operatory podstawowe</span><span class="sxs-lookup"><span data-stu-id="e9bda-109">Primary operators</span></span>

<span data-ttu-id="e9bda-110">Są to operatory najwyższej kolejności.</span><span class="sxs-lookup"><span data-stu-id="e9bda-110">These are the highest precedence operators.</span></span>

<span data-ttu-id="e9bda-111">[x. y](member-access-operators.md#member-access-operator-) — dostęp do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e9bda-111">[x.y](member-access-operators.md#member-access-operator-) – member access.</span></span>

<span data-ttu-id="e9bda-112">[x?. y](member-access-operators.md#null-conditional-operators--and-) – null warunkowy dostęp do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e9bda-112">[x?.y](member-access-operators.md#null-conditional-operators--and-) – null conditional member access.</span></span> <span data-ttu-id="e9bda-113">Zwraca `null` wartość, jeśli argument operacji po lewej stronie ma `null`wartość.</span><span class="sxs-lookup"><span data-stu-id="e9bda-113">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="e9bda-114">[x? [y]](member-access-operators.md#null-conditional-operators--and-) -null element tablicy warunkowej lub dostęp do indeksatora typu.</span><span class="sxs-lookup"><span data-stu-id="e9bda-114">[x?[y]](member-access-operators.md#null-conditional-operators--and-) - null conditional array element or type indexer access.</span></span> <span data-ttu-id="e9bda-115">Zwraca `null` wartość, jeśli argument operacji po lewej stronie ma `null`wartość.</span><span class="sxs-lookup"><span data-stu-id="e9bda-115">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="e9bda-116">[f (x)](member-access-operators.md#invocation-operator-) — wywołanie metody lub delegat wywołania.</span><span class="sxs-lookup"><span data-stu-id="e9bda-116">[f(x)](member-access-operators.md#invocation-operator-) – method call or delegate invocation.</span></span>

<span data-ttu-id="e9bda-117">dostęp do elementu Array [&#91;x&#93; ](member-access-operators.md#indexer-operator-) lub typu indeksatora.</span><span class="sxs-lookup"><span data-stu-id="e9bda-117">[a&#91;x&#93;](member-access-operators.md#indexer-operator-) – array element or type indexer access.</span></span>

<span data-ttu-id="e9bda-118">[x + +](arithmetic-operators.md#increment-operator-) — przyrostek Przyrostkowy.</span><span class="sxs-lookup"><span data-stu-id="e9bda-118">[x++](arithmetic-operators.md#increment-operator-) – postfix increment.</span></span> <span data-ttu-id="e9bda-119">Zwraca wartość x, a następnie aktualizuje lokalizację magazynu o wartości x, która jest większa (zazwyczaj dodaje liczbę całkowitą 1).</span><span class="sxs-lookup"><span data-stu-id="e9bda-119">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="e9bda-120">[x--](arithmetic-operators.md#decrement-operator---) — zmniejszenie przyrostu.</span><span class="sxs-lookup"><span data-stu-id="e9bda-120">[x--](arithmetic-operators.md#decrement-operator---) –  postfix decrement.</span></span> <span data-ttu-id="e9bda-121">Zwraca wartość x, a następnie aktualizuje lokalizację magazynu o wartości x, która jest mniejsza (zazwyczaj odejmuje liczbę całkowitą 1).</span><span class="sxs-lookup"><span data-stu-id="e9bda-121">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="e9bda-122">[nowe](new-operator.md) — Tworzenie wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="e9bda-122">[new](new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="e9bda-123">[typeof](type-testing-and-conversion-operators.md#typeof-operator) — zwraca <xref:System.Type> obiekt reprezentujący operand.</span><span class="sxs-lookup"><span data-stu-id="e9bda-123">[typeof](type-testing-and-conversion-operators.md#typeof-operator) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="e9bda-124">[zaznaczone](../keywords/checked.md) — włącza sprawdzanie przepełnienia dla operacji całkowitych.</span><span class="sxs-lookup"><span data-stu-id="e9bda-124">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="e9bda-125">[](../keywords/unchecked.md) unchecked — wyłącza sprawdzanie przepełnienia dla operacji całkowitych.</span><span class="sxs-lookup"><span data-stu-id="e9bda-125">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="e9bda-126">Jest to domyślne zachowanie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="e9bda-126">This is the default compiler behavior.</span></span>

<span data-ttu-id="e9bda-127">[Default (T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) — tworzy wartość domyślną typu T.</span><span class="sxs-lookup"><span data-stu-id="e9bda-127">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produces the default value of type T.</span></span>

<span data-ttu-id="e9bda-128">[nameof](nameof.md) — umożliwia uzyskanie prostej (niekwalifikowanej) nazwy zmiennej, typu lub składowej jako ciągu stałej.</span><span class="sxs-lookup"><span data-stu-id="e9bda-128">[nameof](nameof.md) - obtains the simple (unqualified) name of a variable, type, or member as a constant string.</span></span>

<span data-ttu-id="e9bda-129">[Delegate](delegate-operator.md) — deklaruje i zwraca wystąpienie delegata.</span><span class="sxs-lookup"><span data-stu-id="e9bda-129">[delegate](delegate-operator.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="e9bda-130">[sizeof](../keywords/sizeof.md) — zwraca rozmiar operandu typu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="e9bda-130">[sizeof](../keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="e9bda-131">[stackalloc](stackalloc.md) — przydziela blok pamięci na stosie.</span><span class="sxs-lookup"><span data-stu-id="e9bda-131">[stackalloc](stackalloc.md) - allocates a block of memory on the stack.</span></span>

<span data-ttu-id="e9bda-132">[->](pointer-related-operators.md#pointer-member-access-operator--)– wskaźnik pośredni połączony z dostępem do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e9bda-132">[->](pointer-related-operators.md#pointer-member-access-operator--) – pointer indirection combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="e9bda-133">Operatory jednoargumentowe</span><span class="sxs-lookup"><span data-stu-id="e9bda-133">Unary operators</span></span>

<span data-ttu-id="e9bda-134">Te operatory mają wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.</span><span class="sxs-lookup"><span data-stu-id="e9bda-134">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9bda-135">[+ x](addition-operator.md) — zwraca wartość x.</span><span class="sxs-lookup"><span data-stu-id="e9bda-135">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="e9bda-136">[-x](subtraction-operator.md) — Negacja liczbowa.</span><span class="sxs-lookup"><span data-stu-id="e9bda-136">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="e9bda-137">x — Negacja logiczna. [ \!](boolean-logical-operators.md#logical-negation-operator-)</span><span class="sxs-lookup"><span data-stu-id="e9bda-137">[\!x](boolean-logical-operators.md#logical-negation-operator-) – logical negation.</span></span>

<span data-ttu-id="e9bda-138">[~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-) — uzupełnienie bitowe.</span><span class="sxs-lookup"><span data-stu-id="e9bda-138">[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bitwise complement.</span></span>

<span data-ttu-id="e9bda-139">[+ + x](arithmetic-operators.md#increment-operator-) — przyrost prefiksu.</span><span class="sxs-lookup"><span data-stu-id="e9bda-139">[++x](arithmetic-operators.md#increment-operator-) – prefix increment.</span></span> <span data-ttu-id="e9bda-140">Zwraca wartość x po zaktualizowaniu lokalizacji magazynu o wartość x, która jest większa (zazwyczaj dodaje liczbę całkowitą 1).</span><span class="sxs-lookup"><span data-stu-id="e9bda-140">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="e9bda-141">[--x](arithmetic-operators.md#decrement-operator---) — zmniejszenie prefiksu.</span><span class="sxs-lookup"><span data-stu-id="e9bda-141">[--x](arithmetic-operators.md#decrement-operator---) – prefix decrement.</span></span> <span data-ttu-id="e9bda-142">Zwraca wartość x po zaktualizowaniu lokalizacji magazynu o wartość x, która jest mniejsza (zazwyczaj odejmuje liczbę całkowitą 1).</span><span class="sxs-lookup"><span data-stu-id="e9bda-142">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="e9bda-143">[(T) x](type-testing-and-conversion-operators.md#cast-operator-) — rzutowanie typów.</span><span class="sxs-lookup"><span data-stu-id="e9bda-143">[(T)x](type-testing-and-conversion-operators.md#cast-operator-) – type casting.</span></span>

<span data-ttu-id="e9bda-144">[await](../keywords/await.md) — czeka na `Task`.</span><span class="sxs-lookup"><span data-stu-id="e9bda-144">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="e9bda-145">[& x](pointer-related-operators.md#address-of-operator-) — adres zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e9bda-145">[&x](pointer-related-operators.md#address-of-operator-) – address of a variable.</span></span>

<span data-ttu-id="e9bda-146">[\* x](pointer-related-operators.md#pointer-indirection-operator-) — wskaźnik pośredni lub wyłuskanie.</span><span class="sxs-lookup"><span data-stu-id="e9bda-146">[\*x](pointer-related-operators.md#pointer-indirection-operator-) – pointer indirection, or dereference.</span></span>

<span data-ttu-id="e9bda-147">[true operator](true-false-operators.md) — zwraca `true` wartość [logiczną](../keywords/bool.md) , aby wskazać, że operand ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="e9bda-147">[true operator](true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely true.</span></span>

<span data-ttu-id="e9bda-148">[operator false](true-false-operators.md) — zwraca `true` wartość [logiczną](../keywords/bool.md) , aby wskazać, że operand ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="e9bda-148">[false operator](true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely false.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="e9bda-149">Operatory multiplikatywne</span><span class="sxs-lookup"><span data-stu-id="e9bda-149">Multiplicative operators</span></span>

<span data-ttu-id="e9bda-150">Te operatory mają wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.</span><span class="sxs-lookup"><span data-stu-id="e9bda-150">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9bda-151">[x \* y](arithmetic-operators.md#multiplication-operator-) — mnożenia.</span><span class="sxs-lookup"><span data-stu-id="e9bda-151">[x \* y](arithmetic-operators.md#multiplication-operator-) – multiplication.</span></span>

<span data-ttu-id="e9bda-152">dzielenie [x/y](arithmetic-operators.md#division-operator-) .</span><span class="sxs-lookup"><span data-stu-id="e9bda-152">[x / y](arithmetic-operators.md#division-operator-) – division.</span></span> <span data-ttu-id="e9bda-153">Jeśli operandy są liczbami całkowitymi, wynik jest liczbą całkowitą obciętym do zera (na `-7 / 2 is -3`przykład).</span><span class="sxs-lookup"><span data-stu-id="e9bda-153">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="e9bda-154">[x% y](arithmetic-operators.md#remainder-operator-) — reszta.</span><span class="sxs-lookup"><span data-stu-id="e9bda-154">[x % y](arithmetic-operators.md#remainder-operator-) – remainder.</span></span> <span data-ttu-id="e9bda-155">Jeśli operandy są liczbami całkowitymi, to zwraca resztę dzielenia x przez y.</span><span class="sxs-lookup"><span data-stu-id="e9bda-155">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="e9bda-156">If `q = x / y` i `r = x % y`, then `x = q * y + r`.</span><span class="sxs-lookup"><span data-stu-id="e9bda-156">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="e9bda-157">Operatory addytywne</span><span class="sxs-lookup"><span data-stu-id="e9bda-157">Additive operators</span></span>

<span data-ttu-id="e9bda-158">Te operatory mają wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.</span><span class="sxs-lookup"><span data-stu-id="e9bda-158">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9bda-159">Dodawanie [x + y](arithmetic-operators.md#addition-operator-) .</span><span class="sxs-lookup"><span data-stu-id="e9bda-159">[x + y](arithmetic-operators.md#addition-operator-) – addition.</span></span>

<span data-ttu-id="e9bda-160">[x – y](arithmetic-operators.md#subtraction-operator--) — odejmowanie.</span><span class="sxs-lookup"><span data-stu-id="e9bda-160">[x – y](arithmetic-operators.md#subtraction-operator--) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="e9bda-161">Operatory przesunięcia</span><span class="sxs-lookup"><span data-stu-id="e9bda-161">Shift operators</span></span>

<span data-ttu-id="e9bda-162">Te operatory mają wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.</span><span class="sxs-lookup"><span data-stu-id="e9bda-162">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9bda-163">[x <\< y](bitwise-and-shift-operators.md#left-shift-operator-) — przesunięcie w lewo i wypełnienie z zerem po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="e9bda-163">[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="e9bda-164">[x > > y](bitwise-and-shift-operators.md#right-shift-operator-) — prawo do usługi BITS.</span><span class="sxs-lookup"><span data-stu-id="e9bda-164">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – shift bits right.</span></span> <span data-ttu-id="e9bda-165">Jeśli argument operacji po lewej `int` stronie `long`ma wartość lub, lewe bity są wypełnione bitem znaku.</span><span class="sxs-lookup"><span data-stu-id="e9bda-165">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="e9bda-166">Jeśli Lewy argument operacji jest `uint` lub `ulong`, lewy bity są wypełnione zerem.</span><span class="sxs-lookup"><span data-stu-id="e9bda-166">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="e9bda-167">Operatory relacyjne i testowe typu</span><span class="sxs-lookup"><span data-stu-id="e9bda-167">Relational and type-testing operators</span></span>

<span data-ttu-id="e9bda-168">Te operatory mają wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.</span><span class="sxs-lookup"><span data-stu-id="e9bda-168">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9bda-169">[ x\< y](comparison-operators.md#less-than-operator-) – mniejsze niż (true, jeśli x jest mniejsze niż y).</span><span class="sxs-lookup"><span data-stu-id="e9bda-169">[x \< y](comparison-operators.md#less-than-operator-) – less than (true if x is less than y).</span></span>

<span data-ttu-id="e9bda-170">[x > y](comparison-operators.md#greater-than-operator-) – większe niż (true, jeśli x jest większe niż y).</span><span class="sxs-lookup"><span data-stu-id="e9bda-170">[x > y](comparison-operators.md#greater-than-operator-) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="e9bda-171">[ x\<= y](comparison-operators.md#less-than-or-equal-operator-) – mniejsze niż lub równe.</span><span class="sxs-lookup"><span data-stu-id="e9bda-171">[x \<= y](comparison-operators.md#less-than-or-equal-operator-) – less than or equal to.</span></span>

<span data-ttu-id="e9bda-172">[x > = y](comparison-operators.md#greater-than-or-equal-operator-) – większe niż lub równe.</span><span class="sxs-lookup"><span data-stu-id="e9bda-172">[x >= y](comparison-operators.md#greater-than-or-equal-operator-) – greater than or equal to.</span></span>

<span data-ttu-id="e9bda-173">[jest](type-testing-and-conversion-operators.md#is-operator) — zgodność typów.</span><span class="sxs-lookup"><span data-stu-id="e9bda-173">[is](type-testing-and-conversion-operators.md#is-operator) – type compatibility.</span></span> <span data-ttu-id="e9bda-174">Zwraca `true` czy oszacowany operand z lewej strony może być rzutowany na typ określony przez prawy operand.</span><span class="sxs-lookup"><span data-stu-id="e9bda-174">Returns `true` if the evaluated left operand can be cast to the type specified by the right operand.</span></span>

<span data-ttu-id="e9bda-175">Konwersja typu " [as](type-testing-and-conversion-operators.md#as-operator) ".</span><span class="sxs-lookup"><span data-stu-id="e9bda-175">[as](type-testing-and-conversion-operators.md#as-operator) – type conversion.</span></span> <span data-ttu-id="e9bda-176">Zwraca rzutowanie lewego operandu do typu określonego przez prawy operand, ale `as` zwraca `null` , gdzie `(T)x` zostałby zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e9bda-176">Returns the left operand cast to the type specified by the right operand, but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="e9bda-177">Operatory równości</span><span class="sxs-lookup"><span data-stu-id="e9bda-177">Equality operators</span></span>

<span data-ttu-id="e9bda-178">Te operatory mają wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.</span><span class="sxs-lookup"><span data-stu-id="e9bda-178">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9bda-179">[x = = t](equality-operators.md#equality-operator-) — równość.</span><span class="sxs-lookup"><span data-stu-id="e9bda-179">[x == y](equality-operators.md#equality-operator-) – equality.</span></span> <span data-ttu-id="e9bda-180">Domyślnie dla typów odwołań innych niż `string`, zwraca równość odwołania (test tożsamości).</span><span class="sxs-lookup"><span data-stu-id="e9bda-180">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="e9bda-181">Jednak typy mogą przeciążać `==`, więc jeśli chcesz przetestować tożsamość, najlepszym rozwiązaniem jest `ReferenceEquals` użycie metody w `object`.</span><span class="sxs-lookup"><span data-stu-id="e9bda-181">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="e9bda-182">[x! = y](equality-operators.md#inequality-operator-) — nie równa się.</span><span class="sxs-lookup"><span data-stu-id="e9bda-182">[x != y](equality-operators.md#inequality-operator-) – not equal.</span></span> <span data-ttu-id="e9bda-183">Zobacz komentarz dla `==`.</span><span class="sxs-lookup"><span data-stu-id="e9bda-183">See comment for `==`.</span></span> <span data-ttu-id="e9bda-184">W przypadku przeciążenia `==`typów, należy przeciążać `!=`.</span><span class="sxs-lookup"><span data-stu-id="e9bda-184">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="e9bda-185">Operator logiczny AND</span><span class="sxs-lookup"><span data-stu-id="e9bda-185">Logical AND operator</span></span>

<span data-ttu-id="e9bda-186">Ten operator ma wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.</span><span class="sxs-lookup"><span data-stu-id="e9bda-186">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9bda-187">`x & y`— [logiczne i](boolean-logical-operators.md#logical-and-operator-) dla `bool` operandów lub [koniunkcji bitowej oraz](bitwise-and-shift-operators.md#logical-and-operator-) dla operandów typów całkowitych.</span><span class="sxs-lookup"><span data-stu-id="e9bda-187">`x & y` – [logical AND](boolean-logical-operators.md#logical-and-operator-) for the `bool` operands or [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) for the operands of the integral types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="e9bda-188">Logiczny operator XOR</span><span class="sxs-lookup"><span data-stu-id="e9bda-188">Logical XOR operator</span></span>

<span data-ttu-id="e9bda-189">Ten operator ma wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.</span><span class="sxs-lookup"><span data-stu-id="e9bda-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9bda-190">`x ^ y`— [logiczna XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) dla `bool` operandów lub [bitowe logiczne XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) dla operandów typów całkowitych.</span><span class="sxs-lookup"><span data-stu-id="e9bda-190">`x ^ y` – [logical XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) for the `bool` operands or [bitwise logical XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) for the operands of the integral types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="e9bda-191">Operator logiczny OR</span><span class="sxs-lookup"><span data-stu-id="e9bda-191">Logical OR operator</span></span>

<span data-ttu-id="e9bda-192">Ten operator ma wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.</span><span class="sxs-lookup"><span data-stu-id="e9bda-192">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9bda-193">`x | y`— [logiczne lub](boolean-logical-operators.md#logical-or-operator-) dla `bool` operandów lub [koniunkcji logicznej lub](bitwise-and-shift-operators.md#logical-or-operator-) dla operandów typów całkowitych.</span><span class="sxs-lookup"><span data-stu-id="e9bda-193">`x | y` – [logical OR](boolean-logical-operators.md#logical-or-operator-) for the `bool` operands or [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) for the operands of the integral types.</span></span>

## <a name="conditional-and-operator"></a><span data-ttu-id="e9bda-194">Operator warunkowy i</span><span class="sxs-lookup"><span data-stu-id="e9bda-194">Conditional AND operator</span></span>

<span data-ttu-id="e9bda-195">Ten operator ma wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.</span><span class="sxs-lookup"><span data-stu-id="e9bda-195">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9bda-196">[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) — koniunkcja i.</span><span class="sxs-lookup"><span data-stu-id="e9bda-196">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – logical AND.</span></span> <span data-ttu-id="e9bda-197">W `x` przypadku wartości zwraca `false`wartość, `y` a następnie nie jest szacowana.</span><span class="sxs-lookup"><span data-stu-id="e9bda-197">If `x` evaluates to `false`, then `y` is not evaluated.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="e9bda-198">Operator warunkowy OR</span><span class="sxs-lookup"><span data-stu-id="e9bda-198">Conditional OR operator</span></span>

<span data-ttu-id="e9bda-199">Ten operator ma wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.</span><span class="sxs-lookup"><span data-stu-id="e9bda-199">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9bda-200">[ &#124; x &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) — logiczne lub.</span><span class="sxs-lookup"><span data-stu-id="e9bda-200">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logical OR.</span></span> <span data-ttu-id="e9bda-201">W `x` przypadku wartości zwraca `true`wartość, `y` a następnie nie jest szacowana.</span><span class="sxs-lookup"><span data-stu-id="e9bda-201">If `x` evaluates to `true`, then `y` is not evaluated.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="e9bda-202">Operator łączenia wartości null</span><span class="sxs-lookup"><span data-stu-id="e9bda-202">Null-coalescing operator</span></span>

<span data-ttu-id="e9bda-203">Ten operator ma wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.</span><span class="sxs-lookup"><span data-stu-id="e9bda-203">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9bda-204">[x?? y](null-coalescing-operator.md) — zwraca `x` czy nie jest-`null`; w przeciwnym razie zwraca `y`.</span><span class="sxs-lookup"><span data-stu-id="e9bda-204">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="e9bda-205">Operator warunkowy</span><span class="sxs-lookup"><span data-stu-id="e9bda-205">Conditional operator</span></span>

<span data-ttu-id="e9bda-206">Ten operator ma wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.</span><span class="sxs-lookup"><span data-stu-id="e9bda-206">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9bda-207">[t? x: y](conditional-operator.md) — Jeśli test `t` ma wartość true, należy obliczyć i zwrócić `x`; w przeciwnym razie obliczyć i zwrócić `y`.</span><span class="sxs-lookup"><span data-stu-id="e9bda-207">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="e9bda-208">Przypisanie i operatory lambda</span><span class="sxs-lookup"><span data-stu-id="e9bda-208">Assignment and lambda operators</span></span>

<span data-ttu-id="e9bda-209">Te operatory mają wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.</span><span class="sxs-lookup"><span data-stu-id="e9bda-209">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="e9bda-210">[x = y](assignment-operator.md) — przypisanie.</span><span class="sxs-lookup"><span data-stu-id="e9bda-210">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="e9bda-211">[x + = y](arithmetic-operators.md#compound-assignment) — przyrost.</span><span class="sxs-lookup"><span data-stu-id="e9bda-211">[x += y](arithmetic-operators.md#compound-assignment) – increment.</span></span> <span data-ttu-id="e9bda-212">Dodaj wartość `y` do `x`wartości, Zapisz wynik w `x`i zwróć nową wartość.</span><span class="sxs-lookup"><span data-stu-id="e9bda-212">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="e9bda-213">Jeśli `x` wyznacza C# [zdarzenie, musi być](../keywords/event.md)odpowiednią metodą, która dodaje jako procedurę obsługi zdarzeń. `y`</span><span class="sxs-lookup"><span data-stu-id="e9bda-213">If `x` designates an [event](../keywords/event.md), then `y` must be an appropriate method that C# adds as an event handler.</span></span>

<span data-ttu-id="e9bda-214">[x-= y](arithmetic-operators.md#compound-assignment) – zmniejszenie.</span><span class="sxs-lookup"><span data-stu-id="e9bda-214">[x -= y](arithmetic-operators.md#compound-assignment) – decrement.</span></span> <span data-ttu-id="e9bda-215">Odejmij wartość `y` od `x`wartości, Zapisz wynik w `x`i zwróć nową wartość.</span><span class="sxs-lookup"><span data-stu-id="e9bda-215">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="e9bda-216">Jeśli `x` wyznacza C# [zdarzenie, musi być](../keywords/event.md)odpowiednią metodą, która usuwa jako procedurę obsługi zdarzeń. `y`</span><span class="sxs-lookup"><span data-stu-id="e9bda-216">If `x` designates an [event](../keywords/event.md), then `y` must be an appropriate method that C# removes as an event handler.</span></span>

<span data-ttu-id="e9bda-217">[x \* =](arithmetic-operators.md#compound-assignment) przypisanie do mnożenia y.</span><span class="sxs-lookup"><span data-stu-id="e9bda-217">[x \*= y](arithmetic-operators.md#compound-assignment) – multiplication assignment.</span></span> <span data-ttu-id="e9bda-218">Pomnóż wartość `y` do `x`wartości, Zapisz wynik w `x`i zwróć nową wartość.</span><span class="sxs-lookup"><span data-stu-id="e9bda-218">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="e9bda-219">przypisanie dzielenia [x/= y](arithmetic-operators.md#compound-assignment) .</span><span class="sxs-lookup"><span data-stu-id="e9bda-219">[x /= y](arithmetic-operators.md#compound-assignment) – division assignment.</span></span> <span data-ttu-id="e9bda-220">Podziel wartość `x` przez `y`wartość, Zapisz wynik w `x`i zwróć nową wartość.</span><span class="sxs-lookup"><span data-stu-id="e9bda-220">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="e9bda-221">przypisanie do pozostałej liczby [x% = y](arithmetic-operators.md#compound-assignment) .</span><span class="sxs-lookup"><span data-stu-id="e9bda-221">[x %= y](arithmetic-operators.md#compound-assignment) – remainder assignment.</span></span> <span data-ttu-id="e9bda-222">Podziel wartość `x` przez `y`wartość, Zapisz resztę w `x`i zwróć nową wartość.</span><span class="sxs-lookup"><span data-stu-id="e9bda-222">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="e9bda-223">[x & = y](boolean-logical-operators.md#compound-assignment) — i przypisanie.</span><span class="sxs-lookup"><span data-stu-id="e9bda-223">[x &= y](boolean-logical-operators.md#compound-assignment) – AND assignment.</span></span> <span data-ttu-id="e9bda-224">I wartość `y` z `x`wartością, Zapisz wynik w `x`i zwróć nową wartość.</span><span class="sxs-lookup"><span data-stu-id="e9bda-224">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="e9bda-225">[x &#124;= y](boolean-logical-operators.md#compound-assignment) — lub przypisanie.</span><span class="sxs-lookup"><span data-stu-id="e9bda-225">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – OR assignment.</span></span> <span data-ttu-id="e9bda-226">Lub wartość `y` o `x`wartości, Zapisz wynik w `x`i zwróć nową wartość.</span><span class="sxs-lookup"><span data-stu-id="e9bda-226">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="e9bda-227">[x ^ = y](boolean-logical-operators.md#compound-assignment) — przypisanie XOR.</span><span class="sxs-lookup"><span data-stu-id="e9bda-227">[x ^= y](boolean-logical-operators.md#compound-assignment) – XOR assignment.</span></span> <span data-ttu-id="e9bda-228">XOR wartość `y` o `x`wartości, Zapisz wynik w `x`i zwróć nową wartość.</span><span class="sxs-lookup"><span data-stu-id="e9bda-228">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="e9bda-229">[x < < = y](bitwise-and-shift-operators.md#compound-assignment) — przypisanie do lewej przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="e9bda-229">[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – left-shift assignment.</span></span> <span data-ttu-id="e9bda-230">Przenieś wartość z `x` lewej strony według `y` miejsc, Zapisz wynik w `x`i zwróć nową wartość.</span><span class="sxs-lookup"><span data-stu-id="e9bda-230">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="e9bda-231">[x > > = y](bitwise-and-shift-operators.md#compound-assignment) — przypisanie do prawej strony.</span><span class="sxs-lookup"><span data-stu-id="e9bda-231">[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – right-shift assignment.</span></span> <span data-ttu-id="e9bda-232">Przesuń wartość `x` w `y`prawowedługmiejsc ,Zapiszwynikizwróćnowąwartość`x`.</span><span class="sxs-lookup"><span data-stu-id="e9bda-232">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="e9bda-233">[=>](lambda-operator.md)— Deklaracja lambda.</span><span class="sxs-lookup"><span data-stu-id="e9bda-233">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9bda-234">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9bda-234">See also</span></span>

- [<span data-ttu-id="e9bda-235">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="e9bda-235">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e9bda-236">Operatory</span><span class="sxs-lookup"><span data-stu-id="e9bda-236">Operators</span></span>](../../programming-guide/statements-expressions-operators/operators.md)
