---
title: Rzutowanie i konwersje
description: Dowiedz się F# , jak język programowania zapewnia operatory konwersji dla konwersji arytmetycznych między różnymi typami pierwotnymi.
ms.date: 02/20/2020
ms.openlocfilehash: 5f9727d14a7ae070e0f0f71fa0a0abe04f662071
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543589"
---
# <a name="casting-and-conversions-f"></a><span data-ttu-id="97346-103">Rzutowanie i konwersje (F#)</span><span class="sxs-lookup"><span data-stu-id="97346-103">Casting and Conversions (F#)</span></span>

<span data-ttu-id="97346-104">W tym temacie opisano obsługę konwersji typów w F#.</span><span class="sxs-lookup"><span data-stu-id="97346-104">This topic describes support for type conversions in F#.</span></span>

## <a name="arithmetic-types"></a><span data-ttu-id="97346-105">Typy arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="97346-105">Arithmetic Types</span></span>

<span data-ttu-id="97346-106">F#zapewnia operatory konwersji dla konwersji arytmetycznych między różnymi typami pierwotnymi, takimi jak między liczbami całkowitymi i zmiennoprzecinkowymi.</span><span class="sxs-lookup"><span data-stu-id="97346-106">F# provides conversion operators for arithmetic conversions between various primitive types, such as between integer and floating point types.</span></span> <span data-ttu-id="97346-107">Operatory konwersji całek i char mają sprawdzone i niesprawdzone formularze; Operatory zmiennoprzecinkowe i operator konwersji `enum` nie.</span><span class="sxs-lookup"><span data-stu-id="97346-107">The integral and char conversion operators have checked and unchecked forms; the floating point operators and the `enum` conversion operator do not.</span></span> <span data-ttu-id="97346-108">Niesprawdzone formularze są zdefiniowane w `Microsoft.FSharp.Core.Operators`, a zaznaczone formularze są zdefiniowane w `Microsoft.FSharp.Core.Operators.Checked`.</span><span class="sxs-lookup"><span data-stu-id="97346-108">The unchecked forms are defined in `Microsoft.FSharp.Core.Operators` and the checked forms are defined in `Microsoft.FSharp.Core.Operators.Checked`.</span></span> <span data-ttu-id="97346-109">Sprawdzone formularze sprawdzają przepełnienie i generują wyjątek czasu wykonywania, jeśli wartość wyników przekracza limity typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="97346-109">The checked forms check for overflow and generate a runtime exception if the resulting value exceeds the limits of the target type.</span></span>

<span data-ttu-id="97346-110">Każdy z tych operatorów ma taką samą nazwę jak nazwa typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="97346-110">Each of these operators has the same name as the name of the destination type.</span></span> <span data-ttu-id="97346-111">Na przykład, w poniższym kodzie, w którym typy są jawnie adnotacje, `byte` pojawia się z dwoma różnymi znaczeniami.</span><span class="sxs-lookup"><span data-stu-id="97346-111">For example, in the following code, in which the types are explicitly annotated, `byte` appears with two different meanings.</span></span> <span data-ttu-id="97346-112">Pierwsze wystąpienie jest typem, a drugi jest operatorem konwersji.</span><span class="sxs-lookup"><span data-stu-id="97346-112">The first occurrence is the type and the second is the conversion operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

<span data-ttu-id="97346-113">W poniższej tabeli przedstawiono operatory konwersji zdefiniowane w F#.</span><span class="sxs-lookup"><span data-stu-id="97346-113">The following table shows conversion operators defined in F#.</span></span>

