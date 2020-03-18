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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73132007"
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="1facd-102">Porady: obustronna konwersja wartości daty i godziny</span><span class="sxs-lookup"><span data-stu-id="1facd-102">How to: Round-trip Date and Time Values</span></span>

<span data-ttu-id="1facd-103">W wielu aplikacjach wartość daty i godziny ma na celu jednoznaczne zidentyfikowanie pojedynczego punktu w czasie.</span><span class="sxs-lookup"><span data-stu-id="1facd-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="1facd-104">W tym temacie pokazano, <xref:System.DateTime> jak <xref:System.DateTimeOffset> zapisać i przywrócić wartość, wartość i wartość daty i godziny z informacjami o strefie czasowej, dzięki czemu przywrócona wartość identyfikuje ten sam czas co zapisana wartość.</span><span class="sxs-lookup"><span data-stu-id="1facd-104">This topic shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>

### <a name="to-round-trip-a-datetime-value"></a><span data-ttu-id="1facd-105">Aby obustronnie konwertować wartość daty/czasu</span><span class="sxs-lookup"><span data-stu-id="1facd-105">To round-trip a DateTime value</span></span>

1. <span data-ttu-id="1facd-106">Konwertuj wartość na <xref:System.DateTime> <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> jego reprezentację ciągu, wywołując metodę z specyfikatorem formatu "o".</span><span class="sxs-lookup"><span data-stu-id="1facd-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="1facd-107">Zapisz reprezentację ciągu <xref:System.DateTime> wartości do pliku lub przekaż ją przez granicę procesu, domeny aplikacji lub komputera.</span><span class="sxs-lookup"><span data-stu-id="1facd-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="1facd-108">Pobierz ciąg reprezentujący <xref:System.DateTime> wartość.</span><span class="sxs-lookup"><span data-stu-id="1facd-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>

4. <span data-ttu-id="1facd-109">Wywołać <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metodę i <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> przekazać jako `styles` wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="1facd-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="1facd-110">W poniższym przykładzie przedstawiono sposób <xref:System.DateTime> w obie strony wartości.</span><span class="sxs-lookup"><span data-stu-id="1facd-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

<span data-ttu-id="1facd-111">Podczas rundy potknięcia <xref:System.DateTime> wartości, ta technika z powodzeniem zachowuje czas dla wszystkich lokalnych i uniwersalnych czasów.</span><span class="sxs-lookup"><span data-stu-id="1facd-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="1facd-112">Jeśli na przykład <xref:System.DateTime> wartość lokalna zostanie zapisana w systemie w standardowej strefie czasowej Stany Zjednoczonego Pacyfiku i zostanie przywrócona w systemie w strefie czasowej standardu centralnego usa, przywrócona data i godzina będą dwie godziny później spożące niż czas pierwotny, który odzwierciedla różnicę czasu między dwiema strefami czasowymi.</span><span class="sxs-lookup"><span data-stu-id="1facd-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="1facd-113">Jednak ta technika nie musi być dokładna dla nieokreślonych czasów.</span><span class="sxs-lookup"><span data-stu-id="1facd-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="1facd-114">Wszystkie <xref:System.DateTime> wartości, <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Unspecified> których właściwość jest traktowana tak, jakby były czasami lokalnymi.</span><span class="sxs-lookup"><span data-stu-id="1facd-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="1facd-115">Jeśli tak nie jest, <xref:System.DateTime> nie zidentyfikuje pomyślnie prawidłowego punktu w czasie.</span><span class="sxs-lookup"><span data-stu-id="1facd-115">If this is not the case, the <xref:System.DateTime> will not successfully identify the correct point in time.</span></span> <span data-ttu-id="1facd-116">Obejściem tego ograniczenia jest ścisłe sparowanie wartości daty i godziny ze strefą czasową dla operacji zapisywania i przywracania.</span><span class="sxs-lookup"><span data-stu-id="1facd-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>

### <a name="to-round-trip-a-datetimeoffset-value"></a><span data-ttu-id="1facd-117">Aby obustronnie konwertować wartość przesunięcia daty/czasu</span><span class="sxs-lookup"><span data-stu-id="1facd-117">To round-trip a DateTimeOffset value</span></span>

1. <span data-ttu-id="1facd-118">Konwertuj wartość na <xref:System.DateTimeOffset> <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> jego reprezentację ciągu, wywołując metodę z specyfikatorem formatu "o".</span><span class="sxs-lookup"><span data-stu-id="1facd-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="1facd-119">Zapisz reprezentację ciągu <xref:System.DateTimeOffset> wartości do pliku lub przekaż ją przez granicę procesu, domeny aplikacji lub komputera.</span><span class="sxs-lookup"><span data-stu-id="1facd-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="1facd-120">Pobierz ciąg reprezentujący <xref:System.DateTimeOffset> wartość.</span><span class="sxs-lookup"><span data-stu-id="1facd-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>

4. <span data-ttu-id="1facd-121">Wywołać <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metodę i <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> przekazać jako `styles` wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="1facd-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="1facd-122">W poniższym przykładzie przedstawiono sposób <xref:System.DateTimeOffset> w obie strony wartości.</span><span class="sxs-lookup"><span data-stu-id="1facd-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

