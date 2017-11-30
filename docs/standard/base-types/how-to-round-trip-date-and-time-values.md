---
title: "Porady: obustronna konwersja wartości daty i godziny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 515a29e279cfa8fc100e0612fc19df7abc6a3b36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="178fd-102">Porady: obustronna konwersja wartości daty i godziny</span><span class="sxs-lookup"><span data-stu-id="178fd-102">How to: Round-trip Date and Time Values</span></span>
<span data-ttu-id="178fd-103">W wielu aplikacjach wartość daty i godziny ma na celu jego jednoznacznej identyfikacji pojedynczy punkt w czasie.</span><span class="sxs-lookup"><span data-stu-id="178fd-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="178fd-104">W tym temacie pokazano, jak zapisywanie i przywracanie <xref:System.DateTime> wartość <xref:System.DateTimeOffset> wartość i wartość daty i godziny z czasem strefy informacje, aby wartość przywróconej identyfikuje jednocześnie jako zapisana wartość.</span><span class="sxs-lookup"><span data-stu-id="178fd-104">This topic shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>  
  
### <a name="to-round-trip-a-datetime-value"></a><span data-ttu-id="178fd-105">Aby obustronnie konwertować wartość daty/czasu</span><span class="sxs-lookup"><span data-stu-id="178fd-105">To round-trip a DateTime value</span></span>  
  
1.  <span data-ttu-id="178fd-106">Konwertuj <xref:System.DateTime> wartość do reprezentacji ciągu przez wywołanie metody <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metody z specyfikator formatu "o".</span><span class="sxs-lookup"><span data-stu-id="178fd-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="178fd-107">Zapisz reprezentację ciągu <xref:System.DateTime> wartość do pliku lub przekaż go za pośrednictwem procesu, domeny aplikacji lub granic maszyny.</span><span class="sxs-lookup"><span data-stu-id="178fd-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="178fd-108">Pobierz ciąg, który reprezentuje <xref:System.DateTime> wartość.</span><span class="sxs-lookup"><span data-stu-id="178fd-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>  
  
4.  <span data-ttu-id="178fd-109">Wywołanie <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> — metoda i przekazać <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako wartość `styles` parametru.</span><span class="sxs-lookup"><span data-stu-id="178fd-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="178fd-110">Poniższy przykład ilustruje sposób przesyłania danych <xref:System.DateTime> wartość.</span><span class="sxs-lookup"><span data-stu-id="178fd-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 <span data-ttu-id="178fd-111">Gdy dwustronną komunikację <xref:System.DateTime> wartość ta technika pomyślnie zachowuje czas zawsze lokalnych i uniwersalnych.</span><span class="sxs-lookup"><span data-stu-id="178fd-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="178fd-112">Na przykład, jeśli na komputerze lokalnym <xref:System.DateTime> wartość jest zapisana w systemie w Stanach Zjednoczonych Pacyficzny standardowa strefy czasowej i przywróceniu w systemie w Stanach Zjednoczonych Strefy Środkowa (czas standardowy), przywróconej Data i godzina będą później niż czas oryginalnego odzwierciedla odstęp czasu między dwiema strefami czasowymi dwóch godzin.</span><span class="sxs-lookup"><span data-stu-id="178fd-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="178fd-113">Jednak ta metoda nie jest zawsze dokładne dla nieokreślonych razy.</span><span class="sxs-lookup"><span data-stu-id="178fd-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="178fd-114">Wszystkie <xref:System.DateTime> wartości, których <xref:System.DateTime.Kind%2A> jest właściwość <xref:System.DateTimeKind.Unspecified> są traktowane jako są godzin czasu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="178fd-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="178fd-115">Jeśli to nie jest w tym przypadku <xref:System.DateTime> zostanie nie pomyślnie zidentyfikować poprawne punktu w czasie.</span><span class="sxs-lookup"><span data-stu-id="178fd-115">If this is not the case, the <xref:System.DateTime> will not successfully identify the correct point in time.</span></span> <span data-ttu-id="178fd-116">Obejście tego ograniczenia jest ściśle połączenie z jego strefą czasową zapisywania wartość daty i godziny, a operacja przywracania.</span><span class="sxs-lookup"><span data-stu-id="178fd-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a><span data-ttu-id="178fd-117">Aby obustronnie konwertować wartość przesunięcia daty/czasu</span><span class="sxs-lookup"><span data-stu-id="178fd-117">To round-trip a DateTimeOffset value</span></span>  
  
1.  <span data-ttu-id="178fd-118">Konwertuj <xref:System.DateTimeOffset> wartość do reprezentacji ciągu przez wywołanie metody <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metody z specyfikator formatu "o".</span><span class="sxs-lookup"><span data-stu-id="178fd-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="178fd-119">Zapisz reprezentację ciągu <xref:System.DateTimeOffset> wartość do pliku lub przekaż go za pośrednictwem procesu, domeny aplikacji lub granic maszyny.</span><span class="sxs-lookup"><span data-stu-id="178fd-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="178fd-120">Pobierz ciąg, który reprezentuje <xref:System.DateTimeOffset> wartość.</span><span class="sxs-lookup"><span data-stu-id="178fd-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>  
  
