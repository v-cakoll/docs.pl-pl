---
title: dateTimeInvalidLocalFormat MDA
ms.date: 03/30/2017
helpviewer_keywords:
- dates [.NET Framework], formatting
- invalid date time local format
- invalid local formats
- MDAs (managed debugging assistants), invalid local formats
- managed debugging assistants (MDAs), invalid local formats
- dateTimeInvalidLocalFormat MDA
- date formatting
- time formatting
- UTC formatting
ms.assetid: c4a942bb-2651-4b65-8718-809f892a0659
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 380334dbe9b91ea369de6cbe58686a9a74254c2c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148229"
---
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="93586-102">dateTimeInvalidLocalFormat MDA</span><span class="sxs-lookup"><span data-stu-id="93586-102">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="93586-103">`dateTimeInvalidLocalFormat` Zdarzenie MDA jest aktywowane podczas <xref:System.DateTime> wystąpienie, które są przechowywane jako uniwersalny czas koordynowany (UTC) jest formatowana przy użyciu formatu, który jest przeznaczony do użycia tylko w przypadku lokalnego <xref:System.DateTime> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="93586-103">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="93586-104">To zdarzenie MDA nie została aktywowana, nie określono tego parametru lub domyślna <xref:System.DateTime> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="93586-104">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="93586-105">Objaw</span><span class="sxs-lookup"><span data-stu-id="93586-105">Symptom</span></span>  
 <span data-ttu-id="93586-106">Aplikacja jest ręczne serializacji formatu UTC <xref:System.DateTime> wystąpienia przy użyciu lokalnego formatu:</span><span class="sxs-lookup"><span data-stu-id="93586-106">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="93586-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="93586-107">Cause</span></span>  
 <span data-ttu-id="93586-108">Format "z" <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metoda zawiera przesunięcie strefy czasu lokalnego, na przykład "10:00" dla czasu Sydney.</span><span class="sxs-lookup"><span data-stu-id="93586-108">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="93586-109">W efekcie powoduje tylko wygenerowanie znaczący wynik przypadku wartość <xref:System.DateTime> jest lokalny.</span><span class="sxs-lookup"><span data-stu-id="93586-109">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="93586-110">Jeśli wartość jest czas UTC <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> obejmuje czas lokalny przesunięcia strefy, ale nie wyświetlić lub dostosować specyfikator strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="93586-110">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="93586-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="93586-111">Resolution</span></span>  
 <span data-ttu-id="93586-112">UTC <xref:System.DateTime> wystąpień powinny być sformatowane w sposób sugerujący, że są one UTC.</span><span class="sxs-lookup"><span data-stu-id="93586-112">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="93586-113">Zalecany format czasu UTC na potrzeby "Z" oznaczają czas UTC:</span><span class="sxs-lookup"><span data-stu-id="93586-113">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="93586-114">Dostępna jest również formatu "o", który serializuje <xref:System.DateTime> korzystające z <xref:System.DateTime.Kind%2A> właściwości, który serializuje prawidłowo, niezależnie od tego, czy wystąpienie jest lokalnym, UTC, lub nieokreślony:</span><span class="sxs-lookup"><span data-stu-id="93586-114">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="93586-115">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="93586-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="93586-116">To zdarzenie MDA nie ma wpływu na środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="93586-116">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="93586-117">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="93586-117">Output</span></span>  
 <span data-ttu-id="93586-118">Istnieje żadne specjalne dane wyjściowe w wyniku tego MDA aktywowanie., natomiast stos wywołań może służyć do określenia lokalizacji <xref:System.DateTime.ToString%2A> wywołania, które aktywowano MDA.</span><span class="sxs-lookup"><span data-stu-id="93586-118">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="93586-119">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="93586-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="93586-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="93586-120">Example</span></span>  
 <span data-ttu-id="93586-121">Rozważmy aplikację, która jest pośrednio serializacji formatu UTC <xref:System.DateTime> wartości za pomocą <xref:System.Xml.XmlConvert> lub <xref:System.Data.DataSet> klasy, w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="93586-121">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="93586-122"><xref:System.Xml.XmlConvert> i <xref:System.Data.DataSet> serializations formaty lokalne serializacji domyślnie używają.</span><span class="sxs-lookup"><span data-stu-id="93586-122">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="93586-123">Dodatkowe opcje są wymagane do wykonywania serializacji innych typów z <xref:System.DateTime> wartości, takich jak UTC.</span><span class="sxs-lookup"><span data-stu-id="93586-123">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="93586-124">W tym przykładzie określonych przekazać `XmlDateTimeSerializationMode.RoundtripKind` do `ToString` wywołanie na `XmlConvert`.</span><span class="sxs-lookup"><span data-stu-id="93586-124">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="93586-125">To serializuje dane jako czas UTC.</span><span class="sxs-lookup"><span data-stu-id="93586-125">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="93586-126">Jeśli przy użyciu <xref:System.Data.DataSet>ustaw <xref:System.Data.DataColumn.DateTimeMode%2A> właściwość <xref:System.Data.DataColumn> obiekt <xref:System.Data.DataSetDateTime.Utc>.</span><span class="sxs-lookup"><span data-stu-id="93586-126">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="93586-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93586-127">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="93586-128">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="93586-128">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
