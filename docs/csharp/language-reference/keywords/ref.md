---
title: ref — słowo kluczowe — odwołanie do języka C#
ms.date: 03/19/2020
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: d54d932ca96f1966ecc05a532a2468b7e16fac46
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805846"
---
# <a name="ref-c-reference"></a><span data-ttu-id="f2bbc-102">ref (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f2bbc-102">ref (C# Reference)</span></span>

<span data-ttu-id="f2bbc-103">Słowo `ref` kluczowe wskazuje wartość, która jest przekazywana przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="f2bbc-104">Jest on używany w czterech różnych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="f2bbc-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="f2bbc-105">W podpisie metody i w wywołaniu metody, aby przekazać argument do metody przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="f2bbc-106">Aby uzyskać więcej informacji, zobacz [Przekazywanie argumentu przez odwołanie](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="f2bbc-106">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="f2bbc-107">W podpisie metody, aby zwrócić wartość do wywołującego przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="f2bbc-108">Aby uzyskać więcej informacji, zobacz [Odwołanie do wartości zwracanej](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="f2bbc-108">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="f2bbc-109">W treści elementu członkowskiego, aby wskazać, że wartość zwracana odwołania jest przechowywana lokalnie jako odwołanie, które obiekt wywołujący zamierza zmodyfikować lub, ogólnie rzecz biorąc, zmienna lokalna uzyskuje dostęp do innej wartości przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="f2bbc-110">Aby uzyskać więcej informacji, zobacz [Ref locals](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="f2bbc-110">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="f2bbc-111">W `struct` oświadczeniu o `ref struct` zadeklarowaniu a lub . `readonly ref struct`</span><span class="sxs-lookup"><span data-stu-id="f2bbc-111">In a `struct` declaration to declare a `ref struct` or a `readonly ref struct`.</span></span> <span data-ttu-id="f2bbc-112">Aby uzyskać więcej informacji, zobacz [typy struktury ref](#ref-struct-types).</span><span class="sxs-lookup"><span data-stu-id="f2bbc-112">For more information, see [ref struct types](#ref-struct-types).</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="f2bbc-113">Przekazywanie argumentu przez odwołanie</span><span class="sxs-lookup"><span data-stu-id="f2bbc-113">Passing an argument by reference</span></span>

