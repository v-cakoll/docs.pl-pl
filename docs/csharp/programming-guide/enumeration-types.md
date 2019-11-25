---
title: Typy wyliczeniowe — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 09/10/2017
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
ms.openlocfilehash: 3573959a1e10b475a9867631767de5d10a08b9ea
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969765"
---
# <a name="enumeration-types-c-programming-guide"></a><span data-ttu-id="620dc-102">Typy wyliczeniowe (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="620dc-102">Enumeration types (C# Programming Guide)</span></span>

<span data-ttu-id="620dc-103">Typ wyliczenia (nazywany również wyliczeniem lub wyliczeniem) zapewnia wydajny sposób definiowania zestawu nazwanych stałych, które mogą być przypisane do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="620dc-103">An enumeration type (also named an enumeration or an enum) provides an efficient way to define a set of named integral constants that may be assigned to a variable.</span></span> <span data-ttu-id="620dc-104">Załóżmy na przykład, że musisz zdefiniować zmienną, której wartość będzie zawierać dzień tygodnia.</span><span class="sxs-lookup"><span data-stu-id="620dc-104">For example, assume that you have to define a variable whose value will represent a day of the week.</span></span> <span data-ttu-id="620dc-105">Istnieje tylko siedem wartości, które będą kiedykolwiek przechowywane w tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="620dc-105">There are only seven meaningful values which that variable will ever store.</span></span> <span data-ttu-id="620dc-106">Aby zdefiniować te wartości, można użyć typu wyliczenia, który jest zadeklarowany za pomocą słowa kluczowego [enum](../language-reference/keywords/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="620dc-106">To define those values, you can use an enumeration type, which is declared by using the [enum](../language-reference/keywords/enum.md) keyword.</span></span>

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

<span data-ttu-id="620dc-107">Domyślnie typem podstawowym każdego elementu w wyliczeniu jest [int](../language-reference/builtin-types/integral-numeric-types.md). Możesz określić inny typ liczbowy całkowity przy użyciu dwukropka, jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="620dc-107">By default the underlying type of each element in the enum is [int](../language-reference/builtin-types/integral-numeric-types.md). You can specify another integral numeric type by using a colon, as shown in the previous example.</span></span> <span data-ttu-id="620dc-108">Aby uzyskać pełną listę możliwych typów, zobacz [Wyliczenie (C# odwołanie)](../language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="620dc-108">For a full list of possible types, see [enum (C# Reference)](../language-reference/keywords/enum.md).</span></span>

<span data-ttu-id="620dc-109">Można sprawdzić bazowe wartości liczbowe przez rzutowanie na typ podstawowy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="620dc-109">You can verify the underlying numeric values by casting  to the underlying type, as the following example shows.</span></span>

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

<span data-ttu-id="620dc-110">Poniżej przedstawiono zalety użycia wyliczenia zamiast typu liczbowego:</span><span class="sxs-lookup"><span data-stu-id="620dc-110">The following are advantages of using an enum instead of a numeric type:</span></span>

- <span data-ttu-id="620dc-111">Jasno określono kod klienta, który wartości są prawidłowe dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="620dc-111">You clearly specify for client code which values are valid for the variable.</span></span>

- <span data-ttu-id="620dc-112">W programie Visual Studio funkcja IntelliSense wyświetla zdefiniowane wartości.</span><span class="sxs-lookup"><span data-stu-id="620dc-112">In Visual Studio, IntelliSense lists the defined values.</span></span>

<span data-ttu-id="620dc-113">Jeśli nie określisz wartości dla elementów na liście moduł wyliczający, wartości są automatycznie zwiększane o 1.</span><span class="sxs-lookup"><span data-stu-id="620dc-113">When you do not specify values for the elements in the enumerator list, the values are automatically incremented by 1.</span></span> <span data-ttu-id="620dc-114">W poprzednim przykładzie `Day.Sunday` ma wartość 0, `Day.Monday` ma wartość 1 i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="620dc-114">In the previous example, `Day.Sunday` has a value of 0, `Day.Monday` has a value of 1, and so on.</span></span> <span data-ttu-id="620dc-115">Podczas tworzenia nowego obiektu `Day` będzie on miał wartość domyślną `Day.Sunday` (0), jeśli nie zostanie jawnie przypisana wartość.</span><span class="sxs-lookup"><span data-stu-id="620dc-115">When you create a new `Day` object, it will have a default value of `Day.Sunday` (0) if you do not explicitly assign it a value.</span></span> <span data-ttu-id="620dc-116">Podczas tworzenia wyliczenia wybierz najbardziej logiczną wartość domyślną i nadaj jej wartość zero.</span><span class="sxs-lookup"><span data-stu-id="620dc-116">When you create an enum, select the most logical default value and give it a value of zero.</span></span> <span data-ttu-id="620dc-117">Spowoduje to, że wszystkie wyliczenia mają tę wartość domyślną, jeśli nie będą jawnie przypisywać wartości podczas tworzenia.</span><span class="sxs-lookup"><span data-stu-id="620dc-117">That will cause all enums to have that default value if they are not explicitly assigned a value when they are created.</span></span>

<span data-ttu-id="620dc-118">Jeśli zmienna `meetingDay` jest typu `Day`, to (bez jawnego rzutowania) można przypisać tylko jedną z wartości zdefiniowanych przez `Day`.</span><span class="sxs-lookup"><span data-stu-id="620dc-118">If the variable `meetingDay` is of type `Day`, then (without an explicit cast) you can only assign it one of the values defined by `Day`.</span></span> <span data-ttu-id="620dc-119">W przypadku zmiany dnia spotkania można przypisać nową wartość z `Day` do `meetingDay`:</span><span class="sxs-lookup"><span data-stu-id="620dc-119">And if the meeting day changes, you can assign a new value from `Day` to `meetingDay`:</span></span>

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> <span data-ttu-id="620dc-120">Możliwe jest przypisanie dowolnej wartości całkowitej do `meetingDay`.</span><span class="sxs-lookup"><span data-stu-id="620dc-120">It's possible to assign any arbitrary integer value to `meetingDay`.</span></span> <span data-ttu-id="620dc-121">Na przykład ten wiersz kodu nie tworzy błędu: `meetingDay = (Day) 42`.</span><span class="sxs-lookup"><span data-stu-id="620dc-121">For example, this line of code does not produce an error: `meetingDay = (Day) 42`.</span></span> <span data-ttu-id="620dc-122">Jednak nie należy tego robić, ponieważ niejawne oczekiwanie jest fakt, że zmienna enum będzie zawierać tylko jedną z wartości zdefiniowanych przez wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="620dc-122">However, you should not do this because the implicit expectation is that an enum variable will only hold one of the values defined by the enum.</span></span> <span data-ttu-id="620dc-123">Aby przypisać arbitralną wartość do zmiennej typu wyliczenia, należy wprowadzić wysokie ryzyko dla błędów.</span><span class="sxs-lookup"><span data-stu-id="620dc-123">To assign an arbitrary value to a variable of an enumeration type is to introduce a high risk for errors.</span></span>

<span data-ttu-id="620dc-124">Można przypisać dowolne wartości do elementów na liście modułów wyliczających typu wyliczenia i można również użyć wartości obliczanych:</span><span class="sxs-lookup"><span data-stu-id="620dc-124">You can assign any values to the elements in the enumerator list of an enumeration type, and you can also use computed values:</span></span>

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="620dc-125">Typy wyliczeniowe jako flagi bitowe</span><span class="sxs-lookup"><span data-stu-id="620dc-125">Enumeration types as bit flags</span></span>

<span data-ttu-id="620dc-126">Możesz użyć typu wyliczenia, aby zdefiniować flagi bitowe, które umożliwiają wystąpienie typu wyliczenia do przechowywania dowolnej kombinacji wartości, które są zdefiniowane na liście modułów wyliczających.</span><span class="sxs-lookup"><span data-stu-id="620dc-126">You can use an enumeration type to define bit flags, which enables an instance of the enumeration type to store any combination of the values that are defined in the enumerator list.</span></span> <span data-ttu-id="620dc-127">(Oczywiście Niektóre kombinacje mogą nie być znaczące ani niedozwolone w kodzie programu).</span><span class="sxs-lookup"><span data-stu-id="620dc-127">(Of course, some combinations may not be meaningful or allowed in your program code.)</span></span>

<span data-ttu-id="620dc-128">Aby utworzyć Wyliczenie flag bitowych, należy zastosować atrybut <xref:System.FlagsAttribute?displayProperty=nameWithType> i odpowiednio zdefiniować wartości, aby można było wykonywać na nich `AND`, `OR`, `NOT` i `XOR` operacje bitowe.</span><span class="sxs-lookup"><span data-stu-id="620dc-128">You create a bit flags enum by applying the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute and defining the values appropriately so that `AND`, `OR`, `NOT` and `XOR` bitwise operations can be performed on them.</span></span> <span data-ttu-id="620dc-129">W wyliczeniu flag bitowych należy uwzględnić nazwaną stałą o wartości zero, co oznacza, że flagi nie są ustawione.</span><span class="sxs-lookup"><span data-stu-id="620dc-129">In a bit flags enum, include a named constant with a value of zero that means "no flags are set."</span></span> <span data-ttu-id="620dc-130">Nie należy dawać flagi wartością zero, jeśli nie ma znaczenia "nie ustawiono flag".</span><span class="sxs-lookup"><span data-stu-id="620dc-130">Do not give a flag a value of zero if it does not mean "no flags are set".</span></span>

<span data-ttu-id="620dc-131">W poniższym przykładzie zdefiniowano inną wersję `Day` Wyliczenie o nazwie `Days`.</span><span class="sxs-lookup"><span data-stu-id="620dc-131">In the following example, another version of the `Day` enum, which is named `Days`, is defined.</span></span> <span data-ttu-id="620dc-132">`Days` ma atrybut `Flags`, a każda wartość jest przypisana kolejną większą potęgą 2.</span><span class="sxs-lookup"><span data-stu-id="620dc-132">`Days` has the `Flags` attribute, and each value is assigned the next greater power of 2.</span></span> <span data-ttu-id="620dc-133">Dzięki temu można utworzyć zmienną `Days`, której wartość jest `Days.Tuesday | Days.Thursday`.</span><span class="sxs-lookup"><span data-stu-id="620dc-133">This enables you to create a `Days` variable whose value is `Days.Tuesday | Days.Thursday`.</span></span>

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

<span data-ttu-id="620dc-134">Aby ustawić flagę w wyliczeniu, użyj operatora `OR` bitowego, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="620dc-134">To set a flag on an enum, use the bitwise `OR` operator as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

<span data-ttu-id="620dc-135">Aby określić, czy określona flaga jest ustawiona, użyj operacji `AND` bitowej, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="620dc-135">To determine whether a specific flag is set, use a bitwise `AND` operation, as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

<span data-ttu-id="620dc-136">Aby uzyskać więcej informacji o tym, co należy wziąć pod uwagę podczas definiowania typów wyliczeniowych z atrybutem <xref:System.FlagsAttribute?displayProperty=nameWithType>, zobacz <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="620dc-136">For more information about what to consider when you define enumeration types with the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a><span data-ttu-id="620dc-137">Używanie metod system. Enum do odnajdywania i manipulowania wartościami wyliczanymi</span><span class="sxs-lookup"><span data-stu-id="620dc-137">Using the System.Enum methods to discover and manipulate enum values</span></span>

<span data-ttu-id="620dc-138">Wszystkie wyliczenia są wystąpieniami typu <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="620dc-138">All enums are instances of the <xref:System.Enum?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="620dc-139">Nie można utworzyć nowych klas na podstawie <xref:System.Enum?displayProperty=nameWithType>, ale można użyć jej metod w celu odnalezienia informacji o wartościach i manipulowania nimi w wystąpieniu wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="620dc-139">You cannot derive new classes from <xref:System.Enum?displayProperty=nameWithType>, but you can use its methods to discover information about and manipulate values in an enum instance.</span></span>

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

<span data-ttu-id="620dc-140">Aby uzyskać więcej informacji, zobacz <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="620dc-140">For more information, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="620dc-141">Możesz również utworzyć nową metodę dla wyliczenia przy użyciu metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="620dc-141">You can also create a new method for an enum by using an extension method.</span></span> <span data-ttu-id="620dc-142">Aby uzyskać więcej informacji, zobacz [jak utworzyć nową metodę wyliczania](./classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="620dc-142">For more information, see [How to create a new method for an enumeration](./classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="620dc-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="620dc-143">See also</span></span>

- <xref:System.Enum?displayProperty=nameWithType>
- [<span data-ttu-id="620dc-144">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="620dc-144">C# Programming Guide</span></span>](./index.md)
- [<span data-ttu-id="620dc-145">enum</span><span class="sxs-lookup"><span data-stu-id="620dc-145">enum</span></span>](../language-reference/keywords/enum.md)
