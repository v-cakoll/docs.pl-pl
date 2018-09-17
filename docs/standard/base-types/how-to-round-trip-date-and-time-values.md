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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55b16d135449cad8ed489a8a3e21db326be0fae0
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45668421"
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="59e9b-102">Porady: obustronna konwersja wartości daty i godziny</span><span class="sxs-lookup"><span data-stu-id="59e9b-102">How to: Round-trip Date and Time Values</span></span>
<span data-ttu-id="59e9b-103">W wielu aplikacjach wartości daty i godziny jest przeznaczona do jego jednoznacznej identyfikacji pojedynczego punktu w czasie.</span><span class="sxs-lookup"><span data-stu-id="59e9b-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="59e9b-104">W tym temacie pokazano, jak zapisywanie i przywracanie <xref:System.DateTime> wartość <xref:System.DateTimeOffset> wartości i wartości daty i godziny, z czasem strefy, aby wartość przywróconej identyfikuje tym samym czasie jako zapisaną wartość.</span><span class="sxs-lookup"><span data-stu-id="59e9b-104">This topic shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>  
  
### <a name="to-round-trip-a-datetime-value"></a><span data-ttu-id="59e9b-105">Aby obustronnie konwertować wartość daty/czasu</span><span class="sxs-lookup"><span data-stu-id="59e9b-105">To round-trip a DateTime value</span></span>  
  
1.  <span data-ttu-id="59e9b-106">Konwertuj <xref:System.DateTime> wartość na jego reprezentację ciągu, wywołując <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metody przy użyciu specyfikatora formatu "o".</span><span class="sxs-lookup"><span data-stu-id="59e9b-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="59e9b-107">Zapisz ciąg reprezentujący <xref:System.DateTime> do pliku lub wartości krzyż procesu, domeny aplikacji lub granic maszyny.</span><span class="sxs-lookup"><span data-stu-id="59e9b-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="59e9b-108">Pobierz ciąg, który reprezentuje <xref:System.DateTime> wartość.</span><span class="sxs-lookup"><span data-stu-id="59e9b-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>  
  
4.  <span data-ttu-id="59e9b-109">Wywołaj <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metody i przekazać <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako wartość `styles` parametru.</span><span class="sxs-lookup"><span data-stu-id="59e9b-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="59e9b-110">Poniższy przykład ilustruje sposób przesłania danych <xref:System.DateTime> wartość.</span><span class="sxs-lookup"><span data-stu-id="59e9b-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 <span data-ttu-id="59e9b-111">Podczas Pełna zgodnooć wersji <xref:System.DateTime> wartość ta technika pomyślnie zachowuje czas cały czas lokalnych i uniwersalnych.</span><span class="sxs-lookup"><span data-stu-id="59e9b-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="59e9b-112">Na przykład, jeśli lokalny <xref:System.DateTime> wartość jest zapisywana w systemie, w Stanach Zjednoczonych Pacyficznego standardowa strefy czasowej i zostanie przywrócony w systemie, w Stanach Zjednoczonych Środkowy czas standardowy strefy, przywróconej datę i godzinę będzie później niż pierwotny czas, który odzwierciedla różnica czasu między dwiema strefami czasowymi dwóch godzin.</span><span class="sxs-lookup"><span data-stu-id="59e9b-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="59e9b-113">Ta technika nie jest jednak zawsze prawidłowe dla nieokreślonych godziny.</span><span class="sxs-lookup"><span data-stu-id="59e9b-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="59e9b-114">Wszystkie <xref:System.DateTime> wartości, których <xref:System.DateTime.Kind%2A> właściwość <xref:System.DateTimeKind.Unspecified> są traktowane tak, są one czas lokalny.</span><span class="sxs-lookup"><span data-stu-id="59e9b-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="59e9b-115">Jeśli nie jest to przypadek, <xref:System.DateTime> nie pomyślnie zidentyfikujesz prawidłowy punkt w czasie.</span><span class="sxs-lookup"><span data-stu-id="59e9b-115">If this is not the case, the <xref:System.DateTime> will not successfully identify the correct point in time.</span></span> <span data-ttu-id="59e9b-116">Obejście tego ograniczenia jest ściśle Połącz wartości daty i godziny z ich strefą czasu, zapisywania i operacji przywracania.</span><span class="sxs-lookup"><span data-stu-id="59e9b-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a><span data-ttu-id="59e9b-117">Aby obustronnie konwertować wartość przesunięcia daty/czasu</span><span class="sxs-lookup"><span data-stu-id="59e9b-117">To round-trip a DateTimeOffset value</span></span>  
  
1.  <span data-ttu-id="59e9b-118">Konwertuj <xref:System.DateTimeOffset> wartość na jego reprezentację ciągu, wywołując <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metody przy użyciu specyfikatora formatu "o".</span><span class="sxs-lookup"><span data-stu-id="59e9b-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="59e9b-119">Zapisz ciąg reprezentujący <xref:System.DateTimeOffset> do pliku lub wartości krzyż procesu, domeny aplikacji lub granic maszyny.</span><span class="sxs-lookup"><span data-stu-id="59e9b-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="59e9b-120">Pobierz ciąg, który reprezentuje <xref:System.DateTimeOffset> wartość.</span><span class="sxs-lookup"><span data-stu-id="59e9b-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>  
  
