---
title: enum — słowo C# kluczowe-odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: e33877d2a5e79866bbef12cd9fec5cb11b044240
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433868"
---
# <a name="enum-c-reference"></a><span data-ttu-id="48bef-102">enum (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="48bef-102">enum (C# Reference)</span></span>

<span data-ttu-id="48bef-103">`enum` Słowo kluczowe jest używane do deklarowania wyliczenia, odrębnego typu, który składa się z zestawu nazwanych stałych o nazwie Lista modułów wyliczających.</span><span class="sxs-lookup"><span data-stu-id="48bef-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>

<span data-ttu-id="48bef-104">Zazwyczaj najlepszym rozwiązaniem jest zdefiniowanie wyliczenia bezpośrednio w przestrzeni nazw, tak aby wszystkie klasy w przestrzeni nazw mogły uzyskać do nich dostęp z taką samą wygodą.</span><span class="sxs-lookup"><span data-stu-id="48bef-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="48bef-105">Jednak Wyliczenie może być również zagnieżdżone w obrębie klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="48bef-105">However, an enum can also be nested within a class or struct.</span></span>

<span data-ttu-id="48bef-106">Domyślnie pierwszy moduł wyliczający ma wartość 0, a wartość każdego kolejnego modułu wyliczającego jest zwiększana o 1.</span><span class="sxs-lookup"><span data-stu-id="48bef-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="48bef-107">Na przykład, w poniższym wyliczeniu `Sat` , `0` `Mon` `Sun` `1` is,isitakdalej`2`.</span><span class="sxs-lookup"><span data-stu-id="48bef-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="48bef-108">Moduły wyliczające mogą używać inicjatorów, aby przesłonić wartości domyślne, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="48bef-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="48bef-109">W tym wyliczeniu kolejność elementów jest wymuszana od `1` `0`zamiast.</span><span class="sxs-lookup"><span data-stu-id="48bef-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="48bef-110">Jednakże, w tym stała o wartości 0 jest zalecana.</span><span class="sxs-lookup"><span data-stu-id="48bef-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="48bef-111">Aby uzyskać więcej informacji, zobacz [typy](../../programming-guide/enumeration-types.md)wyliczeniowe.</span><span class="sxs-lookup"><span data-stu-id="48bef-111">For more information, see [Enumeration Types](../../programming-guide/enumeration-types.md).</span></span>