<span data-ttu-id="f2bbc-114">Gdy jest używany na liście parametrów metody, `ref` słowo kluczowe wskazuje, że argument jest przekazywany przez odwołanie, a nie przez wartość.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="f2bbc-115">Słowo `ref` kluczowe sprawia, że parametr formalny alias dla argumentu, który musi być zmienną.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-115">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="f2bbc-116">Innymi słowy, każda operacja na parametr jest na argument.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-116">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="f2bbc-117">Na przykład jeśli obiekt wywołujący przekazuje wyrażenie zmiennej lokalnej lub wyrażenie dostępu do elementu tablicy, a wywołana metoda zastępuje obiekt, do którego odwołuje się parametr ref, zmienna lokalna wywołującego lub element tablicy odwołuje się teraz do nowego obiektu, gdy metoda zwraca.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-117">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller's local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="f2bbc-118">Nie należy mylić pojęcia przekazywania przez odniesienie z pojęciem typów odwołań.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-118">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="f2bbc-119">Te dwie koncepcje nie są takie same.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-119">The two concepts are not the same.</span></span> <span data-ttu-id="f2bbc-120">Parametr metody można modyfikować, `ref` niezależnie od tego, czy jest to typ wartości, czy typ odwołania.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-120">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="f2bbc-121">Nie ma boksu typu wartości, gdy jest przekazywany przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-121">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="f2bbc-122">Aby użyć `ref` parametru, zarówno definicji metody i metody `ref` wywołującej należy jawnie użyć słowa kluczowego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-122">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="f2bbc-123">Argument, który jest `ref` przekazywany do lub `in` parametru musi być zainicjowany przed przekazaniem.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-123">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="f2bbc-124">Różni [się](out-parameter-modifier.md) to od out parametrów, których argumenty nie muszą być jawnie zainicjowane przed ich przekazaniem.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-124">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="f2bbc-125">Członkowie klasy nie mogą mieć podpisów, `ref`które `in`różnią `out`się tylko przez , lub .</span><span class="sxs-lookup"><span data-stu-id="f2bbc-125">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="f2bbc-126">Błąd kompilatora występuje, jeśli jedyną różnicą między dwoma `ref` elementami członkowskich typu `out`jest `in` to, że jeden z nich ma parametr, a drugi ma parametr , lub.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-126">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="f2bbc-127">Poniższy kod, na przykład, nie skompilować.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-127">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="f2bbc-128">Jednak metody mogą być przeciążone, `ref`gdy `in`jedna `out` metoda ma , lub parametr, a druga ma parametr wartości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-128">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="f2bbc-129">W innych sytuacjach, które wymagają dopasowywania `in`podpisu, `out` takich jak ukrywanie lub zastępowanie, i `ref`są częścią podpisu i nie pasują do siebie.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-129">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="f2bbc-130">Właściwości nie są zmiennymi.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-130">Properties are not variables.</span></span> <span data-ttu-id="f2bbc-131">Są to metody i nie `ref` można ich przekazać do parametrów.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-131">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="f2bbc-132">Nie można użyć `ref`programu `in`, `out` i słów kluczowych dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="f2bbc-132">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="f2bbc-133">Metody asynchroniowe, które można zdefiniować za pomocą modyfikatora [asynchronii.](async.md)</span><span class="sxs-lookup"><span data-stu-id="f2bbc-133">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="f2bbc-134">Metody iteratora, które zawierają `yield break` [zwrotu wydajności](yield.md) lub instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-134">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>

<span data-ttu-id="f2bbc-135">Ponadto [metody rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md) mają następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="f2bbc-135">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="f2bbc-136">Nie `out` można użyć słowa kluczowego w pierwszym argumie metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-136">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="f2bbc-137">Nie `ref` można użyć słowa kluczowego w pierwszym argumie metody rozszerzenia, gdy argument nie jest strukturą lub typem rodzajowym, który nie jest ograniczony do struktury.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-137">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="f2bbc-138">Nie `in` można użyć słowa kluczowego, chyba że pierwszy argument jest strukturą.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-138">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="f2bbc-139">Słowo `in` kluczowe nie może być używane dla dowolnego typu rodzajowego, nawet jeśli jest ograniczona do struktury.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-139">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="f2bbc-140">Przekazywanie argumentu przez odwołanie: Przykład</span><span class="sxs-lookup"><span data-stu-id="f2bbc-140">Passing an argument by reference: An example</span></span>

