---
title: 'Instrukcje: Obustronne wartości daty i godziny'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- round-trip date and time values
- dates [.NET Framework], round-trip values
- time zones [.NET Framework], round-trip date and time values
- time [.NET Framework], round-trip values
- formatting strings [.NET Framework], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
ms.openlocfilehash: 60483a6e29c65fc0c5803e8084053d53d9fc3c37
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290451"
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="06535-102">Instrukcje: Obustronne wartości daty i godziny</span><span class="sxs-lookup"><span data-stu-id="06535-102">How to: Round-trip Date and Time Values</span></span>

<span data-ttu-id="06535-103">W wielu aplikacjach wartość daty i godziny jest przeznaczona do jednoznacznego identyfikowania pojedynczego punktu w czasie.</span><span class="sxs-lookup"><span data-stu-id="06535-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="06535-104">W tym artykule przedstawiono sposób zapisywania i przywracania <xref:System.DateTime> wartości, <xref:System.DateTimeOffset> wartości oraz wartości daty i godziny z informacjami o strefie czasowej, tak aby przywrócona wartość wskazywała ten sam czas co zapisana wartość.</span><span class="sxs-lookup"><span data-stu-id="06535-104">This article shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>

## <a name="round-trip-a-datetime-value"></a><span data-ttu-id="06535-105">Runda wartość daty i godziny</span><span class="sxs-lookup"><span data-stu-id="06535-105">Round-trip a DateTime value</span></span>

1. <span data-ttu-id="06535-106">Przekonwertuj <xref:System.DateTime> wartość na jej reprezentację w postaci ciągu, wywołując <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metodę ze specyfikatorem formatu "o".</span><span class="sxs-lookup"><span data-stu-id="06535-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="06535-107">Zapisz ciąg reprezentujący <xref:System.DateTime> wartość do pliku lub Przekaż go przez proces, domenę aplikacji lub granicę komputera.</span><span class="sxs-lookup"><span data-stu-id="06535-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="06535-108">Pobierz ciąg, który reprezentuje <xref:System.DateTime> wartość.</span><span class="sxs-lookup"><span data-stu-id="06535-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>

4. <span data-ttu-id="06535-109">Wywołaj <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metodę i przekaż <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako wartość `styles` parametru.</span><span class="sxs-lookup"><span data-stu-id="06535-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="06535-110">Poniższy przykład ilustruje sposób rundy <xref:System.DateTime> wartości.</span><span class="sxs-lookup"><span data-stu-id="06535-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

<span data-ttu-id="06535-111">W przypadku rundy <xref:System.DateTime> wartości, ta technika pomyślnie zachowuje czas dla wszystkich lokalnych i uniwersalnych czasów.</span><span class="sxs-lookup"><span data-stu-id="06535-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="06535-112">Jeśli na przykład lokalna <xref:System.DateTime> wartość jest zapisywana w systemie w strefie czasowej USA w Stanach Zjednoczonych i przywrócona w systemie w strefie czasowej w Stanach Zjednoczonych (USA), przywrócona Data i godzina będą miały dwie godziny późniejsze niż pierwotny czas, który odzwierciedla różnicę czasu między dwiema strefami czasowymi.</span><span class="sxs-lookup"><span data-stu-id="06535-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="06535-113">Jednakże ta technika nie musi być dokładna dla nieokreślonych godzin.</span><span class="sxs-lookup"><span data-stu-id="06535-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="06535-114">Wszystkie <xref:System.DateTime> wartości <xref:System.DateTime.Kind%2A> , których właściwość jest <xref:System.DateTimeKind.Unspecified> traktowana jako czas lokalny.</span><span class="sxs-lookup"><span data-stu-id="06535-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="06535-115">Jeśli nie jest to czas lokalny, <xref:System.DateTime> nie zidentyfikuje prawidłowo punktu w czasie.</span><span class="sxs-lookup"><span data-stu-id="06535-115">If it's not a local time, the <xref:System.DateTime> doesn't successfully identify the correct point in time.</span></span> <span data-ttu-id="06535-116">Obejście tego ograniczenia polega na ścisłym połączeniu wartości daty i godziny ze strefą czasową operacji zapisywania i przywracania.</span><span class="sxs-lookup"><span data-stu-id="06535-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>

## <a name="round-trip-a-datetimeoffset-value"></a><span data-ttu-id="06535-117">Przerundy wartość DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="06535-117">Round-trip a DateTimeOffset value</span></span>

1. <span data-ttu-id="06535-118">Przekonwertuj <xref:System.DateTimeOffset> wartość na jej reprezentację w postaci ciągu, wywołując <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metodę ze specyfikatorem formatu "o".</span><span class="sxs-lookup"><span data-stu-id="06535-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="06535-119">Zapisz ciąg reprezentujący <xref:System.DateTimeOffset> wartość do pliku lub Przekaż go przez proces, domenę aplikacji lub granicę komputera.</span><span class="sxs-lookup"><span data-stu-id="06535-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="06535-120">Pobierz ciąg, który reprezentuje <xref:System.DateTimeOffset> wartość.</span><span class="sxs-lookup"><span data-stu-id="06535-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>

