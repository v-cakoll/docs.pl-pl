---
title: ref — słowo C# kluczowe — odwołanie
ms.custom: seodec18
ms.date: 03/26/2019
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: f11137b3c13bb9e8670c4df25fedf3251724a088
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566896"
---
# <a name="ref-c-reference"></a><span data-ttu-id="6d71f-102">ref (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6d71f-102">ref (C# Reference)</span></span>

<span data-ttu-id="6d71f-103">`ref` Słowo kluczowe wskazuje wartość, która jest przenoszona przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6d71f-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="6d71f-104">Jest on używany w czterech różnych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="6d71f-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="6d71f-105">W sygnaturze metody i w wywołaniu metody, aby przekazać argument do metody przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6d71f-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="6d71f-106">Aby uzyskać więcej informacji, zobacz [przekazywanie argumentu przez odwołanie](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="6d71f-106">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="6d71f-107">W podpisie metody, aby zwrócić wartość do obiektu wywołującego przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6d71f-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="6d71f-108">Aby uzyskać więcej informacji, zobacz [odwołania do zwracanych wartości](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="6d71f-108">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="6d71f-109">W treści elementu członkowskiego, aby wskazać, że wartość zwracana przez odwołanie jest przechowywana lokalnie jako odwołanie, które obiekt wywołujący zamierza zmodyfikować lub ogólnie rzecz biorąc, zmienna lokalna uzyskuje dostęp do innej wartości przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6d71f-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="6d71f-110">Aby uzyskać więcej informacji, zobacz [odwołania lokalne](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="6d71f-110">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="6d71f-111">W deklaracji do `ref struct` deklarowania lub `readonly ref struct`. `struct`</span><span class="sxs-lookup"><span data-stu-id="6d71f-111">In a `struct` declaration to declare a `ref struct` or a `readonly ref struct`.</span></span> <span data-ttu-id="6d71f-112">Aby uzyskać więcej informacji, zobacz [typy struktury ref](#ref-struct-types).</span><span class="sxs-lookup"><span data-stu-id="6d71f-112">For more information, see [ref struct types](#ref-struct-types).</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="6d71f-113">Przekazywanie argumentu przez odwołanie</span><span class="sxs-lookup"><span data-stu-id="6d71f-113">Passing an argument by reference</span></span>

