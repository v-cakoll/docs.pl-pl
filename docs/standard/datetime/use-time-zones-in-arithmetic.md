---
title: 'Instrukcje: Używanie stref czasowych w arytmetyce wartości daty i godziny'
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
ms.openlocfilehash: 417d8f00c9323f096a2d6228e853a55b1573f48c
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106713"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a><span data-ttu-id="c66a3-102">Instrukcje: Używanie stref czasowych w arytmetyce wartości daty i godziny</span><span class="sxs-lookup"><span data-stu-id="c66a3-102">How to: Use time zones in date and time arithmetic</span></span>

<span data-ttu-id="c66a3-103">Zwykle podczas wykonywania obliczeń daty i godziny przy użyciu <xref:System.DateTime> lub <xref:System.DateTimeOffset> wartości, wynik nie uwzględnia żadnych reguł korekty strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="c66a3-103">Ordinarily, when you perform date and time arithmetic using <xref:System.DateTime> or <xref:System.DateTimeOffset> values, the result does not reflect any time zone adjustment rules.</span></span> <span data-ttu-id="c66a3-104">Jest to prawdziwe, nawet gdy strefa czasowa wartości daty i godziny jest jasno zidentyfikowana (na przykład gdy <xref:System.DateTime.Kind%2A> właściwość jest ustawiona na <xref:System.DateTimeKind.Local>).</span><span class="sxs-lookup"><span data-stu-id="c66a3-104">This is true even when the time zone of the date and time value is clearly identifiable (for example, when the <xref:System.DateTime.Kind%2A> property is set to <xref:System.DateTimeKind.Local>).</span></span> <span data-ttu-id="c66a3-105">W tym temacie przedstawiono sposób wykonywania operacji arytmetycznych na wartościach daty i godziny, które należą do określonej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="c66a3-105">This topic shows how to perform arithmetic operations on date and time values that belong to a particular time zone.</span></span> <span data-ttu-id="c66a3-106">Wyniki operacji arytmetycznych odzwierciedlają reguły dostosowania strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="c66a3-106">The results of the arithmetic operations will reflect the time zone's adjustment rules.</span></span>

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a><span data-ttu-id="c66a3-107">Aby zastosować reguły dostosowania do operacji arytmetycznych daty i godziny</span><span class="sxs-lookup"><span data-stu-id="c66a3-107">To apply adjustment rules to date and time arithmetic</span></span>

1. <span data-ttu-id="c66a3-108">Zaimplementuj pewną metodę ścisłego sprzęgania wartości daty i godziny ze strefą czasową, do której należy.</span><span class="sxs-lookup"><span data-stu-id="c66a3-108">Implement some method of closely coupling a date and time value with the time zone to which it belongs.</span></span> <span data-ttu-id="c66a3-109">Na przykład Zadeklaruj strukturę, która zawiera zarówno wartość daty, jak i jej strefę czasową.</span><span class="sxs-lookup"><span data-stu-id="c66a3-109">For example, declare a structure that includes both the date and time value and its time zone.</span></span> <span data-ttu-id="c66a3-110">Poniższy przykład używa tego podejścia do łączenia <xref:System.DateTime> wartości ze strefą czasową.</span><span class="sxs-lookup"><span data-stu-id="c66a3-110">The following example uses this approach to link a <xref:System.DateTime> value with its time zone.</span></span>

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. <span data-ttu-id="c66a3-111">Przekształć czas na uniwersalny czas koordynowany (UTC), wywołując <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> metodę <xref:System.TimeZoneInfo.ConvertTime%2A> lub metodę.</span><span class="sxs-lookup"><span data-stu-id="c66a3-111">Convert a time to Coordinated Universal Time (UTC) by calling either the <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> method or the <xref:System.TimeZoneInfo.ConvertTime%2A> method.</span></span>

3. <span data-ttu-id="c66a3-112">Wykonaj operację arytmetyczną na czas UTC.</span><span class="sxs-lookup"><span data-stu-id="c66a3-112">Perform the arithmetic operation on the UTC time.</span></span>

4. <span data-ttu-id="c66a3-113">Przekonwertuj godzinę z czasu UTC na oryginalną strefę czasową skojarzoną z <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> czasem, wywołując metodę.</span><span class="sxs-lookup"><span data-stu-id="c66a3-113">Convert the time from UTC to the original time's associated time zone by calling the <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span>

## <a name="example"></a><span data-ttu-id="c66a3-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="c66a3-114">Example</span></span>

<span data-ttu-id="c66a3-115">Poniższy przykład dodaje dwie godziny i 30 minut do 9 marca 2008, o godz. 1:30 rano</span><span class="sxs-lookup"><span data-stu-id="c66a3-115">The following example adds two hours and thirty minutes to March 9, 2008, at 1:30 A.M.</span></span> <span data-ttu-id="c66a3-116">Środkowy czas standardowy.</span><span class="sxs-lookup"><span data-stu-id="c66a3-116">Central Standard Time.</span></span> <span data-ttu-id="c66a3-117">Przejście strefy czasowej do czasu letniego występuje 30 minut później, o godzinie 2:00</span><span class="sxs-lookup"><span data-stu-id="c66a3-117">The time zone's transition to daylight saving time occurs thirty minutes later, at 2:00 A.M.</span></span> <span data-ttu-id="c66a3-118">9 marca 2008.</span><span class="sxs-lookup"><span data-stu-id="c66a3-118">on March 9, 2008.</span></span> <span data-ttu-id="c66a3-119">Ponieważ przykład jest zgodny z czterema krokami wymienionymi w poprzedniej sekcji, prawidłowo raportuje otrzymany czas jako 5:00 rano</span><span class="sxs-lookup"><span data-stu-id="c66a3-119">Because the example follows the four steps listed in the previous section, it correctly reports the resulting time as 5:00 A.M.</span></span> <span data-ttu-id="c66a3-120">9 marca 2008.</span><span class="sxs-lookup"><span data-stu-id="c66a3-120">on March 9, 2008.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

