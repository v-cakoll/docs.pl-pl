---
title: ref (odwołanie w C#)
ms.date: 03/06/2018
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: a72624d5702ec12bfda98d49a16474cc84205ff0
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245755"
---
# <a name="ref-c-reference"></a><span data-ttu-id="f6260-102">ref (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f6260-102">ref (C# Reference)</span></span>

<span data-ttu-id="f6260-103">`ref` — Słowo kluczowe wskazuje wartość informującą który jest przekazywany przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f6260-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="f6260-104">Jest on używany w czterech różnych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="f6260-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="f6260-105">W podpisie metody i w wywołaniu metody, aby przekazać argument do metody przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f6260-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="f6260-106">Zobacz [przekazywaniem argumentu według odwołania](#passing-an-argument-by-reference) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="f6260-106">See [Passing an argument by reference](#passing-an-argument-by-reference) for more information.</span></span>
- <span data-ttu-id="f6260-107">W podpisie metody, aby zwrócić wartości do obiektu wywołującego przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f6260-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="f6260-108">Zobacz [wartości zwracane odwołanie](#reference-return-values) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="f6260-108">See [Reference return values](#reference-return-values) for more information.</span></span>
- <span data-ttu-id="f6260-109">W treści elementu członkowskiego aby wskazać, że zwracana wartość odwołania są przechowywane lokalnie, jako odwołanie do obiektu wywołującego zamierza zmienić lub ogólnie rzecz biorąc, zmienna lokalna uzyskuje dostęp do innej wartości przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f6260-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="f6260-110">Zobacz [zmienne lokalne Ref](#ref-locals) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="f6260-110">See [Ref locals](#ref-locals) for more information.</span></span>
- <span data-ttu-id="f6260-111">W `struct` deklaracji, aby zadeklarować `ref struct` lub `ref readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="f6260-111">In a `struct` declaration to declare a `ref struct` or a `ref readonly struct`.</span></span> <span data-ttu-id="f6260-112">Zobacz [deklaracji struktury ref](#ref-struct-declarations) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="f6260-112">See [ref struct declarations](#ref-struct-declarations) for more information.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="f6260-113">Przekazywanie argumentów poprzez odwołanie</span><span class="sxs-lookup"><span data-stu-id="f6260-113">Passing an argument by reference</span></span>

<span data-ttu-id="f6260-114">Gdy są używane w liście parametrów metody, `ref` słowo kluczowe wskazuje, że argument jest przekazywany przez odwołanie, nie przez wartość.</span><span class="sxs-lookup"><span data-stu-id="f6260-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="f6260-115">Przekazywanie poprzez odwołanie powoduje, że każda zmiana argumentu w metodzie wywoływanej jest odzwierciedlana w wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="f6260-115">The effect of passing by reference is that any change to the argument in the called method is reflected in the calling method.</span></span> <span data-ttu-id="f6260-116">Na przykład jeśli obiekt wywołujący przekazuje wyrażenie lokalnej zmiennej lub wyrażenia dostępu do elementu tablicy, a następnie wywoływana metoda zastępuje obiekt, do którego odwołuje się parametr ref, a następnie obiekt wywołujący użytkownika lokalnego zmienna lub element tablicy teraz odwołuje się do nowego obiektu po Metoda zwraca.</span><span class="sxs-lookup"><span data-stu-id="f6260-116">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="f6260-117">Nie należy mylić koncepcji przekazywanie poprzez odwołanie z pojęciem typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="f6260-117">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="f6260-118">Dwoma pojęciami nie są takie same.</span><span class="sxs-lookup"><span data-stu-id="f6260-118">The two concepts are not the same.</span></span> <span data-ttu-id="f6260-119">Parametr metody mogą być modyfikowane przez `ref` niezależnie od tego, czy jest typem wartości lub typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="f6260-119">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="f6260-120">Istnieje nie opakowanie typu wartości, gdy jest przekazywany przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f6260-120">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="f6260-121">Aby użyć `ref` jawnie użyć parametru, zarówno definicję metody, jak i wywoływania metody `ref` — słowo kluczowe, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f6260-121">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="f6260-122">Argument, który jest przekazywany do `ref` lub `in` parametr musi zostać zainicjowany przed przekazaniem jej.</span><span class="sxs-lookup"><span data-stu-id="f6260-122">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="f6260-123">To różni się od [się](out-parameter-modifier.md) parametrów, w której argumenty nie trzeba jawnie zainicjowane przed przekazaniem ich.</span><span class="sxs-lookup"><span data-stu-id="f6260-123">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="f6260-124">Składowa klasy nie może mieć podpisów, które różnią się tylko przez `ref`, `in`, lub `out`.</span><span class="sxs-lookup"><span data-stu-id="f6260-124">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="f6260-125">Błąd kompilatora występuje, jeśli jedyną różnicą między dwa elementy członkowskie typu jest, że jedna z nich ma `ref` parametru, a druga ma `out`, lub `in` parametru.</span><span class="sxs-lookup"><span data-stu-id="f6260-125">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="f6260-126">Na przykład, poniższy kod nie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f6260-126">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="f6260-127">Jednak mogą być przeciążone metody, gdy ma jedną z metod `ref`, `in`, lub `out` parametru, a druga ma wartość parametru, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f6260-127">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="f6260-128">W innych sytuacjach, które wymagają podpis dopasowania, takich jak ukrywać lub zastępowanie `in`, `ref`, i `out` są dostępne w ramach sygnatury i nie pasują do siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="f6260-128">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="f6260-129">Właściwości nie są zmienne.</span><span class="sxs-lookup"><span data-stu-id="f6260-129">Properties are not variables.</span></span> <span data-ttu-id="f6260-130">To metody, a nie można przekazać do `ref` parametrów.</span><span class="sxs-lookup"><span data-stu-id="f6260-130">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="f6260-131">Aby dowiedzieć się, jak przekazać tablic, zobacz [przekazywanie tablic za pomocą ref i out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="f6260-131">For information about how to pass arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="f6260-132">Nie można użyć `ref`, `in`, i `out` słowa kluczowe dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="f6260-132">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="f6260-133">Metody asynchroniczne, które można zdefiniować przy użyciu [async](../../../csharp/language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="f6260-133">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
- <span data-ttu-id="f6260-134">Metody iteratora, które obejmują [yield return](../../../csharp/language-reference/keywords/yield.md) lub `yield break` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f6260-134">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="f6260-135">Przekazywanie argumentów poprzez odwołanie: przykład</span><span class="sxs-lookup"><span data-stu-id="f6260-135">Passing an argument by reference: An example</span></span>

<span data-ttu-id="f6260-136">Poprzednie przykłady przekazuj typów wartości przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f6260-136">The previous examples pass value types by reference.</span></span> <span data-ttu-id="f6260-137">Można również użyć `ref` — słowo kluczowe do przekazania odwołania typów przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f6260-137">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="f6260-138">Przekazywanie typu odwołania przez odwołanie pozwala zastąpić obiekt, do którego odwołuje się parametr odwołania w obiekcie wywołującym metodę o nazwie.</span><span class="sxs-lookup"><span data-stu-id="f6260-138">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="f6260-139">Lokalizacja magazynu obiekt jest przekazywany do metody jako wartość parametru odwołania.</span><span class="sxs-lookup"><span data-stu-id="f6260-139">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="f6260-140">Jeśli zmienisz wartość w określonej lokalizacji magazynu parametru (aby wskazywały nowy obiekt), możesz również zmienić lokalizację magazynu, do którego odwołuje się obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="f6260-140">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="f6260-141">Poniższy przykład przekazuje wystąpienia typu referencyjnego jako `ref` parametru.</span><span class="sxs-lookup"><span data-stu-id="f6260-141">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="f6260-142">Aby uzyskać więcej informacji dotyczących przekazywania typów referencyjnych według wartości i według odwołania, zobacz [przekazywanie parametrów typu odwołanie](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f6260-142">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="f6260-143">Wartości zwracane odwołanie</span><span class="sxs-lookup"><span data-stu-id="f6260-143">Reference return values</span></span>

<span data-ttu-id="f6260-144">Wartości zwracane odwołanie (lub zwracanych ref) są wartościami, które metoda zwraca wartość przez odwołanie do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f6260-144">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="f6260-145">Oznacza to obiekt wywołujący, można zmodyfikować wartości zwracanej przez metodę, a ta zmiana jest odzwierciedlana w stan obiektu, który zawiera metodę.</span><span class="sxs-lookup"><span data-stu-id="f6260-145">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span>

<span data-ttu-id="f6260-146">Odwołanie zwracają wartość jest definiowana za pomocą `ref` — słowo kluczowe:</span><span class="sxs-lookup"><span data-stu-id="f6260-146">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="f6260-147">W podpisie metody.</span><span class="sxs-lookup"><span data-stu-id="f6260-147">In the method signature.</span></span> <span data-ttu-id="f6260-148">Na przykład, następujący podpis metody oznacza, że `GetCurrentPrice` metoda zwraca <xref:System.Decimal> wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f6260-148">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentValue()
```

- <span data-ttu-id="f6260-149">Między `return` token i zmienna zwracane w `return` instrukcji w metodzie.</span><span class="sxs-lookup"><span data-stu-id="f6260-149">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="f6260-150">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f6260-150">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="f6260-151">Aby obiekt wywołujący, aby zmodyfikować stan obiektu, musi być przechowywana wartość do zmiennej, która jest jawnie zdefiniowany jako zwrócić odwołanie [odwołanie lokalne](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="f6260-151">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="f6260-152">Aby uzyskać przykład, zobacz [A wartości zwracane ref i przykład zmienne lokalne ref](#a-ref-returns-and-ref-locals-example)</span><span class="sxs-lookup"><span data-stu-id="f6260-152">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example)</span></span>

## <a name="ref-locals"></a><span data-ttu-id="f6260-153">Zmienne lokalne REF</span><span class="sxs-lookup"><span data-stu-id="f6260-153">Ref locals</span></span>

<span data-ttu-id="f6260-154">Zmienna lokalna ref jest używana do odwoływania się do wartości zwracane wartości przy użyciu `return ref`.</span><span class="sxs-lookup"><span data-stu-id="f6260-154">A ref local variable is used to refer to values returned using `return ref`.</span></span>  <span data-ttu-id="f6260-155">Zmienna lokalna ref musi zainicjować i przypisać do wartości zwracane ref.</span><span class="sxs-lookup"><span data-stu-id="f6260-155">A ref local variable must be initialized and assigned to a ref return value.</span></span> <span data-ttu-id="f6260-156">Wszelkie modyfikacje, wartość Zmienna lokalna ref są odzwierciedlane w stan obiektu, którego metoda zwróciła wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f6260-156">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="f6260-157">Zmienna lokalna ref jest definiowane za pomocą `ref` — słowo kluczowe przed deklaracją zmiennej, a także bezpośrednio przed wywołaniem metody, która zwraca wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f6260-157">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="f6260-158">Na przykład następująca instrukcja definiuje lokalna wartość ref, który jest zwracany przez metodę o nazwie `GetEstimatedValue`:</span><span class="sxs-lookup"><span data-stu-id="f6260-158">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="f6260-159">Dostępne wartości przez odwołanie, w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="f6260-159">You can access a value by reference in the same way.</span></span> <span data-ttu-id="f6260-160">W niektórych przypadkach uzyskiwanie dostępu do wartości przez odwołanie zwiększa wydajność, unikając operacji kopiowania potencjalnie kosztowne.</span><span class="sxs-lookup"><span data-stu-id="f6260-160">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="f6260-161">Na przykład następująca instrukcja pokazuje, jak jeden można zdefiniować wartości lokalnej ref, służący do odwoływać się do wartości.</span><span class="sxs-lookup"><span data-stu-id="f6260-161">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="f6260-162">Należy pamiętać, że w obu przykładach `ref` w obu miejscach, można użyć słowa kluczowego lub kompilator generuje błąd CS8172, "Nie można zainicjować zmiennej przez odwołanie o wartości".</span><span class="sxs-lookup"><span data-stu-id="f6260-162">Note that in both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="f6260-163">Element wartości zwracane ref i przykład zmienne lokalne ref</span><span class="sxs-lookup"><span data-stu-id="f6260-163">A ref returns and ref locals example</span></span>

<span data-ttu-id="f6260-164">W poniższym przykładzie zdefiniowano `Book` klasę, która ma dwa <xref:System.String> pól `Title` i `Author`.</span><span class="sxs-lookup"><span data-stu-id="f6260-164">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="f6260-165">Umożliwia on również definiowanie `BookCollection` klasa, która zawiera prywatne tablicę `Book` obiektów.</span><span class="sxs-lookup"><span data-stu-id="f6260-165">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="f6260-166">Poszczególne książki obiekty są zwracane przez odwołanie, przez wywołanie jego `GetBookByTitle` metody.</span><span class="sxs-lookup"><span data-stu-id="f6260-166">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="f6260-167">Gdy obiekt wywołujący przechowuje wartość zwrócona przez obiekt `GetBookByTitle` zmiany, które sprawia, że obiekt wywołujący na wartość zwracaną metody jako lokalną ref, są odzwierciedlane w `BookCollection` obiektu, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="f6260-167">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-declarations"></a><span data-ttu-id="f6260-168">Deklaracje struktury REF</span><span class="sxs-lookup"><span data-stu-id="f6260-168">Ref struct declarations</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f6260-169">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f6260-169">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f6260-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6260-170">See also</span></span>

 [<span data-ttu-id="f6260-171">Semantyka odwołań z typami wartości</span><span class="sxs-lookup"><span data-stu-id="f6260-171">Reference semantics with value types</span></span>](../../reference-semantics-with-value-types.md)  
 [<span data-ttu-id="f6260-172">Przekazywanie parametrów</span><span class="sxs-lookup"><span data-stu-id="f6260-172">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)  
 [<span data-ttu-id="f6260-173">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="f6260-173">Method Parameters</span></span>](method-parameters.md)  
 [<span data-ttu-id="f6260-174">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f6260-174">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="f6260-175">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f6260-175">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="f6260-176">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="f6260-176">C# Keywords</span></span>](index.md)
