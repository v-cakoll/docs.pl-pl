---
title: ref — słowo kluczowe — odwołanie do języka C#
ms.date: 03/26/2019
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 05f0bd8566851678203a3f064b96bfff7dee18b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399365"
---
# <a name="ref-c-reference"></a><span data-ttu-id="0a700-102">ref (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0a700-102">ref (C# Reference)</span></span>

<span data-ttu-id="0a700-103">Słowo `ref` kluczowe wskazuje wartość, która jest przekazywana przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="0a700-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="0a700-104">Jest on używany w czterech różnych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="0a700-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="0a700-105">W podpisie metody i wywołaniu metody, aby przekazać argument do metody przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="0a700-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="0a700-106">Aby uzyskać więcej informacji, zobacz [Przekazywanie argumentu przez odwołanie](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="0a700-106">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="0a700-107">W podpisie metody, aby zwrócić wartość do obiektu wywołującego przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="0a700-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="0a700-108">Aby uzyskać więcej informacji, zobacz [Wartości zwracane odwołania](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="0a700-108">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="0a700-109">W treści elementu członkowskiego, aby wskazać, że wartość zwracana odwołania jest przechowywana lokalnie jako odwołanie, które obiekt wywołujący zamierza zmodyfikować lub, ogólnie rzecz biorąc, zmienna lokalna uzyskuje dostęp do innej wartości przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="0a700-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="0a700-110">Aby uzyskać więcej informacji, zobacz [Ref locals](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="0a700-110">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="0a700-111">W `struct` oświadczeniu o `ref struct` zadeklarowanie a lub a `readonly ref struct`.</span><span class="sxs-lookup"><span data-stu-id="0a700-111">In a `struct` declaration to declare a `ref struct` or a `readonly ref struct`.</span></span> <span data-ttu-id="0a700-112">Aby uzyskać więcej informacji, zobacz [typy struktury ref](#ref-struct-types).</span><span class="sxs-lookup"><span data-stu-id="0a700-112">For more information, see [ref struct types](#ref-struct-types).</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="0a700-113">Przekazywanie argumentu przez odwołanie</span><span class="sxs-lookup"><span data-stu-id="0a700-113">Passing an argument by reference</span></span>

<span data-ttu-id="0a700-114">Gdy jest używany na liście parametrów `ref` metody, słowo kluczowe wskazuje, że argument jest przekazywany przez odwołanie, a nie przez wartość.</span><span class="sxs-lookup"><span data-stu-id="0a700-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="0a700-115">Słowo `ref` kluczowe sprawia, że formalny parametr alias dla argumentu, który musi być zmienna.</span><span class="sxs-lookup"><span data-stu-id="0a700-115">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="0a700-116">Innymi słowy, każda operacja na parametr jest na argument.</span><span class="sxs-lookup"><span data-stu-id="0a700-116">In other words, any operation on the parameter is made on the argument.</span></span> <span data-ttu-id="0a700-117">Na przykład jeśli obiekt wywołujący przekazuje wyrażenie zmiennej lokalnej lub wyrażenie dostępu elementu tablicy, a wywoływana metoda zastępuje obiekt, do którego odwołuje się parametr ref, zmienna lokalna obiektu wywołującego lub element tablicy odwołuje się teraz do nowego obiektu, gdy zwraca metodę.</span><span class="sxs-lookup"><span data-stu-id="0a700-117">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="0a700-118">Nie należy mylić pojęcia przekazywania przez odwołanie z pojęciem typów odwołań.</span><span class="sxs-lookup"><span data-stu-id="0a700-118">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="0a700-119">Te dwie koncepcje nie są takie same.</span><span class="sxs-lookup"><span data-stu-id="0a700-119">The two concepts are not the same.</span></span> <span data-ttu-id="0a700-120">Parametr metody można modyfikować `ref` niezależnie od tego, czy jest to typ wartości, czy typ odwołania.</span><span class="sxs-lookup"><span data-stu-id="0a700-120">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="0a700-121">Nie ma boksu typu wartości, gdy jest przekazywana przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="0a700-121">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="0a700-122">Aby użyć `ref` parametru, zarówno definicji metody, jak i `ref` metody wywołującej należy jawnie użyć słowa kluczowego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0a700-122">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="0a700-123">Argument, który jest `ref` przekazywany do lub `in` parametr uprzedniego przekazania.</span><span class="sxs-lookup"><span data-stu-id="0a700-123">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="0a700-124">Różni się to od [out](out-parameter-modifier.md) parametrów, których argumenty nie muszą być jawnie zainicjowane przed ich przekazaniem.</span><span class="sxs-lookup"><span data-stu-id="0a700-124">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="0a700-125">Członkowie klasy nie mogą mieć podpisów, `ref`które `in`różnią `out`się tylko przez , lub .</span><span class="sxs-lookup"><span data-stu-id="0a700-125">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="0a700-126">Błąd kompilatora występuje, jeśli jedyną różnicą między dwoma `ref` członkami typu jest `out`to, że jeden z nich ma parametr, a drugi ma , lub `in` parametr.</span><span class="sxs-lookup"><span data-stu-id="0a700-126">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="0a700-127">Poniższy kod, na przykład nie kompiluje.</span><span class="sxs-lookup"><span data-stu-id="0a700-127">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="0a700-128">Jednak metody mogą być przeciążone, `ref`gdy `in`jedna `out` metoda ma , lub parametr, a druga ma parametr value, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0a700-128">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="0a700-129">W innych sytuacjach, które wymagają dopasowania podpisu, `ref`takich `out` jak ukrywanie lub zastępowanie , `in`i są częścią podpisu i nie pasują do siebie.</span><span class="sxs-lookup"><span data-stu-id="0a700-129">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="0a700-130">Właściwości nie są zmiennymi.</span><span class="sxs-lookup"><span data-stu-id="0a700-130">Properties are not variables.</span></span> <span data-ttu-id="0a700-131">Są to metody i nie `ref` można ich przekazać do parametrów.</span><span class="sxs-lookup"><span data-stu-id="0a700-131">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="0a700-132">Nie można używać `ref`słów `in` `out` kluczowych i słów kluczowych dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="0a700-132">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="0a700-133">Metody asynchroniczne, które można zdefiniować za pomocą modyfikatora [asynchronii.](async.md)</span><span class="sxs-lookup"><span data-stu-id="0a700-133">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="0a700-134">Metody iterator, które obejmują zwrot `yield break` [uchylić](yield.md) lub instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0a700-134">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="0a700-135">Przekazywanie argumentu przez odwołanie: Przykład</span><span class="sxs-lookup"><span data-stu-id="0a700-135">Passing an argument by reference: An example</span></span>

<span data-ttu-id="0a700-136">Poprzednie przykłady przekazują typy wartości przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="0a700-136">The previous examples pass value types by reference.</span></span> <span data-ttu-id="0a700-137">Można również użyć `ref` słowa kluczowego, aby przekazać typy odwołań przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="0a700-137">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="0a700-138">Przekazywanie typu odwołania przez odwołanie umożliwia wywoływaną metodę, aby zastąpić obiekt, do którego odwołuje się parametr odwołania w obiekcie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="0a700-138">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="0a700-139">Lokalizacja magazynu obiektu jest przekazywana do metody jako wartość parametru referencyjnego.</span><span class="sxs-lookup"><span data-stu-id="0a700-139">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="0a700-140">Jeśli zmienisz wartość w lokalizacji magazynu parametru (aby wskazać nowy obiekt), należy również zmienić lokalizację magazynu, do której odwołuje się obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="0a700-140">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="0a700-141">Poniższy przykład przekazuje wystąpienie typu odwołania `ref` jako parametr.</span><span class="sxs-lookup"><span data-stu-id="0a700-141">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="0a700-142">Aby uzyskać więcej informacji na temat przekazywania typów odwołań według wartości i przez odwołanie, zobacz [Przekazywanie parametrów typu odwołania](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="0a700-142">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="0a700-143">Odwoływanie się do zwracanych wartości</span><span class="sxs-lookup"><span data-stu-id="0a700-143">Reference return values</span></span>

<span data-ttu-id="0a700-144">Wartości zwracane odwołania (lub ref zwraca) są wartości, które zwraca metoda przez odwołanie do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="0a700-144">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="0a700-145">Oznacza to, że obiekt wywołujący można zmodyfikować wartość zwracaną przez metodę, a ta zmiana jest odzwierciedlona w stanie obiektu, który zawiera metodę.</span><span class="sxs-lookup"><span data-stu-id="0a700-145">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span>

<span data-ttu-id="0a700-146">Wartość zwracana odwołania jest definiowana przy użyciu słowa kluczowego: `ref`</span><span class="sxs-lookup"><span data-stu-id="0a700-146">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="0a700-147">W podpisie metody.</span><span class="sxs-lookup"><span data-stu-id="0a700-147">In the method signature.</span></span> <span data-ttu-id="0a700-148">Na przykład następujący podpis metody `GetCurrentPrice` wskazuje, <xref:System.Decimal> że metoda zwraca wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="0a700-148">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="0a700-149">Między `return` tokenem a zmienną `return` zwróconą w instrukcji w metodzie.</span><span class="sxs-lookup"><span data-stu-id="0a700-149">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="0a700-150">Przykład:</span><span class="sxs-lookup"><span data-stu-id="0a700-150">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="0a700-151">Aby obiekt wywołujący zmodyfikować stan obiektu, wartość zwracana odwołania musi być przechowywana w zmiennej, która jest jawnie zdefiniowana jako [ref local](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="0a700-151">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="0a700-152">Wywoływana metoda może również zadeklarować wartość zwracaną, aby `ref readonly` zwrócić wartość przez odwołanie i wymusić, że kod wywołujący nie może zmodyfikować zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="0a700-152">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="0a700-153">Metoda wywołująca można uniknąć kopiowania zwróconej wartości przez przechowywanie wartości w zmiennej local [ref readonly.](#ref-readonly-locals)</span><span class="sxs-lookup"><span data-stu-id="0a700-153">The calling method can avoid copying the returned valued by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="0a700-154">Na przykład zobacz [Ref zwraca i ref locals przykład](#a-ref-returns-and-ref-locals-example).</span><span class="sxs-lookup"><span data-stu-id="0a700-154">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="0a700-155">Ref miejscowi</span><span class="sxs-lookup"><span data-stu-id="0a700-155">Ref locals</span></span>

<span data-ttu-id="0a700-156">Zmienna lokalna ref jest używana do `return ref`odwoływania się do wartości zwracanych przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="0a700-156">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="0a700-157">Zmienna lokalna ref nie może zostać zainicjowana do wartości zwracanej bez ref.</span><span class="sxs-lookup"><span data-stu-id="0a700-157">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="0a700-158">Innymi słowy, prawa strona inicjowania musi być odwołaniem.</span><span class="sxs-lookup"><span data-stu-id="0a700-158">In other words, the right hand side of the initialization must be a reference.</span></span> <span data-ttu-id="0a700-159">Wszelkie modyfikacje wartości ref local są odzwierciedlane w stanie obiektu, którego metoda zwróciła wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="0a700-159">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="0a700-160">Można zdefiniować ref local `ref` przy użyciu słowa kluczowego przed deklaracją zmiennej, a także bezpośrednio przed wywołaniem metody, która zwraca wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="0a700-160">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="0a700-161">Na przykład następująca instrukcja definiuje wartość lokalną ref zwracaną przez metodę o nazwie: `GetEstimatedValue`</span><span class="sxs-lookup"><span data-stu-id="0a700-161">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="0a700-162">Można uzyskać dostęp do wartości przez odwołanie w ten sam sposób.</span><span class="sxs-lookup"><span data-stu-id="0a700-162">You can access a value by reference in the same way.</span></span> <span data-ttu-id="0a700-163">W niektórych przypadkach dostęp do wartości przez odwołanie zwiększa wydajność, unikając potencjalnie kosztownej operacji kopiowania.</span><span class="sxs-lookup"><span data-stu-id="0a700-163">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="0a700-164">Na przykład w poniższej instrukcji pokazano, jak można zdefiniować wartość lokalną ref, która jest używana do odwoływania się do wartości.</span><span class="sxs-lookup"><span data-stu-id="0a700-164">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="0a700-165">Należy zauważyć, że `ref` w obu przykładach słowo kluczowe musi być używane w obu miejscach lub kompilator generuje błąd CS8172, "Nie można zainicjować zmiennej przez odwołanie z wartością."</span><span class="sxs-lookup"><span data-stu-id="0a700-165">Note that in both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="0a700-166">Począwszy od C# 7.3, zmienna `foreach` iteracji instrukcji może być ref lokalnej lub ref readonly zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="0a700-166">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be ref local or ref readonly local variable.</span></span> <span data-ttu-id="0a700-167">Aby uzyskać więcej informacji, zobacz [artykuł foreach instrukcji.](foreach-in.md)</span><span class="sxs-lookup"><span data-stu-id="0a700-167">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

<span data-ttu-id="0a700-168">Również począwszy od C# 7.3, można ponownie przypisać ref lokalnej lub ref readonly zmiennej lokalnej z [operatorem przypisania ref](../operators/assignment-operator.md#ref-assignment-operator).</span><span class="sxs-lookup"><span data-stu-id="0a700-168">Also beginning with C# 7.3, you can reassign a ref local or ref readonly local variable with the [ref assignment operator](../operators/assignment-operator.md#ref-assignment-operator).</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="0a700-169">Ref readonly mieszkańców</span><span class="sxs-lookup"><span data-stu-id="0a700-169">Ref readonly locals</span></span>

<span data-ttu-id="0a700-170">Ref readonly local jest używany do odwoływania się do `ref readonly` wartości zwracanych `return ref`przez metodę lub właściwość, która ma w swoim podpisie i używa .</span><span class="sxs-lookup"><span data-stu-id="0a700-170">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="0a700-171">Zmienna `ref readonly` łączy właściwości zmiennej `ref` lokalnej ze `readonly` zmienną: jest aliasem do magazynu, do których jest przypisany, i nie można go zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="0a700-171">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span>

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="0a700-172">Ref zwraca i ref locals przykład</span><span class="sxs-lookup"><span data-stu-id="0a700-172">A ref returns and ref locals example</span></span>

<span data-ttu-id="0a700-173">W poniższym przykładzie `Book` zdefiniowano <xref:System.String> klasę, `Author`która ma dwa pola i `Title` .</span><span class="sxs-lookup"><span data-stu-id="0a700-173">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="0a700-174">Definiuje również `BookCollection` klasę, która zawiera tablicę prywatną `Book` obiektów.</span><span class="sxs-lookup"><span data-stu-id="0a700-174">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="0a700-175">Poszczególne obiekty książki są zwracane `GetBookByTitle` przez odwołanie przez wywołanie jego metody.</span><span class="sxs-lookup"><span data-stu-id="0a700-175">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="0a700-176">Gdy obiekt wywołujący przechowuje wartość `GetBookByTitle` zwracaną przez metodę jako ref local, zmiany wprowadzone przez `BookCollection` obiekt wywołujący do wartości zwracanej są odzwierciedlane w obiekcie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0a700-176">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a><span data-ttu-id="0a700-177">Typy struktury ref</span><span class="sxs-lookup"><span data-stu-id="0a700-177">Ref struct types</span></span>

<span data-ttu-id="0a700-178">Dodawanie `ref` modyfikatora `struct` do deklaracji definiuje, że wystąpienia tego typu muszą być przydzielane na stosie.</span><span class="sxs-lookup"><span data-stu-id="0a700-178">Adding the `ref` modifier to a `struct` declaration defines that instances of that type must be stack allocated.</span></span> <span data-ttu-id="0a700-179">Innymi słowy wystąpienia tych typów nigdy nie można utworzyć na stercie jako element członkowski innej klasy.</span><span class="sxs-lookup"><span data-stu-id="0a700-179">In other words, instances of these types can never be created on the heap as a member of another class.</span></span> <span data-ttu-id="0a700-180">Główną motywacją dla <xref:System.Span%601> tej funkcji były i powiązane struktury.</span><span class="sxs-lookup"><span data-stu-id="0a700-180">The primary motivation for this feature was <xref:System.Span%601> and related structures.</span></span>

<span data-ttu-id="0a700-181">Celem przechowywania `ref struct` typu jako zmiennej przydzielonej do stosu wprowadza `ref struct` kilka reguł, które kompilator wymusza dla wszystkich typów.</span><span class="sxs-lookup"><span data-stu-id="0a700-181">The goal of keeping a `ref struct` type as a stack-allocated variable introduces several rules that the compiler enforces for all `ref struct` types.</span></span>

- <span data-ttu-id="0a700-182">Nie można boksować `ref struct`pliku .</span><span class="sxs-lookup"><span data-stu-id="0a700-182">You can't box a `ref struct`.</span></span> <span data-ttu-id="0a700-183">Nie można przypisać `ref struct` typu do zmiennej typu `object`lub `dynamic`dowolnego typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0a700-183">You cannot assign a `ref struct` type to a variable of type `object`, `dynamic`, or any interface type.</span></span>
- <span data-ttu-id="0a700-184">`ref struct`typy nie można zaimplementować interfejsów.</span><span class="sxs-lookup"><span data-stu-id="0a700-184">`ref struct` types cannot implement interfaces.</span></span>
- <span data-ttu-id="0a700-185">Nie można zadeklarować `ref struct` jako członka pola klasy lub normalnej struktury.</span><span class="sxs-lookup"><span data-stu-id="0a700-185">You can't declare a `ref struct` as a field member of a class or a normal struct.</span></span> <span data-ttu-id="0a700-186">Obejmuje to deklarowanie właściwości zaimplementowanej automatycznie, która tworzy wygenerowane przez kompilator pole zapasowe.</span><span class="sxs-lookup"><span data-stu-id="0a700-186">This includes declaring an auto-implemented property, which creates a compiler generated backing field.</span></span>
- <span data-ttu-id="0a700-187">Nie można zadeklarować zmiennych lokalnych, które są `ref struct` typami w metodach asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="0a700-187">You cannot declare local variables that are `ref struct` types in async methods.</span></span> <span data-ttu-id="0a700-188">Można zadeklarować je w metodach <xref:System.Threading.Tasks.Task>synchronicznych, które zwracają lub <xref:System.Threading.Tasks.Task%601> `Task`-like typów.</span><span class="sxs-lookup"><span data-stu-id="0a700-188">You can declare them in synchronous methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> or `Task`-like types.</span></span>
- <span data-ttu-id="0a700-189">Nie można `ref struct` zadeklarować zmiennych lokalnych w iteratory.</span><span class="sxs-lookup"><span data-stu-id="0a700-189">You cannot declare `ref struct` local variables in iterators.</span></span>
- <span data-ttu-id="0a700-190">Nie można `ref struct` przechwytywać zmiennych w wyrażeniach lambda lub funkcjach lokalnych.</span><span class="sxs-lookup"><span data-stu-id="0a700-190">You cannot capture `ref struct` variables in lambda expressions or local functions.</span></span>

<span data-ttu-id="0a700-191">Ograniczenia te zapewniają, że nie `ref struct` przypadkowo użyć w sposób, który może promować go do zarządzanego sterty.</span><span class="sxs-lookup"><span data-stu-id="0a700-191">These restrictions ensure you don't accidentally use a `ref struct` in a manner that could promote it to the managed heap.</span></span>

<span data-ttu-id="0a700-192">Modyfikatory można łączyć, aby `readonly ref`zadeklarować strukturę jako .</span><span class="sxs-lookup"><span data-stu-id="0a700-192">You can combine modifiers to declare a struct as `readonly ref`.</span></span> <span data-ttu-id="0a700-193">A `readonly ref struct` łączy korzyści i `ref struct` ograniczenia `readonly struct` i deklaracje.</span><span class="sxs-lookup"><span data-stu-id="0a700-193">A `readonly ref struct` combines the benefits and restrictions of `ref struct` and `readonly struct` declarations.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0a700-194">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0a700-194">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0a700-195">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a700-195">See also</span></span>

- [<span data-ttu-id="0a700-196">Napisz bezpieczny, wydajny kod</span><span class="sxs-lookup"><span data-stu-id="0a700-196">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="0a700-197">Wartości zwracane ref i zmienne lokalne ref</span><span class="sxs-lookup"><span data-stu-id="0a700-197">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="0a700-198">Warunkowe wyrażenie ref</span><span class="sxs-lookup"><span data-stu-id="0a700-198">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="0a700-199">Przekazywanie parametrów</span><span class="sxs-lookup"><span data-stu-id="0a700-199">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="0a700-200">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="0a700-200">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="0a700-201">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="0a700-201">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0a700-202">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="0a700-202">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0a700-203">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0a700-203">C# Keywords</span></span>](index.md)