|<span data-ttu-id="97346-114">Operator</span><span class="sxs-lookup"><span data-stu-id="97346-114">Operator</span></span>|<span data-ttu-id="97346-115">Opis</span><span class="sxs-lookup"><span data-stu-id="97346-115">Description</span></span>|
|--------|-----------|
|`byte`|<span data-ttu-id="97346-116">Konwertuj na bajt, 8-bitowy typ unsigned.</span><span class="sxs-lookup"><span data-stu-id="97346-116">Convert to byte, an 8-bit unsigned type.</span></span>|
|`sbyte`|<span data-ttu-id="97346-117">Konwertuj na bajt ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="97346-117">Convert to signed byte.</span></span>|
|`int16`|<span data-ttu-id="97346-118">Konwertuj na 16-bitową liczbę całkowitą ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="97346-118">Convert to a 16-bit signed integer.</span></span>|
|`uint16`|<span data-ttu-id="97346-119">Konwertuj na 16-bitową liczbę całkowitą bez znaku.</span><span class="sxs-lookup"><span data-stu-id="97346-119">Convert to a 16-bit unsigned integer.</span></span>|
|`int32, int`|<span data-ttu-id="97346-120">Konwertuj na 32-bitową liczbę całkowitą ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="97346-120">Convert to a 32-bit signed integer.</span></span>|
|`uint32`|<span data-ttu-id="97346-121">Konwertuj na 32-bitową liczbę całkowitą bez znaku.</span><span class="sxs-lookup"><span data-stu-id="97346-121">Convert to a 32-bit unsigned integer.</span></span>|
|`int64`|<span data-ttu-id="97346-122">Konwertuj na 64-bitową liczbę całkowitą ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="97346-122">Convert to a 64-bit signed integer.</span></span>|
|`uint64`|<span data-ttu-id="97346-123">Konwertuj na 64-bitową liczbę całkowitą bez znaku.</span><span class="sxs-lookup"><span data-stu-id="97346-123">Convert to a 64-bit unsigned integer.</span></span>|
|`nativeint`|<span data-ttu-id="97346-124">Konwertuj na natywną liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="97346-124">Convert to a native integer.</span></span>|
|`unativeint`|<span data-ttu-id="97346-125">Konwertuj na nieniepodpisana liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="97346-125">Convert to an unsigned native integer.</span></span>|
|`float, double`|<span data-ttu-id="97346-126">Konwertuj na 64-bitową liczbę zmiennoprzecinkową IEEE o podwójnej precyzji.</span><span class="sxs-lookup"><span data-stu-id="97346-126">Convert to a 64-bit double-precision IEEE floating point number.</span></span>|
|`float32, single`|<span data-ttu-id="97346-127">Konwertuj na 32-bitową liczbę zmiennoprzecinkową IEEE o pojedynczej precyzji.</span><span class="sxs-lookup"><span data-stu-id="97346-127">Convert to a 32-bit single-precision IEEE floating point number.</span></span>|
|`decimal`|<span data-ttu-id="97346-128">Konwertuj na `System.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="97346-128">Convert to `System.Decimal`.</span></span>|
|`char`|<span data-ttu-id="97346-129">Konwertuj na `System.Char`, znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="97346-129">Convert to `System.Char`, a Unicode character.</span></span>|
|`enum`|<span data-ttu-id="97346-130">Konwertuj na typ wyliczeniowy.</span><span class="sxs-lookup"><span data-stu-id="97346-130">Convert to an enumerated type.</span></span>|

<span data-ttu-id="97346-131">Oprócz wbudowanych typów pierwotnych można używać tych operatorów z typami, które implementują `op_Explicit` lub `op_Implicit` metody z odpowiednimi sygnaturami.</span><span class="sxs-lookup"><span data-stu-id="97346-131">In addition to built-in primitive types, you can use these operators with types that implement `op_Explicit` or `op_Implicit` methods with appropriate signatures.</span></span> <span data-ttu-id="97346-132">Na przykład operator konwersji `int` działa z dowolnym typem, który udostępnia metodę statyczną `op_Explicit`, która przyjmuje typ jako parametr i zwraca `int`.</span><span class="sxs-lookup"><span data-stu-id="97346-132">For example, the `int` conversion operator works with any type that provides a static method `op_Explicit` that takes the type as a parameter and returns `int`.</span></span> <span data-ttu-id="97346-133">Jako specjalny wyjątek do ogólnej reguły, że metody nie mogą być przeciążone przez zwracany typ, można to zrobić dla `op_Explicit` i `op_Implicit`.</span><span class="sxs-lookup"><span data-stu-id="97346-133">As a special exception to the general rule that methods cannot be overloaded by return type, you can do this for `op_Explicit` and `op_Implicit`.</span></span>

## <a name="enumerated-types"></a><span data-ttu-id="97346-134">Typy wyliczeniowe</span><span class="sxs-lookup"><span data-stu-id="97346-134">Enumerated Types</span></span>

<span data-ttu-id="97346-135">Operator `enum` jest operatorem ogólnym, który przyjmuje jeden parametr typu, który reprezentuje typ `enum` do przekonwertowania.</span><span class="sxs-lookup"><span data-stu-id="97346-135">The `enum` operator is a generic operator that takes one type parameter that represents the type of the `enum` to convert to.</span></span> <span data-ttu-id="97346-136">Podczas konwertowania na typ wyliczeniowy, wnioskowanie typu próbuje określić typ `enum`, do którego chcesz dokonać konwersji.</span><span class="sxs-lookup"><span data-stu-id="97346-136">When it converts to an enumerated type, type inference attempts to determine the type of the `enum` that you want to convert to.</span></span> <span data-ttu-id="97346-137">W poniższym przykładzie zmienna `col1` nie jest jawnie oznaczona adnotacją, ale jej typ jest wnioskowany z późniejszego testu równości.</span><span class="sxs-lookup"><span data-stu-id="97346-137">In the following example, the variable `col1` is not explicitly annotated, but its type is inferred from the later equality test.</span></span> <span data-ttu-id="97346-138">W związku z tym kompilator może wywnioskować, że jest konwertowany na Wyliczenie `Color`.</span><span class="sxs-lookup"><span data-stu-id="97346-138">Therefore, the compiler can deduce that you are converting to a `Color` enumeration.</span></span> <span data-ttu-id="97346-139">Alternatywnie można podać adnotację typu, tak jak w przypadku `col2` w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="97346-139">Alternatively, you can supply a type annotation, as with `col2` in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

<span data-ttu-id="97346-140">Można również określić typ wyliczenia docelowego jawnie jako parametr typu, jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="97346-140">You can also specify the target enumeration type explicitly as a type parameter, as in the following code:</span></span>

```fsharp
let col3 = enum<Color> 3
```

<span data-ttu-id="97346-141">Należy zauważyć, że rzutowania wyliczenia działa tylko wtedy, gdy typ podstawowy wyliczenia jest zgodny z konwertowanym typem.</span><span class="sxs-lookup"><span data-stu-id="97346-141">Note that the enumeration casts work only if the underlying type of the enumeration is compatible with the type being converted.</span></span> <span data-ttu-id="97346-142">W poniższym kodzie konwersja nie zostanie skompilowana z powodu niezgodności między `int32` i `uint32`.</span><span class="sxs-lookup"><span data-stu-id="97346-142">In the following code, the conversion fails to compile because of the mismatch between `int32` and `uint32`.</span></span>

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

<span data-ttu-id="97346-143">Aby uzyskać więcej informacji, zobacz [wyliczenia](enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="97346-143">For more information, see [Enumerations](enumerations.md).</span></span>

## <a name="casting-object-types"></a><span data-ttu-id="97346-144">Rzutowanie typów obiektów</span><span class="sxs-lookup"><span data-stu-id="97346-144">Casting Object Types</span></span>

<span data-ttu-id="97346-145">Konwersja między typami w hierarchii obiektów jest podstawowa dla programowania zorientowanego obiektowo.</span><span class="sxs-lookup"><span data-stu-id="97346-145">Conversion between types in an object hierarchy is fundamental to object-oriented programming.</span></span> <span data-ttu-id="97346-146">Istnieją dwa podstawowe typy konwersji: Rzutowanie w górę (Rzutowanie) i Rzutowanie w dół (Rzutowanie).</span><span class="sxs-lookup"><span data-stu-id="97346-146">There are two basic types of conversions: casting up (upcasting) and casting down (downcasting).</span></span> <span data-ttu-id="97346-147">Rzutowanie hierarchii oznacza rzutowanie z odwołania do obiektu pochodnego na odwołanie do obiektu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="97346-147">Casting up a hierarchy means casting from a derived object reference to a base object reference.</span></span> <span data-ttu-id="97346-148">Takie Rzutowanie jest gwarantowane, o ile Klasa bazowa znajduje się w hierarchii dziedziczenia klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="97346-148">Such a cast is guaranteed to work as long as the base class is in the inheritance hierarchy of the derived class.</span></span> <span data-ttu-id="97346-149">Rzutowanie w dół hierarchii, od odwołania do obiektu podstawowego do odwołania do obiektu pochodnego, powiedzie się tylko wtedy, gdy obiekt faktycznie jest wystąpieniem poprawnego typu docelowego (pochodnego) lub typu pochodnego od typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="97346-149">Casting down a hierarchy, from a base object reference to a derived object reference, succeeds only if the object actually is an instance of the correct destination (derived) type or a type derived from the destination type.</span></span>

<span data-ttu-id="97346-150">F#dostarcza operatory dla tego typu konwersji.</span><span class="sxs-lookup"><span data-stu-id="97346-150">F# provides operators for these types of conversions.</span></span> <span data-ttu-id="97346-151">Operator `:>` rzutuje hierarchię, a operator `:?>` rzutuje hierarchię.</span><span class="sxs-lookup"><span data-stu-id="97346-151">The `:>` operator casts up the hierarchy, and the `:?>` operator casts down the hierarchy.</span></span>

### <a name="upcasting"></a><span data-ttu-id="97346-152">Rzutowanie</span><span class="sxs-lookup"><span data-stu-id="97346-152">Upcasting</span></span>

<span data-ttu-id="97346-153">W wielu językach zorientowanych obiektowo Rzutowanie jest niejawne; w F#programie reguły są nieco inne.</span><span class="sxs-lookup"><span data-stu-id="97346-153">In many object-oriented languages, upcasting is implicit; in F#, the rules are slightly different.</span></span> <span data-ttu-id="97346-154">Rzutowanie jest stosowane automatycznie podczas przekazywania argumentów do metod w typie obiektu.</span><span class="sxs-lookup"><span data-stu-id="97346-154">Upcasting is applied automatically when you pass arguments to methods on an object type.</span></span> <span data-ttu-id="97346-155">Jednak w przypadku funkcji z ograniczeniami w module przerzutowanie nie jest automatyczne, chyba że typ parametru jest zadeklarowany jako typ elastyczny.</span><span class="sxs-lookup"><span data-stu-id="97346-155">However, for let-bound functions in a module, upcasting is not automatic, unless the parameter type is declared as a flexible type.</span></span> <span data-ttu-id="97346-156">Aby uzyskać więcej informacji, zobacz [Typy elastyczne](flexible-Types.md).</span><span class="sxs-lookup"><span data-stu-id="97346-156">For more information, see [Flexible Types](flexible-Types.md).</span></span>

<span data-ttu-id="97346-157">Operator `:>` wykonuje statyczne rzutowanie, co oznacza, że powodzenie rzutowania jest określane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="97346-157">The `:>` operator performs a static cast, which means that the success of the cast is determined at compile time.</span></span> <span data-ttu-id="97346-158">Jeśli rzutowanie, które używa `:>` kompiluje się pomyślnie, jest prawidłowym rzutem i nie ma żadnej szansy błędu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="97346-158">If a cast that uses `:>` compiles successfully, it is a valid cast and has no chance of failure at run time.</span></span>

<span data-ttu-id="97346-159">Można również użyć operatora `upcast`, aby wykonać taką konwersję.</span><span class="sxs-lookup"><span data-stu-id="97346-159">You can also use the `upcast` operator to perform such a conversion.</span></span> <span data-ttu-id="97346-160">Następujące wyrażenie określa konwersję w górę hierarchii:</span><span class="sxs-lookup"><span data-stu-id="97346-160">The following expression specifies a conversion up the hierarchy:</span></span>

```fsharp
upcast expression
```

<span data-ttu-id="97346-161">Gdy używasz operatora przerzutowania, kompilator próbuje wywnioskować typ, który jest konwertowany na podstawie kontekstu.</span><span class="sxs-lookup"><span data-stu-id="97346-161">When you use the upcast operator, the compiler attempts to infer the type you are converting to from the context.</span></span> <span data-ttu-id="97346-162">Jeśli kompilator nie może określić typu docelowego, kompilator zgłosi błąd.</span><span class="sxs-lookup"><span data-stu-id="97346-162">If the compiler is unable to determine the target type, the compiler reports an error.</span></span> <span data-ttu-id="97346-163">Może być wymagana adnotacja typu.</span><span class="sxs-lookup"><span data-stu-id="97346-163">A type annotation may be required.</span></span>

### <a name="downcasting"></a><span data-ttu-id="97346-164">Rzutowanie</span><span class="sxs-lookup"><span data-stu-id="97346-164">Downcasting</span></span>

<span data-ttu-id="97346-165">Operator `:?>` wykonuje rzutowanie dynamiczne, co oznacza, że powodzenie rzutowania jest określane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="97346-165">The `:?>` operator performs a dynamic cast, which means that the success of the cast is determined at run time.</span></span> <span data-ttu-id="97346-166">Rzutowanie używające operatora `:?>` nie jest sprawdzane w czasie kompilacji; ale w czasie wykonywania jest podejmowana próba rzutowania na określony typ.</span><span class="sxs-lookup"><span data-stu-id="97346-166">A cast that uses the `:?>` operator is not checked at compile time; but at run time, an attempt is made to cast to the specified type.</span></span> <span data-ttu-id="97346-167">Jeśli obiekt jest zgodny z typem docelowym, Rzutowanie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="97346-167">If the object is compatible with the target type, the cast succeeds.</span></span> <span data-ttu-id="97346-168">Jeśli obiekt nie jest zgodny z typem docelowym, środowisko uruchomieniowe wywołuje `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="97346-168">If the object is not compatible with the target type, the runtime raises an `InvalidCastException`.</span></span>

