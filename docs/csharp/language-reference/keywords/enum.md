---
title: Enum — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 768d8da320022a686f2ecfe5222880eccacee7dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727641"
---
# <a name="enum-c-reference"></a><span data-ttu-id="6d6b0-102">enum (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6d6b0-102">enum (C# Reference)</span></span>

<span data-ttu-id="6d6b0-103">`enum` Słowo kluczowe jest używane do deklarowania wyliczania, typem samodzielnym, który zawiera zestaw nazwanych stałych zwanego listą modułów wyliczających.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>  

<span data-ttu-id="6d6b0-104">Zazwyczaj najlepiej jest zdefiniowanie wyliczenia bezpośrednio w przestrzeni nazw, tak, aby wszystkie klasy w przestrzeni nazw do niego dostęp za pomocą równy wygody.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="6d6b0-105">Jednak wyliczenia może być zagnieżdżona w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-105">However, an enum can also be nested within a class or struct.</span></span>

<span data-ttu-id="6d6b0-106">Domyślnie pierwszy moduł wyliczający ma wartość 0, a wartość każdego kolejnych moduł wyliczający jest zwiększana o 1.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="6d6b0-107">Na przykład w następujących wyliczenia `Sat` jest `0`, `Sun` jest `1`, `Mon` jest `2`, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="6d6b0-108">Moduły wyliczające umożliwia inicjatory przesłonić wartości domyślne, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="6d6b0-109">W tym wyliczeniu sekwencję elementów jest zmuszony do uruchamiania z `1` zamiast `0`.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="6d6b0-110">Jednak zaleca się tym stałą, który ma wartość 0.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="6d6b0-111">Aby uzyskać więcej informacji, zobacz [Typy wyliczeniowe](../../programming-guide/enumeration-types.md).</span><span class="sxs-lookup"><span data-stu-id="6d6b0-111">For more information, see [Enumeration Types](../../programming-guide/enumeration-types.md).</span></span>

<span data-ttu-id="6d6b0-112">Każdy typ wyliczenia ma podstawowy typ, który może być dowolnego typu całkowitoliczbowego z wyjątkiem [char](char.md).</span><span class="sxs-lookup"><span data-stu-id="6d6b0-112">Every enumeration type has an underlying type, which can be any integral type except [char](char.md).</span></span> <span data-ttu-id="6d6b0-113">Domyślny typ podstawowy wyliczenia elementów to [int](int.md). Aby zadeklarować wyliczenie innego typu całkowitego, takich jak [bajtów](byte.md), użyj dwukropka po identyfikatorze, a następnie według typu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-113">The default underlying type of enumeration elements is [int](int.md). To declare an enum of another integral type, such as [byte](byte.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="6d6b0-114">Zatwierdzone typy wyliczenia [bajtów](byte.md), [sbyte](sbyte.md), [krótki](short.md), [ushort](ushort.md), [int](int.md), [uint](uint.md), [długie](long.md), lub [ulong](ulong.md).</span><span class="sxs-lookup"><span data-stu-id="6d6b0-114">The approved types for an enum are [byte](byte.md), [sbyte](sbyte.md), [short](short.md), [ushort](ushort.md), [int](int.md), [uint](uint.md), [long](long.md), or [ulong](ulong.md).</span></span>

<span data-ttu-id="6d6b0-115">Zmienna typu wyliczeniowego można przypisać dowolną wartość z zakresu typu podstawowego; wartości nie są ograniczone do nazwanych stałych.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-115">A variable of an enumeration type can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>

<span data-ttu-id="6d6b0-116">Wartość domyślna `enum E` jest wartością produkowane przez wyrażenie `(E)0`.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>

> [!NOTE]
> <span data-ttu-id="6d6b0-117">Moduł wyliczający nie może zawierać biały znak w nazwie.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-117">An enumerator cannot contain white space in its name.</span></span>

<span data-ttu-id="6d6b0-118">Podstawowy typ Określa, ile pamięci masowej jest przydzielany dla każdego typu wyliczeniowego.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="6d6b0-119">Jednak jawnego rzutowania jest niezbędne do konwersji z `enum` typu na typ całkowitoliczbowy.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="6d6b0-120">Na przykład następująca instrukcja przypisuje modułu wyliczającego `Sun` do zmiennej typu [int](int.md) przy użyciu rzutowanie do konwersji z `enum` do `int`.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](int.md) by using a cast to convert from `enum` to `int`.</span></span>

```csharp
int x = (int)Day.Sun;
```

