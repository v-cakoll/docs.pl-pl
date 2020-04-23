---
title: ref — słowo kluczowe — odwołanie do języka C#
ms.date: 04/21/2020
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 07e1b49605c83908f7b9af25e0cb2599a97257c5
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102076"
---
# <a name="ref-c-reference"></a><span data-ttu-id="1aa19-102">ref (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1aa19-102">ref (C# Reference)</span></span>

<span data-ttu-id="1aa19-103">Słowo `ref` kluczowe wskazuje wartość, która jest przekazywana przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="1aa19-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="1aa19-104">Jest on używany w czterech różnych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="1aa19-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="1aa19-105">W podpisie metody i w wywołaniu metody, aby przekazać argument do metody przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="1aa19-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="1aa19-106">Aby uzyskać więcej informacji, zobacz [Przekazywanie argumentu przez odwołanie](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="1aa19-106">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="1aa19-107">W podpisie metody, aby zwrócić wartość do wywołującego przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="1aa19-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="1aa19-108">Aby uzyskać więcej informacji, zobacz [Odwołanie do wartości zwracanej](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="1aa19-108">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="1aa19-109">W treści elementu członkowskiego, aby wskazać, że wartość zwracana odwołania jest przechowywana lokalnie jako odwołanie, które obiekt wywołujący zamierza zmodyfikować lub, ogólnie rzecz biorąc, zmienna lokalna uzyskuje dostęp do innej wartości przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="1aa19-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="1aa19-110">Aby uzyskać więcej informacji, zobacz [Ref locals](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="1aa19-110">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="1aa19-111">W `struct` oświadczeniu o `ref struct` zadeklarowaniu a lub . `readonly ref struct`</span><span class="sxs-lookup"><span data-stu-id="1aa19-111">In a `struct` declaration to declare a `ref struct` or a `readonly ref struct`.</span></span> <span data-ttu-id="1aa19-112">Aby uzyskać więcej [ `ref` ](../builtin-types/struct.md#ref-struct) informacji, zobacz sekcję struktury [struktury struktury typów](../builtin-types/struct.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="1aa19-112">For more information, see the [`ref` struct](../builtin-types/struct.md#ref-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="1aa19-113">Przekazywanie argumentu przez odwołanie</span><span class="sxs-lookup"><span data-stu-id="1aa19-113">Passing an argument by reference</span></span>

<span data-ttu-id="1aa19-114">Gdy jest używany na liście parametrów metody, `ref` słowo kluczowe wskazuje, że argument jest przekazywany przez odwołanie, a nie przez wartość.</span><span class="sxs-lookup"><span data-stu-id="1aa19-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="1aa19-115">Słowo `ref` kluczowe sprawia, że parametr formalny alias dla argumentu, który musi być zmienną.</span><span class="sxs-lookup"><span data-stu-id="1aa19-115">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="1aa19-116">Innymi słowy, każda operacja na parametr jest na argument.</span><span class="sxs-lookup"><span data-stu-id="1aa19-116">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="1aa19-117">Na przykład jeśli obiekt wywołujący przekazuje wyrażenie zmiennej lokalnej lub wyrażenie dostępu do elementu tablicy, a wywołana metoda zastępuje obiekt, do którego odwołuje się parametr ref, zmienna lokalna wywołującego lub element tablicy odwołuje się teraz do nowego obiektu, gdy metoda zwraca.</span><span class="sxs-lookup"><span data-stu-id="1aa19-117">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller's local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="1aa19-118">Nie należy mylić pojęcia przekazywania przez odniesienie z pojęciem typów odwołań.</span><span class="sxs-lookup"><span data-stu-id="1aa19-118">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="1aa19-119">Te dwie koncepcje nie są takie same.</span><span class="sxs-lookup"><span data-stu-id="1aa19-119">The two concepts are not the same.</span></span> <span data-ttu-id="1aa19-120">Parametr metody można modyfikować, `ref` niezależnie od tego, czy jest to typ wartości, czy typ odwołania.</span><span class="sxs-lookup"><span data-stu-id="1aa19-120">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="1aa19-121">Nie ma boksu typu wartości, gdy jest przekazywany przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="1aa19-121">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="1aa19-122">Aby użyć `ref` parametru, zarówno definicji metody i metody `ref` wywołującej należy jawnie użyć słowa kluczowego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1aa19-122">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="1aa19-123">Argument, który jest `ref` przekazywany do lub `in` parametru musi być zainicjowany przed przekazaniem.</span><span class="sxs-lookup"><span data-stu-id="1aa19-123">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="1aa19-124">Różni [się](out-parameter-modifier.md) to od out parametrów, których argumenty nie muszą być jawnie zainicjowane przed ich przekazaniem.</span><span class="sxs-lookup"><span data-stu-id="1aa19-124">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="1aa19-125">Członkowie klasy nie mogą mieć podpisów, `ref`które `in`różnią `out`się tylko przez , lub .</span><span class="sxs-lookup"><span data-stu-id="1aa19-125">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="1aa19-126">Błąd kompilatora występuje, jeśli jedyną różnicą między dwoma `ref` elementami członkowskich typu `out`jest `in` to, że jeden z nich ma parametr, a drugi ma parametr , lub.</span><span class="sxs-lookup"><span data-stu-id="1aa19-126">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="1aa19-127">Poniższy kod, na przykład, nie skompilować.</span><span class="sxs-lookup"><span data-stu-id="1aa19-127">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="1aa19-128">Jednak metody mogą być przeciążone, `ref`gdy `in`jedna `out` metoda ma , lub parametr, a druga ma parametr wartości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1aa19-128">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="1aa19-129">W innych sytuacjach, które wymagają dopasowywania `in`podpisu, `out` takich jak ukrywanie lub zastępowanie, i `ref`są częścią podpisu i nie pasują do siebie.</span><span class="sxs-lookup"><span data-stu-id="1aa19-129">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="1aa19-130">Właściwości nie są zmiennymi.</span><span class="sxs-lookup"><span data-stu-id="1aa19-130">Properties are not variables.</span></span> <span data-ttu-id="1aa19-131">Są to metody i nie `ref` można ich przekazać do parametrów.</span><span class="sxs-lookup"><span data-stu-id="1aa19-131">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="1aa19-132">Nie można użyć `ref`programu `in`, `out` i słów kluczowych dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="1aa19-132">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="1aa19-133">Metody asynchroniowe, które można zdefiniować za pomocą modyfikatora [asynchronii.](async.md)</span><span class="sxs-lookup"><span data-stu-id="1aa19-133">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="1aa19-134">Metody iteratora, które zawierają `yield break` [zwrotu wydajności](yield.md) lub instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1aa19-134">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>

<span data-ttu-id="1aa19-135">Ponadto [metody rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md) mają następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="1aa19-135">In addition, [extension methods](../../programming-guide/classes-and-structs/extension-methods.md) have the following restrictions:</span></span>

- <span data-ttu-id="1aa19-136">Nie `out` można użyć słowa kluczowego w pierwszym argumie metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="1aa19-136">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="1aa19-137">Nie `ref` można użyć słowa kluczowego w pierwszym argumie metody rozszerzenia, gdy argument nie jest strukturą lub typem rodzajowym, który nie jest ograniczony do struktury.</span><span class="sxs-lookup"><span data-stu-id="1aa19-137">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="1aa19-138">Nie `in` można użyć słowa kluczowego, chyba że pierwszy argument jest strukturą.</span><span class="sxs-lookup"><span data-stu-id="1aa19-138">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="1aa19-139">Słowo `in` kluczowe nie może być używane dla dowolnego typu rodzajowego, nawet jeśli jest ograniczona do struktury.</span><span class="sxs-lookup"><span data-stu-id="1aa19-139">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="1aa19-140">Przekazywanie argumentu przez odwołanie: Przykład</span><span class="sxs-lookup"><span data-stu-id="1aa19-140">Passing an argument by reference: An example</span></span>

<span data-ttu-id="1aa19-141">Poprzednie przykłady przekazać typy wartości przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="1aa19-141">The previous examples pass value types by reference.</span></span> <span data-ttu-id="1aa19-142">Za pomocą słowa `ref` kluczowego można również przekazać typy odwołań według odwołań.</span><span class="sxs-lookup"><span data-stu-id="1aa19-142">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="1aa19-143">Przekazywanie typu odwołania przez odwołanie umożliwia wywołaną metodę, aby zastąpić obiekt, do którego odwołuje się parametr odwołania w wywołującym.</span><span class="sxs-lookup"><span data-stu-id="1aa19-143">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="1aa19-144">Lokalizacja przechowywania obiektu jest przekazywana do metody jako wartość parametru referencyjnego.</span><span class="sxs-lookup"><span data-stu-id="1aa19-144">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="1aa19-145">Jeśli zmienisz wartość w lokalizacji przechowywania parametru (aby wskazać nowy obiekt), można również zmienić lokalizację magazynu, do którego odwołuje się obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="1aa19-145">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="1aa19-146">Poniższy przykład przekazuje wystąpienie typu `ref` odwołania jako parametr.</span><span class="sxs-lookup"><span data-stu-id="1aa19-146">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="1aa19-147">Aby uzyskać więcej informacji na temat przekazywania typów odwołań według wartości i odwołania, zobacz [Przekazywanie parametrów typu odwołania](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="1aa19-147">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="1aa19-148">Odwoływanie się do zwracanych wartości</span><span class="sxs-lookup"><span data-stu-id="1aa19-148">Reference return values</span></span>

<span data-ttu-id="1aa19-149">Odwołania zwraca wartości (lub ref zwraca) są wartości, które metoda zwraca przez odwołanie do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="1aa19-149">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="1aa19-150">Oznacza to, że obiekt wywołujący można zmodyfikować wartość zwróconą przez metodę, a ta zmiana jest odzwierciedlana w stanie obiektu w metodzie wywołującej.</span><span class="sxs-lookup"><span data-stu-id="1aa19-150">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object in the calling method.</span></span>

<span data-ttu-id="1aa19-151">Referencyjna wartość zwracana jest `ref` definiowana przy użyciu słowa kluczowego:</span><span class="sxs-lookup"><span data-stu-id="1aa19-151">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="1aa19-152">W podpisie metody.</span><span class="sxs-lookup"><span data-stu-id="1aa19-152">In the method signature.</span></span> <span data-ttu-id="1aa19-153">Na przykład następujące podpis metody wskazuje, `GetCurrentPrice` że <xref:System.Decimal> metoda zwraca wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="1aa19-153">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="1aa19-154">Między `return` tokenem a zmienną `return` zwróconą w instrukcji w metodzie.</span><span class="sxs-lookup"><span data-stu-id="1aa19-154">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="1aa19-155">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1aa19-155">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="1aa19-156">Aby obiekt wywołujący zmodyfikował stan obiektu, wartość zwracana odwołanie musi być przechowywana w zmiennej jawnie zdefiniowanej jako [ref local](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="1aa19-156">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="1aa19-157">Oto bardziej kompletny przykład ref return, pokazujący zarówno podpis metody, jak i treść metody.</span><span class="sxs-lookup"><span data-stu-id="1aa19-157">Here is a more complete ref return example, showing both the method signature and method body.</span></span>

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

<span data-ttu-id="1aa19-158">Wywołana metoda może również zadeklarować wartość zwracaną, `ref readonly` aby zwrócić wartość przez odwołanie i wymusić, że kod wywołujący nie może zmodyfikować zwróconą wartość.</span><span class="sxs-lookup"><span data-stu-id="1aa19-158">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="1aa19-159">Wywołanie metoda można uniknąć kopiowania zwracane wartości przez przechowywanie wartości w lokalnym [ref tylko](#ref-readonly-locals) zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1aa19-159">The calling method can avoid copying the returned valued by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="1aa19-160">Na przykład zobacz [A ref zwraca i ref locals przykład](#a-ref-returns-and-ref-locals-example).</span><span class="sxs-lookup"><span data-stu-id="1aa19-160">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="1aa19-161">Ref miejscowi</span><span class="sxs-lookup"><span data-stu-id="1aa19-161">Ref locals</span></span>

<span data-ttu-id="1aa19-162">Zmienna lokalna ref jest używana `return ref`do odwoływania się do wartości zwracanych przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="1aa19-162">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="1aa19-163">Zmiennej lokalnej ref nie można zainicjować do wartości zwracanej non-ref.</span><span class="sxs-lookup"><span data-stu-id="1aa19-163">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="1aa19-164">Innymi słowy po prawej stronie inicjowania musi być odwołanie.</span><span class="sxs-lookup"><span data-stu-id="1aa19-164">In other words, the right-hand side of the initialization must be a reference.</span></span> <span data-ttu-id="1aa19-165">Wszelkie modyfikacje wartości ref local są odzwierciedlane w stanie obiektu, którego metoda zwróciła wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="1aa19-165">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="1aa19-166">Można zdefiniować ref lokalnych `ref` przy użyciu słowa kluczowego przed deklaracją zmiennej, a także bezpośrednio przed wywołaniem metody, która zwraca wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="1aa19-166">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="1aa19-167">Na przykład następująca instrukcja definiuje wartość lokalną ref, `GetEstimatedValue`która jest zwracana przez metodę o nazwie:</span><span class="sxs-lookup"><span data-stu-id="1aa19-167">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="1aa19-168">Można uzyskać dostęp do wartości przez odwołanie w ten sam sposób.</span><span class="sxs-lookup"><span data-stu-id="1aa19-168">You can access a value by reference in the same way.</span></span> <span data-ttu-id="1aa19-169">W niektórych przypadkach dostęp do wartości przez odwołanie zwiększa wydajność, unikając potencjalnie kosztownej operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="1aa19-169">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="1aa19-170">Na przykład poniższa instrukcja pokazuje, jak można zdefiniować wartość lokalną ref, która jest używana do odwoływania się do wartości.</span><span class="sxs-lookup"><span data-stu-id="1aa19-170">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="1aa19-171">W obu przykładach `ref` słowo kluczowe musi być używane w obu miejscach lub kompilator generuje błąd CS8172, "Nie można zainicjować zmiennej by-reference z wartością."</span><span class="sxs-lookup"><span data-stu-id="1aa19-171">In both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="1aa19-172">Począwszy od C# 7.3, zmienną `foreach` iteracji instrukcji może być ref zmiennej lokalnej lub ref readonly zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="1aa19-172">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="1aa19-173">Aby uzyskać więcej informacji, zobacz artykuł [instrukcji foreach.](foreach-in.md)</span><span class="sxs-lookup"><span data-stu-id="1aa19-173">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

<span data-ttu-id="1aa19-174">Również począwszy od C# 7.3, można ponownie przypisać ref lokalnej lub ref readonly zmiennej lokalnej z [operatorem przypisania ref](../operators/assignment-operator.md#ref-assignment-operator).</span><span class="sxs-lookup"><span data-stu-id="1aa19-174">Also beginning with C# 7.3, you can reassign a ref local or ref readonly local variable with the [ref assignment operator](../operators/assignment-operator.md#ref-assignment-operator).</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="1aa19-175">Ref czytajnie tylko miejscowi</span><span class="sxs-lookup"><span data-stu-id="1aa19-175">Ref readonly locals</span></span>

<span data-ttu-id="1aa19-176">Ref readonly local jest używany do odwoływania się do `ref readonly` wartości zwracanych `return ref`przez metodę lub właściwość, która ma w podpisie i używa .</span><span class="sxs-lookup"><span data-stu-id="1aa19-176">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="1aa19-177">Zmienna `ref readonly` łączy właściwości zmiennej `ref` lokalnej ze `readonly` zmienną: jest aliasem magazynu, do których jest przypisana i nie można jej zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="1aa19-177">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span>

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="1aa19-178">Ref zwraca i ref przykład lokalnych</span><span class="sxs-lookup"><span data-stu-id="1aa19-178">A ref returns and ref locals example</span></span>

<span data-ttu-id="1aa19-179">Poniższy przykład definiuje `Book` klasę, <xref:System.String> która `Title` ma `Author`dwa pola i .</span><span class="sxs-lookup"><span data-stu-id="1aa19-179">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="1aa19-180">Definiuje również `BookCollection` klasę, która zawiera prywatną tablicę `Book` obiektów.</span><span class="sxs-lookup"><span data-stu-id="1aa19-180">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="1aa19-181">Poszczególne obiekty książki są zwracane `GetBookByTitle` przez odwołanie, wywołując jego metody.</span><span class="sxs-lookup"><span data-stu-id="1aa19-181">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="1aa19-182">Gdy obiekt wywołujący przechowuje `GetBookByTitle` wartość zwróconą przez metodę jako ref local, zmiany, które `BookCollection` obiekt wywołujący sprawia, że do wartości zwracanej są odzwierciedlane w obiekcie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1aa19-182">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="1aa19-183">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1aa19-183">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1aa19-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1aa19-184">See also</span></span>

- [<span data-ttu-id="1aa19-185">Napisz bezpieczny skuteczny kod</span><span class="sxs-lookup"><span data-stu-id="1aa19-185">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="1aa19-186">Wartości zwracane ref i zmienne lokalne ref</span><span class="sxs-lookup"><span data-stu-id="1aa19-186">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="1aa19-187">Warunkowe wyrażenie ref</span><span class="sxs-lookup"><span data-stu-id="1aa19-187">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="1aa19-188">Przekazywanie parametrów</span><span class="sxs-lookup"><span data-stu-id="1aa19-188">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="1aa19-189">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="1aa19-189">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="1aa19-190">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="1aa19-190">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1aa19-191">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="1aa19-191">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1aa19-192">C# Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="1aa19-192">C# Keywords</span></span>](index.md)
