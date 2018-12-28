---
title: Rzutowanie i konwersje
description: Dowiedz się, jak F# język programowania przewiduje operatory konwersji konwersje arytmetyczne między różnych typów pierwotnych.
ms.date: 05/16/2016
ms.openlocfilehash: 2a12d48106a267edfc67c9e7b3d3a7bd41d8261c
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655988"
---
# <a name="casting-and-conversions-f"></a><span data-ttu-id="f9d01-103">Rzutowanie i konwersje (F#)</span><span class="sxs-lookup"><span data-stu-id="f9d01-103">Casting and Conversions (F#)</span></span>

<span data-ttu-id="f9d01-104">W tym temacie opisano obsługę konwersje typów w F#.</span><span class="sxs-lookup"><span data-stu-id="f9d01-104">This topic describes support for type conversions in F#.</span></span>

## <a name="arithmetic-types"></a><span data-ttu-id="f9d01-105">Typy arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="f9d01-105">Arithmetic Types</span></span>

<span data-ttu-id="f9d01-106">F#zawiera operatory konwersji konwersje arytmetyczne między różnych typów pierwotnych, takich jak między liczb całkowitych i zmiennoprzecinkowych typów.</span><span class="sxs-lookup"><span data-stu-id="f9d01-106">F# provides conversion operators for arithmetic conversions between various primitive types, such as between integer and floating point types.</span></span> <span data-ttu-id="f9d01-107">Sprawdzeniu operatory konwersji liczbę całkowitą i char i unchecked formularze; zmiennoprzecinkowy operatorów i `enum` nie obsługują operatora konwersji.</span><span class="sxs-lookup"><span data-stu-id="f9d01-107">The integral and char conversion operators have checked and unchecked forms; the floating point operators and the `enum` conversion operator do not.</span></span> <span data-ttu-id="f9d01-108">Unchecked formularze są definiowane w `Microsoft.FSharp.Core.Operators` i sprawdzonych formularze są definiowane w `Microsoft.FSharp.Core.Operators.Checked`.</span><span class="sxs-lookup"><span data-stu-id="f9d01-108">The unchecked forms are defined in `Microsoft.FSharp.Core.Operators` and the checked forms are defined in `Microsoft.FSharp.Core.Operators.Checked`.</span></span> <span data-ttu-id="f9d01-109">Checked formularzy sprawdzaj przepełnienie i wygenerować wyjątek czasu wykonywania, jeśli wartość wynikowa przekracza limit typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="f9d01-109">The checked forms check for overflow and generate a runtime exception if the resulting value exceeds the limits of the target type.</span></span>

<span data-ttu-id="f9d01-110">Każda z tych operatorów ma taką samą nazwę jak nazwa typu miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="f9d01-110">Each of these operators has the same name as the name of the destination type.</span></span> <span data-ttu-id="f9d01-111">Na przykład, w następujący kod, w którym typy są jawnie adnotację, `byte` pojawia się z dwóch różne znaczenie.</span><span class="sxs-lookup"><span data-stu-id="f9d01-111">For example, in the following code, in which the types are explicitly annotated, `byte` appears with two different meanings.</span></span> <span data-ttu-id="f9d01-112">Pierwsze wystąpienie jest typem, a drugą jest wartość operatora konwersji.</span><span class="sxs-lookup"><span data-stu-id="f9d01-112">The first occurrence is the type and the second is the conversion operator.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

<span data-ttu-id="f9d01-113">W poniższej tabeli przedstawiono operatory konwersji zdefiniowane w F#.</span><span class="sxs-lookup"><span data-stu-id="f9d01-113">The following table shows conversion operators defined in F#.</span></span>

