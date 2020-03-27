---
title: readonly keyword - C# Reference
ms.date: 03/26/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 344d5e54fcd500e283c52fa7953c6366823f13f0
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345149"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="fd29d-102">readonly (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="fd29d-102">readonly (C# Reference)</span></span>

<span data-ttu-id="fd29d-103">Słowo `readonly` kluczowe jest modyfikatorem, który może być używany w czterech kontekstach:</span><span class="sxs-lookup"><span data-stu-id="fd29d-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="fd29d-104">W [deklaracji](#readonly-field-example)pola `readonly` wskazuje, że przypisanie do pola może nastąpić tylko jako część deklaracji lub w konstruktorze w tej samej klasie.</span><span class="sxs-lookup"><span data-stu-id="fd29d-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="fd29d-105">Pole tylko do odczytu można przypisać i przypisać ponownie wiele razy w deklaracji pola i konstruktora.</span><span class="sxs-lookup"><span data-stu-id="fd29d-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="fd29d-106">Nie `readonly` można przypisać pola po zamknięciu konstruktora.</span><span class="sxs-lookup"><span data-stu-id="fd29d-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="fd29d-107">Ta reguła ma różne implikacje dla typów wartości i typów odwołań:</span><span class="sxs-lookup"><span data-stu-id="fd29d-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="fd29d-108">Ponieważ typy wartości bezpośrednio zawierają ich dane, pole, które jest typem `readonly` wartości, jest niezmienne.</span><span class="sxs-lookup"><span data-stu-id="fd29d-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="fd29d-109">Ponieważ typy odwołań zawierają odwołanie do ich `readonly` danych, pole, które jest typem odwołania, musi zawsze odwoływać się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="fd29d-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="fd29d-110">Ten obiekt nie jest niezmienny.</span><span class="sxs-lookup"><span data-stu-id="fd29d-110">That object isn't immutable.</span></span> <span data-ttu-id="fd29d-111">Modyfikator `readonly` zapobiega zastępowaniu pola przez inne wystąpienie typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="fd29d-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="fd29d-112">Jednak modyfikator nie zapobiega modyfikowaniu danych wystąpienia pola za pomocą pola tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="fd29d-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="fd29d-113">Zewnętrznie widoczny typ, który zawiera zewnętrznie widoczne pole tylko do odczytu, które jest modyfikowalnym typem odwołania, może być luką w zabezpieczeniach i może wywołać ostrzeżenie [CA2104](/visualstudio/code-quality/ca2104) : "Nie zgłaszaj tylko do odczytu typów odwołań modyfikowalnych."</span><span class="sxs-lookup"><span data-stu-id="fd29d-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="fd29d-114">W `readonly struct` definicji `readonly` typu wskazuje, że typ struktury jest niezmienny.</span><span class="sxs-lookup"><span data-stu-id="fd29d-114">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="fd29d-115">Aby uzyskać więcej [ `readonly` ](../builtin-types/struct.md#readonly-struct) informacji, zobacz sekcję struktury [struktury struktury typów](../builtin-types/struct.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="fd29d-115">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="fd29d-116">W [ `readonly` definicji](#readonly-member-examples) `readonly` elementu członkowskiego wskazuje, `struct` że element członkowski a nie mutuje stan wewnętrzny struktury.</span><span class="sxs-lookup"><span data-stu-id="fd29d-116">In a [`readonly` member definition](#readonly-member-examples), `readonly` indicates that a member of a `struct` doesn't mutate the struct's internal state.</span></span>
- <span data-ttu-id="fd29d-117">W [ `ref readonly` powrocie](#ref-readonly-return-example)metody `readonly` modyfikator wskazuje, że metoda zwraca odwołanie i zapisy nie są dozwolone do tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="fd29d-117">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="fd29d-118">`readonly struct` Konteksty `ref readonly` i zostały dodane w języku C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="fd29d-118">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="fd29d-119">`readonly`elementy strukturyzowania zostały dodane w języku C# 8.0</span><span class="sxs-lookup"><span data-stu-id="fd29d-119">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="fd29d-120">Przykład pola tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fd29d-120">Readonly field example</span></span>

<span data-ttu-id="fd29d-121">W tym przykładzie nie `year` można zmienić wartości pola `ChangeYear`w metodzie, nawet jeśli jest przypisana wartość w konstruktorze klasy:</span><span class="sxs-lookup"><span data-stu-id="fd29d-121">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="fd29d-122">Wartość do `readonly` pola można przypisać tylko w następujących kontekstach:</span><span class="sxs-lookup"><span data-stu-id="fd29d-122">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="fd29d-123">Gdy zmienna jest inicjowana w deklaracji, na przykład:</span><span class="sxs-lookup"><span data-stu-id="fd29d-123">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="fd29d-124">W konstruktorze instancji klasy, która zawiera deklarację pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fd29d-124">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="fd29d-125">W statycznym konstruktorze klasy, która zawiera deklarację pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="fd29d-125">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="fd29d-126">Te konteksty konstruktora są również tylko konteksty, `readonly` w których jest prawidłowy, aby przekazać pole jako [out](out-parameter-modifier.md) lub [ref](ref.md) parametru.</span><span class="sxs-lookup"><span data-stu-id="fd29d-126">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="fd29d-127">Słowo `readonly` kluczowe różni się od słowa kluczowego [const.](const.md)</span><span class="sxs-lookup"><span data-stu-id="fd29d-127">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="fd29d-128">Pole `const` można zainicjować tylko w deklaracji pola.</span><span class="sxs-lookup"><span data-stu-id="fd29d-128">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="fd29d-129">Pole `readonly` można przypisać wiele razy w deklaracji pola i w dowolnym konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="fd29d-129">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="fd29d-130">W związku `readonly` z tym pola mogą mieć różne wartości w zależności od używanego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="fd29d-130">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="fd29d-131">Ponadto, podczas `const` gdy pole jest stałą `readonly` w czasie kompilacji, pole może być używane dla stałych w czasie wykonywania, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fd29d-131">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="fd29d-132">W poprzednim przykładzie, jeśli używasz instrukcji, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fd29d-132">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="fd29d-133">zostanie wyświetlony komunikat o błędzie kompilatora:</span><span class="sxs-lookup"><span data-stu-id="fd29d-133">you'll get the compiler error message:</span></span>

<span data-ttu-id="fd29d-134">**Nie można przypisać pola tylko do odczytu (z wyjątkiem konstruktora lub inicjatora zmiennej)**</span><span class="sxs-lookup"><span data-stu-id="fd29d-134">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="readonly-member-examples"></a><span data-ttu-id="fd29d-135">Readonly przykłady członków</span><span class="sxs-lookup"><span data-stu-id="fd29d-135">Readonly member examples</span></span>

<span data-ttu-id="fd29d-136">Innym razem można utworzyć strukturę, która obsługuje mutację.</span><span class="sxs-lookup"><span data-stu-id="fd29d-136">Other times, you may create a struct that supports mutation.</span></span> <span data-ttu-id="fd29d-137">W takich przypadkach kilka członków wystąpienia prawdopodobnie nie będzie modyfikować stan wewnętrzny struktury.</span><span class="sxs-lookup"><span data-stu-id="fd29d-137">In those cases, several of the instance members likely won't modify the internal state of the struct.</span></span> <span data-ttu-id="fd29d-138">Można zadeklarować te elementy `readonly` członkowskie wystąpienia za pomocą modyfikatora.</span><span class="sxs-lookup"><span data-stu-id="fd29d-138">You can declare those instance members with the `readonly` modifier.</span></span> <span data-ttu-id="fd29d-139">Kompilator wymusza intencji.</span><span class="sxs-lookup"><span data-stu-id="fd29d-139">The compiler enforces your intent.</span></span> <span data-ttu-id="fd29d-140">Jeśli ten element członkowski modyfikuje stan bezpośrednio lub uzyskuje `readonly` dostęp do elementu członkowskiego, który nie jest również zadeklarowany za pomocą modyfikatora, wynikiem jest błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fd29d-140">If that member modifies state directly or accesses a member that isn't also declared with the `readonly` modifier, the result is a compile-time error.</span></span> <span data-ttu-id="fd29d-141">Modyfikator `readonly` jest `struct` prawidłowy `class` w `interface` deklaracjach elementów członkowskich, nie lub członkowskich.</span><span class="sxs-lookup"><span data-stu-id="fd29d-141">The `readonly` modifier is valid on `struct` members, not `class` or `interface` member declarations.</span></span>

<span data-ttu-id="fd29d-142">Zyskujesz dwie zalety, `readonly` stosując modyfikator do odpowiednich `struct` metod.</span><span class="sxs-lookup"><span data-stu-id="fd29d-142">You gain two advantages by applying the `readonly` modifier to applicable `struct` methods.</span></span> <span data-ttu-id="fd29d-143">Co najważniejsze kompilator wymusza intencji.</span><span class="sxs-lookup"><span data-stu-id="fd29d-143">Most importantly, the compiler enforces your intent.</span></span> <span data-ttu-id="fd29d-144">Kod, który modyfikuje stan `readonly` nie jest prawidłowy w metodzie.</span><span class="sxs-lookup"><span data-stu-id="fd29d-144">Code that modifies state isn't valid in a `readonly` method.</span></span> <span data-ttu-id="fd29d-145">Kompilator może również korzystać z modyfikatora, `readonly` aby włączyć optymalizacje wydajności.</span><span class="sxs-lookup"><span data-stu-id="fd29d-145">The compiler may also make use of the `readonly` modifier to enable performance optimizations.</span></span> <span data-ttu-id="fd29d-146">Gdy `struct` duże typy `in` są przekazywane przez odwołanie, kompilator musi wygenerować kopię obronną, jeśli stan struktury może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="fd29d-146">When large `struct` types are passed by `in` reference, the compiler must generate a defensive copy if the state of the struct might be modified.</span></span> <span data-ttu-id="fd29d-147">Jeśli `readonly` tylko elementy członkowskie są dostępne, kompilator nie może utworzyć kopii obronnej.</span><span class="sxs-lookup"><span data-stu-id="fd29d-147">If only `readonly` members are accessed, the compiler may not create the defensive copy.</span></span>

<span data-ttu-id="fd29d-148">Modyfikator `readonly` jest prawidłowy dla `struct`większości elementów członkowskich , <xref:System.Object?displayProperty=nameWithType>w tym metod, które zastępują metody zadeklarowane w .</span><span class="sxs-lookup"><span data-stu-id="fd29d-148">The `readonly` modifier is valid on most members of a `struct`, including methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fd29d-149">Istnieją pewne ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="fd29d-149">There are some restrictions:</span></span>

- <span data-ttu-id="fd29d-150">Nie można zadeklarować `readonly` metod statycznych lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="fd29d-150">You can't declare `readonly` static methods or properties.</span></span>
- <span data-ttu-id="fd29d-151">Nie można zadeklarować `readonly` konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="fd29d-151">You can't declare `readonly` constructors.</span></span>

<span data-ttu-id="fd29d-152">`readonly` Modyfikator można dodać do właściwości lub deklaracji indeksatora:</span><span class="sxs-lookup"><span data-stu-id="fd29d-152">You can add the `readonly` modifier to a property or indexer declaration:</span></span>

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

<span data-ttu-id="fd29d-153">Modyfikator można również dodać `get` `set` do poszczególnych lub akcesorów właściwości lub indeksatora: `readonly`</span><span class="sxs-lookup"><span data-stu-id="fd29d-153">You may also add the `readonly` modifier to individual `get` or `set` accessors of a property or indexer:</span></span>

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

<span data-ttu-id="fd29d-154">Nie można dodać `readonly` modyfikatora do właściwości i co najmniej jednego z akcesorów tej samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="fd29d-154">You may not add the `readonly` modifier to both a property and one or more of that same property's accessors.</span></span> <span data-ttu-id="fd29d-155">To samo ograniczenie dotyczy indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="fd29d-155">That same restriction applies to indexers.</span></span>

<span data-ttu-id="fd29d-156">Kompilator niejawnie `readonly` stosuje modyfikator do właściwości automatycznie implementowane, gdzie kompilator zaimplementowany kod nie modyfikuje stanu.</span><span class="sxs-lookup"><span data-stu-id="fd29d-156">The compiler implicitly applies the `readonly` modifier to auto-implemented properties where the compiler implemented code doesn't modify state.</span></span> <span data-ttu-id="fd29d-157">Jest to równoważne z następującymi deklaracjami:</span><span class="sxs-lookup"><span data-stu-id="fd29d-157">It's equivalent to the following declarations:</span></span>

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
```

<span data-ttu-id="fd29d-158">`readonly` Modyfikator można dodać w tych lokalizacjach, ale nie będzie miał znaczącego wpływu.</span><span class="sxs-lookup"><span data-stu-id="fd29d-158">You may add the `readonly` modifier in those locations, but it will have no meaningful effect.</span></span> <span data-ttu-id="fd29d-159">`readonly` Modyfikator nie może być dodawany do zestawu właściwości zaimplementowanych automatycznie ani do właściwości automatycznie implementowanych odczytu/zapisu.</span><span class="sxs-lookup"><span data-stu-id="fd29d-159">You may not add the `readonly` modifier to an auto-implemented property setter, or to a read/write auto-implemented property.</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="fd29d-160">Ref readonly return example (Przykład zwrotu tylko w celu odesłania)</span><span class="sxs-lookup"><span data-stu-id="fd29d-160">Ref readonly return example</span></span>

<span data-ttu-id="fd29d-161">Modyfikator `readonly` na `ref return` wskazuje, że zwracanego odwołania nie można zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="fd29d-161">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="fd29d-162">Poniższy przykład zwraca odwołanie do pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="fd29d-162">The following example returns a reference to the origin.</span></span> <span data-ttu-id="fd29d-163">Używa modyfikatora, `readonly` aby wskazać, że wywołujący nie można zmodyfikować pochodzenia:</span><span class="sxs-lookup"><span data-stu-id="fd29d-163">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="fd29d-164">Zwracany typ nie musi być `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="fd29d-164">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="fd29d-165">Każdy typ, który `ref` może zostać `ref readonly`zwrócony przez może być zwrócony przez .</span><span class="sxs-lookup"><span data-stu-id="fd29d-165">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fd29d-166">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="fd29d-166">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="fd29d-167">Można również zobaczyć propozycje specyfikacji języka:</span><span class="sxs-lookup"><span data-stu-id="fd29d-167">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="fd29d-168">readonly ref i readonly struct</span><span class="sxs-lookup"><span data-stu-id="fd29d-168">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="fd29d-169">readonly strumyk elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="fd29d-169">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="fd29d-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd29d-170">See also</span></span>

- [<span data-ttu-id="fd29d-171">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="fd29d-171">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fd29d-172">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="fd29d-172">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fd29d-173">C# Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="fd29d-173">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="fd29d-174">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="fd29d-174">Modifiers</span></span>](index.md)
- [<span data-ttu-id="fd29d-175">const</span><span class="sxs-lookup"><span data-stu-id="fd29d-175">const</span></span>](const.md)
- [<span data-ttu-id="fd29d-176">Pola</span><span class="sxs-lookup"><span data-stu-id="fd29d-176">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
