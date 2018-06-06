---
title: ref (odwołanie w C#)
ms.date: 03/06/2018
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: a4d5719bccd240658880cc5c6e549e8c912ca1b9
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696397"
---
# <a name="ref-c-reference"></a><span data-ttu-id="6a9a5-102">ref (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6a9a5-102">ref (C# Reference)</span></span>

<span data-ttu-id="6a9a5-103">`ref` — Słowo kluczowe wskazuje wartość, która jest przekazywana przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="6a9a5-104">Jest on używany w trzech różnych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="6a9a5-104">It is used in three different contexts:</span></span> 

- <span data-ttu-id="6a9a5-105">W podpisie metody i w wywołaniu metody, przekazując argument do metody przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="6a9a5-106">Zobacz [przekazywanie argumentów poprzez odwołanie](#passing-an-argument-by-reference) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-106">See [Passing an argument by reference](#passing-an-argument-by-reference) for more information.</span></span>

- <span data-ttu-id="6a9a5-107">W podpisie metody, aby zwrócić wartość do obiektu wywołującego przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="6a9a5-108">Zobacz [odwołanie zwracane wartości](#reference-return-values) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-108">See [Reference return values](#reference-return-values) for more information.</span></span>

- <span data-ttu-id="6a9a5-109">W treści elementu członkowskiego aby wskazać, że odwołanie do wartości zwracanej są przechowywane lokalnie, jako odwołanie do wywołującego zamierza zmienić lub ogólnie rzecz biorąc, zmienna lokalna uzyskuje dostęp do innej wartości przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="6a9a5-110">Zobacz [zmiennych lokalnych Ref](#ref-locals) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-110">See [Ref locals](#ref-locals) for more information.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="6a9a5-111">Przekazywanie argumentów poprzez odwołanie</span><span class="sxs-lookup"><span data-stu-id="6a9a5-111">Passing an argument by reference</span></span>

<span data-ttu-id="6a9a5-112">W przypadku używania w liście parametrów metody, `ref` — słowo kluczowe wskazuje, że argument jest przekazywany przez odwołanie, nie przez wartość.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-112">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="6a9a5-113">Przekazywanie poprzez odwołanie powoduje, że każda zmiana argumentu w metodzie wywołane znajduje odzwierciedlenie w metody wywołującej.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-113">The effect of passing by reference is that any change to the argument in the called method is reflected in the calling method.</span></span> <span data-ttu-id="6a9a5-114">Na przykład jeśli wywołujący wyrażenie lokalnej zmiennej lub wyrażenie dostępu do elementu tablicy i wywołana metoda zastępuje obiekt, do którego odwołuje się parametr ref, a następnie lokalnego obiektu wywołującego zmiennej lub element tablicy teraz odwołuje się do nowego obiektu po Metoda zwraca.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-114">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
>  <span data-ttu-id="6a9a5-115">Nie należy mylić koncepcji przekazywanie poprzez odwołanie z pojęciem typy referencyjne.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-115">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="6a9a5-116">Dwa pojęcia nie są takie same.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-116">The two concepts are not the same.</span></span> <span data-ttu-id="6a9a5-117">Parametr metody mogą być modyfikowane przez `ref` niezależnie od tego, czy jest typem wartości lub typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-117">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="6a9a5-118">Istnieje nie pakującej typu wartości, gdy jest przekazywana przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-118">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="6a9a5-119">Aby użyć `ref` jawnie należy użyć parametru definicję metody i wywołanie metody `ref` — słowo kluczowe, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-119">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="6a9a5-120">Argument przekazywany do `ref` lub `in` parametr musi zostać zainicjowany przed przekazaniem.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-120">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="6a9a5-121">To różni się od [limit](out-parameter-modifier.md) parametrów, argumentów, których nie trzeba jawnie zainicjowane przed są one przekazywane.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-121">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="6a9a5-122">Element członkowski klasy nie mogą mieć sygnatur różniących się tylko `ref`, `in`, lub `out`.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-122">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="6a9a5-123">Błąd kompilatora występuje, jeśli jedyną różnicą między dwoma elementami członkowskimi typu jest, że jedna z nich ma `ref` ma parametr, a druga `out`, lub `in` parametru.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-123">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="6a9a5-124">Na przykład następujący kod nie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-124">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
<span data-ttu-id="6a9a5-125">Jednak metod można przeciążać, gdy ma jedną metodę `ref`, `in`, lub `out` parametr, a druga ma parametr wartość, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-125">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="6a9a5-126">W innych sytuacjach wymagających podpisu dopasowania, takich jak ukrywanie lub przesłonięcie `in`, `ref`, i `out` stanowią część podpisu i nie pasują do siebie.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-126">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="6a9a5-127">Właściwości nie są zmiennymi.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-127">Properties are not variables.</span></span> <span data-ttu-id="6a9a5-128">Metody i nie można przekazać do `ref` parametrów.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-128">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="6a9a5-129">Aby uzyskać informacje o sposobie przekazać tablice, zobacz [przekazywanie tablic za pomocą ref i out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="6a9a5-129">For information about how to pass arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="6a9a5-130">Nie można użyć `ref`, `in`, i `out` słowa kluczowe dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="6a9a5-130">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="6a9a5-131">Metody asynchroniczne, które definiują przy użyciu [async](../../../csharp/language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-131">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
- <span data-ttu-id="6a9a5-132">Metody iteracyjne, które obejmują [yield return](../../../csharp/language-reference/keywords/yield.md) lub `yield break` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-132">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="6a9a5-133">Przekazywanie argumentów poprzez odwołanie: przykład</span><span class="sxs-lookup"><span data-stu-id="6a9a5-133">Passing an argument by reference: An example</span></span>

<span data-ttu-id="6a9a5-134">Poprzednich przykładach przekazuj typów wartości przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-134">The previous examples pass value types by reference.</span></span> <span data-ttu-id="6a9a5-135">Można również użyć `ref` — słowo kluczowe do przekazania odwołania typów przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-135">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="6a9a5-136">Przekazywanie poprzez odwołanie typu odwołania umożliwia wywołaną metodę zastąpić obiekt, do którego odwołuje się parametr odwołania w wywołującego.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-136">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="6a9a5-137">Lokalizacja magazynu obiektu jest przekazywany do metody jako wartość parametru odwołania.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-137">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="6a9a5-138">Wartość w lokalizacji przechowywania parametru (aby wskazywały nowy obiekt), możesz także zmiana lokalizacji przechowywania, do którego odwołuje się element wywołujący.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-138">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="6a9a5-139">Poniższy przykład przekazuje wystąpienia typu referencyjnego jako `ref` parametru.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-139">The following example passes an instance of a reference type as a `ref` parameter.</span></span>   
  
[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="6a9a5-140">Aby uzyskać więcej informacji na temat przekazywania typów referencyjnych według wartości i według odwołania, zobacz [przekazywanie parametrów typu odwołanie](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6a9a5-140">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="6a9a5-141">Odwołanie do zwracanych wartości</span><span class="sxs-lookup"><span data-stu-id="6a9a5-141">Reference return values</span></span>

<span data-ttu-id="6a9a5-142">Odwołanie zwracane wartości (lub zwraca ref) to wartości, które metoda zwraca wartość przez odwołanie do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-142">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="6a9a5-143">Oznacza to wywołujący może zmodyfikować wartość zwrócona przez metodę, a zmiana ta jest uwzględniana w stan obiektu, który zawiera metodę.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-143">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span> 

<span data-ttu-id="6a9a5-144">Odwołanie zwrócić wartość jest definiowana za pomocą `ref` — słowo kluczowe:</span><span class="sxs-lookup"><span data-stu-id="6a9a5-144">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="6a9a5-145">W podpisie metody.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-145">In the method signature.</span></span> <span data-ttu-id="6a9a5-146">Na przykład następujące Określa podpis metody który `GetCurrentPrice` metoda zwraca <xref:System.Decimal> wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-146">For example, the following method signature inidicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

   ```csharp
   public ref decimal GetCurrentValue()
   ``` 
- <span data-ttu-id="6a9a5-147">Między `return` token i zwracany w zmiennej `return` instrukcji w metodzie.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-147">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="6a9a5-148">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="6a9a5-148">For example:</span></span>
 
   ```csharp
   return ref DecimalArray[0];
   ``` 

<span data-ttu-id="6a9a5-149">Aby dla obiekt wywołujący, aby zmodyfikować stan obiektu odwołania zwrócić wartość musi być przechowywany w zmiennej, który jest jawnie zdefiniowany jako [lokalnej typu ref](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="6a9a5-149">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span> 

<span data-ttu-id="6a9a5-150">Na przykład zobacz [A ref zwraca i przykładowe elementy lokalne ref](#a-ref-returns-and-ref-locals-example)</span><span class="sxs-lookup"><span data-stu-id="6a9a5-150">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example)</span></span>

## <a name="ref-locals"></a><span data-ttu-id="6a9a5-151">Zmienne lokalne REF</span><span class="sxs-lookup"><span data-stu-id="6a9a5-151">Ref locals</span></span>

<span data-ttu-id="6a9a5-152">Zmienna lokalna ref jest używana do odwoływania się do wartości zwracanych przy użyciu `return ref`.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-152">A ref local variable is used to refer to values returned using `return ref`.</span></span>  <span data-ttu-id="6a9a5-153">Zmienna lokalna ref należy zainicjować i przypisane do wartości zwracanej ref.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-153">A ref local variable must be initialized and assigned to a ref return value.</span></span> <span data-ttu-id="6a9a5-154">Wszelkie modyfikacje wartość Zmienna lokalna ref są uwzględniane w stan obiektu, którego metoda zwróciła wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-154">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="6a9a5-155">Zdefiniuj zmienna lokalna ref przy użyciu `ref` — słowo kluczowe przed deklaracją zmiennej, a także bezpośrednio przed wywołaniem metody, która zwraca wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-155">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span> 

<span data-ttu-id="6a9a5-156">Na przykład następująca instrukcja definiuje ref wartości lokalnej, który jest zwracany przez metodę o nazwie `GetEstimatedValue`:</span><span class="sxs-lookup"><span data-stu-id="6a9a5-156">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="6a9a5-157">Dostępne wartości przez odwołanie w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-157">You can access a value by reference in the same way.</span></span> <span data-ttu-id="6a9a5-158">W niektórych przypadkach dostępu do wartość przez odwołanie zwiększa wydajność, unikając operacji kopiowania potencjalnie kosztowne.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-158">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="6a9a5-159">Na przykład następująca instrukcja pokazuje, jak jedną można zdefiniować wartości lokalnej ref, służący do odwołać się do wartości.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-159">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="6a9a5-160">Należy pamiętać, że w obu przykładach `ref` — słowo kluczowe może być używane w obu miejscach lub kompilator generuje błąd CS8172 "Nie można zainicjować zmiennej dostępnej przez odwołanie o wartości".</span><span class="sxs-lookup"><span data-stu-id="6a9a5-160">Note that in both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 
 
## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="6a9a5-161">A przykład zmiennych lokalnych ref i zwraca ref</span><span class="sxs-lookup"><span data-stu-id="6a9a5-161">A ref returns and ref locals example</span></span>

<span data-ttu-id="6a9a5-162">W poniższym przykładzie zdefiniowano `Book` klasy, która ma dwa <xref:System.String> pól, `Title` i `Author`.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-162">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="6a9a5-163">Definiuje również `BookCollection` klasa, która zawiera prywatne tablicę `Book` obiektów.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-163">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="6a9a5-164">Podręcznik poszczególnych obiektów są zwracane przez odwołanie przez wywołanie jego `GetBookByTitle` metody.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-164">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="6a9a5-165">Gdy obiekt wywołujący przechowuje wartość zwrócona przez `GetBookByTitle` metodę jako zmiennej lokalnej typu ref, zmiany wywołującego sprawia, że do wartości zwracanej są odzwierciedlane w `BookCollection` obiektu, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6a9a5-165">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="6a9a5-166">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6a9a5-166">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6a9a5-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a9a5-167">See also</span></span>  
 [<span data-ttu-id="6a9a5-168">Semantyka odwołań z typami wartości</span><span class="sxs-lookup"><span data-stu-id="6a9a5-168">Reference semantics with value types</span></span>](../../reference-semantics-with-value-types.md)  
 [<span data-ttu-id="6a9a5-169">Przekazywanie parametrów</span><span class="sxs-lookup"><span data-stu-id="6a9a5-169">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)  
 [<span data-ttu-id="6a9a5-170">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="6a9a5-170">Method Parameters</span></span>](method-parameters.md)  
 [<span data-ttu-id="6a9a5-171">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="6a9a5-171">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="6a9a5-172">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6a9a5-172">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="6a9a5-173">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="6a9a5-173">C# Keywords</span></span>](index.md)
