---
title: REF — słowo kluczowe (odwołanie w C#)
ms.date: 10/24/2018
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 9165a388122eeda5ca0499c6d75c2266780a6004
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195973"
---
# <a name="ref-c-reference"></a><span data-ttu-id="20942-102">ref (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="20942-102">ref (C# Reference)</span></span>

<span data-ttu-id="20942-103">`ref` — Słowo kluczowe wskazuje wartość informującą który jest przekazywany przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="20942-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="20942-104">Jest on używany w czterech różnych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="20942-104">It is used in four different contexts:</span></span>

- <span data-ttu-id="20942-105">W podpisie metody i w wywołaniu metody, aby przekazać argument do metody przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="20942-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="20942-106">Aby uzyskać więcej informacji, zobacz [przekazywaniem argumentu według odwołania](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="20942-106">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="20942-107">W podpisie metody, aby zwrócić wartości do obiektu wywołującego przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="20942-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="20942-108">Aby uzyskać więcej informacji, zobacz [wartości zwracane odwołanie](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="20942-108">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="20942-109">W treści elementu członkowskiego aby wskazać, że zwracana wartość odwołania są przechowywane lokalnie, jako odwołanie do obiektu wywołującego zamierza zmienić lub ogólnie rzecz biorąc, zmienna lokalna uzyskuje dostęp do innej wartości przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="20942-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify or, in general, a local variable accesses another value by reference.</span></span> <span data-ttu-id="20942-110">Aby uzyskać więcej informacji, zobacz [zmienne lokalne Ref](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="20942-110">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="20942-111">W `struct` deklaracji, aby zadeklarować `ref struct` lub `ref readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="20942-111">In a `struct` declaration to declare a `ref struct` or a `ref readonly struct`.</span></span> <span data-ttu-id="20942-112">Aby uzyskać więcej informacji, zobacz [typy struktury ref](#ref-struct-types).</span><span class="sxs-lookup"><span data-stu-id="20942-112">For more information, see [ref struct types](#ref-struct-types).</span></span>


## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="20942-113">Przekazywanie argumentów poprzez odwołanie</span><span class="sxs-lookup"><span data-stu-id="20942-113">Passing an argument by reference</span></span>

<span data-ttu-id="20942-114">Gdy są używane w liście parametrów metody, `ref` słowo kluczowe wskazuje, że argument jest przekazywany przez odwołanie, nie przez wartość.</span><span class="sxs-lookup"><span data-stu-id="20942-114">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="20942-115">Przekazywanie poprzez odwołanie powoduje, że każda zmiana argumentu w metodzie wywoływanej jest odzwierciedlana w wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="20942-115">The effect of passing by reference is that any change to the argument in the called method is reflected in the calling method.</span></span> <span data-ttu-id="20942-116">Na przykład jeśli obiekt wywołujący przekazuje wyrażenie lokalnej zmiennej lub wyrażenia dostępu do elementu tablicy, a następnie wywoływana metoda zastępuje obiekt, do którego odwołuje się parametr ref, a następnie obiekt wywołujący użytkownika lokalnego zmienna lub element tablicy teraz odwołuje się do nowego obiektu po Metoda zwraca.</span><span class="sxs-lookup"><span data-stu-id="20942-116">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="20942-117">Nie należy mylić koncepcji przekazywanie poprzez odwołanie z pojęciem typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="20942-117">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="20942-118">Dwoma pojęciami nie są takie same.</span><span class="sxs-lookup"><span data-stu-id="20942-118">The two concepts are not the same.</span></span> <span data-ttu-id="20942-119">Parametr metody mogą być modyfikowane przez `ref` niezależnie od tego, czy jest typem wartości lub typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="20942-119">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="20942-120">Istnieje nie opakowanie typu wartości, gdy jest przekazywany przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="20942-120">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="20942-121">Aby użyć `ref` jawnie użyć parametru, zarówno definicję metody, jak i wywoływania metody `ref` — słowo kluczowe, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="20942-121">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="20942-122">Argument, który jest przekazywany do `ref` lub `in` parametr musi zostać zainicjowany przed przekazaniem jej.</span><span class="sxs-lookup"><span data-stu-id="20942-122">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="20942-123">To różni się od [się](out-parameter-modifier.md) parametrów, w której argumenty nie trzeba jawnie zainicjowane przed przekazaniem ich.</span><span class="sxs-lookup"><span data-stu-id="20942-123">This differs from [out](out-parameter-modifier.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="20942-124">Składowa klasy nie może mieć podpisów, które różnią się tylko przez `ref`, `in`, lub `out`.</span><span class="sxs-lookup"><span data-stu-id="20942-124">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="20942-125">Błąd kompilatora występuje, jeśli jedyną różnicą między dwa elementy członkowskie typu jest, że jedna z nich ma `ref` parametru, a druga ma `out`, lub `in` parametru.</span><span class="sxs-lookup"><span data-stu-id="20942-125">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="20942-126">Na przykład, poniższy kod nie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="20942-126">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="20942-127">Jednak mogą być przeciążone metody, gdy ma jedną z metod `ref`, `in`, lub `out` parametru, a druga ma wartość parametru, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="20942-127">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="20942-128">W innych sytuacjach, które wymagają podpis dopasowania, takich jak ukrywać lub zastępowanie `in`, `ref`, i `out` są dostępne w ramach sygnatury i nie pasują do siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="20942-128">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="20942-129">Właściwości nie są zmienne.</span><span class="sxs-lookup"><span data-stu-id="20942-129">Properties are not variables.</span></span> <span data-ttu-id="20942-130">To metody, a nie można przekazać do `ref` parametrów.</span><span class="sxs-lookup"><span data-stu-id="20942-130">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="20942-131">Nie można użyć `ref`, `in`, i `out` słowa kluczowe dla następujących rodzajów metod:</span><span class="sxs-lookup"><span data-stu-id="20942-131">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="20942-132">Metody asynchroniczne, które można zdefiniować przy użyciu [async](async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="20942-132">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="20942-133">Metody iteratora, które obejmują [yield return](yield.md) lub `yield break` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="20942-133">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="20942-134">Przekazywanie argumentów poprzez odwołanie: przykład</span><span class="sxs-lookup"><span data-stu-id="20942-134">Passing an argument by reference: An example</span></span>

<span data-ttu-id="20942-135">Poprzednie przykłady przekazuj typów wartości przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="20942-135">The previous examples pass value types by reference.</span></span> <span data-ttu-id="20942-136">Można również użyć `ref` — słowo kluczowe do przekazania odwołania typów przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="20942-136">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="20942-137">Przekazywanie typu odwołania przez odwołanie pozwala zastąpić obiekt, do którego odwołuje się parametr odwołania w obiekcie wywołującym metodę o nazwie.</span><span class="sxs-lookup"><span data-stu-id="20942-137">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="20942-138">Lokalizacja magazynu obiekt jest przekazywany do metody jako wartość parametru odwołania.</span><span class="sxs-lookup"><span data-stu-id="20942-138">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="20942-139">Jeśli zmienisz wartość w określonej lokalizacji magazynu parametru (aby wskazywały nowy obiekt), możesz również zmienić lokalizację magazynu, do którego odwołuje się obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="20942-139">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="20942-140">Poniższy przykład przekazuje wystąpienia typu referencyjnego jako `ref` parametru.</span><span class="sxs-lookup"><span data-stu-id="20942-140">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="20942-141">Aby uzyskać więcej informacji dotyczących przekazywania typów referencyjnych według wartości i według odwołania, zobacz [przekazywanie parametrów typu odwołanie](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="20942-141">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="20942-142">Wartości zwracane odwołanie</span><span class="sxs-lookup"><span data-stu-id="20942-142">Reference return values</span></span>

<span data-ttu-id="20942-143">Wartości zwracane odwołanie (lub zwracanych ref) są wartościami, które metoda zwraca wartość przez odwołanie do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="20942-143">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="20942-144">Oznacza to obiekt wywołujący, można zmodyfikować wartości zwracanej przez metodę, a ta zmiana jest odzwierciedlana w stan obiektu, który zawiera metodę.</span><span class="sxs-lookup"><span data-stu-id="20942-144">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span>

<span data-ttu-id="20942-145">Odwołanie zwracają wartość jest definiowana za pomocą `ref` — słowo kluczowe:</span><span class="sxs-lookup"><span data-stu-id="20942-145">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="20942-146">W podpisie metody.</span><span class="sxs-lookup"><span data-stu-id="20942-146">In the method signature.</span></span> <span data-ttu-id="20942-147">Na przykład, następujący podpis metody oznacza, że `GetCurrentPrice` metoda zwraca <xref:System.Decimal> wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="20942-147">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="20942-148">Między `return` token i zmienna zwracane w `return` instrukcji w metodzie.</span><span class="sxs-lookup"><span data-stu-id="20942-148">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="20942-149">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="20942-149">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="20942-150">Aby obiekt wywołujący, aby zmodyfikować stan obiektu, musi być przechowywana wartość do zmiennej, która jest jawnie zdefiniowany jako zwrócić odwołanie [odwołanie lokalne](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="20942-150">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="20942-151">Wywoływana metoda również mogą zadeklarować wartość zwracana jako `ref readonly` zwraca wartość przez odwołanie w celu wymuszenia, aby kod wywołujący nie można zmodyfikować zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="20942-151">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code cannot modify the returned value.</span></span> <span data-ttu-id="20942-152">Kopiowanie zwracanego zwracającej dzięki przechowywaniu wartości w lokalnej uniknąć wywoływania metody [ref tylko do odczytu](#ref-readonly-locals) zmiennej.</span><span class="sxs-lookup"><span data-stu-id="20942-152">The calling method can avoid copying the returned valued by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="20942-153">Aby uzyskać przykład, zobacz [A wartości zwracane ref i przykład zmienne lokalne ref](#a-ref-returns-and-ref-locals-example)</span><span class="sxs-lookup"><span data-stu-id="20942-153">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example)</span></span>

## <a name="ref-locals"></a><span data-ttu-id="20942-154">Zmienne lokalne REF</span><span class="sxs-lookup"><span data-stu-id="20942-154">Ref locals</span></span>

<span data-ttu-id="20942-155">Zmienna lokalna ref jest używana do odwoływania się do wartości zwracane wartości przy użyciu `return ref`.</span><span class="sxs-lookup"><span data-stu-id="20942-155">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="20942-156">Zmienna lokalna ref nie można zainicjować do wartości zwracanej-ref.</span><span class="sxs-lookup"><span data-stu-id="20942-156">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="20942-157">Innymi słowy po prawej stronie inicjowania musi być odwołaniem.</span><span class="sxs-lookup"><span data-stu-id="20942-157">In other words, the right hand side of the initialization must be a reference.</span></span> <span data-ttu-id="20942-158">Wszelkie modyfikacje, wartość Zmienna lokalna ref są odzwierciedlane w stan obiektu, którego metoda zwróciła wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="20942-158">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="20942-159">Zmienna lokalna ref jest definiowane za pomocą `ref` — słowo kluczowe przed deklaracją zmiennej, a także bezpośrednio przed wywołaniem metody, która zwraca wartość przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="20942-159">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="20942-160">Na przykład następująca instrukcja definiuje lokalna wartość ref, który jest zwracany przez metodę o nazwie `GetEstimatedValue`:</span><span class="sxs-lookup"><span data-stu-id="20942-160">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="20942-161">Dostępne wartości przez odwołanie, w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="20942-161">You can access a value by reference in the same way.</span></span> <span data-ttu-id="20942-162">W niektórych przypadkach uzyskiwanie dostępu do wartości przez odwołanie zwiększa wydajność, unikając operacji kopiowania potencjalnie kosztowne.</span><span class="sxs-lookup"><span data-stu-id="20942-162">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="20942-163">Na przykład następująca instrukcja pokazuje, jak jeden można zdefiniować wartości lokalnej ref, służący do odwoływać się do wartości.</span><span class="sxs-lookup"><span data-stu-id="20942-163">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="20942-164">Należy pamiętać, że w obu przykładach `ref` w obu miejscach, można użyć słowa kluczowego lub kompilator generuje błąd CS8172, "Nie można zainicjować zmiennej przez odwołanie o wartości".</span><span class="sxs-lookup"><span data-stu-id="20942-164">Note that in both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="20942-165">Zmienne lokalne REF tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="20942-165">Ref readonly locals</span></span>

<span data-ttu-id="20942-166">Odwołanie lokalne tylko do odczytu jest używana do odwoływania się do wartości zwracanych przez metodę lub właściwość, która ma `ref readonly` w jego podpisu i używa `return ref`.</span><span class="sxs-lookup"><span data-stu-id="20942-166">A ref readonly local is used to refer to values returned by the method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="20942-167">A `ref readonly` zmiennej łączy właściwości `ref` zmienna lokalna o `readonly` zmiennej: jest to alias do magazynu jest przypisany do, a nie można modyfikować.</span><span class="sxs-lookup"><span data-stu-id="20942-167">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it is an alias to the storage it's assigned to, and it cannot be modified.</span></span> 

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="20942-168">Element wartości zwracane ref i przykład zmienne lokalne ref</span><span class="sxs-lookup"><span data-stu-id="20942-168">A ref returns and ref locals example</span></span>

<span data-ttu-id="20942-169">W poniższym przykładzie zdefiniowano `Book` klasę, która ma dwa <xref:System.String> pól `Title` i `Author`.</span><span class="sxs-lookup"><span data-stu-id="20942-169">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="20942-170">Umożliwia on również definiowanie `BookCollection` klasa, która zawiera prywatne tablicę `Book` obiektów.</span><span class="sxs-lookup"><span data-stu-id="20942-170">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="20942-171">Poszczególne książki obiekty są zwracane przez odwołanie, przez wywołanie jego `GetBookByTitle` metody.</span><span class="sxs-lookup"><span data-stu-id="20942-171">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="20942-172">Gdy obiekt wywołujący przechowuje wartość zwrócona przez obiekt `GetBookByTitle` zmiany, które sprawia, że obiekt wywołujący na wartość zwracaną metody jako lokalną ref, są odzwierciedlane w `BookCollection` obiektu, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="20942-172">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a><span data-ttu-id="20942-173">Typy struktury REF</span><span class="sxs-lookup"><span data-stu-id="20942-173">Ref struct types</span></span>

<span data-ttu-id="20942-174">Dodawanie `ref` modyfikatora `struct` deklaracja określa, że wystąpienia tego typu musi znajdować się na stosie.</span><span class="sxs-lookup"><span data-stu-id="20942-174">Adding the `ref` modifier to a `struct` declaration defines that instances of that type must be stack allocated.</span></span> <span data-ttu-id="20942-175">Innymi słowy te typy można nigdy nie można tworzyć wystąpień na stosie jest członkiem innej klasy.</span><span class="sxs-lookup"><span data-stu-id="20942-175">In other words, instances of these types can never be created on the heap as a member of another class.</span></span> <span data-ttu-id="20942-176">Główną motywacją do tej funkcji został <xref:System.Span%601> i pokrewne struktury.</span><span class="sxs-lookup"><span data-stu-id="20942-176">The primary motivation for this feature was <xref:System.Span%601> and related structures.</span></span>

<span data-ttu-id="20942-177">Celem zachowywaniu `ref struct` wpisz zmienną przydzielanych ze stosów wprowadza kilka reguł, które kompilator wymusza dla wszystkich `ref struct` typów.</span><span class="sxs-lookup"><span data-stu-id="20942-177">The goal of keeping a `ref struct` type as a stack-allocated variable introduces several rules that the compiler enforces for all `ref struct` types.</span></span>

- <span data-ttu-id="20942-178">Nie można polu `ref struct`.</span><span class="sxs-lookup"><span data-stu-id="20942-178">You can't box a `ref struct`.</span></span> <span data-ttu-id="20942-179">Nie można przypisać `ref struct` typ do zmiennej typu `object`, `dynamic`, lub dowolny typ interfejsu.</span><span class="sxs-lookup"><span data-stu-id="20942-179">You cannot assign a `ref struct` type to a variable of type `object`, `dynamic`, or any interface type.</span></span>
- <span data-ttu-id="20942-180">`ref struct` typy nie mogą implementować interfejsów.</span><span class="sxs-lookup"><span data-stu-id="20942-180">`ref struct` types cannot implement interfaces.</span></span>
- <span data-ttu-id="20942-181">Nie można zadeklarować `ref struct` jako członek klasy lub struktury normalny.</span><span class="sxs-lookup"><span data-stu-id="20942-181">You can't declare a `ref struct` as a member of a class or a normal struct.</span></span>
- <span data-ttu-id="20942-182">Nie można zadeklarować zmienne lokalne, które są `ref struct` typów w metodach asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="20942-182">You cannot declare local variables that are `ref struct` types in async methods.</span></span> <span data-ttu-id="20942-183">Można zadeklarować je metod synchronicznych, które zwracają <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> lub `Task`— takich jak typy.</span><span class="sxs-lookup"><span data-stu-id="20942-183">You can declare them in synchronous methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> or `Task`-like types.</span></span>
- <span data-ttu-id="20942-184">Nie można zadeklarować `ref struct` zmiennych lokalnych w iteratorach.</span><span class="sxs-lookup"><span data-stu-id="20942-184">You cannot declare `ref struct` local variables in iterators.</span></span>
- <span data-ttu-id="20942-185">Nie można dokonać przechwytu `ref struct` zmiennych w wyrażeniach lambda lub funkcji lokalnych.</span><span class="sxs-lookup"><span data-stu-id="20942-185">You cannot capture `ref struct` variables in lambda expressions or local functions.</span></span>

<span data-ttu-id="20942-186">Te ograniczenia, upewnij się, nie używasz przypadkowo `ref struct` w taki sposób, który można podwyższyć poziom do zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="20942-186">These restrictions ensure you don't accidentally use a `ref struct` in a manner that could promote it to the managed heap.</span></span>

<span data-ttu-id="20942-187">Można połączyć modyfikatorów, aby zadeklarować struktury jako `readonly ref`.</span><span class="sxs-lookup"><span data-stu-id="20942-187">You can combine modifiers to declare a struct as `readonly ref`.</span></span> <span data-ttu-id="20942-188">A `readonly ref struct` łączy korzyści i ograniczeń dotyczących `ref struct` i `readonly struct` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="20942-188">A `readonly ref struct` combines the benefits and restrictions of `ref struct` and `readonly struct` declarations.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="20942-189">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="20942-189">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="20942-190">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20942-190">See also</span></span>

- [<span data-ttu-id="20942-191">Pisanie kodu efektywne bezpieczne</span><span class="sxs-lookup"><span data-stu-id="20942-191">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)  
- [<span data-ttu-id="20942-192">Przekazywanie parametrów</span><span class="sxs-lookup"><span data-stu-id="20942-192">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)  
- [<span data-ttu-id="20942-193">Parametry metody</span><span class="sxs-lookup"><span data-stu-id="20942-193">Method Parameters</span></span>](method-parameters.md)  
- [<span data-ttu-id="20942-194">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="20942-194">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="20942-195">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="20942-195">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="20942-196">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="20942-196">C# Keywords</span></span>](index.md)
