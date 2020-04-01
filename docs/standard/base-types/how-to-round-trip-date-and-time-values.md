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
ms.openlocfilehash: 4fc38b6b852f8a7b8f268fd9e8624bdf350744c8
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523817"
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="7b0bc-102">Instrukcje: Obustronne wartości daty i godziny</span><span class="sxs-lookup"><span data-stu-id="7b0bc-102">How to: Round-trip Date and Time Values</span></span>

<span data-ttu-id="7b0bc-103">W wielu aplikacjach wartość daty i godziny jest przeznaczona do jednoznacznego identyfikowania pojedynczego punktu w czasie.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="7b0bc-104">W tym temacie pokazano, <xref:System.DateTime> jak zapisać <xref:System.DateTimeOffset> i przywrócić wartość, wartość oraz wartość daty i godziny z informacjami o strefie czasowej, tak aby przywrócona wartość określała ten sam czas co zapisana wartość.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-104">This topic shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>

## <a name="round-trip-a-datetime-value"></a><span data-ttu-id="7b0bc-105">W obie strony wartość DateTime</span><span class="sxs-lookup"><span data-stu-id="7b0bc-105">Round-trip a DateTime value</span></span>

1. <span data-ttu-id="7b0bc-106">Przekonwertować <xref:System.DateTime> wartość na jego <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> reprezentację ciągu, wywołując metodę z specyfikatorem formatu "o".</span><span class="sxs-lookup"><span data-stu-id="7b0bc-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="7b0bc-107">Zapisz reprezentację ciągu <xref:System.DateTime> wartości w pliku lub przekaż ją przez obwiednię procesu, domeny aplikacji lub komputera.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="7b0bc-108">Pobierz ciąg, który <xref:System.DateTime> reprezentuje wartość.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>

4. <span data-ttu-id="7b0bc-109">Wywołaj <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metodę i <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> przekaż jako `styles` wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="7b0bc-110">Poniższy przykład ilustruje sposób <xref:System.DateTime> w obie strony wartości.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

<span data-ttu-id="7b0bc-111">Podczas zaokrąglania <xref:System.DateTime> wartości ta technika z powodzeniem zachowuje czas dla wszystkich czasów lokalnych i uniwersalnych.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="7b0bc-112">Jeśli na przykład <xref:System.DateTime> wartość lokalna jest zapisywana w systemie w standardowej strefie czasowej stanów Pacyfiku stanów Zjednoczonych i przywracana w systemie w centralnej standardowej strefie czasowej STANÓW Zjednoczonych, przywrócona data i godzina będą dwie godziny później niż pierwotny czas, co odzwierciedla różnicę czasu między dwiema strefami czasowymi.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="7b0bc-113">Jednak ta technika nie musi być dokładna dla nieokreślonych czasów.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="7b0bc-114">Wszystkie <xref:System.DateTime> wartości, <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Unspecified> których właściwość jest traktowana tak, jakby były one czas lokalny.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="7b0bc-115">Jeśli tak nie jest, <xref:System.DateTime> nie będzie pomyślnie zidentyfikować prawidłowy punkt w czasie.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-115">If this is not the case, the <xref:System.DateTime> will not successfully identify the correct point in time.</span></span> <span data-ttu-id="7b0bc-116">Obejście tego ograniczenia polega na ścisłym połączeniu wartości daty i godziny ze strefą czasową dla operacji zapisywania i przywracania.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>

## <a name="round-trip-a-datetimeoffset-value"></a><span data-ttu-id="7b0bc-117">W obie strony wartość DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="7b0bc-117">Round-trip a DateTimeOffset value</span></span>

1. <span data-ttu-id="7b0bc-118">Przekonwertować <xref:System.DateTimeOffset> wartość na jego <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> reprezentację ciągu, wywołując metodę z specyfikatorem formatu "o".</span><span class="sxs-lookup"><span data-stu-id="7b0bc-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="7b0bc-119">Zapisz reprezentację ciągu <xref:System.DateTimeOffset> wartości w pliku lub przekaż ją przez obwiednię procesu, domeny aplikacji lub komputera.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="7b0bc-120">Pobierz ciąg, który <xref:System.DateTimeOffset> reprezentuje wartość.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>

4. <span data-ttu-id="7b0bc-121">Wywołaj <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metodę i <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> przekaż jako `styles` wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="7b0bc-122">Poniższy przykład ilustruje sposób <xref:System.DateTimeOffset> w obie strony wartości.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

