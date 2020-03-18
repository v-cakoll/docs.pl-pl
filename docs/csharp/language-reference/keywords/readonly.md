---
title: słowo kluczowe tylko do odczytu — odwołanie do języka C#
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 165b6287e1610e013b289601e1535a08fdd3b5c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399358"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="1d245-102">readonly (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1d245-102">readonly (C# Reference)</span></span>

<span data-ttu-id="1d245-103">Słowo `readonly` kluczowe jest modyfikatorem, który może być używany w czterech kontekstach:</span><span class="sxs-lookup"><span data-stu-id="1d245-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="1d245-104">W [deklaracji](#readonly-field-example)pola `readonly` wskazuje, że przypisanie do pola może wystąpić tylko jako część deklaracji lub w konstruktorze w tej samej klasie.</span><span class="sxs-lookup"><span data-stu-id="1d245-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="1d245-105">Pole tylko do odczytu można przypisać i przypisać je wielokrotnie w ramach deklaracji pola i konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1d245-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="1d245-106">Nie `readonly` można przypisać pola po wyjściu konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1d245-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="1d245-107">Ta reguła ma różne implikacje dla typów wartości i typów odwołań:</span><span class="sxs-lookup"><span data-stu-id="1d245-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="1d245-108">Ponieważ typy wartości bezpośrednio zawierają ich dane, pole, które jest typem `readonly` wartości jest niezmienne.</span><span class="sxs-lookup"><span data-stu-id="1d245-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="1d245-109">Ponieważ typy odwołań zawierają odwołanie do ich `readonly` danych, pole, które jest typem odwołania, musi zawsze odwoływać się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1d245-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="1d245-110">Ten obiekt nie jest niezmienny.</span><span class="sxs-lookup"><span data-stu-id="1d245-110">That object isn't immutable.</span></span> <span data-ttu-id="1d245-111">Modyfikator `readonly` zapobiega zastępowaniu pola innym wystąpieniem typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="1d245-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="1d245-112">Jednak modyfikator nie uniemożliwia modyfikowania danych wystąpienia pola za pomocą pola tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="1d245-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="1d245-113">Typ widoczny zewnętrznie, który zawiera widoczne z zewnątrz pole tylko do odczytu, które jest typu odwołanie mofntabela może być luka w zabezpieczeniach i może wyzwolić ostrzeżenie [CA2104:](/visualstudio/code-quality/ca2104) "Nie deklarują tylko do odczytu typy odwołań tylko do odczytu."</span><span class="sxs-lookup"><span data-stu-id="1d245-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="1d245-114">W [ `readonly struct` definicji](#readonly-struct-example) `readonly` wskazuje, `struct` że jest niezmienny.</span><span class="sxs-lookup"><span data-stu-id="1d245-114">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="1d245-115">W [ `readonly` definicji elementu członkowskiego](#readonly-member-examples)wskazuje, `struct` `readonly` że element członkowski nie mutuje stanu wewnętrznego struktury.</span><span class="sxs-lookup"><span data-stu-id="1d245-115">In a [`readonly` member definition](#readonly-member-examples), `readonly` indicates that a member of a `struct` doesn't mutate the struct's internal state.</span></span>
- <span data-ttu-id="1d245-116">W [ `ref readonly` zwracanej metodzie](#ref-readonly-return-example) `readonly` modyfikator wskazuje, że metoda zwraca odwołanie i zapisuje nie są dozwolone do tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="1d245-116">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="1d245-117">I `readonly struct` `ref readonly` konteksty zostały dodane w języku C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="1d245-117">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="1d245-118">`readonly`elementy składek zostały dodane w języku C# 8.0</span><span class="sxs-lookup"><span data-stu-id="1d245-118">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="1d245-119">Przykład pola tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1d245-119">Readonly field example</span></span>

<span data-ttu-id="1d245-120">W tym przykładzie wartość pola `year` nie można zmienić w `ChangeYear`metodzie, mimo że jest przypisana wartość w konstruktorze klasy:</span><span class="sxs-lookup"><span data-stu-id="1d245-120">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="1d245-121">Wartość można przypisać do `readonly` pola tylko w następujących kontekstach:</span><span class="sxs-lookup"><span data-stu-id="1d245-121">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="1d245-122">Gdy zmienna jest inicjowana w deklaracji, na przykład:</span><span class="sxs-lookup"><span data-stu-id="1d245-122">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="1d245-123">W konstruktora wystąpienia klasy, która zawiera deklarację pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1d245-123">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="1d245-124">W konstruktorze statycznym klasy, która zawiera deklarację pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="1d245-124">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="1d245-125">Te konstruktory konteksty są również tylko konteksty, `readonly` w których jest prawidłowy przekazać pole jako [out](out-parameter-modifier.md) lub [ref](ref.md) parametru.</span><span class="sxs-lookup"><span data-stu-id="1d245-125">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="1d245-126">Słowo `readonly` kluczowe różni się od słowa kluczowego [const.](const.md)</span><span class="sxs-lookup"><span data-stu-id="1d245-126">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="1d245-127">Pole `const` można zainicjować tylko w deklaracji pola.</span><span class="sxs-lookup"><span data-stu-id="1d245-127">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="1d245-128">Pole `readonly` można przypisać wiele razy w deklaracji pola i w dowolnym konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="1d245-128">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="1d245-129">W `readonly` związku z tym pola mogą mieć różne wartości w zależności od konstruktora używane.</span><span class="sxs-lookup"><span data-stu-id="1d245-129">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="1d245-130">Ponadto, gdy `const` pole jest stałą w `readonly` czasie kompilacji, pole może służyć do stałych w czasie wykonywania, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1d245-130">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="1d245-131">W poprzednim przykładzie, jeśli używasz instrukcji, takich jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1d245-131">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="1d245-132">pojawi się komunikat o błędzie kompilatora:</span><span class="sxs-lookup"><span data-stu-id="1d245-132">you'll get the compiler error message:</span></span>

<span data-ttu-id="1d245-133">**Nie można przypisać pola tylko do odczytu (z wyjątkiem konstruktora lub inicjatora zmiennego)**</span><span class="sxs-lookup"><span data-stu-id="1d245-133">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="readonly-struct-example"></a><span data-ttu-id="1d245-134">Przykład struktury tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1d245-134">Readonly struct example</span></span>

<span data-ttu-id="1d245-135">Modyfikator `readonly` `struct` definicji deklaruje, że struktura jest **niezmienna**.</span><span class="sxs-lookup"><span data-stu-id="1d245-135">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="1d245-136">Każde pole wystąpienia `struct` musi `readonly`być oznaczone, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1d245-136">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

<span data-ttu-id="1d245-137">W poprzednim przykładzie używa [właściwości auto tylko do odczytu,](../../properties.md#read-only) aby zadeklarować jego magazyn.</span><span class="sxs-lookup"><span data-stu-id="1d245-137">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="1d245-138">Który instruuje kompilator, aby utworzyć `readonly` pola zapasowe dla tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="1d245-138">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="1d245-139">Można również `readonly` zadeklarować pola bezpośrednio:</span><span class="sxs-lookup"><span data-stu-id="1d245-139">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="1d245-140">Dodanie pola nie `readonly` oznaczonego generuje `CS8340`błąd kompilatora: "Pola wystąpienia struktur tylko do odczytu muszą być tylko do odczytu".</span><span class="sxs-lookup"><span data-stu-id="1d245-140">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="readonly-member-examples"></a><span data-ttu-id="1d245-141">Przykłady członków tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1d245-141">Readonly member examples</span></span>

<span data-ttu-id="1d245-142">Innym razem, można utworzyć strukturę, która obsługuje mutacji.</span><span class="sxs-lookup"><span data-stu-id="1d245-142">Other times, you may create a struct that supports mutation.</span></span> <span data-ttu-id="1d245-143">W takich przypadkach kilka elementów członkowskich wystąpienia prawdopodobnie nie zmodyfikuje stan wewnętrzny struktury.</span><span class="sxs-lookup"><span data-stu-id="1d245-143">In those cases, several of the instance members likely won't modify the internal state of the struct.</span></span> <span data-ttu-id="1d245-144">Można zadeklarować tych elementów `readonly` członkowskich wystąpienia z modyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="1d245-144">You can declare those instance members with the `readonly` modifier.</span></span> <span data-ttu-id="1d245-145">Kompilator wymusza intencji.</span><span class="sxs-lookup"><span data-stu-id="1d245-145">The compiler enforces your intent.</span></span> <span data-ttu-id="1d245-146">Jeśli ten element członkowski modyfikuje stan bezpośrednio lub uzyskuje dostęp do elementu członkowskiego, który nie jest również zadeklarowany za pomocą `readonly` modyfikatora, wynik jest błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1d245-146">If that member modifies state directly or accesses a member that isn't also declared with the `readonly` modifier, the result is a compile-time error.</span></span> <span data-ttu-id="1d245-147">Modyfikator `readonly` jest `struct` prawidłowy `class` `interface` na członków, nie lub deklaracji elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="1d245-147">The `readonly` modifier is valid on `struct` members, not `class` or `interface` member declarations.</span></span>

<span data-ttu-id="1d245-148">Zyskujesz dwie zalety, `readonly` stosując `struct` modyfikator do odpowiednich metod.</span><span class="sxs-lookup"><span data-stu-id="1d245-148">You gain two advantages by applying the `readonly` modifier to applicable `struct` methods.</span></span> <span data-ttu-id="1d245-149">Co najważniejsze kompilator wymusza intencji.</span><span class="sxs-lookup"><span data-stu-id="1d245-149">Most importantly, the compiler enforces your intent.</span></span> <span data-ttu-id="1d245-150">Kod, który modyfikuje stan nie `readonly` jest prawidłowy w metodzie.</span><span class="sxs-lookup"><span data-stu-id="1d245-150">Code that modifies state isn't valid in a `readonly` method.</span></span> <span data-ttu-id="1d245-151">Kompilator może również `readonly` korzystać z modyfikatora, aby włączyć optymalizacje wydajności.</span><span class="sxs-lookup"><span data-stu-id="1d245-151">The compiler may also make use of the `readonly` modifier to enable performance optimizations.</span></span> <span data-ttu-id="1d245-152">Gdy `struct` duże typy `in` są przekazywane przez odwołanie, kompilator musi wygenerować kopię obronną, jeśli stan struktury może zostać zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="1d245-152">When large `struct` types are passed by `in` reference, the compiler must generate a defensive copy if the state of the struct might be modified.</span></span> <span data-ttu-id="1d245-153">Jeśli `readonly` dostęp są tylko elementy członkowskie, kompilator nie może utworzyć kopię obronną.</span><span class="sxs-lookup"><span data-stu-id="1d245-153">If only `readonly` members are accessed, the compiler may not create the defensive copy.</span></span>

<span data-ttu-id="1d245-154">Modyfikator `readonly` jest prawidłowy `struct`dla większości elementów członkowskich , w <xref:System.Object?displayProperty=nameWithType>tym metody, które zastępują metody zadeklarowane w .</span><span class="sxs-lookup"><span data-stu-id="1d245-154">The `readonly` modifier is valid on most members of a `struct`, including methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1d245-155">Istnieją pewne ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="1d245-155">There are some restrictions:</span></span>

- <span data-ttu-id="1d245-156">Nie można zadeklarować `readonly` metod ani właściwości statycznych.</span><span class="sxs-lookup"><span data-stu-id="1d245-156">You can't declare `readonly` static methods or properties.</span></span>
- <span data-ttu-id="1d245-157">Nie można zadeklarować `readonly` konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="1d245-157">You can't declare `readonly` constructors.</span></span>

<span data-ttu-id="1d245-158">`readonly` Modyfikator można dodać do deklaracji właściwości lub indeksatora:</span><span class="sxs-lookup"><span data-stu-id="1d245-158">You can add the `readonly` modifier to a property or indexer declaration:</span></span>

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

<span data-ttu-id="1d245-159">Można również dodać `readonly` modyfikator do poszczególnych `get` lub `set` akcesorów właściwości lub indeksatora:</span><span class="sxs-lookup"><span data-stu-id="1d245-159">You may also add the `readonly` modifier to individual `get` or `set` accessors of a property or indexer:</span></span>

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

<span data-ttu-id="1d245-160">Nie można dodać `readonly` modyfikatora do właściwości i jeden lub więcej akcesorów tej samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="1d245-160">You may not add the `readonly` modifier to both a property and one or more of that same property's accessors.</span></span> <span data-ttu-id="1d245-161">To samo ograniczenie dotyczy indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="1d245-161">That same restriction applies to indexers.</span></span>

<span data-ttu-id="1d245-162">Kompilator niejawnie `readonly` stosuje modyfikator do właściwości implementowane automatycznie, gdzie kompilator zaimplementowany kod nie modyfikuje stan.</span><span class="sxs-lookup"><span data-stu-id="1d245-162">The compiler implicitly applies the `readonly` modifier to auto-implemented properties where the compiler implemented code doesn't modify state.</span></span> <span data-ttu-id="1d245-163">Jest to równoważne z następującymi deklaracjami:</span><span class="sxs-lookup"><span data-stu-id="1d245-163">It's equivalent to the following declarations:</span></span>

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
```

<span data-ttu-id="1d245-164">Możesz dodać `readonly` modyfikator w tych lokalizacjach, ale nie będzie miał znaczącego wpływu.</span><span class="sxs-lookup"><span data-stu-id="1d245-164">You may add the `readonly` modifier in those locations, but it will have no meaningful effect.</span></span> <span data-ttu-id="1d245-165">`readonly` Modyfikator nie może być dodawany do automatycznie implementowane go właściwości ustawiające właściwości lub do odczytu/zapisu właściwości autoimplementowane.</span><span class="sxs-lookup"><span data-stu-id="1d245-165">You may not add the `readonly` modifier to an auto-implemented property setter, or to a read/write auto-implemented property.</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="1d245-166">Przykład zwrotu tylko do odczytu ref</span><span class="sxs-lookup"><span data-stu-id="1d245-166">Ref readonly return example</span></span>

<span data-ttu-id="1d245-167">Modyfikator `readonly` `ref return` na wskazuje, że zwrócone odwołanie nie można modyfikować.</span><span class="sxs-lookup"><span data-stu-id="1d245-167">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="1d245-168">Poniższy przykład zwraca odwołanie do początku.</span><span class="sxs-lookup"><span data-stu-id="1d245-168">The following example returns a reference to the origin.</span></span> <span data-ttu-id="1d245-169">Używa modyfikatora, `readonly` aby wskazać, że obiekty wywołujące nie można modyfikować pochodzenia:</span><span class="sxs-lookup"><span data-stu-id="1d245-169">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
<span data-ttu-id="1d245-170">Zwracany typ nie musi być `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="1d245-170">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="1d245-171">Każdy typ, który może `ref` zostać zwrócony `ref readonly`przez mogą być zwracane przez .</span><span class="sxs-lookup"><span data-stu-id="1d245-171">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1d245-172">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1d245-172">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="1d245-173">Możesz również zobaczyć propozycje specyfikacji języka:</span><span class="sxs-lookup"><span data-stu-id="1d245-173">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="1d245-174">readonly ref i readonly struct</span><span class="sxs-lookup"><span data-stu-id="1d245-174">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="1d245-175">tylko do odczytu elementy składowe</span><span class="sxs-lookup"><span data-stu-id="1d245-175">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="1d245-176">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d245-176">See also</span></span>

- [<span data-ttu-id="1d245-177">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="1d245-177">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1d245-178">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="1d245-178">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1d245-179">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="1d245-179">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1d245-180">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="1d245-180">Modifiers</span></span>](index.md)
- [<span data-ttu-id="1d245-181">const</span><span class="sxs-lookup"><span data-stu-id="1d245-181">const</span></span>](const.md)
- [<span data-ttu-id="1d245-182">Pola</span><span class="sxs-lookup"><span data-stu-id="1d245-182">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