<span data-ttu-id="1facd-123">Ta technika zawsze jednoznacznie <xref:System.DateTimeOffset> identyfikuje wartość jako pojedynczy punkt w czasie.</span><span class="sxs-lookup"><span data-stu-id="1facd-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="1facd-124">Wartość można następnie przekonwertować na skoordynowany czas <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> uniwersalny (UTC) przez wywołanie metody lub można ją <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> przekonwertować na czas w określonej strefie czasowej, wywołując lub metody.</span><span class="sxs-lookup"><span data-stu-id="1facd-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1facd-125">Głównym ograniczeniem tej techniki jest to, że data i godzina arytmetyka, gdy wykonywane na <xref:System.DateTimeOffset> wartość, która reprezentuje czas w określonej strefie czasowej, może nie dawać dokładne wyniki dla tej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="1facd-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="1facd-126">Dzieje się tak, ponieważ gdy <xref:System.DateTimeOffset> wartość jest tworzone, jest odłączony od jego strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="1facd-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="1facd-127">W związku z tym reguły korekty tej strefy czasowej nie mogą być już stosowane podczas wykonywania obliczeń daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="1facd-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="1facd-128">Można obejść ten problem, definiując typ niestandardowy, który zawiera zarówno wartość daty i godziny, jak i towarzyszącą jej strefę czasową.</span><span class="sxs-lookup"><span data-stu-id="1facd-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>

### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="1facd-129">Aby obustronnie konwertować wartość daty i czasu z ich strefą czasu</span><span class="sxs-lookup"><span data-stu-id="1facd-129">To round-trip a date and time value with its time zone</span></span>

1. <span data-ttu-id="1facd-130">Zdefiniuj klasę lub strukturę z dwoma polami.</span><span class="sxs-lookup"><span data-stu-id="1facd-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="1facd-131">Pierwsze pole to <xref:System.DateTime> <xref:System.DateTimeOffset> obiekt lub obiekt, a <xref:System.TimeZoneInfo> drugie jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="1facd-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="1facd-132">Poniższy przykład jest prostą wersją takiego typu.</span><span class="sxs-lookup"><span data-stu-id="1facd-132">The following example is a simple version of such a type.</span></span>

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. <span data-ttu-id="1facd-133">Oznacz klasę <xref:System.SerializableAttribute> atrybutem.</span><span class="sxs-lookup"><span data-stu-id="1facd-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>

3. <span data-ttu-id="1facd-134">Serializowania obiektu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="1facd-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="1facd-135">Przywróć obiekt <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> za pomocą metody.</span><span class="sxs-lookup"><span data-stu-id="1facd-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>

5. <span data-ttu-id="1facd-136">Rzutować (w języku C#) lub konwertować (w języku Visual Basic) obiekt zdeserializowany do obiektu odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="1facd-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>

<span data-ttu-id="1facd-137">W poniższym przykładzie pokazano, jak w obie strony obiektu, który przechowuje zarówno daty i godziny i informacji o strefie czasowej.</span><span class="sxs-lookup"><span data-stu-id="1facd-137">The following example illustrates how to round-trip an object that stores both date and time and time zone information.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

<span data-ttu-id="1facd-138">Technika ta powinna zawsze jednoznacznie odzwierciedlać prawidłowy punkt czasu zarówno przed, jak i po jego zapisaniu i przywróceniu, pod warunkiem, że implementacja połączonego obiektu daty i godziny oraz strefy czasowej nie pozwala, aby wartość daty nie była zsynchronizowana z obiektem wartości strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="1facd-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="1facd-139">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1facd-139">Compiling the Code</span></span>

<span data-ttu-id="1facd-140">Poteki wymagają:</span><span class="sxs-lookup"><span data-stu-id="1facd-140">These examples require:</span></span>

- <span data-ttu-id="1facd-141">Zaimportowanie następujących obszarów nazw `using` z instrukcjami Języka C# lub instrukcjami języka Visual Basic: `Imports`</span><span class="sxs-lookup"><span data-stu-id="1facd-141">That the following namespaces be imported with C# `using` statements or Visual Basic `Imports` statements:</span></span>

  - <span data-ttu-id="1facd-142"><xref:System>(tylko C#).</span><span class="sxs-lookup"><span data-stu-id="1facd-142"><xref:System> (C# only).</span></span>

  - <span data-ttu-id="1facd-143"><xref:System.Globalization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1facd-143"><xref:System.Globalization?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="1facd-144"><xref:System.IO?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1facd-144"><xref:System.IO?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="1facd-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1facd-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="1facd-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1facd-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="1facd-147">Każdy przykład kodu, `DateInTimeZone` inne niż klasa, powinny być zawarte w klasie lub Visual Basic `Main` moduł, opakowane w metody i wywoływane z metody.</span><span class="sxs-lookup"><span data-stu-id="1facd-147">Each code example, other than the `DateInTimeZone` class, should be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>

## <a name="see-also"></a><span data-ttu-id="1facd-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1facd-148">See also</span></span>

- [<span data-ttu-id="1facd-149">Wykonywanie operacji formatowania</span><span class="sxs-lookup"><span data-stu-id="1facd-149">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)
- [<span data-ttu-id="1facd-150">Wybieranie między datetime, DateTimeOffset, TimeSpan i TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="1facd-150">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../../../docs/standard/datetime/choosing-between-datetime.md)
- [<span data-ttu-id="1facd-151">Standardowe ciągi formatujące datę i godzinę</span><span class="sxs-lookup"><span data-stu-id="1facd-151">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
