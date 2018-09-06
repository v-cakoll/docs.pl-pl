---
title: 'Porady: użycie stref czasowych w arytmetyka daty i godziny'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], adding and subtracting
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c9f7b2623b4ed766fb44b46c3f54caa962c07eb
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041525"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a><span data-ttu-id="4eef4-102">Porady: użycie stref czasowych w arytmetyka daty i godziny</span><span class="sxs-lookup"><span data-stu-id="4eef4-102">How to: Use time zones in date and time arithmetic</span></span>

<span data-ttu-id="4eef4-103">Zazwyczaj podczas możesz wykonać daty i godziny arytmetycznych przy użyciu <xref:System.DateTime> lub <xref:System.DateTimeOffset> wartości, wynik nie odzwierciedla żadnych reguł dopasowania stref czasowych.</span><span class="sxs-lookup"><span data-stu-id="4eef4-103">Ordinarily, when you perform date and time arithmetic using <xref:System.DateTime> or <xref:System.DateTimeOffset> values, the result does not reflect any time zone adjustment rules.</span></span> <span data-ttu-id="4eef4-104">Ta zasada obowiązuje nawet wtedy, gdy jest wyraźnie strefy czasowej w wartości daty i godziny (na przykład, gdy <xref:System.DateTime.Kind%2A> właściwość jest ustawiona na <xref:System.DateTimeKind.Local>).</span><span class="sxs-lookup"><span data-stu-id="4eef4-104">This is true even when the time zone of the date and time value is clearly identifiable (for example, when the <xref:System.DateTime.Kind%2A> property is set to <xref:System.DateTimeKind.Local>).</span></span> <span data-ttu-id="4eef4-105">W tym temacie pokazano, jak wykonywać operacje arytmetyczne na wartości daty i godziny, które należą do określonej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="4eef4-105">This topic shows how to perform arithmetic operations on date and time values that belong to a particular time zone.</span></span> <span data-ttu-id="4eef4-106">Wyniki operacji arytmetycznych odzwierciedlają reguł korygowania strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="4eef4-106">The results of the arithmetic operations will reflect the time zone's adjustment rules.</span></span>

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a><span data-ttu-id="4eef4-107">Aby zastosować reguły dopasowania do arytmetyka daty i godziny</span><span class="sxs-lookup"><span data-stu-id="4eef4-107">To apply adjustment rules to date and time arithmetic</span></span>

1. <span data-ttu-id="4eef4-108">Zaimplementowanie niektóre metody ściśle sprzężenia wartości daty i godziny ze strefą czasową, do której należy.</span><span class="sxs-lookup"><span data-stu-id="4eef4-108">Implement some method of closely coupling a date and time value with the time zone to which it belongs.</span></span> <span data-ttu-id="4eef4-109">Na przykład można zadeklarować strukturę, która zawiera datę i wartości godziny i strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="4eef4-109">For example, declare a structure that includes both the date and time value and its time zone.</span></span> <span data-ttu-id="4eef4-110">W poniższym przykładzie użyto tego podejścia połączyć <xref:System.DateTime> wartość z ich strefą czasu.</span><span class="sxs-lookup"><span data-stu-id="4eef4-110">The following example uses this approach to link a <xref:System.DateTime> value with its time zone.</span></span>

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. <span data-ttu-id="4eef4-111">Konwertuj czas uniwersalny czas koordynowany (UTC), wywołując jedną <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> metody lub <xref:System.TimeZoneInfo.ConvertTime%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4eef4-111">Convert a time to Coordinated Universal Time (UTC) by calling either the <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> method or the <xref:System.TimeZoneInfo.ConvertTime%2A> method.</span></span>

3. <span data-ttu-id="4eef4-112">Wykonywanie operacji arytmetycznej na czas UTC.</span><span class="sxs-lookup"><span data-stu-id="4eef4-112">Perform the arithmetic operation on the UTC time.</span></span>

4. <span data-ttu-id="4eef4-113">Przekonwertować wartość czasu względem czasu UTC na pierwotny czas skojarzone strefę czasową, wywołując <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="4eef4-113">Convert the time from UTC to the original time's associated time zone by calling the <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span>

## <a name="example"></a><span data-ttu-id="4eef4-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="4eef4-114">Example</span></span>

<span data-ttu-id="4eef4-115">Poniższy przykład dodaje dwie godziny i 30 minut do 9 marca 2008 roku o godzinie 1:30</span><span class="sxs-lookup"><span data-stu-id="4eef4-115">The following example adds two hours and thirty minutes to March 9, 2008, at 1:30 A.M.</span></span> <span data-ttu-id="4eef4-116">Środkowy czas standardowy.</span><span class="sxs-lookup"><span data-stu-id="4eef4-116">Central Standard Time.</span></span> <span data-ttu-id="4eef4-117">Strefa czasowa przejścia do czasu letniego występuje trzydzieści minut później, o 2:00</span><span class="sxs-lookup"><span data-stu-id="4eef4-117">The time zone's transition to daylight saving time occurs thirty minutes later, at 2:00 A.M.</span></span> <span data-ttu-id="4eef4-118">9 marca 2008.</span><span class="sxs-lookup"><span data-stu-id="4eef4-118">on March 9, 2008.</span></span> <span data-ttu-id="4eef4-119">Ponieważ w przykładzie poniżej czterech kroków opisanych w poprzedniej sekcji, poprawnie raporty wynikowego czas jako 05:00.</span><span class="sxs-lookup"><span data-stu-id="4eef4-119">Because the example follows the four steps listed in the previous section, it correctly reports the resulting time as 5:00 A.M.</span></span> <span data-ttu-id="4eef4-120">9 marca 2008.</span><span class="sxs-lookup"><span data-stu-id="4eef4-120">on March 9, 2008.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