<span data-ttu-id="6d6b0-121">Po zastosowaniu <xref:System.FlagsAttribute?displayProperty=nameWithType> z wyliczeniem, który zawiera elementy, które mogą być łączone z bitową `OR` operacji, ten atrybut ma wpływ na zachowanie `enum` gdy jest używany z narzędziami.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="6d6b0-122">Można zauważyć te zmiany, korzystając z narzędzi takich jak <xref:System.Console> klas, metod i ewaluatora wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="6d6b0-123">(Zobacz trzeci przykład).</span><span class="sxs-lookup"><span data-stu-id="6d6b0-123">(See the third example.)</span></span>

## <a name="robust-programming"></a><span data-ttu-id="6d6b0-124">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="6d6b0-124">Robust programming</span></span>

<span data-ttu-id="6d6b0-125">Podobnie jak w przypadku dowolną stałą wszystkie odwołania do poszczególnych wartości wyliczenia są konwertowane na literały numeryczne w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="6d6b0-126">To utworzenie potencjalne problemy z wersjonowaniem, zgodnie z opisem w [stałe](../../programming-guide/classes-and-structs/constants.md).</span><span class="sxs-lookup"><span data-stu-id="6d6b0-126">This can create potential versioning issues as described in [Constants](../../programming-guide/classes-and-structs/constants.md).</span></span>

<span data-ttu-id="6d6b0-127">Przypisywanie dodatkowych wartości do nowych wersji wyliczenia lub zmiana wartości elementów członkowskich wyliczenia w nowej wersji, może powodować problemy, które kodu źródłowego zależnych.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="6d6b0-128">Wartości wyliczeniowe są często używane w [Przełącz](switch.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-128">Enum values often are used in [switch](switch.md) statements.</span></span> <span data-ttu-id="6d6b0-129">Jeśli dodatkowe elementy zostały dodane do `enum` nieoczekiwanie można wybrać domyślną sekcję instrukcji switch typu.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>

<span data-ttu-id="6d6b0-130">Użycie kodu, inni deweloperzy dostarczają wytyczne dotyczące sposobu ich kod powinien reagować, jeśli nowe elementy są dodawane do dowolnej `enum` typów.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>

## <a name="example"></a><span data-ttu-id="6d6b0-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d6b0-131">Example</span></span>

<span data-ttu-id="6d6b0-132">W poniższym przykładzie wyliczenie `Day`, jest zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-132">In the following example, an enumeration, `Day`, is declared.</span></span> <span data-ttu-id="6d6b0-133">Dwa moduły wyliczające są jawnie konwertowany na liczbę całkowitą i przypisane do zmiennych całkowitych.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a><span data-ttu-id="6d6b0-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d6b0-134">Example</span></span>

<span data-ttu-id="6d6b0-135">W poniższym przykładzie opcja Typ podstawowy jest używane do deklarowania `enum` której członkami są typu `long`.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="6d6b0-136">Należy zauważyć, że nawet jeśli jest podstawowym typem wyliczenia `long`, elementy członkowskie wyliczenia nadal muszą być jawnie konwertowane na typ `long` przy użyciu rzutowania.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a><span data-ttu-id="6d6b0-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d6b0-137">Example</span></span>

<span data-ttu-id="6d6b0-138">Poniższy przykład kodu ilustruje stosowanie i efekt <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybutu na `enum` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="6d6b0-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a><span data-ttu-id="6d6b0-139">Komentarze</span><span class="sxs-lookup"><span data-stu-id="6d6b0-139">Comments</span></span>

<span data-ttu-id="6d6b0-140">Jeśli usuniesz `Flags`, w przykładzie są wyświetlane następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="6d6b0-140">If you remove `Flags`, the example displays the following values:</span></span>

`5`

`5`

## <a name="c-language-specification"></a><span data-ttu-id="6d6b0-141">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6d6b0-141">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6d6b0-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d6b0-142">See also</span></span>

- [<span data-ttu-id="6d6b0-143">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6d6b0-143">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6d6b0-144">Typy wyliczeniowe</span><span class="sxs-lookup"><span data-stu-id="6d6b0-144">Enumeration Types</span></span>](../../programming-guide/enumeration-types.md)
- [<span data-ttu-id="6d6b0-145">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="6d6b0-145">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6d6b0-146">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="6d6b0-146">Integral Types Table</span></span>](integral-types-table.md)
- [<span data-ttu-id="6d6b0-147">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="6d6b0-147">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="6d6b0-148">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="6d6b0-148">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="6d6b0-149">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="6d6b0-149">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="6d6b0-150">Konwencje nazewnictwa typu wyliczeniowego</span><span class="sxs-lookup"><span data-stu-id="6d6b0-150">Enum Naming Conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