<span data-ttu-id="f2bbc-141">Poprzednie przykłady przekazać typy wartości przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-141">The previous examples pass value types by reference.</span></span> <span data-ttu-id="f2bbc-142">Za pomocą słowa `ref` kluczowego można również przekazać typy odwołań według odwołań.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-142">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="f2bbc-143">Przekazywanie typu odwołania przez odwołanie umożliwia wywołaną metodę, aby zastąpić obiekt, do którego odwołuje się parametr odwołania w wywołującym.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-143">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="f2bbc-144">Lokalizacja przechowywania obiektu jest przekazywana do metody jako wartość parametru referencyjnego.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-144">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="f2bbc-145">Jeśli zmienisz wartość w lokalizacji przechowywania parametru (aby wskazać nowy obiekt), można również zmienić lokalizację magazynu, do którego odwołuje się obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-145">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="f2bbc-146">Poniższy przykład przekazuje wystąpienie typu `ref` odwołania jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-146">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="f2bbc-147">Aby uzyskać więcej informacji na temat przekazywania typów odwołań według wartości i odwołania, zobacz [Przekazywanie parametrów typu odwołania](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f2bbc-147">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="f2bbc-148">Odwoływanie się do zwracanych wartości</span><span class="sxs-lookup"><span data-stu-id="f2bbc-148">Reference return values</span></span>

<span data-ttu-id="f2bbc-149">Odwołania zwraca wartości (lub ref zwraca) są wartości, które metoda zwraca przez odwołanie do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-149">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="f2bbc-150">Oznacza to, że obiekt wywołujący można zmodyfikować wartość zwróconą przez metodę, a ta zmiana jest odzwierciedlana w stanie obiektu, który zawiera metodę.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-150">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span>

<span data-ttu-id="f2bbc-151">Referencyjna wartość zwracana jest `ref` definiowana przy użyciu słowa kluczowego:</span><span class="sxs-lookup"><span data-stu-id="f2bbc-151">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="f2bbc-152">W podpisie metody.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-152">In the method signature.</span></span> <span data-ttu-id="f2bbc-153">Na przykład następujące podpis metody wskazuje, `GetCurrentPrice` że <xref:System.Decimal> metoda zwraca wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-153">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="f2bbc-154">Między `return` tokenem a zmienną `return` zwróconą w instrukcji w metodzie.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-154">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="f2bbc-155">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f2bbc-155">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="f2bbc-156">Aby obiekt wywołujący zmodyfikował stan obiektu, wartość zwracana odwołanie musi być przechowywana w zmiennej jawnie zdefiniowanej jako [ref local](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="f2bbc-156">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="f2bbc-157">Wywołana metoda może również zadeklarować wartość zwracaną, `ref readonly` aby zwrócić wartość przez odwołanie i wymusić, że kod wywołujący nie może zmodyfikować zwróconą wartość.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-157">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="f2bbc-158">Wywołanie metoda można uniknąć kopiowania zwracane wartości przez przechowywanie wartości w lokalnym [ref tylko](#ref-readonly-locals) zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-158">The calling method can avoid copying the returned valued by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="f2bbc-159">Na przykład zobacz [A ref zwraca i ref locals przykład](#a-ref-returns-and-ref-locals-example).</span><span class="sxs-lookup"><span data-stu-id="f2bbc-159">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="f2bbc-160">Ref miejscowi</span><span class="sxs-lookup"><span data-stu-id="f2bbc-160">Ref locals</span></span>

<span data-ttu-id="f2bbc-161">Zmienna lokalna ref jest używana `return ref`do odwoływania się do wartości zwracanych przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="f2bbc-161">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="f2bbc-162">Zmiennej lokalnej ref nie można zainicjować do wartości zwracanej non-ref.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-162">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="f2bbc-163">Innymi słowy po prawej stronie inicjowania musi być odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-163">In other words, the right-hand side of the initialization must be a reference.</span></span> <span data-ttu-id="f2bbc-164">Wszelkie modyfikacje wartości ref local są odzwierciedlane w stanie obiektu, którego metoda zwróciła wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-164">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="f2bbc-165">Można zdefiniować ref lokalnych `ref` przy użyciu słowa kluczowego przed deklaracją zmiennej, a także bezpośrednio przed wywołaniem metody, która zwraca wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-165">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="f2bbc-166">Na przykład następująca instrukcja definiuje wartość lokalną ref, `GetEstimatedValue`która jest zwracana przez metodę o nazwie:</span><span class="sxs-lookup"><span data-stu-id="f2bbc-166">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="f2bbc-167">Można uzyskać dostęp do wartości przez odwołanie w ten sam sposób.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-167">You can access a value by reference in the same way.</span></span> <span data-ttu-id="f2bbc-168">W niektórych przypadkach dostęp do wartości przez odwołanie zwiększa wydajność, unikając potencjalnie kosztownej operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-168">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="f2bbc-169">Na przykład poniższa instrukcja pokazuje, jak można zdefiniować wartość lokalną ref, która jest używana do odwoływania się do wartości.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-169">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="f2bbc-170">W obu przykładach `ref` słowo kluczowe musi być używane w obu miejscach lub kompilator generuje błąd CS8172, "Nie można zainicjować zmiennej by-reference z wartością."</span><span class="sxs-lookup"><span data-stu-id="f2bbc-170">In both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="f2bbc-171">Począwszy od C# 7.3, zmienną `foreach` iteracji instrukcji może być ref zmiennej lokalnej lub ref readonly zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-171">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="f2bbc-172">Aby uzyskać więcej informacji, zobacz artykuł [instrukcji foreach.](foreach-in.md)</span><span class="sxs-lookup"><span data-stu-id="f2bbc-172">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

<span data-ttu-id="f2bbc-173">Również począwszy od C# 7.3, można ponownie przypisać ref lokalnej lub ref readonly zmiennej lokalnej z [operatorem przypisania ref](../operators/assignment-operator.md#ref-assignment-operator).</span><span class="sxs-lookup"><span data-stu-id="f2bbc-173">Also beginning with C# 7.3, you can reassign a ref local or ref readonly local variable with the [ref assignment operator](../operators/assignment-operator.md#ref-assignment-operator).</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="f2bbc-174">Ref czytajnie tylko miejscowi</span><span class="sxs-lookup"><span data-stu-id="f2bbc-174">Ref readonly locals</span></span>

<span data-ttu-id="f2bbc-175">Ref readonly local jest używany do odwoływania się do `ref readonly` wartości zwracanych `return ref`przez metodę lub właściwość, która ma w podpisie i używa .</span><span class="sxs-lookup"><span data-stu-id="f2bbc-175">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="f2bbc-176">Zmienna `ref readonly` łączy właściwości zmiennej `ref` lokalnej ze `readonly` zmienną: jest aliasem magazynu, do których jest przypisana i nie można jej zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-176">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span>

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="f2bbc-177">Ref zwraca i ref przykład lokalnych</span><span class="sxs-lookup"><span data-stu-id="f2bbc-177">A ref returns and ref locals example</span></span>

<span data-ttu-id="f2bbc-178">Poniższy przykład definiuje `Book` klasę, <xref:System.String> która `Title` ma `Author`dwa pola i .</span><span class="sxs-lookup"><span data-stu-id="f2bbc-178">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="f2bbc-179">Definiuje również `BookCollection` klasę, która zawiera prywatną tablicę `Book` obiektów.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-179">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="f2bbc-180">Poszczególne obiekty książki są zwracane `GetBookByTitle` przez odwołanie, wywołując jego metody.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-180">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="f2bbc-181">Gdy obiekt wywołujący przechowuje `GetBookByTitle` wartość zwróconą przez metodę jako ref local, zmiany, które `BookCollection` obiekt wywołujący sprawia, że do wartości zwracanej są odzwierciedlane w obiekcie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-181">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a><span data-ttu-id="f2bbc-182">Ref struct typów</span><span class="sxs-lookup"><span data-stu-id="f2bbc-182">Ref struct types</span></span>

<span data-ttu-id="f2bbc-183">Dodanie `ref` modyfikatora `struct` do deklaracji definiuje, że wystąpienia tego typu muszą być przydzielone stos.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-183">Adding the `ref` modifier to a `struct` declaration defines that instances of that type must be stack allocated.</span></span> <span data-ttu-id="f2bbc-184">Innymi słowy wystąpienia tych typów nigdy nie mogą być tworzone na stosie jako członek innej klasy.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-184">In other words, instances of these types can never be created on the heap as a member of another class.</span></span> <span data-ttu-id="f2bbc-185">Główną motywacją dla <xref:System.Span%601> tej funkcji były i powiązane struktury.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-185">The primary motivation for this feature was <xref:System.Span%601> and related structures.</span></span>

<span data-ttu-id="f2bbc-186">Celem zachowania `ref struct` typu jako zmiennej przydzielonej do stosu wprowadza kilka reguł, które kompilator wymusza dla wszystkich `ref struct` typów.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-186">The goal of keeping a `ref struct` type as a stack-allocated variable introduces several rules that the compiler enforces for all `ref struct` types.</span></span>

- <span data-ttu-id="f2bbc-187">Nie można pole `ref struct`.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-187">You can't box a `ref struct`.</span></span> <span data-ttu-id="f2bbc-188">Nie można `ref struct` przypisać typu do `object`zmiennej typu `dynamic`lub dowolnego typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-188">You cannot assign a `ref struct` type to a variable of type `object`, `dynamic`, or any interface type.</span></span>
- <span data-ttu-id="f2bbc-189">`ref struct`typy nie można zaimplementować interfejsów.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-189">`ref struct` types cannot implement interfaces.</span></span>
- <span data-ttu-id="f2bbc-190">Nie można zadeklarować `ref struct` jako członka pola klasy lub normalnej struktury.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-190">You can't declare a `ref struct` as a field member of a class or a normal struct.</span></span> <span data-ttu-id="f2bbc-191">Obejmuje to deklarowanie właściwości zaimplementowane automatycznie, która tworzy pole zapasowe generowane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-191">This includes declaring an auto-implemented property, which creates a compiler-generated backing field.</span></span>
- <span data-ttu-id="f2bbc-192">Nie można zadeklarować zmiennych lokalnych, które są `ref struct` typami w metodach asynchronizacyjnych.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-192">You cannot declare local variables that are `ref struct` types in async methods.</span></span> <span data-ttu-id="f2bbc-193">Można zadeklarować je w metodach <xref:System.Threading.Tasks.Task>synchronicznych, które zwracają , <xref:System.Threading.Tasks.Task%601>lub `Task`-like typów.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-193">You can declare them in synchronous methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `Task`-like types.</span></span>
- <span data-ttu-id="f2bbc-194">Nie można `ref struct` zadeklarować zmiennych lokalnych w iteratorach.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-194">You cannot declare `ref struct` local variables in iterators.</span></span>
- <span data-ttu-id="f2bbc-195">Nie można `ref struct` przechwycić zmiennych w wyrażeniach lambda lub funkcji lokalnych.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-195">You cannot capture `ref struct` variables in lambda expressions or local functions.</span></span>

<span data-ttu-id="f2bbc-196">Te ograniczenia upewnij się, że `ref struct` nie przypadkowo używać w sposób, który może promować go do zarządzanego stosu.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-196">These restrictions ensure you don't accidentally use a `ref struct` in a manner that could promote it to the managed heap.</span></span>

<span data-ttu-id="f2bbc-197">Można połączyć modyfikatory, aby `readonly ref`zadeklarować strukturę jako .</span><span class="sxs-lookup"><span data-stu-id="f2bbc-197">You can combine modifiers to declare a struct as `readonly ref`.</span></span> <span data-ttu-id="f2bbc-198">A `readonly ref struct` łączy korzyści i ograniczenia `ref struct` `readonly struct` i deklaracje.</span><span class="sxs-lookup"><span data-stu-id="f2bbc-198">A `readonly ref struct` combines the benefits and restrictions of `ref struct` and `readonly struct` declarations.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f2bbc-199">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f2bbc-199">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f2bbc-200">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2bbc-200">See also</span></span>

- [<span data-ttu-id="f2bbc-201">Napisz bezpieczny skuteczny kod</span><span class="sxs-lookup"><span data-stu-id="f2bbc-201">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="f2bbc-202">Wartości zwracane ref i zmienne lokalne ref</span><span class="sxs-lookup"><span data-stu-id="f2bbc-202">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="f2bbc-203">Warunkowe wyrażenie ref</span><span class="sxs-lookup"><span data-stu-id="f2bbc-203">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="f2bbc-204">Przekazywanie parametrów</span><span class="sxs-lookup"><span data-stu-id="f2bbc-204">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="f2bbc-205">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="f2bbc-205">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="f2bbc-206">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="f2bbc-206">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f2bbc-207">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="f2bbc-207">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f2bbc-208">C# Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="f2bbc-208">C# Keywords</span></span>](index.md)
