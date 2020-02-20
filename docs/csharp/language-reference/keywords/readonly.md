---
title: ReadOnly — słowo C# kluczowe-odwołanie
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: c3db8f7791e510768608e834339526fb82771979
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451944"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="75ff9-102">readonly (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="75ff9-102">readonly (C# Reference)</span></span>

<span data-ttu-id="75ff9-103">Słowo kluczowe `readonly` jest modyfikatorem, który może być używany w czterech kontekstach:</span><span class="sxs-lookup"><span data-stu-id="75ff9-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="75ff9-104">W [deklaracji pola](#readonly-field-example)`readonly` wskazuje, że przypisanie do pola może wystąpić tylko jako część deklaracji lub w konstruktorze w tej samej klasie.</span><span class="sxs-lookup"><span data-stu-id="75ff9-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="75ff9-105">Pole tylko do odczytu można przypisać i ponownie przypisać wiele razy w deklaracji pola i konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="75ff9-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span> 
  
  <span data-ttu-id="75ff9-106">Nie można przypisać pola `readonly` po zakończeniu konstruktora.</span><span class="sxs-lookup"><span data-stu-id="75ff9-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="75ff9-107">Ta reguła ma inne konsekwencje dla typów wartości i typów referencyjnych:</span><span class="sxs-lookup"><span data-stu-id="75ff9-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="75ff9-108">Ponieważ typy wartości bezpośrednio zawierają swoje dane, pole, które jest `readonly` typem wartości jest niezmienne.</span><span class="sxs-lookup"><span data-stu-id="75ff9-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span> 
  - <span data-ttu-id="75ff9-109">Ponieważ typy odwołań zawierają odwołanie do swoich danych, pole, które jest typem referencyjnym `readonly` musi zawsze odwoływać się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="75ff9-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="75ff9-110">Ten obiekt nie jest niezmienny.</span><span class="sxs-lookup"><span data-stu-id="75ff9-110">That object isn't immutable.</span></span> <span data-ttu-id="75ff9-111">Modyfikator `readonly` uniemożliwia zastąpienie pola przez inne wystąpienie typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="75ff9-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="75ff9-112">Jednak modyfikator nie zapobiega modyfikowaniu danych wystąpienia pola za pośrednictwem pola tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="75ff9-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="75ff9-113">Typ widoczny na zewnątrz, który zawiera zewnętrzny widoczny pole tylko do odczytu, które jest modyfikowalnym typem odwołania może być luką w zabezpieczeniach i może wyzwolić ostrzeżenie [CA2104](/visualstudio/code-quality/ca2104) : "nie deklaruj tylko odczytu modyfikowalnych typów odwołań".</span><span class="sxs-lookup"><span data-stu-id="75ff9-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="75ff9-114">W [definicji`readonly struct`](#readonly-struct-example)`readonly` wskazuje, że `struct` jest niezmienny.</span><span class="sxs-lookup"><span data-stu-id="75ff9-114">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="75ff9-115">W [definicji elementu członkowskiego`readonly`](#readonly-member-examples)`readonly` wskazuje, że element członkowski `struct` nie ulega mutacji w wewnętrznym stanie struktury.</span><span class="sxs-lookup"><span data-stu-id="75ff9-115">In a [`readonly` member definition](#readonly-member-examples), `readonly` indicates that a member of a `struct` doesn't mutate the struct's internal state.</span></span>
- <span data-ttu-id="75ff9-116">W [`ref readonly` zwraca metodę](#ref-readonly-return-example), modyfikator `readonly` wskazuje, że metoda zwraca odwołanie, a zapisy nie są dozwolone dla tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="75ff9-116">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="75ff9-117">Konteksty `readonly struct` i `ref readonly` zostały dodane do C# 7,2.</span><span class="sxs-lookup"><span data-stu-id="75ff9-117">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="75ff9-118">`readonly` członkowie struktury zostali dodani C# do 8,0</span><span class="sxs-lookup"><span data-stu-id="75ff9-118">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="75ff9-119">Przykład pola tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="75ff9-119">Readonly field example</span></span>

<span data-ttu-id="75ff9-120">W tym przykładzie nie można zmienić wartości pola `year` w metodzie `ChangeYear`, nawet jeśli przypisano mu wartość w konstruktorze klasy:</span><span class="sxs-lookup"><span data-stu-id="75ff9-120">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="75ff9-121">Wartość można przypisać do pola `readonly` tylko w następujących kontekstach:</span><span class="sxs-lookup"><span data-stu-id="75ff9-121">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="75ff9-122">Gdy zmienna jest inicjowana w deklaracji, na przykład:</span><span class="sxs-lookup"><span data-stu-id="75ff9-122">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="75ff9-123">W konstruktorze wystąpienia klasy, która zawiera deklarację pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="75ff9-123">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="75ff9-124">W konstruktorze statycznym klasy, która zawiera deklarację pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="75ff9-124">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="75ff9-125">Te konteksty konstruktorów są również jedynymi kontekstami, w których są poprawne do przekazywania pola `readonly` jako parametru [out](out-parameter-modifier.md) lub [ref](ref.md) .</span><span class="sxs-lookup"><span data-stu-id="75ff9-125">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="75ff9-126">Słowo kluczowe `readonly` różni się od słowa kluczowego [const](const.md) .</span><span class="sxs-lookup"><span data-stu-id="75ff9-126">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="75ff9-127">Pole `const` można zainicjować tylko w deklaracji pola.</span><span class="sxs-lookup"><span data-stu-id="75ff9-127">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="75ff9-128">Pole `readonly` można przypisać wiele razy w deklaracji pola i w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="75ff9-128">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="75ff9-129">W związku z tym pola `readonly` mogą mieć różne wartości w zależności od użytego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="75ff9-129">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="75ff9-130">Ponadto, chociaż `const` pole jest stałą czasu kompilacji, pole `readonly` może być używane dla stałych w czasie wykonywania, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="75ff9-130">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="75ff9-131">W poprzednim przykładzie, jeśli używasz instrukcji podobnej do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="75ff9-131">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="75ff9-132">zostanie wyświetlony komunikat o błędzie kompilatora:</span><span class="sxs-lookup"><span data-stu-id="75ff9-132">you'll get the compiler error message:</span></span>

<span data-ttu-id="75ff9-133">**Nie można przypisać do pola tylko do odczytu (z wyjątkiem w konstruktorze lub inicjatorze zmiennych).**</span><span class="sxs-lookup"><span data-stu-id="75ff9-133">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="readonly-struct-example"></a><span data-ttu-id="75ff9-134">Przykład struktury ReadOnly</span><span class="sxs-lookup"><span data-stu-id="75ff9-134">Readonly struct example</span></span>

<span data-ttu-id="75ff9-135">Modyfikator `readonly` w definicji `struct` deklaruje, że struktura jest **niezmienna**.</span><span class="sxs-lookup"><span data-stu-id="75ff9-135">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="75ff9-136">Każde pole wystąpienia `struct` musi być oznaczone `readonly`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="75ff9-136">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

<span data-ttu-id="75ff9-137">Poprzedni przykład używa [Właściwości autoreadonly](../../properties.md#read-only) do deklarowania magazynu.</span><span class="sxs-lookup"><span data-stu-id="75ff9-137">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="75ff9-138">Powoduje, że kompilator tworzy `readonly` pól zapasowych dla tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="75ff9-138">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="75ff9-139">Można również zadeklarować bezpośrednio `readonly` pól:</span><span class="sxs-lookup"><span data-stu-id="75ff9-139">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="75ff9-140">Dodawanie pola, które nie jest oznaczone `readonly` generuje błąd kompilatora `CS8340`: "wystąpienia pól struktur tylko do odczytu muszą być tylko do odczytu".</span><span class="sxs-lookup"><span data-stu-id="75ff9-140">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="readonly-member-examples"></a><span data-ttu-id="75ff9-141">Przykłady elementu członkowskiego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="75ff9-141">Readonly member examples</span></span>

<span data-ttu-id="75ff9-142">Innym razem można utworzyć strukturę, która obsługuje mutację.</span><span class="sxs-lookup"><span data-stu-id="75ff9-142">Other times, you may create a struct that supports mutation.</span></span> <span data-ttu-id="75ff9-143">W takich przypadkach niektóre elementy członkowskie wystąpienia mogłyby nie modyfikować stanu wewnętrznego struktury.</span><span class="sxs-lookup"><span data-stu-id="75ff9-143">In those cases, several of the instance members likely won't modify the internal state of the struct.</span></span> <span data-ttu-id="75ff9-144">Można zadeklarować te elementy członkowskie wystąpienia za pomocą modyfikatora `readonly`.</span><span class="sxs-lookup"><span data-stu-id="75ff9-144">You can declare those instance members with the `readonly` modifier.</span></span> <span data-ttu-id="75ff9-145">Kompilator wymusza przeznaczenie.</span><span class="sxs-lookup"><span data-stu-id="75ff9-145">The compiler enforces your intent.</span></span> <span data-ttu-id="75ff9-146">Jeśli ten element członkowski modyfikuje stan bezpośrednio lub uzyskuje dostęp do elementu członkowskiego, który nie jest również zadeklarowany za pomocą modyfikatora `readonly`, wynikiem jest błąd czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="75ff9-146">If that member modifies state directly or accesses a member that isn't also declared with the `readonly` modifier, the result is a compile-time error.</span></span> <span data-ttu-id="75ff9-147">Modyfikator `readonly` jest prawidłowy dla elementów członkowskich `struct`, a nie `class` lub `interface` deklaracjach składowych.</span><span class="sxs-lookup"><span data-stu-id="75ff9-147">The `readonly` modifier is valid on `struct` members, not `class` or `interface` member declarations.</span></span>

<span data-ttu-id="75ff9-148">Aby uzyskać dwie korzyści, należy zastosować modyfikator `readonly` do odpowiednich metod `struct`.</span><span class="sxs-lookup"><span data-stu-id="75ff9-148">You gain two advantages by applying the `readonly` modifier to applicable `struct` methods.</span></span> <span data-ttu-id="75ff9-149">Co najważniejsze, kompilator wymusza przeznaczenie.</span><span class="sxs-lookup"><span data-stu-id="75ff9-149">Most importantly, the compiler enforces your intent.</span></span> <span data-ttu-id="75ff9-150">Kod, który modyfikuje stan, nie jest prawidłowy w metodzie `readonly`.</span><span class="sxs-lookup"><span data-stu-id="75ff9-150">Code that modifies state isn't valid in a `readonly` method.</span></span> <span data-ttu-id="75ff9-151">Kompilator może również używać modyfikatora `readonly`, aby włączyć optymalizacje wydajności.</span><span class="sxs-lookup"><span data-stu-id="75ff9-151">The compiler may also make use of the `readonly` modifier to enable performance optimizations.</span></span> <span data-ttu-id="75ff9-152">Gdy duże typy `struct` są przesyłane przez odwołanie `in`, kompilator musi wygenerować kopię obronną, jeśli stan struktury może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="75ff9-152">When large `struct` types are passed by `in` reference, the compiler must generate a defensive copy if the state of the struct might be modified.</span></span> <span data-ttu-id="75ff9-153">W przypadku uzyskiwania dostępu tylko do `readonly` członków kompilator nie może utworzyć kopii obronnej.</span><span class="sxs-lookup"><span data-stu-id="75ff9-153">If only `readonly` members are accessed, the compiler may not create the defensive copy.</span></span>

<span data-ttu-id="75ff9-154">Modyfikator `readonly` jest prawidłowy dla większości elementów członkowskich `struct`, w tym metod, które zastępują metody zadeklarowane w <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="75ff9-154">The `readonly` modifier is valid on most members of a `struct`, including methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="75ff9-155">Istnieją pewne ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="75ff9-155">There are some restrictions:</span></span>

- <span data-ttu-id="75ff9-156">Nie można zadeklarować `readonly` statycznych metod lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="75ff9-156">You can't declare `readonly` static methods or properties.</span></span>
- <span data-ttu-id="75ff9-157">Nie można zadeklarować konstruktorów `readonly`.</span><span class="sxs-lookup"><span data-stu-id="75ff9-157">You can't declare `readonly` constructors.</span></span>

<span data-ttu-id="75ff9-158">Modyfikator `readonly` można dodać do deklaracji właściwości lub indeksatora:</span><span class="sxs-lookup"><span data-stu-id="75ff9-158">You can add the `readonly` modifier to a property or indexer declaration:</span></span>

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

<span data-ttu-id="75ff9-159">Możliwe jest również dodanie modyfikatora `readonly` do poszczególnych `get` lub `set` metod dostępu do właściwości lub indeksatora:</span><span class="sxs-lookup"><span data-stu-id="75ff9-159">You may also add the `readonly` modifier to individual `get` or `set` accessors of a property or indexer:</span></span>

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

<span data-ttu-id="75ff9-160">Nie można dodać modyfikatora `readonly` do właściwości i co najmniej jednej metody dostępu tej samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="75ff9-160">You may not add the `readonly` modifier to both a property and one or more of that same property's accessors.</span></span> <span data-ttu-id="75ff9-161">To samo ograniczenie dotyczy indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="75ff9-161">That same restriction applies to indexers.</span></span>

<span data-ttu-id="75ff9-162">Kompilator niejawnie stosuje modyfikator `readonly`, aby wstępnie zaimplementowane właściwości, w których zaimplementowany kod kompilatora nie modyfikuje stanu.</span><span class="sxs-lookup"><span data-stu-id="75ff9-162">The compiler implicitly applies the `readonly` modifier to auto-implemented properties where the compiler implemented code doesn't modify state.</span></span> <span data-ttu-id="75ff9-163">Jest to równoważne z następującymi deklaracjami:</span><span class="sxs-lookup"><span data-stu-id="75ff9-163">It's equivalent to the following declarations:</span></span>

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
``` 

<span data-ttu-id="75ff9-164">Można dodać modyfikator `readonly` w tych lokalizacjach, ale nie będzie to miało znaczącego efektu.</span><span class="sxs-lookup"><span data-stu-id="75ff9-164">You may add the `readonly` modifier in those locations, but it will have no meaningful effect.</span></span> <span data-ttu-id="75ff9-165">Nie można dodać modyfikatora `readonly` do autozaimplementowanej metody ustawiającej właściwości lub do właściwości autoimplementacji do odczytu/zapisu.</span><span class="sxs-lookup"><span data-stu-id="75ff9-165">You may not add the `readonly` modifier to an auto-implemented property setter, or to a read/write auto-implemented property.</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="75ff9-166">Przykład powrotu ref ReadOnly</span><span class="sxs-lookup"><span data-stu-id="75ff9-166">Ref readonly return example</span></span>

<span data-ttu-id="75ff9-167">Modyfikator `readonly` na `ref return` wskazuje, że zwracane odwołanie nie może być modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="75ff9-167">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="75ff9-168">Poniższy przykład zwraca odwołanie do źródła.</span><span class="sxs-lookup"><span data-stu-id="75ff9-168">The following example returns a reference to the origin.</span></span> <span data-ttu-id="75ff9-169">Używa modyfikatora `readonly`, aby wskazać, że obiekty wywołujące nie mogą modyfikować pochodzenia:</span><span class="sxs-lookup"><span data-stu-id="75ff9-169">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
<span data-ttu-id="75ff9-170">Zwrócony typ nie musi być `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="75ff9-170">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="75ff9-171">Wszystkie typy, które mogą być zwracane przez `ref` mogą być zwracane przez `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="75ff9-171">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="75ff9-172">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="75ff9-172">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="75ff9-173">Możesz również zobaczyć propozycje specyfikacji języka:</span><span class="sxs-lookup"><span data-stu-id="75ff9-173">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="75ff9-174">Typ ref i tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="75ff9-174">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="75ff9-175">elementy członkowskie struktury tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="75ff9-175">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="75ff9-176">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75ff9-176">See also</span></span>

- [<span data-ttu-id="75ff9-177">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="75ff9-177">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="75ff9-178">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="75ff9-178">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="75ff9-179">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="75ff9-179">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="75ff9-180">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="75ff9-180">Modifiers</span></span>](index.md)
- [<span data-ttu-id="75ff9-181">const</span><span class="sxs-lookup"><span data-stu-id="75ff9-181">const</span></span>](const.md)
- [<span data-ttu-id="75ff9-182">Pola</span><span class="sxs-lookup"><span data-stu-id="75ff9-182">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
