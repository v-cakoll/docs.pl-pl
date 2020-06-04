---
title: ReadOnly — słowo kluczowe — odwołanie w C#
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 66a096e8831f72a2216e8ba5dd9866046504624f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368624"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="89271-102">readonly (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="89271-102">readonly (C# Reference)</span></span>

<span data-ttu-id="89271-103">`readonly`Słowo kluczowe jest modyfikatorem, który może być używany w czterech kontekstach:</span><span class="sxs-lookup"><span data-stu-id="89271-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="89271-104">W [deklaracji pola](#readonly-field-example)wskazuje, `readonly` że przypisanie do pola może wystąpić tylko jako część deklaracji lub w konstruktorze w tej samej klasie.</span><span class="sxs-lookup"><span data-stu-id="89271-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="89271-105">Pole tylko do odczytu można przypisać i ponownie przypisać wiele razy w deklaracji pola i konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="89271-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="89271-106">`readonly`Nie można przypisać pola po zakończeniu konstruktora.</span><span class="sxs-lookup"><span data-stu-id="89271-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="89271-107">Ta reguła ma inne konsekwencje dla typów wartości i typów referencyjnych:</span><span class="sxs-lookup"><span data-stu-id="89271-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="89271-108">Ponieważ typy wartości bezpośrednio zawierają swoje dane, pole, które jest `readonly` typem wartości, jest niezmienne.</span><span class="sxs-lookup"><span data-stu-id="89271-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="89271-109">Ponieważ typy odwołań zawierają odwołanie do swoich danych, pole, które jest `readonly` typem referencyjnym, musi zawsze odwoływać się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="89271-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="89271-110">Ten obiekt nie jest niezmienny.</span><span class="sxs-lookup"><span data-stu-id="89271-110">That object isn't immutable.</span></span> <span data-ttu-id="89271-111">`readonly`Modyfikator zapobiega zastąpieniu pola przez inne wystąpienie typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="89271-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="89271-112">Jednak modyfikator nie zapobiega modyfikowaniu danych wystąpienia pola za pośrednictwem pola tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="89271-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="89271-113">Typ widoczny na zewnątrz, który zawiera zewnętrzny widoczny pole tylko do odczytu, które jest modyfikowalnym typem odwołania może być luką w zabezpieczeniach i może wyzwolić ostrzeżenie [CA2104](/visualstudio/code-quality/ca2104) : "nie deklaruj tylko odczytu modyfikowalnych typów odwołań".</span><span class="sxs-lookup"><span data-stu-id="89271-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="89271-114">W `readonly struct` definicji typu wskazuje, `readonly` że typ struktury jest niezmienny.</span><span class="sxs-lookup"><span data-stu-id="89271-114">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="89271-115">Aby uzyskać więcej informacji, zobacz sekcję [ `readonly` struktury](../builtin-types/struct.md#readonly-struct) w artykule [typy struktury](../builtin-types/struct.md) .</span><span class="sxs-lookup"><span data-stu-id="89271-115">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="89271-116">W deklaracji elementu członkowskiego wystąpienia w typie struktury `readonly` wskazuje, że element członkowski wystąpienia nie modyfikuje stanu struktury.</span><span class="sxs-lookup"><span data-stu-id="89271-116">In an instance member declaration within a structure type, `readonly` indicates that an instance member doesn't modify the state of the structure.</span></span> <span data-ttu-id="89271-117">Aby uzyskać więcej informacji, zobacz sekcję [ `readonly` elementy członkowskie wystąpienia](../builtin-types/struct.md#readonly-instance-members) w artykule [typy struktury](../builtin-types/struct.md) .</span><span class="sxs-lookup"><span data-stu-id="89271-117">For more information, see the [`readonly` instance members](../builtin-types/struct.md#readonly-instance-members) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="89271-118">W [ `ref readonly` zwracanej metodzie](#ref-readonly-return-example) `readonly` modyfikator wskazuje, że metoda zwraca odwołanie, a zapisy nie są dozwolone dla tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="89271-118">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="89271-119">`readonly struct` `ref readonly` Konteksty i zostały dodane w języku C# 7,2.</span><span class="sxs-lookup"><span data-stu-id="89271-119">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="89271-120">`readonly`elementy członkowskie struktury zostały dodane w języku C# 8,0</span><span class="sxs-lookup"><span data-stu-id="89271-120">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="89271-121">Przykład pola tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="89271-121">Readonly field example</span></span>

<span data-ttu-id="89271-122">W tym przykładzie wartość pola `year` nie może zostać zmieniona w metodzie `ChangeYear` , mimo że jest przypisana wartość w konstruktorze klasy:</span><span class="sxs-lookup"><span data-stu-id="89271-122">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](snippets/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="89271-123">Można przypisać wartość do `readonly` pola tylko w następujących kontekstach:</span><span class="sxs-lookup"><span data-stu-id="89271-123">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="89271-124">Gdy zmienna jest inicjowana w deklaracji, na przykład:</span><span class="sxs-lookup"><span data-stu-id="89271-124">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="89271-125">W konstruktorze wystąpienia klasy, która zawiera deklarację pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="89271-125">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="89271-126">W konstruktorze statycznym klasy, która zawiera deklarację pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="89271-126">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="89271-127">Te konteksty konstruktorów są również jedynymi kontekstami, w których są prawidłowe w celu przekazania `readonly` pola jako parametru [out](out-parameter-modifier.md) lub [ref](ref.md) .</span><span class="sxs-lookup"><span data-stu-id="89271-127">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="89271-128">`readonly`Słowo kluczowe różni się od słowa kluczowego [const](const.md) .</span><span class="sxs-lookup"><span data-stu-id="89271-128">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="89271-129">`const`Pole może być inicjowane tylko w deklaracji pola.</span><span class="sxs-lookup"><span data-stu-id="89271-129">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="89271-130">`readonly`Pole można przypisać wiele razy w deklaracji pola i w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="89271-130">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="89271-131">W związku z tym `readonly` pola mogą mieć różne wartości w zależności od użytego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="89271-131">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="89271-132">Ponadto, gdy `const` pole jest stałą czasu kompilacji, `readonly` pole może być używane dla stałych czasu wykonywania, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="89271-132">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](snippets/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="89271-133">W poprzednim przykładzie, jeśli używasz instrukcji podobnej do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="89271-133">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="89271-134">zostanie wyświetlony komunikat o błędzie kompilatora:</span><span class="sxs-lookup"><span data-stu-id="89271-134">you'll get the compiler error message:</span></span>

<span data-ttu-id="89271-135">**Nie można przypisać do pola tylko do odczytu (z wyjątkiem w konstruktorze lub inicjatorze zmiennych).**</span><span class="sxs-lookup"><span data-stu-id="89271-135">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="89271-136">Przykład powrotu ref ReadOnly</span><span class="sxs-lookup"><span data-stu-id="89271-136">Ref readonly return example</span></span>

<span data-ttu-id="89271-137">`readonly`Modyfikator na `ref return` wskazuje, że zwracane odwołanie nie może być modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="89271-137">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="89271-138">Poniższy przykład zwraca odwołanie do źródła.</span><span class="sxs-lookup"><span data-stu-id="89271-138">The following example returns a reference to the origin.</span></span> <span data-ttu-id="89271-139">Używa `readonly` modyfikatora, aby wskazać, że obiekty wywołujące nie mogą modyfikować pochodzenia:</span><span class="sxs-lookup"><span data-stu-id="89271-139">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly return example](snippets/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="89271-140">Zwracany typ nie musi być `readonly struct` .</span><span class="sxs-lookup"><span data-stu-id="89271-140">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="89271-141">Każdy typ, który może być zwracany przez, `ref` może być zwracany przez `ref readonly` .</span><span class="sxs-lookup"><span data-stu-id="89271-141">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="89271-142">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="89271-142">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="89271-143">Możesz również zobaczyć propozycje specyfikacji języka:</span><span class="sxs-lookup"><span data-stu-id="89271-143">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="89271-144">Typ ref i tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="89271-144">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="89271-145">elementy członkowskie struktury tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="89271-145">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="89271-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89271-146">See also</span></span>

- [<span data-ttu-id="89271-147">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="89271-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="89271-148">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="89271-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="89271-149">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="89271-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="89271-150">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="89271-150">Modifiers</span></span>](index.md)
- [<span data-ttu-id="89271-151">const</span><span class="sxs-lookup"><span data-stu-id="89271-151">const</span></span>](const.md)
- [<span data-ttu-id="89271-152">Pola</span><span class="sxs-lookup"><span data-stu-id="89271-152">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