<span data-ttu-id="48bef-112">Każdy typ wyliczeniowy ma typ podstawowy, który może być dowolnym [typem liczb całkowitych](../builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="48bef-112">Every enumeration type has an underlying type, which can be any [integral numeric type](../builtin-types/integral-numeric-types.md).</span></span> <span data-ttu-id="48bef-113">Typ [char](char.md) nie może być podstawowym typem wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="48bef-113">The [char](char.md) type cannot be an underlying type of an enum.</span></span> <span data-ttu-id="48bef-114">Domyślny typ podstawowy elementów wyliczenia to [int](../builtin-types/integral-numeric-types.md). Aby zadeklarować Wyliczenie innego typu całkowitego, takiego jak [Byte](../builtin-types/integral-numeric-types.md), Użyj dwukropka po identyfikatorze, po którym następuje typ, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="48bef-114">The default underlying type of enumeration elements is [int](../builtin-types/integral-numeric-types.md). To declare an enum of another integral type, such as [byte](../builtin-types/integral-numeric-types.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="48bef-115">Do zmiennej typu wyliczenia można przypisać dowolną wartość z zakresu typu bazowego; wartości nie są ograniczone do nazwanych stałych.</span><span class="sxs-lookup"><span data-stu-id="48bef-115">A variable of an enumeration type can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>

<span data-ttu-id="48bef-116">Wartość `enum E` domyślna jest wartością wygenerowaną przez wyrażenie `(E)0`.</span><span class="sxs-lookup"><span data-stu-id="48bef-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>

> [!NOTE]
> <span data-ttu-id="48bef-117">Moduł wyliczający nie może zawierać białych znaków w nazwie.</span><span class="sxs-lookup"><span data-stu-id="48bef-117">An enumerator cannot contain white space in its name.</span></span>

<span data-ttu-id="48bef-118">Typ podstawowy określa, ile miejsca do magazynowania przydzielono dla każdego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="48bef-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="48bef-119">Jednak jawne rzutowanie jest niezbędne do konwersji z `enum` typu na typ całkowity.</span><span class="sxs-lookup"><span data-stu-id="48bef-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="48bef-120">Na przykład Poniższa `Sun` instrukcja przypisuje moduł wyliczający do zmiennej typu [int](../builtin-types/integral-numeric-types.md) przy użyciu rzutowania do konwersji z `enum` na. `int`</span><span class="sxs-lookup"><span data-stu-id="48bef-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](../builtin-types/integral-numeric-types.md) by using a cast to convert from `enum` to `int`.</span></span>

```csharp
int x = (int)Day.Sun;
```

<span data-ttu-id="48bef-121">Po zastosowaniu <xref:System.FlagsAttribute?displayProperty=nameWithType> do wyliczenia zawierającego elementy, które mogą być połączone z operacją bitową `OR` , atrybut `enum` ma wpływ na zachowanie, gdy jest używany w przypadku niektórych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="48bef-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="48bef-122">Te zmiany można zauważyć przy użyciu narzędzi, takich jak <xref:System.Console> metody klasy i ewaluatora wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="48bef-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="48bef-123">(Zobacz trzeci przykład).</span><span class="sxs-lookup"><span data-stu-id="48bef-123">(See the third example.)</span></span>

## <a name="robust-programming"></a><span data-ttu-id="48bef-124">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="48bef-124">Robust programming</span></span>

<span data-ttu-id="48bef-125">Podobnie jak w przypadku każdej stałej, wszystkie odwołania do poszczególnych wartości wyliczenia są konwertowane na literały numeryczne w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="48bef-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="48bef-126">Może to powodować problemy z wersjami, jak opisano w [stałych](../../programming-guide/classes-and-structs/constants.md).</span><span class="sxs-lookup"><span data-stu-id="48bef-126">This can create potential versioning issues as described in [Constants](../../programming-guide/classes-and-structs/constants.md).</span></span>

<span data-ttu-id="48bef-127">Przypisanie dodatkowych wartości do nowych wersji wyliczeń lub zmiana wartości elementów członkowskich wyliczenia w nowej wersji może spowodować problemy z zależnym kodem źródłowym.</span><span class="sxs-lookup"><span data-stu-id="48bef-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="48bef-128">Wartości wyliczeniowe często są używane w instrukcjach [Switch](switch.md) .</span><span class="sxs-lookup"><span data-stu-id="48bef-128">Enum values often are used in [switch](switch.md) statements.</span></span> <span data-ttu-id="48bef-129">Jeśli do `enum` typu Dodano dodatkowe elementy, sekcja domyślna instrukcji switch może zostać nieoczekiwanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="48bef-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>

<span data-ttu-id="48bef-130">Jeśli inni deweloperzy używają kodu, należy podać wskazówki dotyczące sposobu reakcji ich kodu, jeśli nowe elementy są dodawane do dowolnego `enum` typu.</span><span class="sxs-lookup"><span data-stu-id="48bef-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>

## <a name="example"></a><span data-ttu-id="48bef-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="48bef-131">Example</span></span>

<span data-ttu-id="48bef-132">W poniższym przykładzie jest zadeklarowane Wyliczenie `Day`.</span><span class="sxs-lookup"><span data-stu-id="48bef-132">In the following example, an enumeration, `Day`, is declared.</span></span> <span data-ttu-id="48bef-133">Dwa moduły wyliczające są jawnie konwertowane na liczbę całkowitą i są przypisane do zmiennych całkowitych.</span><span class="sxs-lookup"><span data-stu-id="48bef-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a><span data-ttu-id="48bef-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="48bef-134">Example</span></span>

<span data-ttu-id="48bef-135">W poniższym przykładzie opcja typu podstawowego służy do deklarowania, `enum` którego składowe są typu. `long`</span><span class="sxs-lookup"><span data-stu-id="48bef-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="48bef-136">Należy zauważyć, że mimo że typ podstawowy wyliczenia to `long`, elementy członkowskie wyliczenia nadal muszą być jawnie konwertowane na typ `long` za pomocą rzutowania.</span><span class="sxs-lookup"><span data-stu-id="48bef-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a><span data-ttu-id="48bef-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="48bef-137">Example</span></span>

<span data-ttu-id="48bef-138">Poniższy przykład kodu ilustruje użycie i efekt <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybutu `enum` w deklaracji.</span><span class="sxs-lookup"><span data-stu-id="48bef-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a><span data-ttu-id="48bef-139">Komentarze</span><span class="sxs-lookup"><span data-stu-id="48bef-139">Comments</span></span>

<span data-ttu-id="48bef-140">W przypadku usunięcia `Flags`tego przykładu zostaną wyświetlone następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="48bef-140">If you remove `Flags`, the example displays the following values:</span></span>

`5`

`5`

## <a name="c-language-specification"></a><span data-ttu-id="48bef-141">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="48bef-141">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="48bef-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48bef-142">See also</span></span>

- [<span data-ttu-id="48bef-143">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="48bef-143">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="48bef-144">Typy wyliczeniowe</span><span class="sxs-lookup"><span data-stu-id="48bef-144">Enumeration Types</span></span>](../../programming-guide/enumeration-types.md)
- [<span data-ttu-id="48bef-145">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="48bef-145">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="48bef-146">Typy całkowite</span><span class="sxs-lookup"><span data-stu-id="48bef-146">Integral types</span></span>](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="48bef-147">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="48bef-147">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="48bef-148">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="48bef-148">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="48bef-149">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="48bef-149">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="48bef-150">Wyliczeniowe konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="48bef-150">Enum Naming Conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
