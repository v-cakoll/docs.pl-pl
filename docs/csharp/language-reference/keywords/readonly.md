---
title: ReadOnly — słowo kluczowe (odwołanie w C#)
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 96607f1dd7f019169446e29a08496fb54e1ed493
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961186"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="9b201-102">readonly (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9b201-102">readonly (C# Reference)</span></span>

<span data-ttu-id="9b201-103">`readonly` — Słowo kluczowe jest modyfikator, który może być używana w kontekstach trzy:</span><span class="sxs-lookup"><span data-stu-id="9b201-103">The `readonly` keyword is a modifier that can be used in three contexts:</span></span>

- <span data-ttu-id="9b201-104">W [pola deklaracji](#readonly-field-example), `readonly` wskazuje przypisania do pola mogą występować wyłącznie jako część deklaracji lub za pomocą konstruktora w tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="9b201-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span>
- <span data-ttu-id="9b201-105">W [ `readonly struct` definicji](#readonly-struct-example), `readonly` wskazuje, że `struct` można modyfikować.</span><span class="sxs-lookup"><span data-stu-id="9b201-105">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="9b201-106">W [ `ref readonly` zwrotu metody](#ref-readonly-return-example), `readonly` modyfikator wskazuje, że metoda zwraca odwołanie i zapisy są niedozwolone do tego odwołania.</span><span class="sxs-lookup"><span data-stu-id="9b201-106">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes are not allowed to that reference.</span></span>

<span data-ttu-id="9b201-107">Końcowe dwa konteksty zostały dodane w języku C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="9b201-107">The final two contexts were added in C# 7.2.</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="9b201-108">Przykład pola tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9b201-108">Readonly field example</span></span>  

<span data-ttu-id="9b201-109">W tym przykładzie wartość pola `year` nie można zmienić w metodzie `ChangeYear`, nawet jeśli jest do niej przypisana wartość w konstruktorze klasy:</span><span class="sxs-lookup"><span data-stu-id="9b201-109">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>  
  
[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]  
  
<span data-ttu-id="9b201-110">Można przypisać wartości do `readonly` tylko w następujących kontekstów się:</span><span class="sxs-lookup"><span data-stu-id="9b201-110">You can assign a value to a `readonly` field only in the following contexts:</span></span>  
  
- <span data-ttu-id="9b201-111">Gdy zmienna jest inicjowana w deklaracji, na przykład:</span><span class="sxs-lookup"><span data-stu-id="9b201-111">When the variable is initialized in the declaration, for example:</span></span>  

```csharp
public readonly int y = 5;  
```

- <span data-ttu-id="9b201-112">W konstruktorze wystąpienia klasy, który zawiera deklarację pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9b201-112">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="9b201-113">W konstruktorze statycznym klasy, który zawiera deklarację pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="9b201-113">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="9b201-114">Tych kontekstach Konstruktor są również tylko kontekstów, w których jest on prawidłowy do przekazania `readonly` pola jako [się](out-parameter-modifier.md) lub [ref](ref.md) parametru.</span><span class="sxs-lookup"><span data-stu-id="9b201-114">These constructor contexts are also the only contexts in which it is valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b201-115">`readonly` — Słowo kluczowe różni się od [const](const.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="9b201-115">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="9b201-116">A `const` pola mogą być inicjowane tylko na deklarację pola.</span><span class="sxs-lookup"><span data-stu-id="9b201-116">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="9b201-117">A `readonly` pola mogą być inicjowane w deklaracji lub w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="9b201-117">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="9b201-118">W związku z tym `readonly` pola mogą mieć różne wartości w zależności od używanego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="9b201-118">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="9b201-119">Ponadto, podczas gdy `const` pole jest stałą czasu kompilacji `readonly` pole może być używane dla stałych środowiska uruchomieniowego, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9b201-119">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>  

```csharp
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]  
  
<span data-ttu-id="9b201-120">W poprzednim przykładzie, jeśli korzystasz z instrukcji, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9b201-120">In the preceding example, if you use a statement like the following example:</span></span>  
  
`p2.y = 66;        // Error`  
  
<span data-ttu-id="9b201-121">zostanie wyświetlony komunikat o błędzie kompilatora:</span><span class="sxs-lookup"><span data-stu-id="9b201-121">you will get the compiler error message:</span></span>  
  
`The left-hand side of an assignment must be an l-value`  
  
<span data-ttu-id="9b201-122">który jest ten sam błąd, która pojawia się po użytkownik podejmie próbę przypisania wartości do stałej.</span><span class="sxs-lookup"><span data-stu-id="9b201-122">which is the same error you get when you attempt to assign a value to a constant.</span></span>  

## <a name="readonly-struct-example"></a><span data-ttu-id="9b201-123">Przykład struktury tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9b201-123">Readonly struct example</span></span>

<span data-ttu-id="9b201-124">`readonly` Modyfikator na `struct` definicji oświadcza, że struktura **niezmienne**.</span><span class="sxs-lookup"><span data-stu-id="9b201-124">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="9b201-125">Wszystkie pola wystąpienia `struct` muszą być oznaczone jako `readonly`, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9b201-125">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]  

<span data-ttu-id="9b201-126">W poprzednim przykładzie użyto [tylko do odczytu właściwości automatyczne](../../properties.md#read-only) można zadeklarować magazynu.</span><span class="sxs-lookup"><span data-stu-id="9b201-126">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="9b201-127">Która instruuje kompilator, aby utworzyć `readonly` kopii pola dla tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="9b201-127">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="9b201-128">Można również zadeklarować `readonly` pól bezpośrednio:</span><span class="sxs-lookup"><span data-stu-id="9b201-128">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="9b201-129">Dodawanie pola niezaznaczonych `readonly` generuje błąd kompilatora `CS8340`: "wystąpienia pól struktur tylko do odczytu muszą być tylko do odczytu."</span><span class="sxs-lookup"><span data-stu-id="9b201-129">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="9b201-130">Przykład zwracane tylko do odczytu REF</span><span class="sxs-lookup"><span data-stu-id="9b201-130">Ref readonly return example</span></span>

<span data-ttu-id="9b201-131">`readonly` Modyfikator na `ref return` wskazuje, że zwracane odwołanie nie może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="9b201-131">The `readonly` modifier on a `ref return` indicates that the returned reference cannot be modified.</span></span> <span data-ttu-id="9b201-132">Poniższy przykład zwraca odwołanie do źródła.</span><span class="sxs-lookup"><span data-stu-id="9b201-132">The following example returns a reference to the origin.</span></span> <span data-ttu-id="9b201-133">Używa ona `readonly` modyfikator, aby wskazać, że obiekty wywołujące nie można zmodyfikować punkt początkowy:</span><span class="sxs-lookup"><span data-stu-id="9b201-133">It uses the `readonly` modifier to indicate that callers cannot modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]  
<span data-ttu-id="9b201-134">Typ zwracany nie musi być `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="9b201-134">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="9b201-135">Dowolny typ, który może zostać zwrócony przez `ref` mogą być zwrócone przez `ref readonly`</span><span class="sxs-lookup"><span data-stu-id="9b201-135">Any type that can be returned by `ref` can be returned by `ref readonly`</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9b201-136">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9b201-136">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9b201-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b201-137">See Also</span></span>  
[<span data-ttu-id="9b201-138">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9b201-138">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="9b201-139">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9b201-139">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="9b201-140">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="9b201-140">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="9b201-141">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="9b201-141">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
[<span data-ttu-id="9b201-142">const</span><span class="sxs-lookup"><span data-stu-id="9b201-142">const</span></span>](../../../csharp/language-reference/keywords/const.md)  
[<span data-ttu-id="9b201-143">Pola</span><span class="sxs-lookup"><span data-stu-id="9b201-143">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)