4.  <span data-ttu-id="178fd-121">Wywołanie <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> — metoda i przekazać <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako wartość `styles` parametru.</span><span class="sxs-lookup"><span data-stu-id="178fd-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="178fd-122">Poniższy przykład ilustruje sposób przesyłania danych <xref:System.DateTimeOffset> wartość.</span><span class="sxs-lookup"><span data-stu-id="178fd-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 <span data-ttu-id="178fd-123">Ta metoda zawsze jednoznacznie identyfikuje <xref:System.DateTimeOffset> wartość jako pojedynczy punkt w czasie.</span><span class="sxs-lookup"><span data-stu-id="178fd-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="178fd-124">Następnie można przekonwertować wartość uniwersalny czas koordynowany (UTC), wywołując <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metody, lub można przekonwertować na czas w strefie czasowej określonej przez wywołanie metody <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> lub <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> — metoda.</span><span class="sxs-lookup"><span data-stu-id="178fd-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="178fd-125">Główne ograniczenie tej metody jest data i czas arytmetyczne, wykonywane na <xref:System.DateTimeOffset> wartość, która reprezentuje czas, w szczególności strefie czasowej, nie może utworzyć prawidłowych wyników dla tej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="178fd-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="178fd-126">Jest to spowodowane podczas <xref:System.DateTimeOffset> wartość zostanie uruchomiony, jest on oddzielone od strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="178fd-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="178fd-127">W związku z tym reguł korygowania strefy czasowej nie będzie można zastosować podczas wykonywania obliczeń daty i czasu.</span><span class="sxs-lookup"><span data-stu-id="178fd-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="178fd-128">Ten problem można obejść przez definiowanie niestandardowego typu, który zawiera datę i godzinę i towarzyszące strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="178fd-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="178fd-129">Aby obustronnie konwertować wartość daty i czasu z ich strefą czasu</span><span class="sxs-lookup"><span data-stu-id="178fd-129">To round-trip a date and time value with its time zone</span></span>  
  
1.  <span data-ttu-id="178fd-130">Zdefiniuj klasą lub strukturą z dwoma polami.</span><span class="sxs-lookup"><span data-stu-id="178fd-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="178fd-131">Pierwsze pole to albo <xref:System.DateTime> lub <xref:System.DateTimeOffset> obiektu, a drugi jest <xref:System.TimeZoneInfo> obiektu.</span><span class="sxs-lookup"><span data-stu-id="178fd-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="178fd-132">Poniższy przykład jest proste wersji takiego typu.</span><span class="sxs-lookup"><span data-stu-id="178fd-132">The following example is a simple version of such a type.</span></span>  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  <span data-ttu-id="178fd-133">Oznacz klasę z <xref:System.SerializableAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="178fd-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>  
  
3.  <span data-ttu-id="178fd-134">Serializować obiektów przy użyciu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="178fd-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>  
  
4.  <span data-ttu-id="178fd-135">Przywracanie obiektów przy użyciu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="178fd-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>  
  
5.  <span data-ttu-id="178fd-136">Rzutowanie (C#) lub konwertowania (w języku Visual Basic) zdeserializowany obiekt na obiekt odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="178fd-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>  
  
 <span data-ttu-id="178fd-137">Poniższy przykład ilustruje sposób przesyłania danych obiektu, który przechowuje informacje o datę i godzinę i strefę czasową.</span><span class="sxs-lookup"><span data-stu-id="178fd-137">The following example illustrates how to round-trip an object that stores both date and time and time zone information.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 <span data-ttu-id="178fd-138">Ta metoda zawsze jednoznacznie powinien odzwierciedlać poprawne punktu zarówno przed i po jego jest zapisywany i przywracany, przeznaczony implementacji Scalonej datę i godzinę i strefę czasową obiektu nie zezwala zostać zsynchronizowany z wartości typu date wartości strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="178fd-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="178fd-139">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="178fd-139">Compiling the Code</span></span>  
 <span data-ttu-id="178fd-140">Wymagaj te przykłady:</span><span class="sxs-lookup"><span data-stu-id="178fd-140">These examples require:</span></span>  
  
-   <span data-ttu-id="178fd-141">Czy następujących przestrzeni nazw można zaimportować w języku C# `using` instrukcji lub [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="178fd-141">That the following namespaces be imported with C# `using` statements or [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `Imports` statements:</span></span>  
  
    -   <span data-ttu-id="178fd-142"><xref:System>(C# tylko).</span><span class="sxs-lookup"><span data-stu-id="178fd-142"><xref:System> (C# only).</span></span>  
  
    -   <span data-ttu-id="178fd-143"><xref:System.Globalization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="178fd-143"><xref:System.Globalization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="178fd-144"><xref:System.IO?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="178fd-144"><xref:System.IO?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="178fd-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="178fd-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="178fd-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="178fd-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="178fd-147">Odwołania do System.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="178fd-147">A reference to System.Core.dll.</span></span>  
  
-   <span data-ttu-id="178fd-148">Przykład każdego kodu innego niż `DateInTimeZone` klasy, powinny być uwzględnione w klasie lub module języka Visual Basic, ujęte w metody i wywoływane z `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="178fd-148">Each code example, other than the `DateInTimeZone` class, should be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="178fd-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="178fd-149">See Also</span></span>  
 [<span data-ttu-id="178fd-150">Wykonywanie operacji formatowania</span><span class="sxs-lookup"><span data-stu-id="178fd-150">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [<span data-ttu-id="178fd-151">Wybieranie pomiędzy DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="178fd-151">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../../../docs/standard/datetime/choosing-between-datetime.md)  
 [<span data-ttu-id="178fd-152">Ciągi formatujące standardowa Data i godzina</span><span class="sxs-lookup"><span data-stu-id="178fd-152">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
