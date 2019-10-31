---
title: 'Porady: obustronna konwersja wartości daty i godziny'
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
ms.openlocfilehash: 2e3a58ffe8332e0afec62461f6897d673e1da09f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132007"
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="c56a7-102">Porady: obustronna konwersja wartości daty i godziny</span><span class="sxs-lookup"><span data-stu-id="c56a7-102">How to: Round-trip Date and Time Values</span></span>

<span data-ttu-id="c56a7-103">W wielu aplikacjach wartość daty i godziny jest przeznaczona do jednoznacznego identyfikowania pojedynczego punktu w czasie.</span><span class="sxs-lookup"><span data-stu-id="c56a7-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="c56a7-104">W tym temacie przedstawiono sposób zapisywania i przywracania wartości <xref:System.DateTime>, wartości <xref:System.DateTimeOffset> oraz wartości daty i godziny z informacjami o strefie czasowej, tak aby przywrócona wartość wskazywała ten sam czas co zapisana wartość.</span><span class="sxs-lookup"><span data-stu-id="c56a7-104">This topic shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>

### <a name="to-round-trip-a-datetime-value"></a><span data-ttu-id="c56a7-105">Aby obustronnie konwertować wartość daty/czasu</span><span class="sxs-lookup"><span data-stu-id="c56a7-105">To round-trip a DateTime value</span></span>

1. <span data-ttu-id="c56a7-106">Przekonwertuj wartość <xref:System.DateTime> na jej reprezentację ciągu, wywołując metodę <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> przy użyciu specyfikatora formatu "o".</span><span class="sxs-lookup"><span data-stu-id="c56a7-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="c56a7-107">Zapisz ciąg reprezentujący wartość <xref:System.DateTime> w pliku lub Przekaż go przez proces, domenę aplikacji lub granicę komputera.</span><span class="sxs-lookup"><span data-stu-id="c56a7-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="c56a7-108">Pobierz ciąg, który reprezentuje wartość <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="c56a7-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>

4. <span data-ttu-id="c56a7-109">Wywołaj metodę <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> i przekaż <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako wartość parametru `styles`.</span><span class="sxs-lookup"><span data-stu-id="c56a7-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="c56a7-110">Poniższy przykład ilustruje sposób rundy wartości <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="c56a7-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

<span data-ttu-id="c56a7-111">W przypadku dwukrotnego wyzwolenia wartości <xref:System.DateTime> ta technika pomyślnie zachowuje czas dla wszystkich lokalnych i uniwersalnych czasów.</span><span class="sxs-lookup"><span data-stu-id="c56a7-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="c56a7-112">Jeśli na przykład lokalna wartość <xref:System.DateTime> jest zapisywana w systemie w strefie czasowej USA w Stanach Zjednoczonych i zostanie przywrócona w systemie w strefie czasowej w Stanach Zjednoczonych (w warstwie Standardowa), przywrócona Data i godzina będą dwie godziny późniejsze od oryginalnego czasu , co odzwierciedla różnicę czasu między dwiema strefami czasowymi.</span><span class="sxs-lookup"><span data-stu-id="c56a7-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="c56a7-113">Jednakże ta technika nie musi być dokładna dla nieokreślonych godzin.</span><span class="sxs-lookup"><span data-stu-id="c56a7-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="c56a7-114">Wszystkie wartości <xref:System.DateTime>, których właściwość <xref:System.DateTime.Kind%2A> jest <xref:System.DateTimeKind.Unspecified>, są traktowane tak, jakby były czasami lokalnymi.</span><span class="sxs-lookup"><span data-stu-id="c56a7-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="c56a7-115">W takim przypadku <xref:System.DateTime> nie będzie pomyślnie identyfikować poprawnego punktu w czasie.</span><span class="sxs-lookup"><span data-stu-id="c56a7-115">If this is not the case, the <xref:System.DateTime> will not successfully identify the correct point in time.</span></span> <span data-ttu-id="c56a7-116">Obejście tego ograniczenia polega na ścisłym połączeniu wartości daty i godziny ze strefą czasową operacji zapisywania i przywracania.</span><span class="sxs-lookup"><span data-stu-id="c56a7-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>

### <a name="to-round-trip-a-datetimeoffset-value"></a><span data-ttu-id="c56a7-117">Aby obustronnie konwertować wartość przesunięcia daty/czasu</span><span class="sxs-lookup"><span data-stu-id="c56a7-117">To round-trip a DateTimeOffset value</span></span>

1. <span data-ttu-id="c56a7-118">Przekonwertuj wartość <xref:System.DateTimeOffset> na jej reprezentację ciągu, wywołując metodę <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> przy użyciu specyfikatora formatu "o".</span><span class="sxs-lookup"><span data-stu-id="c56a7-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="c56a7-119">Zapisz ciąg reprezentujący wartość <xref:System.DateTimeOffset> w pliku lub Przekaż go przez proces, domenę aplikacji lub granicę komputera.</span><span class="sxs-lookup"><span data-stu-id="c56a7-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="c56a7-120">Pobierz ciąg, który reprezentuje wartość <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="c56a7-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>

4. <span data-ttu-id="c56a7-121">Wywołaj metodę <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> i przekaż <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako wartość parametru `styles`.</span><span class="sxs-lookup"><span data-stu-id="c56a7-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="c56a7-122">Poniższy przykład ilustruje sposób rundy wartości <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="c56a7-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