<span data-ttu-id="6d71f-114">W przypadku użycia na liście `ref` parametrów metody słowo kluczowe wskazuje, że argument jest przenoszona przez odwołanie, a nie przez wartość.</span><span class="sxs-lookup"><span data-stu-id="6d71f-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="6d71f-115">`ref` Słowo kluczowe powoduje, że parametr formalny jest aliasem dla argumentu, który musi być zmienną.</span><span class="sxs-lookup"><span data-stu-id="6d71f-115">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="6d71f-116">Innymi słowy, każda operacja na parametrze jest wykonywana na argumencie.</span><span class="sxs-lookup"><span data-stu-id="6d71f-116">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="6d71f-117">Na przykład, jeśli obiekt wywołujący przekazuje wyrażenie zmiennej lokalnej lub wyrażenie dostępu do elementu tablicy, a wywoływana metoda zastępuje obiekt, do którego odwołuje się parametr ref, wówczas zmienna lokalna obiektu wywołującego lub element array odwołuje się teraz do nowego obiektu, gdy Zwraca metodę.</span><span class="sxs-lookup"><span data-stu-id="6d71f-117">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="6d71f-118">Nie należy mylić koncepcji przekazywania przez odwołanie z koncepcją typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="6d71f-118">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="6d71f-119">Te dwa koncepcje nie są takie same.</span><span class="sxs-lookup"><span data-stu-id="6d71f-119">The two concepts are not the same.</span></span> <span data-ttu-id="6d71f-120">Parametr metody można zmodyfikować, `ref` niezależnie od tego, czy jest to typ wartości, czy też typ referencyjny.</span><span class="sxs-lookup"><span data-stu-id="6d71f-120">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="6d71f-121">Nie istnieje opakowanie typu wartości, gdy jest ono przesyłane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6d71f-121">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="6d71f-122">Aby użyć `ref` parametru, zarówno definicja metody, jak i Metoda wywołująca muszą jawnie `ref` użyć słowa kluczowego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6d71f-122">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="6d71f-123">Argument, który jest przesyłany do `ref` parametru `in` lub musi zostać zainicjowany przed jego przekazaniem.</span><span class="sxs-lookup"><span data-stu-id="6d71f-123">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="6d71f-124">Różni się to od parametrów [out](out-parameter-modifier.md) , których argumenty nie muszą być jawnie inicjowane przed ich przekazaniem.</span><span class="sxs-lookup"><span data-stu-id="6d71f-124">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="6d71f-125">Elementy członkowskie klasy nie mogą mieć sygnatur, które różnią `ref`się `in`tylko przez `out`, lub.</span><span class="sxs-lookup"><span data-stu-id="6d71f-125">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="6d71f-126">Błąd kompilatora występuje `out`, jeśli jedyną różnicą między dwoma elementami członkowskimi tego typu jest, że jeden z nich `ref` ma parametr, a drugi ma parametr, `in` lub.</span><span class="sxs-lookup"><span data-stu-id="6d71f-126">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="6d71f-127">Poniższy kod, na przykład, nie kompiluje.</span><span class="sxs-lookup"><span data-stu-id="6d71f-127">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="6d71f-128">Jednakże metody mogą być przeciążone, gdy jedna metoda ma `ref`parametr `in`,, `out` lub, a drugi ma parametr value, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6d71f-128">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="6d71f-129">W innych sytuacjach, które wymagają dopasowania podpisu, takich jak ukrywanie lub zastępowanie `ref`, `in`, `out` , i są częścią podpisu i nie pasują do siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="6d71f-129">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="6d71f-130">Właściwości nie są zmiennymi.</span><span class="sxs-lookup"><span data-stu-id="6d71f-130">Properties are not variables.</span></span> <span data-ttu-id="6d71f-131">Są to metody i nie można ich przekazywać `ref` do parametrów.</span><span class="sxs-lookup"><span data-stu-id="6d71f-131">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="6d71f-132">Nie można używać `ref`słów kluczowych `in`, i `out` dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="6d71f-132">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="6d71f-133">Metody asynchroniczne zdefiniowane za pomocą modyfikatora [Async](async.md) .</span><span class="sxs-lookup"><span data-stu-id="6d71f-133">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="6d71f-134">Metody iteratorów, które zawierają instrukcję [yield return](yield.md) lub `yield break` .</span><span class="sxs-lookup"><span data-stu-id="6d71f-134">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="6d71f-135">Przekazywanie argumentu przez odwołanie: Przykład</span><span class="sxs-lookup"><span data-stu-id="6d71f-135">Passing an argument by reference: An example</span></span>

<span data-ttu-id="6d71f-136">Poprzednie przykłady przechodzą typy wartości według odwołania.</span><span class="sxs-lookup"><span data-stu-id="6d71f-136">The previous examples pass value types by reference.</span></span> <span data-ttu-id="6d71f-137">Możesz również użyć słowa kluczowego, `ref` aby przekazać typy odwołań przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6d71f-137">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="6d71f-138">Przekazywanie typu referencyjnego przez odwołanie włącza wywoływaną metodę, aby zastąpić obiekt, do którego odwołuje się parametr Reference w wywołującym.</span><span class="sxs-lookup"><span data-stu-id="6d71f-138">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="6d71f-139">Lokalizacja przechowywania obiektu jest przenoszona do metody jako wartość parametru Reference.</span><span class="sxs-lookup"><span data-stu-id="6d71f-139">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="6d71f-140">Jeśli zmienisz wartość w lokalizacji magazynu parametru (w celu wskazywania nowego obiektu), zmienisz również lokalizację magazynu, do którego odwołuje się obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="6d71f-140">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="6d71f-141">Poniższy przykład przekazuje wystąpienie typu odwołania jako `ref` parametr.</span><span class="sxs-lookup"><span data-stu-id="6d71f-141">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="6d71f-142">Aby uzyskać więcej informacji na temat przekazywania typów odwołań według wartości i według odwołania, zobacz [przekazywanie parametrów typu odwołania](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6d71f-142">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="6d71f-143">Odwoływanie się do zwracanych wartości</span><span class="sxs-lookup"><span data-stu-id="6d71f-143">Reference return values</span></span>