<span data-ttu-id="c66a3-121">Oba <xref:System.DateTime> i<xref:System.DateTimeOffset> wartości są nieskojarzone ze strefą czasową, do której mogą się one znajdować.</span><span class="sxs-lookup"><span data-stu-id="c66a3-121">Both <xref:System.DateTime> and <xref:System.DateTimeOffset> values are disassociated from any time zone to which they might belong.</span></span> <span data-ttu-id="c66a3-122">Aby wykonać operacje arytmetyczne daty i godziny w sposób, który automatycznie stosuje reguły dostosowania strefy czasowej, strefa czasowa, do której należy każda wartość daty i godziny musi być od razu możliwa do zidentyfikowania.</span><span class="sxs-lookup"><span data-stu-id="c66a3-122">To perform date and time arithmetic in a way that automatically applies a time zone's adjustment rules, the time zone to which any date and time value belongs must be immediately identifiable.</span></span> <span data-ttu-id="c66a3-123">Oznacza to, że data i godzina oraz skojarzona ze strefą czasową muszą być ściśle sprzężone.</span><span class="sxs-lookup"><span data-stu-id="c66a3-123">This means that a date and time and its associated time zone must be tightly coupled.</span></span> <span data-ttu-id="c66a3-124">Można to zrobić na kilka sposobów:</span><span class="sxs-lookup"><span data-stu-id="c66a3-124">There are several ways to do this, which include the following:</span></span>

- <span data-ttu-id="c66a3-125">Załóżmy, że wszystkie godziny używane w aplikacji należą do określonej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="c66a3-125">Assume that all times used in an application belong to a particular time zone.</span></span> <span data-ttu-id="c66a3-126">Chociaż jest to odpowiednie w niektórych przypadkach, ta metoda oferuje ograniczoną elastyczność i prawdopodobnie ograniczoną przenośność.</span><span class="sxs-lookup"><span data-stu-id="c66a3-126">Although appropriate in some cases, this approach offers limited flexibility and possibly limited portability.</span></span>

- <span data-ttu-id="c66a3-127">Zdefiniuj typ, który ściśle Couples datę i godzinę ze skojarzoną strefą czasową przez uwzględnienie obu pól jako pola typu.</span><span class="sxs-lookup"><span data-stu-id="c66a3-127">Define a type that tightly couples a date and time with its associated time zone by including both as fields of the type.</span></span> <span data-ttu-id="c66a3-128">To podejście jest używane w przykładowym kodzie, który definiuje strukturę do przechowywania daty i godziny i strefy czasowej w dwóch polach elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="c66a3-128">This approach is used in the code example, which defines a structure to store the date and time and the time zone in two member fields.</span></span>

<span data-ttu-id="c66a3-129">Przykład ilustruje sposób wykonywania operacji arytmetycznych na <xref:System.DateTime> wartościach, dzięki czemu do wyniku są stosowane reguły dopasowywania strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="c66a3-129">The example illustrates how to perform arithmetic operations on <xref:System.DateTime> values so that time zone adjustment rules are applied to the result.</span></span> <span data-ttu-id="c66a3-130"><xref:System.DateTimeOffset> Jednak wartości mogą być używane równie łatwo.</span><span class="sxs-lookup"><span data-stu-id="c66a3-130">However, <xref:System.DateTimeOffset> values can be used just as easily.</span></span> <span data-ttu-id="c66a3-131">Poniższy przykład ilustruje, jak kod w oryginalnym przykładzie może zostać dostosowany do użycia <xref:System.DateTimeOffset> <xref:System.DateTime> zamiast wartości.</span><span class="sxs-lookup"><span data-stu-id="c66a3-131">The following example illustrates how the code in the original example might be adapted to use <xref:System.DateTimeOffset> instead of <xref:System.DateTime> values.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

<span data-ttu-id="c66a3-132">Należy pamiętać, że jeśli ten dodatkowy element jest po <xref:System.DateTimeOffset> prostu wykonywany na wartości bez wcześniejszego przekonwertowania na czas UTC, wynik odzwierciedla prawidłowy punkt w czasie, ale jego przesunięcie nie odzwierciedla tego, czy określona strefa czasowa jest w tym czasie.</span><span class="sxs-lookup"><span data-stu-id="c66a3-132">Note that if this addition is simply performed on the <xref:System.DateTimeOffset> value without first converting it to UTC, the result reflects the correct point in time but its offset does not reflect that of the designated time zone for that time.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="c66a3-133">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c66a3-133">Compiling the code</span></span>

<span data-ttu-id="c66a3-134">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="c66a3-134">This example requires:</span></span>

- <span data-ttu-id="c66a3-135">Że przestrzeń nazw ma zostać zaimportowana `using` przy użyciu instrukcji C# (wymaganej w kodzie). <xref:System></span><span class="sxs-lookup"><span data-stu-id="c66a3-135">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="c66a3-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c66a3-136">See also</span></span>

- [<span data-ttu-id="c66a3-137">Daty, godziny i strefy czasowe</span><span class="sxs-lookup"><span data-stu-id="c66a3-137">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="c66a3-138">Wykonywanie operacji arytmetycznych na wartościach dat i godzin</span><span class="sxs-lookup"><span data-stu-id="c66a3-138">Performing arithmetic operations with dates and times</span></span>](../../../docs/standard/datetime/performing-arithmetic-operations.md)