|<span data-ttu-id="f9d01-114">Operator</span><span class="sxs-lookup"><span data-stu-id="f9d01-114">Operator</span></span>|<span data-ttu-id="f9d01-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f9d01-115">Description</span></span>|
|--------|-----------|
|`byte`|<span data-ttu-id="f9d01-116">Konwertuj na wartość bajtu, 8-bitowy typ bez znaku.</span><span class="sxs-lookup"><span data-stu-id="f9d01-116">Convert to byte, an 8-bit unsigned type.</span></span>|
|`sbyte`|<span data-ttu-id="f9d01-117">Konwertuj na bajt oznaczony.</span><span class="sxs-lookup"><span data-stu-id="f9d01-117">Convert to signed byte.</span></span>|
|`int16`|<span data-ttu-id="f9d01-118">Konwertuj na wartość całkowita 16-bitowych.</span><span class="sxs-lookup"><span data-stu-id="f9d01-118">Convert to a 16-bit signed integer.</span></span>|
|`uint16`|<span data-ttu-id="f9d01-119">Konwertuj na wartość 16-bitowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="f9d01-119">Convert to a 16-bit unsigned integer.</span></span>|
|`int32, int`|<span data-ttu-id="f9d01-120">Konwertuj na wartość całkowita 32-bitowych.</span><span class="sxs-lookup"><span data-stu-id="f9d01-120">Convert to a 32-bit signed integer.</span></span>|
|`uint32`|<span data-ttu-id="f9d01-121">Konwertuj na 32-bitowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="f9d01-121">Convert to a 32-bit unsigned integer.</span></span>|
|`int64`|<span data-ttu-id="f9d01-122">Konwertuj na wartość całkowita 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="f9d01-122">Convert to a 64-bit signed integer.</span></span>|
|`uint64`|<span data-ttu-id="f9d01-123">Konwertuj na wartość 64-bitowej nieoznaczonej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="f9d01-123">Convert to a 64-bit unsigned integer.</span></span>|
|`nativeint`|<span data-ttu-id="f9d01-124">Konwertuj na wartość całkowitą natywnych.</span><span class="sxs-lookup"><span data-stu-id="f9d01-124">Convert to a native integer.</span></span>|
|`unativeint`|<span data-ttu-id="f9d01-125">Konwertuj na wartość całkowitą bez znaku natywnych.</span><span class="sxs-lookup"><span data-stu-id="f9d01-125">Convert to an unsigned native integer.</span></span>|
|`float, double`|<span data-ttu-id="f9d01-126">Konwertuj na IEEE podwójnej precyzji 64-bitowych, liczba zmiennoprzecinkowa.</span><span class="sxs-lookup"><span data-stu-id="f9d01-126">Convert to a 64-bit double-precision IEEE floating point number.</span></span>|
|`float32, single`|<span data-ttu-id="f9d01-127">Konwertuj na IEEE pojedynczej precyzji 32-bitowa liczba zmiennoprzecinkowa.</span><span class="sxs-lookup"><span data-stu-id="f9d01-127">Convert to a 32-bit single-precision IEEE floating point number.</span></span>|
|`decimal`|<span data-ttu-id="f9d01-128">Konwertuj na `System.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="f9d01-128">Convert to `System.Decimal`.</span></span>|
|`char`|<span data-ttu-id="f9d01-129">Konwertuj na `System.Char`, znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="f9d01-129">Convert to `System.Char`, a Unicode character.</span></span>|
|`enum`|<span data-ttu-id="f9d01-130">Konwertuj na typ wyliczany.</span><span class="sxs-lookup"><span data-stu-id="f9d01-130">Convert to an enumerated type.</span></span>|

<span data-ttu-id="f9d01-131">Oprócz wbudowanych typów pierwotnych, można użyć tych operatorów z typami, które implementują `op_Explicit` lub `op_Implicit` metod z odpowiednią sygnaturą.</span><span class="sxs-lookup"><span data-stu-id="f9d01-131">In addition to built-in primitive types, you can use these operators with types that implement `op_Explicit` or `op_Implicit` methods with appropriate signatures.</span></span> <span data-ttu-id="f9d01-132">Na przykład `int` operatora konwersji współpracuje z dowolnego typu, który udostępnia metodę statyczną `op_Explicit` która przyjmuje typ jako parametr i zwraca `int`.</span><span class="sxs-lookup"><span data-stu-id="f9d01-132">For example, the `int` conversion operator works with any type that provides a static method `op_Explicit` that takes the type as a parameter and returns `int`.</span></span> <span data-ttu-id="f9d01-133">Jako specjalne wyjątek ogólną zasadą, że typem zwracanym nie mogą być przeciążone metody, można to zrobić `op_Explicit` i `op_Implicit`.</span><span class="sxs-lookup"><span data-stu-id="f9d01-133">As a special exception to the general rule that methods cannot be overloaded by return type, you can do this for `op_Explicit` and `op_Implicit`.</span></span>

## <a name="enumerated-types"></a><span data-ttu-id="f9d01-134">Typy wyliczone</span><span class="sxs-lookup"><span data-stu-id="f9d01-134">Enumerated Types</span></span>

<span data-ttu-id="f9d01-135">`enum` Operator jest ogólny operator, który przyjmuje jeden parametr typu, który reprezentuje typ `enum` do przekonwertowania na.</span><span class="sxs-lookup"><span data-stu-id="f9d01-135">The `enum` operator is a generic operator that takes one type parameter that represents the type of the `enum` to convert to.</span></span> <span data-ttu-id="f9d01-136">Gdy są konwertowane na typ wyliczany, wpisz wnioskowania próbuje określić typ `enum` , którą chcesz przekonwertować.</span><span class="sxs-lookup"><span data-stu-id="f9d01-136">When it converts to an enumerated type, type inference attempts to determine the type of the `enum` that you want to convert to.</span></span> <span data-ttu-id="f9d01-137">W poniższym przykładzie zmienna `col1` nie jest jawnie oznaczona, ale jego typ jest wnioskowany z nowszych testu równości.</span><span class="sxs-lookup"><span data-stu-id="f9d01-137">In the following example, the variable `col1` is not explicitly annotated, but its type is inferred from the later equality test.</span></span> <span data-ttu-id="f9d01-138">W związku z tym, kompilator może wywnioskować, jest konwertowane na `Color` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f9d01-138">Therefore, the compiler can deduce that you are converting to a `Color` enumeration.</span></span> <span data-ttu-id="f9d01-139">Alternatywnie, można podać adnotacji typu, podobnie jak w przypadku `col2` w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f9d01-139">Alternatively, you can supply a type annotation, as with `col2` in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

<span data-ttu-id="f9d01-140">Typ wyliczeniowy docelowym można również określić jawnie, co parametr typu zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="f9d01-140">You can also specify the target enumeration type explicitly as a type parameter, as in the following code:</span></span>

```fsharp
let col3 = enum<Color> 3
```

<span data-ttu-id="f9d01-141">Należy pamiętać, wyliczenia rzutuje pracy, tylko wtedy, gdy podstawowy typ wyliczenia jest niezgodny z typem konwersji.</span><span class="sxs-lookup"><span data-stu-id="f9d01-141">Note that the enumeration casts work only if the underlying type of the enumeration is compatible with the type being converted.</span></span> <span data-ttu-id="f9d01-142">W poniższym kodzie konwersji nie powiedzie się skompilować z powodu niezgodności między `int32` i `uint32`.</span><span class="sxs-lookup"><span data-stu-id="f9d01-142">In the following code, the conversion fails to compile because of the mismatch between `int32` and `uint32`.</span></span>

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

<span data-ttu-id="f9d01-143">Aby uzyskać więcej informacji, zobacz [wyliczenia](enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="f9d01-143">For more information, see [Enumerations](enumerations.md).</span></span>

## <a name="casting-object-types"></a><span data-ttu-id="f9d01-144">Rzutowanie typów obiektów</span><span class="sxs-lookup"><span data-stu-id="f9d01-144">Casting Object Types</span></span>

<span data-ttu-id="f9d01-145">Konwersja między typami w hierarchii obiektów ma podstawowe znaczenie dla programowania obiektowego.</span><span class="sxs-lookup"><span data-stu-id="f9d01-145">Conversion between types in an object hierarchy is fundamental to object-oriented programming.</span></span> <span data-ttu-id="f9d01-146">Istnieją dwa podstawowe rodzaje konwersje: rzutowanie w górę (Rzutowanie rozszerzające) i rzutowanie w dół (rzutowanie).</span><span class="sxs-lookup"><span data-stu-id="f9d01-146">There are two basic types of conversions: casting up (upcasting) and casting down (downcasting).</span></span> <span data-ttu-id="f9d01-147">Rzutowanie hierarchii oznacza rzutowanie z odwołaniem pochodnego obiektu do obiektu podstawowego odwołania.</span><span class="sxs-lookup"><span data-stu-id="f9d01-147">Casting up a hierarchy means casting from a derived object reference to a base object reference.</span></span> <span data-ttu-id="f9d01-148">Takie rzutowanie jest gwarantowane tak długo, jak klasy bazowej znajduje się w hierarchii dziedziczenia klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="f9d01-148">Such a cast is guaranteed to work as long as the base class is in the inheritance hierarchy of the derived class.</span></span> <span data-ttu-id="f9d01-149">Rzutowanie w dół hierarchii z obiektu podstawowego odwołania do odwołanie do obiektu pochodnej, zakończy się powodzeniem, tylko wtedy, gdy obiekt jest rzeczywiście wystąpienia typu odpowiedniego miejsca docelowego (derived) lub typ pochodzący od typu miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="f9d01-149">Casting down a hierarchy, from a base object reference to a derived object reference, succeeds only if the object actually is an instance of the correct destination (derived) type or a type derived from the destination type.</span></span>

<span data-ttu-id="f9d01-150">F#zawiera operatory dla tych typów konwersji.</span><span class="sxs-lookup"><span data-stu-id="f9d01-150">F# provides operators for these types of conversions.</span></span> <span data-ttu-id="f9d01-151">`:>` Operator rzutuje w hierarchii i `:?>` rzutuje operatora w dół hierarchii.</span><span class="sxs-lookup"><span data-stu-id="f9d01-151">The `:>` operator casts up the hierarchy, and the `:?>` operator casts down the hierarchy.</span></span>

### <a name="upcasting"></a><span data-ttu-id="f9d01-152">Rzutowanie rozszerzające</span><span class="sxs-lookup"><span data-stu-id="f9d01-152">Upcasting</span></span>

<span data-ttu-id="f9d01-153">W wielu językach obiektowych Rzutowanie rozszerzające jest niejawne; w F#, zasady są nieco inne.</span><span class="sxs-lookup"><span data-stu-id="f9d01-153">In many object-oriented languages, upcasting is implicit; in F#, the rules are slightly different.</span></span> <span data-ttu-id="f9d01-154">Rzutowanie rozszerzające jest stosowane automatycznie, gdy argument jest przekazywany do metody typu obiektu.</span><span class="sxs-lookup"><span data-stu-id="f9d01-154">Upcasting is applied automatically when you pass arguments to methods on an object type.</span></span> <span data-ttu-id="f9d01-155">W przypadku funkcji powiązanych z umożliwiają w module Rzutowanie rozszerzające nie jest jednak automatyczne, chyba że typ parametru jest zadeklarowany jako typ elastyczne.</span><span class="sxs-lookup"><span data-stu-id="f9d01-155">However, for let-bound functions in a module, upcasting is not automatic, unless the parameter type is declared as a flexible type.</span></span> <span data-ttu-id="f9d01-156">Aby uzyskać więcej informacji, zobacz [typy elastyczne](flexible-Types.md).</span><span class="sxs-lookup"><span data-stu-id="f9d01-156">For more information, see [Flexible Types](flexible-Types.md).</span></span>

<span data-ttu-id="f9d01-157">`:>` Operator wykonuje statyczną rzutowania, co oznacza, że sukces rzutowanie jest określana w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f9d01-157">The `:>` operator performs a static cast, which means that the success of the cast is determined at compile time.</span></span> <span data-ttu-id="f9d01-158">Jeśli rzutowania, który używa `:>` kompiluje pomyślnie, jest prawidłowy rzutowania i ma nie ryzyko wystąpienia awarii w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f9d01-158">If a cast that uses `:>` compiles successfully, it is a valid cast and has no chance of failure at run time.</span></span>

<span data-ttu-id="f9d01-159">Można również użyć `upcast` operatora w celu wykonania takich konwersji.</span><span class="sxs-lookup"><span data-stu-id="f9d01-159">You can also use the `upcast` operator to perform such a conversion.</span></span> <span data-ttu-id="f9d01-160">Poniższe wyrażenie określa konwersji w hierarchii:</span><span class="sxs-lookup"><span data-stu-id="f9d01-160">The following expression specifies a conversion up the hierarchy:</span></span>

```fsharp
upcast expression
```

<span data-ttu-id="f9d01-161">Gdy używasz upcast — operator, kompilator spróbuje wywnioskować typu, który jest konwertowane na z kontekstu.</span><span class="sxs-lookup"><span data-stu-id="f9d01-161">When you use the upcast operator, the compiler attempts to infer the type you are converting to from the context.</span></span> <span data-ttu-id="f9d01-162">Jeśli kompilator nie może określić typu docelowego, kompilator zgłosi błąd.</span><span class="sxs-lookup"><span data-stu-id="f9d01-162">If the compiler is unable to determine the target type, the compiler reports an error.</span></span>

### <a name="downcasting"></a><span data-ttu-id="f9d01-163">Rzutowanie</span><span class="sxs-lookup"><span data-stu-id="f9d01-163">Downcasting</span></span>

<span data-ttu-id="f9d01-164">`:?>` Operator wykonuje dynamiczny rzutowania, co oznacza, że sukces rzutowanie jest określana w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f9d01-164">The `:?>` operator performs a dynamic cast, which means that the success of the cast is determined at run time.</span></span> <span data-ttu-id="f9d01-165">Rzutowania, który używa `:?>` operator nie jest sprawdzana w czasie kompilacji; ale w czasie wykonywania, zostanie podjęta próba rzutowanie do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="f9d01-165">A cast that uses the `:?>` operator is not checked at compile time; but at run time, an attempt is made to cast to the specified type.</span></span> <span data-ttu-id="f9d01-166">Jeśli obiekt jest zgodny z typem docelowym, rzutowanie zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f9d01-166">If the object is compatible with the target type, the cast succeeds.</span></span> <span data-ttu-id="f9d01-167">Jeśli obiekt nie jest zgodny z typem docelowym, środowisko uruchomieniowe zgłasza `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="f9d01-167">If the object is not compatible with the target type, the runtime raises an `InvalidCastException`.</span></span>