<span data-ttu-id="6d71f-144">Wartości zwracane przez odwołanie (lub zwroty odwołań) to wartości, które Metoda zwraca przez odwołanie do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="6d71f-144">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="6d71f-145">Oznacza to, że obiekt wywołujący może zmodyfikować wartość zwróconą przez metodę, a ta zmiana jest odzwierciedlona w stanie obiektu, który zawiera metodę.</span><span class="sxs-lookup"><span data-stu-id="6d71f-145">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span>

<span data-ttu-id="6d71f-146">Wartość zwracana przez odwołanie jest definiowana za pomocą `ref` słowa kluczowego:</span><span class="sxs-lookup"><span data-stu-id="6d71f-146">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="6d71f-147">W podpisie metody.</span><span class="sxs-lookup"><span data-stu-id="6d71f-147">In the method signature.</span></span> <span data-ttu-id="6d71f-148">Na przykład następująca sygnatura metody wskazuje, że `GetCurrentPrice` Metoda <xref:System.Decimal> zwraca wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6d71f-148">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="6d71f-149">Między tokenem i zmienną zwróconą `return` w instrukcji w metodzie. `return`</span><span class="sxs-lookup"><span data-stu-id="6d71f-149">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="6d71f-150">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="6d71f-150">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="6d71f-151">Aby obiekt wywołujący zmodyfikował stan obiektu, wartość zwracana odwołania musi być przechowywana w zmiennej, która jest jawnie zdefiniowana jako [lokalna jako ref](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="6d71f-151">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="6d71f-152">Wywołana metoda może również deklarować wartość zwracaną jako `ref readonly` zwracającą wartość przez odwołanie i wymusić, że wywoływany kod nie może zmodyfikować zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="6d71f-152">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="6d71f-153">Metoda wywołująca może uniknąć kopiowania zwracanej wartości przez zapisanie wartości w lokalnej zmiennej [ref ReadOnly](#ref-readonly-locals) .</span><span class="sxs-lookup"><span data-stu-id="6d71f-153">The calling method can avoid copying the returned valued by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="6d71f-154">Aby zapoznać się z przykładem, zobacz [przykład ref Returns i ref locales](#a-ref-returns-and-ref-locals-example).</span><span class="sxs-lookup"><span data-stu-id="6d71f-154">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="6d71f-155">Odwołania lokalne</span><span class="sxs-lookup"><span data-stu-id="6d71f-155">Ref locals</span></span>

<span data-ttu-id="6d71f-156">Referencyjna zmienna lokalna służy do odwoływania się do wartości zwracanych przy użyciu `return ref`.</span><span class="sxs-lookup"><span data-stu-id="6d71f-156">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="6d71f-157">Nie można zainicjować zmiennej lokalnej ref do wartości zwracanej niebędącej odwołaniem.</span><span class="sxs-lookup"><span data-stu-id="6d71f-157">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="6d71f-158">Innymi słowy, prawa strona inicjowania musi być odwołaniem.</span><span class="sxs-lookup"><span data-stu-id="6d71f-158">In other words, the right hand side of the initialization must be a reference.</span></span> <span data-ttu-id="6d71f-159">Wszelkie modyfikacje wartości lokalnego elementu ref są odzwierciedlane w stanie obiektu, którego Metoda zwróciła wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6d71f-159">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="6d71f-160">Można zdefiniować odwołanie lokalne przy użyciu `ref` słowa kluczowego przed deklaracją zmiennej, a także bezpośrednio przed wywołaniem metody, która zwraca wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6d71f-160">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="6d71f-161">Na przykład poniższa instrukcja definiuje wartość lokalną ref zwracaną przez metodę o nazwie `GetEstimatedValue`:</span><span class="sxs-lookup"><span data-stu-id="6d71f-161">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="6d71f-162">Możesz uzyskać dostęp do wartości przez odwołanie w ten sam sposób.</span><span class="sxs-lookup"><span data-stu-id="6d71f-162">You can access a value by reference in the same way.</span></span> <span data-ttu-id="6d71f-163">W niektórych przypadkach uzyskanie dostępu do wartości przez odwołanie zwiększa wydajność poprzez uniknięcie potencjalnie kosztownej operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="6d71f-163">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="6d71f-164">Na przykład poniższa instrukcja pokazuje, jak jedna z nich może definiować wartość lokalna ref, która jest używana do odwoływania się do wartości.</span><span class="sxs-lookup"><span data-stu-id="6d71f-164">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="6d71f-165">Należy zauważyć, że w obu `ref` przykładach słowo kluczowe musi być używane w obu miejscach lub kompilator generuje błąd CS8172, "nie można zainicjować zmiennej przez odwołanie za pomocą wartości".</span><span class="sxs-lookup"><span data-stu-id="6d71f-165">Note that in both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="6d71f-166">Począwszy od C# 7,3, zmienna `foreach` iteracji instrukcji może być lokalna lokalną lub ref tylko do odczytu zmienna lokalna.</span><span class="sxs-lookup"><span data-stu-id="6d71f-166">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="6d71f-167">Aby uzyskać więcej informacji, zobacz artykuł [instrukcji foreach](foreach-in.md) .</span><span class="sxs-lookup"><span data-stu-id="6d71f-167">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="6d71f-168">Odwołania do elementów lokalnych ReadOnly</span><span class="sxs-lookup"><span data-stu-id="6d71f-168">Ref readonly locals</span></span>