<span data-ttu-id="c56a7-123">Ta technika zawsze jednoznacznie identyfikuje wartość <xref:System.DateTimeOffset> jako pojedynczy punkt w czasie.</span><span class="sxs-lookup"><span data-stu-id="c56a7-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="c56a7-124">Wartość można następnie przekonwertować na uniwersalny czas koordynowany (UTC), wywołując metodę <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> lub można ją przekonwertować na czas w określonej strefie czasowej, wywołując metodę <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> lub <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c56a7-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c56a7-125">Głównym ograniczeniem tej metody jest to, że data i czas arytmetyczny, gdy jest wykonywane na wartości <xref:System.DateTimeOffset>, która reprezentuje czas w określonej strefie czasowej, może nie generować dokładnych wyników dla tej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="c56a7-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="c56a7-126">Wynika to z faktu, że w przypadku wystąpienia wartości <xref:System.DateTimeOffset> zostanie ona nieskojarzona ze strefą czasową.</span><span class="sxs-lookup"><span data-stu-id="c56a7-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="c56a7-127">W związku z tym reguły dostosowania strefy czasowej nie mogą być stosowane podczas obliczeń daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="c56a7-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="c56a7-128">Ten problem można obejść, definiując typ niestandardowy, który zawiera zarówno wartość daty, jak i godzinę oraz towarzyszącą strefę czasową.</span><span class="sxs-lookup"><span data-stu-id="c56a7-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>

### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="c56a7-129">Aby obustronnie konwertować wartość daty i czasu z ich strefą czasu</span><span class="sxs-lookup"><span data-stu-id="c56a7-129">To round-trip a date and time value with its time zone</span></span>

1. <span data-ttu-id="c56a7-130">Zdefiniuj klasę lub strukturę z dwoma polami.</span><span class="sxs-lookup"><span data-stu-id="c56a7-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="c56a7-131">Pierwsze pole jest obiektem <xref:System.DateTime> lub <xref:System.DateTimeOffset>, a drugi jest obiektem <xref:System.TimeZoneInfo>.</span><span class="sxs-lookup"><span data-stu-id="c56a7-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="c56a7-132">Poniższy przykład jest prostą wersją tego typu.</span><span class="sxs-lookup"><span data-stu-id="c56a7-132">The following example is a simple version of such a type.</span></span>

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. <span data-ttu-id="c56a7-133">Oznacz klasę atrybutem <xref:System.SerializableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c56a7-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>

3. <span data-ttu-id="c56a7-134">Serializacja obiektu za pomocą metody <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c56a7-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="c56a7-135">Przywróć obiekt za pomocą metody <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A>.</span><span class="sxs-lookup"><span data-stu-id="c56a7-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>

5. <span data-ttu-id="c56a7-136">Cast (in C#) lub Convert (w Visual Basic) obiekt deserializowany do obiektu odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="c56a7-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>

<span data-ttu-id="c56a7-137">Poniższy przykład ilustruje sposób rundy, który przechowuje informacje o dacie i godzinie oraz o strefie czasowej.</span><span class="sxs-lookup"><span data-stu-id="c56a7-137">The following example illustrates how to round-trip an object that stores both date and time and time zone information.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

<span data-ttu-id="c56a7-138">Ta technika powinna zawsze jednoznacznie odzwierciedlać prawidłowy punkt czasu przed i po jego zapisaniu i przywrócenia, pod warunkiem, że wdrożenie połączonej daty i godziny i obiektu strefy czasowej nie zezwala na synchronizację wartości daty z wartość strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="c56a7-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="c56a7-139">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c56a7-139">Compiling the Code</span></span>

<span data-ttu-id="c56a7-140">Te przykłady wymagają:</span><span class="sxs-lookup"><span data-stu-id="c56a7-140">These examples require:</span></span>

- <span data-ttu-id="c56a7-141">Następujące przestrzenie nazw można zaimportować za C# pomocą instrukcji `using` lub instrukcji Visual Basic `Imports`:</span><span class="sxs-lookup"><span data-stu-id="c56a7-141">That the following namespaces be imported with C# `using` statements or Visual Basic `Imports` statements:</span></span>

  - <span data-ttu-id="c56a7-142"><xref:System> (C# tylko).</span><span class="sxs-lookup"><span data-stu-id="c56a7-142"><xref:System> (C# only).</span></span>

  - <span data-ttu-id="c56a7-143"><xref:System.Globalization?displayProperty=nameWithType>.,</span><span class="sxs-lookup"><span data-stu-id="c56a7-143"><xref:System.Globalization?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="c56a7-144"><xref:System.IO?displayProperty=nameWithType>.,</span><span class="sxs-lookup"><span data-stu-id="c56a7-144"><xref:System.IO?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="c56a7-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.,</span><span class="sxs-lookup"><span data-stu-id="c56a7-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="c56a7-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.,</span><span class="sxs-lookup"><span data-stu-id="c56a7-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="c56a7-147">Każdy przykład kodu, inny niż Klasa `DateInTimeZone`, powinien być uwzględniony w module klasy lub Visual Basic, opakowany w metodach i wywoływany z metody `Main`.</span><span class="sxs-lookup"><span data-stu-id="c56a7-147">Each code example, other than the `DateInTimeZone` class, should be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>

## <a name="see-also"></a><span data-ttu-id="c56a7-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c56a7-148">See also</span></span>

- [<span data-ttu-id="c56a7-149">Wykonywanie operacji formatowania</span><span class="sxs-lookup"><span data-stu-id="c56a7-149">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)
- [<span data-ttu-id="c56a7-150">Wybieranie między elementami DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="c56a7-150">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../../../docs/standard/datetime/choosing-between-datetime.md)
- [<span data-ttu-id="c56a7-151">Standardowe ciągi formatujące datę i godzinę</span><span class="sxs-lookup"><span data-stu-id="c56a7-151">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