<span data-ttu-id="4eef4-121">Zarówno <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości są oddzielone od dowolnej strefie czasowej, do których może należeć.</span><span class="sxs-lookup"><span data-stu-id="4eef4-121">Both <xref:System.DateTime> and <xref:System.DateTimeOffset> values are disassociated from any time zone to which they might belong.</span></span> <span data-ttu-id="4eef4-122">Aby wykonać arytmetyka w taki sposób, aby automatycznie stosuje reguły dopasowania jest strefa czasowa daty i godziny, strefę czasową, do której wszystkie daty i godziny wartość należy musi być natychmiastowe określenie.</span><span class="sxs-lookup"><span data-stu-id="4eef4-122">To perform date and time arithmetic in a way that automatically applies a time zone's adjustment rules, the time zone to which any date and time value belongs must be immediately identifiable.</span></span> <span data-ttu-id="4eef4-123">Oznacza to, że datę i godzinę i jego skojarzone strefę czasową musi być ściśle powiązane.</span><span class="sxs-lookup"><span data-stu-id="4eef4-123">This means that a date and time and its associated time zone must be tightly coupled.</span></span> <span data-ttu-id="4eef4-124">Istnieje kilka sposobów, w tym celu, m.in:</span><span class="sxs-lookup"><span data-stu-id="4eef4-124">There are several ways to do this, which include the following:</span></span>

* <span data-ttu-id="4eef4-125">Załóżmy, że cały czas używane w aplikacji należących do określonej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="4eef4-125">Assume that all times used in an application belong to a particular time zone.</span></span> <span data-ttu-id="4eef4-126">Mimo że jest to stosowne, w niektórych przypadkach, to podejście zapewnia ograniczoną elastyczność i przenośność prawdopodobnie ograniczone.</span><span class="sxs-lookup"><span data-stu-id="4eef4-126">Although appropriate in some cases, this approach offers limited flexibility and possibly limited portability.</span></span>

* <span data-ttu-id="4eef4-127">Zdefiniuj typ, który jest ściśle couples daty i godziny za pomocą jego skojarzonego strefy czasowej, umieszczając zarówno jako pola tego typu.</span><span class="sxs-lookup"><span data-stu-id="4eef4-127">Define a type that tightly couples a date and time with its associated time zone by including both as fields of the type.</span></span> <span data-ttu-id="4eef4-128">Ta metoda jest używana w przykładzie kodu, który definiuje strukturę do przechowywania datę i godzinę i strefę czasową w dwóch pól członka.</span><span class="sxs-lookup"><span data-stu-id="4eef4-128">This approach is used in the code example, which defines a structure to store the date and time and the time zone in two member fields.</span></span>

<span data-ttu-id="4eef4-129">W przykładzie pokazano, jak wykonywać operacje arytmetyczne na <xref:System.DateTime> wartości, tak aby reguł dopasowania stref czasowych są stosowane do wyniku.</span><span class="sxs-lookup"><span data-stu-id="4eef4-129">The example illustrates how to perform arithmetic operations on <xref:System.DateTime> values so that time zone adjustment rules are applied to the result.</span></span> <span data-ttu-id="4eef4-130">Jednak <xref:System.DateTimeOffset> równie łatwo można używać wartości.</span><span class="sxs-lookup"><span data-stu-id="4eef4-130">However, <xref:System.DateTimeOffset> values can be used just as easily.</span></span> <span data-ttu-id="4eef4-131">W poniższym przykładzie pokazano, jak kod w przykładzie, oryginalnym musi być dostosowane do użytku <xref:System.DateTimeOffset> zamiast <xref:System.DateTime> wartości.</span><span class="sxs-lookup"><span data-stu-id="4eef4-131">The following example illustrates how the code in the original example might be adapted to use <xref:System.DateTimeOffset> instead of <xref:System.DateTime> values.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

<span data-ttu-id="4eef4-132">Należy pamiętać, że jeśli to dodawanie po prostu jest wykonywana na <xref:System.DateTimeOffset> wartości bez najpierw podczas konwertowania go na czas UTC, wynik odzwierciedla prawidłowe punktu w czasie, ale przesunięcie nie odzwierciedla z wyznaczonym strefę czasową dla wybranego okresu.</span><span class="sxs-lookup"><span data-stu-id="4eef4-132">Note that if this addition is simply performed on the <xref:System.DateTimeOffset> value without first converting it to UTC, the result reflects the correct point in time but its offset does not reflect that of the designated time zone for that time.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="4eef4-133">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4eef4-133">Compiling the code</span></span>

<span data-ttu-id="4eef4-134">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="4eef4-134">This example requires:</span></span>

* <span data-ttu-id="4eef4-135">Odwołania do System.Core.dll dodania do projektu.</span><span class="sxs-lookup"><span data-stu-id="4eef4-135">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="4eef4-136">Czy <xref:System> zaimportowane wraz z przestrzeni nazw `using` — instrukcja (wymagane w kodzie języka C#).</span><span class="sxs-lookup"><span data-stu-id="4eef4-136">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="4eef4-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4eef4-137">See also</span></span>

* [<span data-ttu-id="4eef4-138">Daty, godziny i strefy czasowe</span><span class="sxs-lookup"><span data-stu-id="4eef4-138">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
* [<span data-ttu-id="4eef4-139">Wykonywanie operacji arytmetycznych na wartościach dat i godzin</span><span class="sxs-lookup"><span data-stu-id="4eef4-139">Performing arithmetic operations with dates and times</span></span>](../../../docs/standard/datetime/performing-arithmetic-operations.md)