<span data-ttu-id="97346-169">Można również użyć operatora `downcast`, aby przeprowadzić konwersję typu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="97346-169">You can also use the `downcast` operator to perform a dynamic type conversion.</span></span> <span data-ttu-id="97346-170">Następujące wyrażenie określa konwersję w dół hierarchii do typu, który jest wywnioskowany z kontekstu programu:</span><span class="sxs-lookup"><span data-stu-id="97346-170">The following expression specifies a conversion down the hierarchy to a type that is inferred from program context:</span></span>

```fsharp
downcast expression
```

<span data-ttu-id="97346-171">Jak dla operatora `upcast`, jeśli kompilator nie może wywnioskować określonego typu docelowego z kontekstu, zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="97346-171">As for the `upcast` operator, if the compiler cannot infer a specific target type from the context, it reports an error.</span></span> <span data-ttu-id="97346-172">Może być wymagana adnotacja typu.</span><span class="sxs-lookup"><span data-stu-id="97346-172">A type annotation may be required.</span></span>

<span data-ttu-id="97346-173">Poniższy kod ilustruje użycie operatorów `:>` i `:?>`.</span><span class="sxs-lookup"><span data-stu-id="97346-173">The following code illustrates the use of the `:>` and `:?>` operators.</span></span> <span data-ttu-id="97346-174">Kod ilustruje, że operator `:?>` jest najlepiej używany, gdy wiadomo, że konwersja powiedzie się, ponieważ generuje `InvalidCastException`, jeśli konwersja nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="97346-174">The code illustrates that the `:?>` operator is best used when you know that conversion will succeed, because it throws `InvalidCastException` if the conversion fails.</span></span> <span data-ttu-id="97346-175">Jeśli nie wiesz, że konwersja powiedzie się, test typu, który używa wyrażenia `match`, jest lepszy, ponieważ pozwala uniknąć narzutu na generowanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="97346-175">If you do not know that a conversion will succeed, a type test that uses a `match` expression is better because it avoids the overhead of generating an exception.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

<span data-ttu-id="97346-176">Ponieważ operatory generyczne `downcast` i `upcast` polegają na wnioskach o typie w celu określenia argumentu i zwracanego typu, w powyższym kodzie można zastąpić</span><span class="sxs-lookup"><span data-stu-id="97346-176">Because generic operators `downcast` and `upcast` rely on type inference to determine the argument and return type, in the above code, you can replace</span></span>

```fsharp
let base1 = d1 :> Base1
```

<span data-ttu-id="97346-177">elementem</span><span class="sxs-lookup"><span data-stu-id="97346-177">with</span></span>

```fsharp
let base1: Base1 = upcast d1
```

<span data-ttu-id="97346-178">Należy zauważyć, że adnotacja typu jest wymagana, ponieważ `upcast` przez siebie sama nie mogła ustalić klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="97346-178">Note that a type annotation is required, since `upcast` by itself could not determine the base class.</span></span>

## <a name="see-also"></a><span data-ttu-id="97346-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97346-179">See also</span></span>

- [<span data-ttu-id="97346-180">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="97346-180">F# Language Reference</span></span>](index.md)