<span data-ttu-id="7b0bc-123">Ta technika zawsze jednoznacznie identyfikuje <xref:System.DateTimeOffset> wartość jako pojedynczy punkt w czasie.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="7b0bc-124">Wartość można następnie przekonwertować na skoordynowany czas uniwersalny (UTC) przez wywołanie <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metody lub można ją <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> przekonwertować na czas w określonej strefie czasowej, wywołując metodę lub.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7b0bc-125">Głównym ograniczeniem tej techniki jest ta arytmetyka daty <xref:System.DateTimeOffset> i godziny, gdy jest wykonywana na wartości reprezentującej czas w określonej strefie czasowej, może nie dawać dokładnych wyników dla tej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="7b0bc-126">Dzieje się tak, ponieważ po wystąpieniu <xref:System.DateTimeOffset> wartości jest on adosoiczony, jest odłączony od jego strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="7b0bc-127">W związku z tym reguły dopasowania tej strefy czasowej nie mogą być już stosowane podczas wykonywania obliczeń daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="7b0bc-128">Można obejść ten problem, definiując typ niestandardowy, który zawiera zarówno wartość daty i godziny, jak i towarzyszącą jej strefę czasową.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>

## <a name="round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="7b0bc-129">W obie strony wartość daty i godziny ze strefą czasową</span><span class="sxs-lookup"><span data-stu-id="7b0bc-129">Round-trip a date and time value with its time zone</span></span>

1. <span data-ttu-id="7b0bc-130">Zdefiniuj klasę lub strukturę z dwoma polami.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="7b0bc-131">Pierwsze pole jest obiektem <xref:System.DateTime> <xref:System.DateTimeOffset> lub obiektem, a <xref:System.TimeZoneInfo> drugim obiektem.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="7b0bc-132">Poniższy przykład jest prostą wersją takiego typu.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-132">The following example is a simple version of such a type.</span></span>

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. <span data-ttu-id="7b0bc-133">Oznacz klasę atrybutem. <xref:System.SerializableAttribute></span><span class="sxs-lookup"><span data-stu-id="7b0bc-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>

3. <span data-ttu-id="7b0bc-134">Serializuj obiekt <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="7b0bc-135">Przywróć <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> obiekt przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>

5. <span data-ttu-id="7b0bc-136">Rzutowanie (w języku C#) lub konwersji (w języku Visual Basic) deserialized obiektu do obiektu odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>

<span data-ttu-id="7b0bc-137">Poniższy przykład ilustruje sposób w obie strony obiektu, który przechowuje informacje o dacie i godzinie i strefie czasowej.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-137">The following example illustrates how to round-trip an object that stores both date and time and time zone information.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

<span data-ttu-id="7b0bc-138">Ta technika powinna zawsze jednoznacznie odzwierciedlać prawidłowy punkt czasu zarówno przed, jak i po zapisaniu i przywróceniu, pod warunkiem że implementacja połączonego obiektu daty i godziny i strefy czasowej nie pozwala na zsynchronizowanie wartości daty z wartością strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="7b0bc-139">Skompiluj kod</span><span class="sxs-lookup"><span data-stu-id="7b0bc-139">Compile the code</span></span>

<span data-ttu-id="7b0bc-140">Te przykłady wymagają, aby:</span><span class="sxs-lookup"><span data-stu-id="7b0bc-140">These examples require that:</span></span>

- <span data-ttu-id="7b0bc-141">Następujące obszary nazw mają być importowane z dyrektywami języka C# `using` lub instrukcjami języka Visual Basic: `Imports`</span><span class="sxs-lookup"><span data-stu-id="7b0bc-141">The following namespaces be imported with C# `using` directives or Visual Basic `Imports` statements:</span></span>

  - <span data-ttu-id="7b0bc-142"><xref:System>(tylko C#)</span><span class="sxs-lookup"><span data-stu-id="7b0bc-142"><xref:System> (C# only)</span></span>

  - <xref:System.Globalization?displayProperty=nameWithType>

  - <xref:System.IO?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>

- <span data-ttu-id="7b0bc-143">Każdy przykład kodu, `DateInTimeZone` inne niż klasa, należy uwzględnić w klasie lub visual basic `Main` moduł, zawinięte w metody i wywoływane z metody.</span><span class="sxs-lookup"><span data-stu-id="7b0bc-143">Each code example, other than the `DateInTimeZone` class, be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b0bc-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b0bc-144">See also</span></span>

- [<span data-ttu-id="7b0bc-145">Wybieranie między datą, datownikami, timespan i timezoneinfo</span><span class="sxs-lookup"><span data-stu-id="7b0bc-145">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../../../docs/standard/datetime/choosing-between-datetime.md)
- [<span data-ttu-id="7b0bc-146">Standardowe ciągi formatujące datę i godzinę</span><span class="sxs-lookup"><span data-stu-id="7b0bc-146">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