4. <span data-ttu-id="06535-121">Wywołaj <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metodę i przekaż <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako wartość `styles` parametru.</span><span class="sxs-lookup"><span data-stu-id="06535-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="06535-122">Poniższy przykład ilustruje sposób rundy <xref:System.DateTimeOffset> wartości.</span><span class="sxs-lookup"><span data-stu-id="06535-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

<span data-ttu-id="06535-123">Ta technika zawsze jednoznacznie identyfikuje <xref:System.DateTimeOffset> wartość jako pojedynczy punkt w czasie.</span><span class="sxs-lookup"><span data-stu-id="06535-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="06535-124">Wartość można następnie przekonwertować na uniwersalny czas koordynowany (UTC) przez wywołanie <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metody lub można ją przekonwertować na czas w określonej strefie czasowej przez wywołanie <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metody lub.</span><span class="sxs-lookup"><span data-stu-id="06535-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="06535-125">Głównym ograniczeniem tej metody jest to, że data i czas arytmetyczny, gdy jest wykonywane na <xref:System.DateTimeOffset> wartości, która reprezentuje czas w określonej strefie czasowej, może nie generować dokładnych wyników dla tej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="06535-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="06535-126">Wynika to z faktu <xref:System.DateTimeOffset> , że w przypadku wystąpienia wartości jest ona nieskojarzona ze strefą czasową.</span><span class="sxs-lookup"><span data-stu-id="06535-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="06535-127">W związku z tym reguły dostosowania strefy czasowej nie mogą być stosowane podczas obliczeń daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="06535-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="06535-128">Ten problem można obejść, definiując typ niestandardowy, który zawiera zarówno wartość daty, jak i godzinę oraz towarzyszącą strefę czasową.</span><span class="sxs-lookup"><span data-stu-id="06535-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>

## <a name="round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="06535-129">Wartość daty i godziny w postaci dwukierunkowej dla strefy czasowej</span><span class="sxs-lookup"><span data-stu-id="06535-129">Round-trip a date and time value with its time zone</span></span>

1. <span data-ttu-id="06535-130">Zdefiniuj klasę lub strukturę z dwoma polami.</span><span class="sxs-lookup"><span data-stu-id="06535-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="06535-131">Pierwsze pole jest albo <xref:System.DateTime> <xref:System.DateTimeOffset> obiektem, a drugi jest <xref:System.TimeZoneInfo> obiektem.</span><span class="sxs-lookup"><span data-stu-id="06535-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="06535-132">Poniższy przykład jest prostą wersją tego typu.</span><span class="sxs-lookup"><span data-stu-id="06535-132">The following example is a simple version of such a type.</span></span>

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. <span data-ttu-id="06535-133">Oznacz klasę <xref:System.SerializableAttribute> atrybutem.</span><span class="sxs-lookup"><span data-stu-id="06535-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>

3. <span data-ttu-id="06535-134">Serializacja obiektu za pomocą <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="06535-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="06535-135">Przywróć obiekt za pomocą <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="06535-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>

5. <span data-ttu-id="06535-136">Cast (w języku C#) lub Convert (w Visual Basic) obiekt deserializowany do obiektu odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="06535-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>

<span data-ttu-id="06535-137">Poniższy przykład ilustruje sposób rundy, który przechowuje zarówno informacje o strefie czasowej, jak i dacie i godzinie.</span><span class="sxs-lookup"><span data-stu-id="06535-137">The following example illustrates how to round-trip an object that stores both time zone and date and time information.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

<span data-ttu-id="06535-138">Ta technika powinna zawsze jednoznacznie odzwierciedlać prawidłowy punkt czasu przed i po jego zapisaniu i przywracania, pod warunkiem, że wdrożenie połączonej daty i godziny i obiektu strefy czasowej nie zezwala na synchronizację wartości daty z wartością strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="06535-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="06535-139">Kompiluj kod</span><span class="sxs-lookup"><span data-stu-id="06535-139">Compile the code</span></span>

<span data-ttu-id="06535-140">Te przykłady wymagają:</span><span class="sxs-lookup"><span data-stu-id="06535-140">These examples require that:</span></span>

- <span data-ttu-id="06535-141">Następujące przestrzenie nazw można zaimportować przy użyciu dyrektyw języka C# `using` lub `Imports` instrukcji Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="06535-141">The following namespaces be imported with C# `using` directives or Visual Basic `Imports` statements:</span></span>

  - <span data-ttu-id="06535-142"><xref:System>(Tylko w języku C#)</span><span class="sxs-lookup"><span data-stu-id="06535-142"><xref:System> (C# only)</span></span>

  - <xref:System.Globalization?displayProperty=nameWithType>

  - <xref:System.IO?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>

- <span data-ttu-id="06535-143">Każdy przykład kodu, inny niż `DateInTimeZone` Klasa, jest uwzględniony w module klasy lub Visual Basic, opakowany w metodach i wywoływany z `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="06535-143">Each code example, other than the `DateInTimeZone` class, be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>

## <a name="see-also"></a><span data-ttu-id="06535-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06535-144">See also</span></span>

- [<span data-ttu-id="06535-145">Wybieranie między elementami DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="06535-145">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../datetime/choosing-between-datetime.md)
- [<span data-ttu-id="06535-146">Standardowe ciągi formatujące datę i godzinę</span><span class="sxs-lookup"><span data-stu-id="06535-146">Standard Date and Time Format Strings</span></span>](standard-date-and-time-format-strings.md)