<span data-ttu-id="f9d01-168">Można również użyć `downcast` operatora w celu wykonania konwersji typu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="f9d01-168">You can also use the `downcast` operator to perform a dynamic type conversion.</span></span> <span data-ttu-id="f9d01-169">Poniższe wyrażenie określa konwersji w dół hierarchii do typu, który jest wnioskowany z kontekstu programu:</span><span class="sxs-lookup"><span data-stu-id="f9d01-169">The following expression specifies a conversion down the hierarchy to a type that is inferred from program context:</span></span>

```fsharp
downcast expression
```

<span data-ttu-id="f9d01-170">Jak w przypadku `upcast` operatora, jeśli kompilator nie można wywnioskować typu konkretnego docelowego z kontekstu, zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="f9d01-170">As for the `upcast` operator, if the compiler cannot infer a specific target type from the context, it reports an error.</span></span>

<span data-ttu-id="f9d01-171">Poniższy kod ilustruje sposób korzystania z `:>` i `:?>` operatorów.</span><span class="sxs-lookup"><span data-stu-id="f9d01-171">The following code illustrates the use of the `:>` and `:?>` operators.</span></span> <span data-ttu-id="f9d01-172">Kod pokazuje, że `:?>` operator najlepiej jest używany, gdy wiadomo, że konwersja kończy się pomyślnie, ponieważ w wyniku weryfikacji zgłasza wyjątek `InvalidCastException` Jeśli konwersja nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="f9d01-172">The code illustrates that the `:?>` operator is best used when you know that conversion will succeed, because it throws `InvalidCastException` if the conversion fails.</span></span> <span data-ttu-id="f9d01-173">Jeśli nie wiesz, że konwersja powiedzie się, test typ, który używa `match` lepiej jest wyrażenia, ponieważ eliminuje narzut generowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f9d01-173">If you do not know that a conversion will succeed, a type test that uses a `match` expression is better because it avoids the overhead of generating an exception.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

