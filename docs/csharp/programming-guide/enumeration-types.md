---
title: Typy wyliczeniowe - C# Programming Guide
ms.custom: seodec18
ms.date: 09/10/2017
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
ms.openlocfilehash: 669357bbd6527324bbedbcf1f537bf570c63ce5b
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423671"
---
# <a name="enumeration-types-c-programming-guide"></a><span data-ttu-id="fd853-102">Typy wyliczeniowe (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="fd853-102">Enumeration types (C# Programming Guide)</span></span>

<span data-ttu-id="fd853-103">Typ wyliczenia (zwaną również wyliczenia lub typu wyliczeniowego) udostępnia efektywny sposób, aby zdefiniować zestaw nazwanych stałych liczbach całkowitych, które można przypisać do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="fd853-103">An enumeration type (also named an enumeration or an enum) provides an efficient way to define a set of named integral constants that may be assigned to a variable.</span></span> <span data-ttu-id="fd853-104">Na przykład załóżmy, że trzeba zdefiniować zmienną, w której wartość będzie reprezentować dnia tygodnia.</span><span class="sxs-lookup"><span data-stu-id="fd853-104">For example, assume that you have to define a variable whose value will represent a day of the week.</span></span> <span data-ttu-id="fd853-105">Istnieją tylko siedem istotne wartości, które nigdy nie będą przechowywane w tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="fd853-105">There are only seven meaningful values which that variable will ever store.</span></span> <span data-ttu-id="fd853-106">Aby zdefiniować te wartości, można użyć typem wyliczenia, która jest zadeklarowana za pomocą [wyliczenia](../../csharp/language-reference/keywords/enum.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="fd853-106">To define those values, you can use an enumeration type, which is declared by using the [enum](../../csharp/language-reference/keywords/enum.md) keyword.</span></span>

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

<span data-ttu-id="fd853-107">Domyślnie jest podstawowym typem każdy element w typie wyliczeniowym [int](../../csharp/language-reference/builtin-types/integral-numeric-types.md). Za pomocą dwukropka, można określić inny typ liczbowy całkowity, jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fd853-107">By default the underlying type of each element in the enum is [int](../../csharp/language-reference/builtin-types/integral-numeric-types.md). You can specify another integral numeric type by using a colon, as shown in the previous example.</span></span> <span data-ttu-id="fd853-108">Aby uzyskać pełną listę możliwych typów, zobacz [enum (odwołanie w C#)](../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="fd853-108">For a full list of possible types, see [enum (C# Reference)](../../csharp/language-reference/keywords/enum.md).</span></span>

<span data-ttu-id="fd853-109">Podstawowej wartości liczbowe można sprawdzić przez rzutowanie typu podstawowego, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="fd853-109">You can verify the underlying numeric values by casting  to the underlying type, as the following example shows.</span></span>

```csharp
Day today = Day.Monday;
int dayNumber =(int)today;
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);

Month thisMonth = Month.Dec;
byte monthNumber = (byte)thisMonth;
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);

// Output:
// Monday is day number #1.
// Dec is month number #11.
```

<span data-ttu-id="fd853-110">Korzyści wynikające z używania wyliczenia zamiast typu numerycznego są następujące:</span><span class="sxs-lookup"><span data-stu-id="fd853-110">The following are advantages of using an enum instead of a numeric type:</span></span>

- <span data-ttu-id="fd853-111">Jednoznacznie określić kod klienta, które wartości są prawidłowe dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="fd853-111">You clearly specify for client code which values are valid for the variable.</span></span>

- <span data-ttu-id="fd853-112">W programie Visual Studio funkcja IntelliSense wyświetla zdefiniowanymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="fd853-112">In Visual Studio, IntelliSense lists the defined values.</span></span>

<span data-ttu-id="fd853-113">Jeśli nie określisz wartości elementów na liście modułu wyliczającego, wartości są automatycznie zwiększany o 1.</span><span class="sxs-lookup"><span data-stu-id="fd853-113">When you do not specify values for the elements in the enumerator list, the values are automatically incremented by 1.</span></span> <span data-ttu-id="fd853-114">W poprzednim przykładzie `Day.Sunday` ma wartość 0, `Day.Monday` ma wartość 1 i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="fd853-114">In the previous example, `Day.Sunday` has a value of 0, `Day.Monday` has a value of 1, and so on.</span></span> <span data-ttu-id="fd853-115">Podczas tworzenia nowego `Day` obiektu ma wartość domyślną `Day.Sunday` (0), jeśli nie jawnie przypisać jej wartości.</span><span class="sxs-lookup"><span data-stu-id="fd853-115">When you create a new `Day` object, it will have a default value of `Day.Sunday` (0) if you do not explicitly assign it a value.</span></span> <span data-ttu-id="fd853-116">Podczas tworzenia wyliczenia wybrać najbardziej logicznym wartość domyślną, a następnie nadaj mu wartość zero.</span><span class="sxs-lookup"><span data-stu-id="fd853-116">When you create an enum, select the most logical default value and give it a value of zero.</span></span> <span data-ttu-id="fd853-117">Który spowoduje, że wszystkie typy wyliczeniowe za tę wartość domyślną, jeśli ich nie są jawnie przypisane wartości podczas ich tworzenia.</span><span class="sxs-lookup"><span data-stu-id="fd853-117">That will cause all enums to have that default value if they are not explicitly assigned a value when they are created.</span></span>

<span data-ttu-id="fd853-118">Jeśli zmienna `meetingDay` typu `Day`, a następnie (bez jawnego rzutowania) można przypisać tylko ona jedną z wartości zdefiniowanych przez `Day`.</span><span class="sxs-lookup"><span data-stu-id="fd853-118">If the variable `meetingDay` is of type `Day`, then (without an explicit cast) you can only assign it one of the values defined by `Day`.</span></span> <span data-ttu-id="fd853-119">Jeśli zmieni się w dniu spotkania, może przypisać nowej wartości z `Day` do `meetingDay`:</span><span class="sxs-lookup"><span data-stu-id="fd853-119">And if the meeting day changes, you can assign a new value from `Day` to `meetingDay`:</span></span>

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> <span data-ttu-id="fd853-120">Można przypisać dowolną wartość dowolnego liczby całkowitej do `meetingDay`.</span><span class="sxs-lookup"><span data-stu-id="fd853-120">It's possible to assign any arbitrary integer value to `meetingDay`.</span></span> <span data-ttu-id="fd853-121">Na przykład ten wiersz kodu nie generuje błąd: `meetingDay = (Day) 42`.</span><span class="sxs-lookup"><span data-stu-id="fd853-121">For example, this line of code does not produce an error: `meetingDay = (Day) 42`.</span></span> <span data-ttu-id="fd853-122">Jednak możesz nie należy tego robić, ponieważ niejawna oczekuje się, że zmienna enum będzie zawierać tylko jedną z wartości zdefiniowanych przez wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="fd853-122">However, you should not do this because the implicit expectation is that an enum variable will only hold one of the values defined by the enum.</span></span> <span data-ttu-id="fd853-123">Aby przypisać dowolną wartość do zmiennej typu wyliczeniowego jest wprowadzenie wysokie ryzyko błędów.</span><span class="sxs-lookup"><span data-stu-id="fd853-123">To assign an arbitrary value to a variable of an enumeration type is to introduce a high risk for errors.</span></span>

<span data-ttu-id="fd853-124">Wszelkie wartości można przypisać do elementów na liście moduł wyliczający typu wyliczeniowego, a można również użyć obliczonych wartości:</span><span class="sxs-lookup"><span data-stu-id="fd853-124">You can assign any values to the elements in the enumerator list of an enumeration type, and you can also use computed values:</span></span>

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="fd853-125">Typy wyliczeniowe jako znaczniki bitowe</span><span class="sxs-lookup"><span data-stu-id="fd853-125">Enumeration types as bit flags</span></span>

<span data-ttu-id="fd853-126">Typ wyliczenia można użyć do zdefiniowania flag bitowych, co umożliwia wystąpienie typu wyliczenia do przechowywania dowolną kombinację wartości, które zostały zdefiniowane na liście modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="fd853-126">You can use an enumeration type to define bit flags, which enables an instance of the enumeration type to store any combination of the values that are defined in the enumerator list.</span></span> <span data-ttu-id="fd853-127">(Oczywiście niektóre kombinacje mogą nie być znaczenia lub dozwolonych w kodzie programu.)</span><span class="sxs-lookup"><span data-stu-id="fd853-127">(Of course, some combinations may not be meaningful or allowed in your program code.)</span></span>

<span data-ttu-id="fd853-128">Utwórz trochę wyliczenia flag, stosując <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybut i odpowiednio definiowanie wartości tak, aby `AND`, `OR`, `NOT` i `XOR` Operacje bitowe mogą być wykonywane na nich.</span><span class="sxs-lookup"><span data-stu-id="fd853-128">You create a bit flags enum by applying the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute and defining the values appropriately so that `AND`, `OR`, `NOT` and `XOR` bitwise operations can be performed on them.</span></span> <span data-ttu-id="fd853-129">W trochę wyliczenia flag obejmują nazwanej stałej o wartości zero, co oznacza "nie flagi są ustawione."</span><span class="sxs-lookup"><span data-stu-id="fd853-129">In a bit flags enum, include a named constant with a value of zero that means "no flags are set."</span></span> <span data-ttu-id="fd853-130">Nie ma flagi wartość zero, jeśli nie oznacza "nie flagi są ustawione".</span><span class="sxs-lookup"><span data-stu-id="fd853-130">Do not give a flag a value of zero if it does not mean "no flags are set".</span></span>

<span data-ttu-id="fd853-131">W poniższym przykładzie inną wersję `Day` wyliczenia, które nosi nazwę `Days`, jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="fd853-131">In the following example, another version of the `Day` enum, which is named `Days`, is defined.</span></span> <span data-ttu-id="fd853-132">`Days` ma `Flags` atrybutu, a każda wartość jest przypisany następną większa potęgą liczby 2.</span><span class="sxs-lookup"><span data-stu-id="fd853-132">`Days` has the `Flags` attribute, and each value is assigned the next greater power of 2.</span></span> <span data-ttu-id="fd853-133">Dzięki temu można utworzyć `Days` zmienna, której wartość jest `Days.Tuesday | Days.Thursday`.</span><span class="sxs-lookup"><span data-stu-id="fd853-133">This enables you to create a `Days` variable whose value is `Days.Tuesday | Days.Thursday`.</span></span>

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

<span data-ttu-id="fd853-134">Aby ustawić flagę w wyliczeniu, użyj operatora testu koniunkcji `OR` operatora, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fd853-134">To set a flag on an enum, use the bitwise `OR` operator as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

<span data-ttu-id="fd853-135">Aby określić, czy ustawiono flagę określonego, użyj bitowej `AND` operacji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fd853-135">To determine whether a specific flag is set, use a bitwise `AND` operation, as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

<span data-ttu-id="fd853-136">Aby uzyskać więcej informacji o tym, co należy wziąć pod uwagę podczas definiowania typów wyliczeń za pomocą <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybutów, zobacz <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fd853-136">For more information about what to consider when you define enumeration types with the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a><span data-ttu-id="fd853-137">Korzystając z metody System.Enum odnajdywać i manipulować wartościami typu enum</span><span class="sxs-lookup"><span data-stu-id="fd853-137">Using the System.Enum methods to discover and manipulate enum values</span></span>

<span data-ttu-id="fd853-138">Wszystkie typy wyliczeniowe są wystąpieniami <xref:System.Enum?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="fd853-138">All enums are instances of the <xref:System.Enum?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="fd853-139">Nie możesz wywodzić nowe klasy z <xref:System.Enum?displayProperty=nameWithType>, ale jego metody umożliwia odnajdywanie informacji o i manipulować wartościami w wystąpieniu typu wyliczeniowego.</span><span class="sxs-lookup"><span data-stu-id="fd853-139">You cannot derive new classes from <xref:System.Enum?displayProperty=nameWithType>, but you can use its methods to discover information about and manipulate values in an enum instance.</span></span>

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

<span data-ttu-id="fd853-140">Aby uzyskać więcej informacji, zobacz <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fd853-140">For more information, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="fd853-141">Można również utworzyć nowej metody dla wyliczenia przy użyciu metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="fd853-141">You can also create a new method for an enum by using an extension method.</span></span> <span data-ttu-id="fd853-142">Aby uzyskać więcej informacji, zobacz [jak: Utworzenie nowej metody wyliczania](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="fd853-142">For more information, see [How to: Create a New Method for an Enumeration](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fd853-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd853-143">See also</span></span>

- <xref:System.Enum?displayProperty=nameWithType>
- [<span data-ttu-id="fd853-144">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="fd853-144">C# Programming Guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="fd853-145">enum</span><span class="sxs-lookup"><span data-stu-id="fd853-145">enum</span></span>](../../csharp/language-reference/keywords/enum.md)
