---
title: Rzutowanie i konwersje (F#)
description: "Dowiedz się, jak język programowania w języku F # przewiduje operatory konwersji konwersje arytmetyczne między różnych typów pierwotnych."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: db30db67-da21-4206-bf0c-9211bd3cb22f
ms.openlocfilehash: f17d3919c59c5881213d28a59cea7ae184493949
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="casting-and-conversions-f"></a><span data-ttu-id="0d86b-104">Rzutowanie i konwersje (F#)</span><span class="sxs-lookup"><span data-stu-id="0d86b-104">Casting and Conversions (F#)</span></span>

<span data-ttu-id="0d86b-105">W tym temacie opisano obsługę konwersje typów w języku F #.</span><span class="sxs-lookup"><span data-stu-id="0d86b-105">This topic describes support for type conversions in F#.</span></span>

## <a name="arithmetic-types"></a><span data-ttu-id="0d86b-106">Typów arytmetycznych</span><span class="sxs-lookup"><span data-stu-id="0d86b-106">Arithmetic Types</span></span>
<span data-ttu-id="0d86b-107">F # zawiera operatory konwersji konwersje arytmetyczne między różne typy pierwotne, takich jak między liczb całkowitych i zmiennoprzecinkowych typów.</span><span class="sxs-lookup"><span data-stu-id="0d86b-107">F# provides conversion operators for arithmetic conversions between various primitive types, such as between integer and floating point types.</span></span> <span data-ttu-id="0d86b-108">Operatory konwersji typu całkowitego lub char zaznaczono i niezaznaczone formularze; zmiennoprzecinkowy operatory i `enum` operatora konwersji nie.</span><span class="sxs-lookup"><span data-stu-id="0d86b-108">The integral and char conversion operators have checked and unchecked forms; the floating point operators and the `enum` conversion operator do not.</span></span> <span data-ttu-id="0d86b-109">Zaznaczenie opcji formularze są definiowane w `Microsoft.FSharp.Core.Operators` i zaznaczone formularze są definiowane w `Microsoft.FSharp.Core.Operators.Checked`.</span><span class="sxs-lookup"><span data-stu-id="0d86b-109">The unchecked forms are defined in `Microsoft.FSharp.Core.Operators` and the checked forms are defined in `Microsoft.FSharp.Core.Operators.Checked`.</span></span> <span data-ttu-id="0d86b-110">Checked formularzy sprawdzaj przepełnienie i Generuj wyjątek czasu wykonywania, jeśli wartość wynikową przekracza limity typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="0d86b-110">The checked forms check for overflow and generate a runtime exception if the resulting value exceeds the limits of the target type.</span></span>

<span data-ttu-id="0d86b-111">Każdy z tych operatorów ma taką samą nazwę jak nazwa typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="0d86b-111">Each of these operators has the same name as the name of the destination type.</span></span> <span data-ttu-id="0d86b-112">Na przykład w następującym kodem, w którym mają jawnie adnotacje typów, `byte` pojawi się z dwóch różnych znaczenie.</span><span class="sxs-lookup"><span data-stu-id="0d86b-112">For example, in the following code, in which the types are explicitly annotated, `byte` appears with two different meanings.</span></span> <span data-ttu-id="0d86b-113">Pierwsze wystąpienie znajduje się typ, a drugą jest wartość operatora konwersji.</span><span class="sxs-lookup"><span data-stu-id="0d86b-113">The first occurrence is the type and the second is the conversion operator.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

<span data-ttu-id="0d86b-114">W poniższej tabeli przedstawiono operatory konwersji zdefiniowany w języku F #.</span><span class="sxs-lookup"><span data-stu-id="0d86b-114">The following table shows conversion operators defined in F#.</span></span>

|<span data-ttu-id="0d86b-115">Operator</span><span class="sxs-lookup"><span data-stu-id="0d86b-115">Operator</span></span>|<span data-ttu-id="0d86b-116">Opis</span><span class="sxs-lookup"><span data-stu-id="0d86b-116">Description</span></span>|
|--------|-----------|
|`byte`|<span data-ttu-id="0d86b-117">Konwertuj na bajt, 8-bitowego typu bez znaku.</span><span class="sxs-lookup"><span data-stu-id="0d86b-117">Convert to byte, an 8-bit unsigned type.</span></span>|
|`sbyte`|<span data-ttu-id="0d86b-118">Konwertuj na bajtu ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="0d86b-118">Convert to signed byte.</span></span>|
|`int16`|<span data-ttu-id="0d86b-119">Konwertuj na 16-bitową liczbę całkowitą ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="0d86b-119">Convert to a 16-bit signed integer.</span></span>|
|`uint16`|<span data-ttu-id="0d86b-120">Konwertuj na 16-bitową liczbę całkowitą bez znaku.</span><span class="sxs-lookup"><span data-stu-id="0d86b-120">Convert to a 16-bit unsigned integer.</span></span>|
|`int32, int`|<span data-ttu-id="0d86b-121">Konwertuj na 32-bitowej podpisanej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="0d86b-121">Convert to a 32-bit signed integer.</span></span>|
|`uint32`|<span data-ttu-id="0d86b-122">Konwertuj na 32-bitowej liczby całkowitej bez znaku.</span><span class="sxs-lookup"><span data-stu-id="0d86b-122">Convert to a 32-bit unsigned integer.</span></span>|
|`int64`|<span data-ttu-id="0d86b-123">Konwertuj na 64-bitowej podpisanej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="0d86b-123">Convert to a 64-bit signed integer.</span></span>|
|`uint64`|<span data-ttu-id="0d86b-124">Konwertuj na 64-bitowej liczby całkowitej bez znaku.</span><span class="sxs-lookup"><span data-stu-id="0d86b-124">Convert to a 64-bit unsigned integer.</span></span>|
|`nativeint`|<span data-ttu-id="0d86b-125">Konwertuj natywnego wartości całkowitej.</span><span class="sxs-lookup"><span data-stu-id="0d86b-125">Convert to a native integer.</span></span>|
|`unativeint`|<span data-ttu-id="0d86b-126">Konwertuj na liczbę całkowitą bez znaku macierzystego.</span><span class="sxs-lookup"><span data-stu-id="0d86b-126">Convert to an unsigned native integer.</span></span>|
|`float, double`|<span data-ttu-id="0d86b-127">Konwertuj na 64-bitowych IEEE podwójnej precyzji, liczba zmiennoprzecinkowa.</span><span class="sxs-lookup"><span data-stu-id="0d86b-127">Convert to a 64-bit double-precision IEEE floating point number.</span></span>|
|`float32, single`|<span data-ttu-id="0d86b-128">Konwertuj na 32-bitowych IEEE pojedynczej precyzji, liczba zmiennoprzecinkowa.</span><span class="sxs-lookup"><span data-stu-id="0d86b-128">Convert to a 32-bit single-precision IEEE floating point number.</span></span>|
|`decimal`|<span data-ttu-id="0d86b-129">Konwertuj na `System.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0d86b-129">Convert to `System.Decimal`.</span></span>|
|`char`|<span data-ttu-id="0d86b-130">Konwertuj na `System.Char`, znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="0d86b-130">Convert to `System.Char`, a Unicode character.</span></span>|
|`enum`|<span data-ttu-id="0d86b-131">Konwertuj na typ wyliczeniowy.</span><span class="sxs-lookup"><span data-stu-id="0d86b-131">Convert to an enumerated type.</span></span>|
<span data-ttu-id="0d86b-132">Oprócz wbudowanych typów pierwotnych, obu operatorów można używać z typów, które implementują `op_Explicit` lub `op_Implicit` metod z odpowiednim podpisem.</span><span class="sxs-lookup"><span data-stu-id="0d86b-132">In addition to built-in primitive types, you can use these operators with types that implement `op_Explicit` or `op_Implicit` methods with appropriate signatures.</span></span> <span data-ttu-id="0d86b-133">Na przykład `int` operatora konwersji współpracuje z dowolnego typu, który udostępnia metodę statyczną `op_Explicit` który przyjmuje jako parametr typu i zwraca `int`.</span><span class="sxs-lookup"><span data-stu-id="0d86b-133">For example, the `int` conversion operator works with any type that provides a static method `op_Explicit` that takes the type as a parameter and returns `int`.</span></span> <span data-ttu-id="0d86b-134">Specjalne wyjątku do zasady, że metody nie może zostać przeciążony przez typ zwracany, możesz to zrobić `op_Explicit` i `op_Implicit`.</span><span class="sxs-lookup"><span data-stu-id="0d86b-134">As a special exception to the general rule that methods cannot be overloaded by return type, you can do this for `op_Explicit` and `op_Implicit`.</span></span>

## <a name="enumerated-types"></a><span data-ttu-id="0d86b-135">Typy wyliczane</span><span class="sxs-lookup"><span data-stu-id="0d86b-135">Enumerated Types</span></span>
<span data-ttu-id="0d86b-136">`enum` Operator jest ogólny operator, który przyjmuje jeden parametr typu, który reprezentuje typ `enum` można przekonwertować na.</span><span class="sxs-lookup"><span data-stu-id="0d86b-136">The `enum` operator is a generic operator that takes one type parameter that represents the type of the `enum` to convert to.</span></span> <span data-ttu-id="0d86b-137">Podczas konwertowania na typ wyliczeniowy, wpisz wnioskowania spróbuje określić typ `enum` , który chcesz przekonwertować.</span><span class="sxs-lookup"><span data-stu-id="0d86b-137">When it converts to an enumerated type, type inference attempts to determine the type of the `enum` that you want to convert to.</span></span> <span data-ttu-id="0d86b-138">W poniższym przykładzie zmienna `col1` nie ma jawnie adnotacji, ale jego typ jest wywnioskowany na podstawie nowsze testu równości.</span><span class="sxs-lookup"><span data-stu-id="0d86b-138">In the following example, the variable `col1` is not explicitly annotated, but its type is inferred from the later equality test.</span></span> <span data-ttu-id="0d86b-139">W związku z tym kompilator można wywnioskować, że przekonwertowania na `Color` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="0d86b-139">Therefore, the compiler can deduce that you are converting to a `Color` enumeration.</span></span> <span data-ttu-id="0d86b-140">Alternatywnie możesz podać adnotację typu, jak `col2` w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0d86b-140">Alternatively, you can supply a type annotation, as with `col2` in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]
    
<span data-ttu-id="0d86b-141">Docelowy typ wyliczenia można również określić jawnie jako parametr typu, zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="0d86b-141">You can also specify the target enumeration type explicitly as a type parameter, as in the following code:</span></span>

```fsharp
let col3 = enum<Color> 3
```

<span data-ttu-id="0d86b-142">Należy zwrócić uwagę, czy wyliczenia rzutuje pracy tylko, jeśli typ podstawowy wyliczenia jest niezgodny z typem konwersji.</span><span class="sxs-lookup"><span data-stu-id="0d86b-142">Note that the enumeration casts work only if the underlying type of the enumeration is compatible with the type being converted.</span></span> <span data-ttu-id="0d86b-143">W poniższym kodzie konwersji nie powiedzie się skompilować z powodu niezgodności między `int32` i `uint32`.</span><span class="sxs-lookup"><span data-stu-id="0d86b-143">In the following code, the conversion fails to compile because of the mismatch between `int32` and `uint32`.</span></span>

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

<span data-ttu-id="0d86b-144">Aby uzyskać więcej informacji, zobacz [wyliczenia](enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="0d86b-144">For more information, see [Enumerations](enumerations.md).</span></span>

## <a name="casting-object-types"></a><span data-ttu-id="0d86b-145">Rzutowanie typów obiektów</span><span class="sxs-lookup"><span data-stu-id="0d86b-145">Casting Object Types</span></span>
<span data-ttu-id="0d86b-146">Konwersja między typami w hierarchii obiektów jest niezbędne, aby programowanie zorientowane obiektowo.</span><span class="sxs-lookup"><span data-stu-id="0d86b-146">Conversion between types in an object hierarchy is fundamental to object-oriented programming.</span></span> <span data-ttu-id="0d86b-147">Istnieją dwa typy podstawowe konwersji: rzutowanie w górę (rzutowanie w górę) i rzutowanie w dół (rzutowanie w dół).</span><span class="sxs-lookup"><span data-stu-id="0d86b-147">There are two basic types of conversions: casting up (upcasting) and casting down (downcasting).</span></span> <span data-ttu-id="0d86b-148">Rzutowanie w górę hierarchii oznacza rzutowanie obiektu pochodnego odwołanie do odwołania obiektu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="0d86b-148">Casting up a hierarchy means casting from a derived object reference to a base object reference.</span></span> <span data-ttu-id="0d86b-149">Takie rzutowanie jest gwarantowane tak długo, jak klasa podstawowa jest w hierarchii dziedziczenia klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="0d86b-149">Such a cast is guaranteed to work as long as the base class is in the inheritance hierarchy of the derived class.</span></span> <span data-ttu-id="0d86b-150">Rzutowanie w dół hierarchii z odwołaniem obiektu podstawowego odwołania do obiektu pochodnego powiedzie się tylko wtedy, gdy obiekt jest rzeczywiście wystąpienia typu poprawny docelowy (ustalona) lub typu pochodzącego od typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="0d86b-150">Casting down a hierarchy, from a base object reference to a derived object reference, succeeds only if the object actually is an instance of the correct destination (derived) type or a type derived from the destination type.</span></span>

<span data-ttu-id="0d86b-151">F # zawiera operatory dla tych typów konwersji.</span><span class="sxs-lookup"><span data-stu-id="0d86b-151">F# provides operators for these types of conversions.</span></span> <span data-ttu-id="0d86b-152">`:>` Operator rzutowań w hierarchii i `:?>` operator rzutowań w dół hierarchii.</span><span class="sxs-lookup"><span data-stu-id="0d86b-152">The `:>` operator casts up the hierarchy, and the `:?>` operator casts down the hierarchy.</span></span>

### <a name="upcasting"></a><span data-ttu-id="0d86b-153">Rzutowanie w górę</span><span class="sxs-lookup"><span data-stu-id="0d86b-153">Upcasting</span></span>
<span data-ttu-id="0d86b-154">W wielu językach zorientowane obiektowo rzutowanie w górę jest niejawnie; w języku F # reguły są nieco inne.</span><span class="sxs-lookup"><span data-stu-id="0d86b-154">In many object-oriented languages, upcasting is implicit; in F#, the rules are slightly different.</span></span> <span data-ttu-id="0d86b-155">Rzutowanie w górę jest stosowana automatycznie, gdy argument jest przekazywany do metody typu obiektu.</span><span class="sxs-lookup"><span data-stu-id="0d86b-155">Upcasting is applied automatically when you pass arguments to methods on an object type.</span></span> <span data-ttu-id="0d86b-156">Jednak powiązane z let funkcji w module, rzutowanie w górę nie jest automatyczne, jeśli typ parametru jest zadeklarowany jako typ elastyczne.</span><span class="sxs-lookup"><span data-stu-id="0d86b-156">However, for let-bound functions in a module, upcasting is not automatic, unless the parameter type is declared as a flexible type.</span></span> <span data-ttu-id="0d86b-157">Aby uzyskać więcej informacji, zobacz [typy elastyczne](flexible-Types.md).</span><span class="sxs-lookup"><span data-stu-id="0d86b-157">For more information, see [Flexible Types](flexible-Types.md).</span></span>

<span data-ttu-id="0d86b-158">`:>` Operator wykonuje statycznego rzutowania, co oznacza, że powodzenie rzutowanie jest określana w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0d86b-158">The `:>` operator performs a static cast, which means that the success of the cast is determined at compile time.</span></span> <span data-ttu-id="0d86b-159">Jeśli rzutowania, która używa `:>` kompiluje pomyślnie, jest prawidłową rzutowania i ma bez możliwości błąd w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0d86b-159">If a cast that uses `:>` compiles successfully, it is a valid cast and has no chance of failure at run time.</span></span>

<span data-ttu-id="0d86b-160">Można również użyć `upcast` operatora, aby wykonać takie konwersji.</span><span class="sxs-lookup"><span data-stu-id="0d86b-160">You can also use the `upcast` operator to perform such a conversion.</span></span> <span data-ttu-id="0d86b-161">Poniższe wyrażenie określa konwersji w hierarchii:</span><span class="sxs-lookup"><span data-stu-id="0d86b-161">The following expression specifies a conversion up the hierarchy:</span></span>

```fsharp
upcast expression
```

<span data-ttu-id="0d86b-162">Jeśli używasz upcast — operator kompilator próbuje wnioskować o typie, który ma zostać zmieniony na w kontekście.</span><span class="sxs-lookup"><span data-stu-id="0d86b-162">When you use the upcast operator, the compiler attempts to infer the type you are converting to from the context.</span></span> <span data-ttu-id="0d86b-163">Jeśli nie można określić typ docelowy jest kompilatora, kompilator zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="0d86b-163">If the compiler is unable to determine the target type, the compiler reports an error.</span></span>

### <a name="downcasting"></a><span data-ttu-id="0d86b-164">Rzutowanie w dół</span><span class="sxs-lookup"><span data-stu-id="0d86b-164">Downcasting</span></span>
<span data-ttu-id="0d86b-165">`:?>` Operator wykonuje dynamicznym rzutowania, co oznacza, że powodzenie rzutowanie jest określana w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0d86b-165">The `:?>` operator performs a dynamic cast, which means that the success of the cast is determined at run time.</span></span> <span data-ttu-id="0d86b-166">Rzutowanie, która używa `:?>` operator nie jest zaznaczone pole w czasie kompilacji; ale w czasie wykonywania, próby rzutowanie do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="0d86b-166">A cast that uses the `:?>` operator is not checked at compile time; but at run time, an attempt is made to cast to the specified type.</span></span> <span data-ttu-id="0d86b-167">Jeśli obiekt jest zgodny z typem docelowym, rzutowanie zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0d86b-167">If the object is compatible with the target type, the cast succeeds.</span></span> <span data-ttu-id="0d86b-168">Jeśli obiekt nie jest zgodny z typem docelowym, środowisko uruchomieniowe zgłasza `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="0d86b-168">If the object is not compatible with the target type, the runtime raises an `InvalidCastException`.</span></span>

<span data-ttu-id="0d86b-169">Można również użyć `downcast` operatora, aby dokonać konwersji typu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="0d86b-169">You can also use the `downcast` operator to perform a dynamic type conversion.</span></span> <span data-ttu-id="0d86b-170">Poniższe wyrażenie określa konwersji w dół hierarchii do typu, który jest wywnioskowany na podstawie kontekstu program:</span><span class="sxs-lookup"><span data-stu-id="0d86b-170">The following expression specifies a conversion down the hierarchy to a type that is inferred from program context:</span></span>

```fsharp
downcast expression
```

<span data-ttu-id="0d86b-171">Jak w przypadku `upcast` operatora, jeśli kompilator nie można wnioskować o typie docelowej określonej w kontekście zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="0d86b-171">As for the `upcast` operator, if the compiler cannot infer a specific target type from the context, it reports an error.</span></span>

<span data-ttu-id="0d86b-172">Poniższy kod przedstawia użycie `:>` i `:?>` operatorów.</span><span class="sxs-lookup"><span data-stu-id="0d86b-172">The following code illustrates the use of the `:>` and `:?>` operators.</span></span> <span data-ttu-id="0d86b-173">Kod ilustruje, który `:?>` operator najlepiej jest używany, gdy wiesz, że konwersja kończy się pomyślnie, ponieważ zgłasza `InvalidCastException` Jeśli konwersji nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="0d86b-173">The code illustrates that the `:?>` operator is best used when you know that conversion will succeed, because it throws `InvalidCastException` if the conversion fails.</span></span> <span data-ttu-id="0d86b-174">Jeśli nie wiesz, że konwersji powiedzie się, test typu, który używa `match` wyrażenie jest lepszym rozwiązaniem, ponieważ pozwala ona na uniknięcie koszty generowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="0d86b-174">If you do not know that a conversion will succeed, a type test that uses a `match` expression is better because it avoids the overhead of generating an exception.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

<span data-ttu-id="0d86b-175">Ponieważ operatory ogólnego `downcast` i `upcast` polegać na wnioskowanie o typie, aby określić typ argumentów i w powyższym kodzie, możesz zastąpić</span><span class="sxs-lookup"><span data-stu-id="0d86b-175">Because generic operators `downcast` and `upcast` rely on type inference to determine the argument and return type, in the above code, you can replace</span></span>

```fsharp
let base1 = d1 :> Base1
```

<span data-ttu-id="0d86b-176">with</span><span class="sxs-lookup"><span data-stu-id="0d86b-176">with</span></span>

```fsharp
base1 = upcast d1
```

<span data-ttu-id="0d86b-177">W poprzednim kodzie typ argumentu i zwracane typy są `Derived1` i `Base1`odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="0d86b-177">In the previous code, the argument type and return types are `Derived1` and `Base1`, respectively.</span></span>

<span data-ttu-id="0d86b-178">Aby uzyskać więcej informacji o testach typu, zobacz [wyrażenia dopasowania](match-Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="0d86b-178">For more information about type tests, see [Match Expressions](match-Expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d86b-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d86b-179">See Also</span></span>
[<span data-ttu-id="0d86b-180">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="0d86b-180">F# Language Reference</span></span>](index.md)