<span data-ttu-id="f9d01-174">Ponieważ operatory ogólny `downcast` i `upcast` polegają na wnioskowanie o typie, aby określić typ argumentów i w powyższym kodzie, można zastąpić</span><span class="sxs-lookup"><span data-stu-id="f9d01-174">Because generic operators `downcast` and `upcast` rely on type inference to determine the argument and return type, in the above code, you can replace</span></span>

```fsharp
let base1 = d1 :> Base1
```

<span data-ttu-id="f9d01-175">with</span><span class="sxs-lookup"><span data-stu-id="f9d01-175">with</span></span>

```fsharp
let base1 = upcast d1
```

<span data-ttu-id="f9d01-176">W poprzednim kodzie typ argumentu i zwracane typy są `Derived1` i `Base1`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="f9d01-176">In the previous code, the argument type and return types are `Derived1` and `Base1`, respectively.</span></span>

<span data-ttu-id="f9d01-177">Aby uzyskać więcej informacji na temat testów typ zobacz [wyrażenia dopasowań](match-Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f9d01-177">For more information about type tests, see [Match Expressions](match-Expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f9d01-178">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9d01-178">See also</span></span>

- [<span data-ttu-id="f9d01-179">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="f9d01-179">F# Language Reference</span></span>](index.md)