<span data-ttu-id="6d71f-169">Wartość Ref Local ReadOnly jest używana do odwoływania się do wartości zwracanych przez metodę lub właściwość `ref readonly` , która ma w jej `return ref`podpisie i używa.</span><span class="sxs-lookup"><span data-stu-id="6d71f-169">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="6d71f-170">Zmienna łączy właściwości `ref` zmiennej lokalnej ze `readonly` zmienną: jest to alias do magazynu, do którego jest przypisany, i nie może być modyfikowany. `ref readonly`</span><span class="sxs-lookup"><span data-stu-id="6d71f-170">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span> 

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="6d71f-171">Przykład odwołania ref i lokalne odwołania ref</span><span class="sxs-lookup"><span data-stu-id="6d71f-171">A ref returns and ref locals example</span></span>

<span data-ttu-id="6d71f-172">W poniższym przykładzie zdefiniowano `Book` klasę, która ma <xref:System.String> dwa pola `Title` i `Author`.</span><span class="sxs-lookup"><span data-stu-id="6d71f-172">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="6d71f-173">Definiuje `BookCollection` również klasę, która zawiera prywatną `Book` tablicę obiektów.</span><span class="sxs-lookup"><span data-stu-id="6d71f-173">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="6d71f-174">Poszczególne obiekty książek są zwracane przez odwołanie poprzez wywołanie `GetBookByTitle` metody.</span><span class="sxs-lookup"><span data-stu-id="6d71f-174">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="6d71f-175">Gdy obiekt wywołujący przechowuje wartość zwróconą przez `GetBookByTitle` metodę jako odwołanie lokalne, zmiany, które obiekt wywołujący wprowadza do wartości zwracanej, są odzwierciedlone `BookCollection` w obiekcie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6d71f-175">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a><span data-ttu-id="6d71f-176">Typy struktur ref</span><span class="sxs-lookup"><span data-stu-id="6d71f-176">Ref struct types</span></span>

<span data-ttu-id="6d71f-177">Dodanie modyfikatora `struct` do deklaracji definiuje, że wystąpienia tego typu muszą mieć przydzieloną stos. `ref`</span><span class="sxs-lookup"><span data-stu-id="6d71f-177">Adding the `ref` modifier to a `struct` declaration defines that instances of that type must be stack allocated.</span></span> <span data-ttu-id="6d71f-178">Innymi słowy, wystąpienia tych typów nigdy nie mogą być tworzone na stercie jako element członkowski innej klasy.</span><span class="sxs-lookup"><span data-stu-id="6d71f-178">In other words, instances of these types can never be created on the heap as a member of another class.</span></span> <span data-ttu-id="6d71f-179">Główną motywacją tej funkcji były <xref:System.Span%601> i powiązane struktury.</span><span class="sxs-lookup"><span data-stu-id="6d71f-179">The primary motivation for this feature was <xref:System.Span%601> and related structures.</span></span>

<span data-ttu-id="6d71f-180">Celem zachowania `ref struct` typu jako zmiennej przydzieloną stosowo wprowadzono kilka reguł, które kompilator wymusza dla wszystkich `ref struct` typów.</span><span class="sxs-lookup"><span data-stu-id="6d71f-180">The goal of keeping a `ref struct` type as a stack-allocated variable introduces several rules that the compiler enforces for all `ref struct` types.</span></span>

