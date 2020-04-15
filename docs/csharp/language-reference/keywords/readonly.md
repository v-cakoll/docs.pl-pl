---
title: readonly keyword - C# Reference
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 03b0aa63eda3e7a9d8745baaa33479fd5e85b01b
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389054"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="72bc3-102">readonly (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="72bc3-102">readonly (C# Reference)</span></span>

<span data-ttu-id="72bc3-103">Słowo `readonly` kluczowe jest modyfikatorem, który może być używany w czterech kontekstach:</span><span class="sxs-lookup"><span data-stu-id="72bc3-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="72bc3-104">W [deklaracji](#readonly-field-example)pola `readonly` wskazuje, że przypisanie do pola może nastąpić tylko jako część deklaracji lub w konstruktorze w tej samej klasie.</span><span class="sxs-lookup"><span data-stu-id="72bc3-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="72bc3-105">Pole tylko do odczytu można przypisać i przypisać ponownie wiele razy w deklaracji pola i konstruktora.</span><span class="sxs-lookup"><span data-stu-id="72bc3-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="72bc3-106">Nie `readonly` można przypisać pola po zamknięciu konstruktora.</span><span class="sxs-lookup"><span data-stu-id="72bc3-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="72bc3-107">Ta reguła ma różne implikacje dla typów wartości i typów odwołań:</span><span class="sxs-lookup"><span data-stu-id="72bc3-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="72bc3-108">Ponieważ typy wartości bezpośrednio zawierają ich dane, pole, które jest typem `readonly` wartości, jest niezmienne.</span><span class="sxs-lookup"><span data-stu-id="72bc3-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="72bc3-109">Ponieważ typy odwołań zawierają odwołanie do ich `readonly` danych, pole, które jest typem odwołania, musi zawsze odwoływać się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="72bc3-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="72bc3-110">Ten obiekt nie jest niezmienny.</span><span class="sxs-lookup"><span data-stu-id="72bc3-110">That object isn't immutable.</span></span> <span data-ttu-id="72bc3-111">Modyfikator `readonly` zapobiega zastępowaniu pola przez inne wystąpienie typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="72bc3-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="72bc3-112">Jednak modyfikator nie zapobiega modyfikowaniu danych wystąpienia pola za pomocą pola tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="72bc3-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="72bc3-113">Zewnętrznie widoczny typ, który zawiera zewnętrznie widoczne pole tylko do odczytu, które jest modyfikowalnym typem odwołania, może być luką w zabezpieczeniach i może wywołać ostrzeżenie [CA2104](/visualstudio/code-quality/ca2104) : "Nie zgłaszaj tylko do odczytu typów odwołań modyfikowalnych."</span><span class="sxs-lookup"><span data-stu-id="72bc3-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="72bc3-114">W `readonly struct` definicji `readonly` typu wskazuje, że typ struktury jest niezmienny.</span><span class="sxs-lookup"><span data-stu-id="72bc3-114">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="72bc3-115">Aby uzyskać więcej [ `readonly` ](../builtin-types/struct.md#readonly-struct) informacji, zobacz sekcję struktury [struktury struktury typów](../builtin-types/struct.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="72bc3-115">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="72bc3-116">W deklaracji elementu członkowskiego wystąpienia `readonly` w typie struktury wskazuje, że element członkowski wystąpienia nie modyfikuje stanu struktury.</span><span class="sxs-lookup"><span data-stu-id="72bc3-116">In an instance member declaration within a structure type, `readonly` indicates that an instance member doesn't modify the state of the structure.</span></span> <span data-ttu-id="72bc3-117">Aby uzyskać więcej [ `readonly` ](../builtin-types/struct.md#readonly-instance-members) informacji, zobacz sekcję członków wystąpienia w artykule [Typy struktury.](../builtin-types/struct.md)</span><span class="sxs-lookup"><span data-stu-id="72bc3-117">For more information, see the [`readonly` instance members](../builtin-types/struct.md#readonly-instance-members) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="72bc3-118">W [ `ref readonly` powrocie](#ref-readonly-return-example)metody `readonly` modyfikator wskazuje, że metoda zwraca odwołanie i zapisy nie są dozwolone do tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="72bc3-118">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="72bc3-119">`readonly struct` Konteksty `ref readonly` i zostały dodane w języku C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="72bc3-119">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="72bc3-120">`readonly`elementy strukturyzowania zostały dodane w języku C# 8.0</span><span class="sxs-lookup"><span data-stu-id="72bc3-120">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="72bc3-121">Przykład pola tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="72bc3-121">Readonly field example</span></span>

<span data-ttu-id="72bc3-122">W tym przykładzie nie `year` można zmienić wartości pola `ChangeYear`w metodzie, nawet jeśli jest przypisana wartość w konstruktorze klasy:</span><span class="sxs-lookup"><span data-stu-id="72bc3-122">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="72bc3-123">Wartość do `readonly` pola można przypisać tylko w następujących kontekstach:</span><span class="sxs-lookup"><span data-stu-id="72bc3-123">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="72bc3-124">Gdy zmienna jest inicjowana w deklaracji, na przykład:</span><span class="sxs-lookup"><span data-stu-id="72bc3-124">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="72bc3-125">W konstruktorze instancji klasy, która zawiera deklarację pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="72bc3-125">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="72bc3-126">W statycznym konstruktorze klasy, która zawiera deklarację pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="72bc3-126">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="72bc3-127">Te konteksty konstruktora są również tylko konteksty, `readonly` w których jest prawidłowy, aby przekazać pole jako [out](out-parameter-modifier.md) lub [ref](ref.md) parametru.</span><span class="sxs-lookup"><span data-stu-id="72bc3-127">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="72bc3-128">Słowo `readonly` kluczowe różni się od słowa kluczowego [const.](const.md)</span><span class="sxs-lookup"><span data-stu-id="72bc3-128">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="72bc3-129">Pole `const` można zainicjować tylko w deklaracji pola.</span><span class="sxs-lookup"><span data-stu-id="72bc3-129">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="72bc3-130">Pole `readonly` można przypisać wiele razy w deklaracji pola i w dowolnym konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="72bc3-130">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="72bc3-131">W związku `readonly` z tym pola mogą mieć różne wartości w zależności od używanego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="72bc3-131">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="72bc3-132">Ponadto, podczas `const` gdy pole jest stałą `readonly` w czasie kompilacji, pole może być używane dla stałych w czasie wykonywania, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="72bc3-132">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="72bc3-133">W poprzednim przykładzie, jeśli używasz instrukcji, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="72bc3-133">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="72bc3-134">zostanie wyświetlony komunikat o błędzie kompilatora:</span><span class="sxs-lookup"><span data-stu-id="72bc3-134">you'll get the compiler error message:</span></span>

<span data-ttu-id="72bc3-135">**Nie można przypisać pola tylko do odczytu (z wyjątkiem konstruktora lub inicjatora zmiennej)**</span><span class="sxs-lookup"><span data-stu-id="72bc3-135">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="72bc3-136">Ref readonly return example (Przykład zwrotu tylko w celu odesłania)</span><span class="sxs-lookup"><span data-stu-id="72bc3-136">Ref readonly return example</span></span>

<span data-ttu-id="72bc3-137">Modyfikator `readonly` na `ref return` wskazuje, że zwracanego odwołania nie można zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="72bc3-137">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="72bc3-138">Poniższy przykład zwraca odwołanie do pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="72bc3-138">The following example returns a reference to the origin.</span></span> <span data-ttu-id="72bc3-139">Używa modyfikatora, `readonly` aby wskazać, że wywołujący nie można zmodyfikować pochodzenia:</span><span class="sxs-lookup"><span data-stu-id="72bc3-139">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly return example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="72bc3-140">Zwracany typ nie musi być `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="72bc3-140">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="72bc3-141">Każdy typ, który `ref` może zostać `ref readonly`zwrócony przez może być zwrócony przez .</span><span class="sxs-lookup"><span data-stu-id="72bc3-141">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="72bc3-142">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="72bc3-142">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="72bc3-143">Można również zobaczyć propozycje specyfikacji języka:</span><span class="sxs-lookup"><span data-stu-id="72bc3-143">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="72bc3-144">readonly ref i readonly struct</span><span class="sxs-lookup"><span data-stu-id="72bc3-144">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="72bc3-145">readonly strumyk elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="72bc3-145">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="72bc3-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72bc3-146">See also</span></span>

- [<span data-ttu-id="72bc3-147">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="72bc3-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="72bc3-148">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="72bc3-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="72bc3-149">C# Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="72bc3-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="72bc3-150">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="72bc3-150">Modifiers</span></span>](index.md)
- [<span data-ttu-id="72bc3-151">const</span><span class="sxs-lookup"><span data-stu-id="72bc3-151">const</span></span>](const.md)
- [<span data-ttu-id="72bc3-152">Pola</span><span class="sxs-lookup"><span data-stu-id="72bc3-152">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