4.  <span data-ttu-id="59e9b-121">Wywołaj <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metody i przekazać <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako wartość `styles` parametru.</span><span class="sxs-lookup"><span data-stu-id="59e9b-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="59e9b-122">Poniższy przykład ilustruje sposób przesłania danych <xref:System.DateTimeOffset> wartość.</span><span class="sxs-lookup"><span data-stu-id="59e9b-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 <span data-ttu-id="59e9b-123">Ta technika zawsze jednoznacznie identyfikuje <xref:System.DateTimeOffset> wartość jako pojedynczy punkt w czasie.</span><span class="sxs-lookup"><span data-stu-id="59e9b-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="59e9b-124">Można następnie można konwertować wartości do uniwersalny czas koordynowany (UTC) przez wywołanie metody <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metodę, lub można przekonwertować na czas w strefie czasowej określonej przez wywołanie metody <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> lub <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="59e9b-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="59e9b-125">Główne ograniczenia tej techniki jest tej daty i godziny operacje arytmetyczne, gdy przeprowadzane na <xref:System.DateTimeOffset> wartość, która reprezentuje czas w określonej strefie czasowej, nie może wygenerować dokładne wyniki dla tej strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="59e9b-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="59e9b-126">To dlatego, gdy <xref:System.DateTimeOffset> konkretyzacji wartość, jej jest oddzielone od strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="59e9b-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="59e9b-127">W związku z tym nie jest już można zastosować reguł korygowania tej strefy czasowej, kiedy można wykonywać obliczenia daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="59e9b-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="59e9b-128">Ten problem można obejść, definiując typ niestandardowy, który zawiera wartość typu date i wartość czasu i towarzyszące strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="59e9b-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="59e9b-129">Aby obustronnie konwertować wartość daty i czasu z ich strefą czasu</span><span class="sxs-lookup"><span data-stu-id="59e9b-129">To round-trip a date and time value with its time zone</span></span>  
  
1.  <span data-ttu-id="59e9b-130">Zdefiniuj klasę lub strukturę z dwóch pól.</span><span class="sxs-lookup"><span data-stu-id="59e9b-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="59e9b-131">Pierwsze pole to <xref:System.DateTime> lub <xref:System.DateTimeOffset> obiektu, a drugi jest <xref:System.TimeZoneInfo> obiektu.</span><span class="sxs-lookup"><span data-stu-id="59e9b-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="59e9b-132">Poniższy przykład jest prosta wersja takiego typu.</span><span class="sxs-lookup"><span data-stu-id="59e9b-132">The following example is a simple version of such a type.</span></span>  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  <span data-ttu-id="59e9b-133">Oznacz klasę za pomocą <xref:System.SerializableAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="59e9b-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>  
  
3.  <span data-ttu-id="59e9b-134">Serializowanie przy użyciu obiektu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="59e9b-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>  
  
4.  <span data-ttu-id="59e9b-135">Przywrócić dane przy użyciu obiektu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="59e9b-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>  
  
5.  <span data-ttu-id="59e9b-136">Rzutowanie (C#) lub przekonwertować (w języku Visual Basic) obiektu po deserializacji obiektu odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="59e9b-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>  
  
 <span data-ttu-id="59e9b-137">W poniższym przykładzie pokazano, jak przesyłania danych obiektu, który przechowuje informacje o datę i godzinę i strefę czasową.</span><span class="sxs-lookup"><span data-stu-id="59e9b-137">The following example illustrates how to round-trip an object that stores both date and time and time zone information.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 <span data-ttu-id="59e9b-138">Ta technika zawsze jednoznacznie powinny odzwierciedlać poprawne momencie zarówno przed i po jego jest zapisywany i przywracany, pod warunkiem wykonania połączonego obiektu daty i godziny i strefy czasowej nie zezwala na wartość daty zostać zsynchronizowany z wartości strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="59e9b-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="59e9b-139">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="59e9b-139">Compiling the Code</span></span>  
 <span data-ttu-id="59e9b-140">Wymagaj tych przykładach:</span><span class="sxs-lookup"><span data-stu-id="59e9b-140">These examples require:</span></span>  
  
-   <span data-ttu-id="59e9b-141">Czy następujących przestrzeni nazw można zaimportować za pomocą języka C# `using` instrukcji lub Visual Basic `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="59e9b-141">That the following namespaces be imported with C# `using` statements or Visual Basic `Imports` statements:</span></span>  
  
    -   <span data-ttu-id="59e9b-142"><xref:System> (Tylko język C#).</span><span class="sxs-lookup"><span data-stu-id="59e9b-142"><xref:System> (C# only).</span></span>  
  
    -   <span data-ttu-id="59e9b-143"><xref:System.Globalization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="59e9b-143"><xref:System.Globalization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="59e9b-144"><xref:System.IO?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="59e9b-144"><xref:System.IO?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="59e9b-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="59e9b-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="59e9b-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="59e9b-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="59e9b-147">Odwołanie do biblioteki System.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="59e9b-147">A reference to System.Core.dll.</span></span>  
  
-   <span data-ttu-id="59e9b-148">Przykład kodowych innych niż `DateInTimeZone` klasy, powinny być uwzględnione w klasie lub module języka Visual Basic, opakowane w metodach i wywoływane z `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="59e9b-148">Each code example, other than the `DateInTimeZone` class, should be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59e9b-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59e9b-149">See also</span></span>

- [<span data-ttu-id="59e9b-150">Wykonywanie operacji formatowania</span><span class="sxs-lookup"><span data-stu-id="59e9b-150">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)  
- [<span data-ttu-id="59e9b-151">Wybieranie pomiędzy DateTime, DateTimeOffset, TimeSpan i TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="59e9b-151">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../../../docs/standard/datetime/choosing-between-datetime.md)  
- [<span data-ttu-id="59e9b-152">Standardowe ciągi formatujące datę i godzinę</span><span class="sxs-lookup"><span data-stu-id="59e9b-152">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