- <span data-ttu-id="6d71f-181">Nie można Box a `ref struct`.</span><span class="sxs-lookup"><span data-stu-id="6d71f-181">You can't box a `ref struct`.</span></span> <span data-ttu-id="6d71f-182">Nie można przypisać `ref struct` typu do zmiennej typu `object`, `dynamic`lub dowolnego typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6d71f-182">You cannot assign a `ref struct` type to a variable of type `object`, `dynamic`, or any interface type.</span></span>
- <span data-ttu-id="6d71f-183">`ref struct`typy nie mogą implementować interfejsów.</span><span class="sxs-lookup"><span data-stu-id="6d71f-183">`ref struct` types cannot implement interfaces.</span></span>
- <span data-ttu-id="6d71f-184">Nie można zadeklarować `ref struct` jako elementu członkowskiego pola klasy lub normalnej struktury.</span><span class="sxs-lookup"><span data-stu-id="6d71f-184">You can't declare a `ref struct` as a field member of a class or a normal struct.</span></span> <span data-ttu-id="6d71f-185">Obejmuje to deklarowanie automatycznie zaimplementowanej właściwości, co powoduje utworzenie pola zapasowego wygenerowanego przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="6d71f-185">This includes declaring an auto-implemented property, which creates a compiler generated backing field.</span></span> 
- <span data-ttu-id="6d71f-186">Nie można zadeklarować zmiennych lokalnych, `ref struct` które są typami w metodach asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="6d71f-186">You cannot declare local variables that are `ref struct` types in async methods.</span></span> <span data-ttu-id="6d71f-187">Można je zadeklarować w metodach synchronicznych <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> które `Task`zwracają lub tak jak typy.</span><span class="sxs-lookup"><span data-stu-id="6d71f-187">You can declare them in synchronous methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> or `Task`-like types.</span></span>
- <span data-ttu-id="6d71f-188">Nie można zadeklarować `ref struct` zmiennych lokalnych w iteratorach.</span><span class="sxs-lookup"><span data-stu-id="6d71f-188">You cannot declare `ref struct` local variables in iterators.</span></span>
- <span data-ttu-id="6d71f-189">Nie można przechwytywać `ref struct` zmiennych w wyrażeniach lambda ani lokalnych funkcjach.</span><span class="sxs-lookup"><span data-stu-id="6d71f-189">You cannot capture `ref struct` variables in lambda expressions or local functions.</span></span>

<span data-ttu-id="6d71f-190">Te ograniczenia uniemożliwiają przypadkowe użycie programu `ref struct` w sposób, który mógłby wspierać go dla sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="6d71f-190">These restrictions ensure you don't accidentally use a `ref struct` in a manner that could promote it to the managed heap.</span></span>

<span data-ttu-id="6d71f-191">Można połączyć modyfikatory, aby zadeklarować strukturę jako `readonly ref`.</span><span class="sxs-lookup"><span data-stu-id="6d71f-191">You can combine modifiers to declare a struct as `readonly ref`.</span></span> <span data-ttu-id="6d71f-192">A `readonly ref struct` obejmuje zalety i `ref struct` ograniczenia deklaracji i `readonly struct` .</span><span class="sxs-lookup"><span data-stu-id="6d71f-192">A `readonly ref struct` combines the benefits and restrictions of `ref struct` and `readonly struct` declarations.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6d71f-193">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6d71f-193">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6d71f-194">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d71f-194">See also</span></span>

- [<span data-ttu-id="6d71f-195">Zapisz bezpieczny wydajny kod</span><span class="sxs-lookup"><span data-stu-id="6d71f-195">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="6d71f-196">Wartości zwracane ref i zmienne lokalne ref</span><span class="sxs-lookup"><span data-stu-id="6d71f-196">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="6d71f-197">Wyrażenie warunkowe ref</span><span class="sxs-lookup"><span data-stu-id="6d71f-197">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="6d71f-198">operator przypisania ref</span><span class="sxs-lookup"><span data-stu-id="6d71f-198">ref assignment operator</span></span>](../operators/assignment-operator.md#ref-assignment-operator)
- [<span data-ttu-id="6d71f-199">Przekazywanie parametrów</span><span class="sxs-lookup"><span data-stu-id="6d71f-199">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="6d71f-200">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="6d71f-200">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="6d71f-201">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6d71f-201">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6d71f-202">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6d71f-202">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6d71f-203">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="6d71f-203">C# Keywords</span></span>](index.md)
