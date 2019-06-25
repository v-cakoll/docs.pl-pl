---
title: ReadOnly — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 4a51bb0e854de127c632c28f613a7602bf09f432
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348010"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="10b16-102">readonly (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="10b16-102">readonly (C# Reference)</span></span>

<span data-ttu-id="10b16-103">`readonly` — Słowo kluczowe jest modyfikator, który może być używana w kontekstach trzy:</span><span class="sxs-lookup"><span data-stu-id="10b16-103">The `readonly` keyword is a modifier that can be used in three contexts:</span></span>

- <span data-ttu-id="10b16-104">W [pola deklaracji](#readonly-field-example), `readonly` wskazuje przypisania do pola mogą występować wyłącznie jako część deklaracji lub za pomocą konstruktora w tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="10b16-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="10b16-105">Pola tylko do odczytu mogą zostać przypisane i ponownie przypisać wiele razy w ramach deklarację pola i konstruktora.</span><span class="sxs-lookup"><span data-stu-id="10b16-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span> 
  
  <span data-ttu-id="10b16-106">Element `readonly` nie można przypisać pola, po zakończeniu konstruktora.</span><span class="sxs-lookup"><span data-stu-id="10b16-106">A `readonly` field cannot be assigned after the constructor exits.</span></span> <span data-ttu-id="10b16-107">Która ma inny wpływ dla typów wartości i typy referencyjne:</span><span class="sxs-lookup"><span data-stu-id="10b16-107">That has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="10b16-108">Ponieważ typy wartości zawierają bezpośrednio swoje dane, pole to `readonly` typ wartości jest niezmienny.</span><span class="sxs-lookup"><span data-stu-id="10b16-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span> 
  - <span data-ttu-id="10b16-109">Ponieważ typy odwołań zawierają odwołania do swoich danych, pola to `readonly` typu odwołania zawsze musi odwoływać się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="10b16-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="10b16-110">Ten obiekt jest niezmienny.</span><span class="sxs-lookup"><span data-stu-id="10b16-110">That object is not immutable.</span></span> <span data-ttu-id="10b16-111">`readonly` Modyfikator zapobiega zastępowane przez inne wystąpienie typu odwołania pola.</span><span class="sxs-lookup"><span data-stu-id="10b16-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="10b16-112">Jednak modyfikator nie uniemożliwia dane wystąpienia pola modyfikowana za pomocą pola tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="10b16-112">However, the modifier does not prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="10b16-113">Typ widoczny na zewnątrz zawiera widoczne na zewnątrz pole tylko do odczytu, która jest typu referencji zmiennej może być luki w zabezpieczeniach i mogą wyzwalać ostrzeżenie [CA2104](/visualstudio/code-quality/ca2104-do-not-declare-read-only-mutable-reference-types) : "Nie deklaruj odczytu modyfikowalnych typów referencyjnych tylko."</span><span class="sxs-lookup"><span data-stu-id="10b16-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104-do-not-declare-read-only-mutable-reference-types) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="10b16-114">W [ `readonly struct` definicji](#readonly-struct-example), `readonly` wskazuje, że `struct` można modyfikować.</span><span class="sxs-lookup"><span data-stu-id="10b16-114">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="10b16-115">W [ `ref readonly` zwrotu metody](#ref-readonly-return-example), `readonly` modyfikator wskazuje, że metoda zwraca odwołanie i zapisy są niedozwolone do tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="10b16-115">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes are not allowed to that reference.</span></span>

<span data-ttu-id="10b16-116">Końcowe dwa konteksty zostały dodane w języku C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="10b16-116">The final two contexts were added in C# 7.2.</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="10b16-117">Przykład pola tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="10b16-117">Readonly field example</span></span>

<span data-ttu-id="10b16-118">W tym przykładzie wartość pola `year` nie można zmienić w metodzie `ChangeYear`, nawet jeśli jest do niej przypisana wartość w konstruktorze klasy:</span><span class="sxs-lookup"><span data-stu-id="10b16-118">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="10b16-119">Można przypisać wartości do `readonly` tylko w następujących kontekstów się:</span><span class="sxs-lookup"><span data-stu-id="10b16-119">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="10b16-120">Gdy zmienna jest inicjowana w deklaracji, na przykład:</span><span class="sxs-lookup"><span data-stu-id="10b16-120">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="10b16-121">W konstruktorze wystąpienia klasy, który zawiera deklarację pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="10b16-121">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="10b16-122">W konstruktorze statycznym klasy, który zawiera deklarację pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="10b16-122">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="10b16-123">Tych kontekstach Konstruktor są również tylko kontekstów, w których jest on prawidłowy do przekazania `readonly` pola jako [się](out-parameter-modifier.md) lub [ref](ref.md) parametru.</span><span class="sxs-lookup"><span data-stu-id="10b16-123">These constructor contexts are also the only contexts in which it is valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="10b16-124">`readonly` — Słowo kluczowe różni się od [const](const.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="10b16-124">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="10b16-125">A `const` pola mogą być inicjowane tylko na deklarację pola.</span><span class="sxs-lookup"><span data-stu-id="10b16-125">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="10b16-126">A `readonly` pola można przypisać wiele razy w deklarację pola i dowolny Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="10b16-126">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="10b16-127">W związku z tym `readonly` pola mogą mieć różne wartości w zależności od używanego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="10b16-127">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="10b16-128">Ponadto, podczas gdy `const` pole jest stałą czasu kompilacji `readonly` pole może być używane dla stałych środowiska uruchomieniowego, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="10b16-128">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="10b16-129">W poprzednim przykładzie, jeśli korzystasz z instrukcji, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="10b16-129">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="10b16-130">zostanie wyświetlony komunikat o błędzie kompilatora:</span><span class="sxs-lookup"><span data-stu-id="10b16-130">you will get the compiler error message:</span></span>

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a><span data-ttu-id="10b16-131">Przykład struktury tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="10b16-131">Readonly struct example</span></span>

<span data-ttu-id="10b16-132">`readonly` Modyfikator na `struct` definicji oświadcza, że struktura **niezmienne**.</span><span class="sxs-lookup"><span data-stu-id="10b16-132">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="10b16-133">Wszystkie pola wystąpienia `struct` muszą być oznaczone jako `readonly`, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="10b16-133">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

<span data-ttu-id="10b16-134">W poprzednim przykładzie użyto [tylko do odczytu właściwości automatyczne](../../properties.md#read-only) można zadeklarować magazynu.</span><span class="sxs-lookup"><span data-stu-id="10b16-134">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="10b16-135">Która instruuje kompilator, aby utworzyć `readonly` kopii pola dla tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="10b16-135">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="10b16-136">Można również zadeklarować `readonly` pól bezpośrednio:</span><span class="sxs-lookup"><span data-stu-id="10b16-136">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="10b16-137">Dodawanie pola niezaznaczonych `readonly` generuje błąd kompilatora `CS8340`: "Wystąpienia pól struktur tylko do odczytu muszą być tylko do odczytu."</span><span class="sxs-lookup"><span data-stu-id="10b16-137">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="10b16-138">Przykład zwracane tylko do odczytu REF</span><span class="sxs-lookup"><span data-stu-id="10b16-138">Ref readonly return example</span></span>

<span data-ttu-id="10b16-139">`readonly` Modyfikator na `ref return` wskazuje, że zwracane odwołanie nie może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="10b16-139">The `readonly` modifier on a `ref return` indicates that the returned reference cannot be modified.</span></span> <span data-ttu-id="10b16-140">Poniższy przykład zwraca odwołanie do źródła.</span><span class="sxs-lookup"><span data-stu-id="10b16-140">The following example returns a reference to the origin.</span></span> <span data-ttu-id="10b16-141">Używa ona `readonly` modyfikator, aby wskazać, że obiekty wywołujące nie można zmodyfikować punkt początkowy:</span><span class="sxs-lookup"><span data-stu-id="10b16-141">It uses the `readonly` modifier to indicate that callers cannot modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
<span data-ttu-id="10b16-142">Typ zwracany nie musi być `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="10b16-142">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="10b16-143">Dowolny typ, który może zostać zwrócony przez `ref` mogą być zwrócone przez `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="10b16-143">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="10b16-144">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="10b16-144">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="10b16-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10b16-145">See also</span></span>

- [<span data-ttu-id="10b16-146">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="10b16-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="10b16-147">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="10b16-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="10b16-148">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="10b16-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="10b16-149">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="10b16-149">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="10b16-150">const</span><span class="sxs-lookup"><span data-stu-id="10b16-150">const</span></span>](const.md)
- [<span data-ttu-id="10b16-151">Pola</span><span class="sxs-lookup"><span data-stu-id="10b16-151">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
