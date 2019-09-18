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
ms.openlocfilehash: 32217b9e681179c246560ff5b51b65b4f4e044d5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052887"
---
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="384ce-102">dateTimeInvalidLocalFormat MDA</span><span class="sxs-lookup"><span data-stu-id="384ce-102">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="384ce-103">Zdarzenie MDA jest uaktywniane, <xref:System.DateTime> gdy wystąpienie, które jest przechowywane jako uniwersalny czas koordynowany (UTC) jest sformatowane przy użyciu formatu, który jest przeznaczony do użycia tylko dla wystąpień lokalnych <xref:System.DateTime>. `dateTimeInvalidLocalFormat`</span><span class="sxs-lookup"><span data-stu-id="384ce-103">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="384ce-104">Ta wartość MDA nie została aktywowana dla wystąpień nieokreślonych lub domyślnych <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="384ce-104">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="384ce-105">Objaw</span><span class="sxs-lookup"><span data-stu-id="384ce-105">Symptom</span></span>  
 <span data-ttu-id="384ce-106">Aplikacja ręcznie Serializowanie wystąpienia czasu UTC <xref:System.DateTime> przy użyciu formatu lokalnego:</span><span class="sxs-lookup"><span data-stu-id="384ce-106">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="384ce-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="384ce-107">Cause</span></span>  
 <span data-ttu-id="384ce-108">Format "z" dla <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metody obejmuje przesunięcie lokalnej strefy czasowej, na przykład "+ 10:00" dla czasu Sydney.</span><span class="sxs-lookup"><span data-stu-id="384ce-108">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="384ce-109">W związku z tym zostanie wygenerowane znaczące wyniki tylko wtedy, gdy wartość <xref:System.DateTime> jest lokalna.</span><span class="sxs-lookup"><span data-stu-id="384ce-109">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="384ce-110">Jeśli wartość jest czasu UTC, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> uwzględnia przesunięcie strefy czasowej, ale nie wyświetla ani nie dostosowuje specyfikatora strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="384ce-110">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="384ce-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="384ce-111">Resolution</span></span>  
 <span data-ttu-id="384ce-112">Wystąpienia <xref:System.DateTime> czasu UTC powinny być sformatowane w taki sposób, aby wskazywały czas UTC.</span><span class="sxs-lookup"><span data-stu-id="384ce-112">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="384ce-113">Zalecany format czasu UTC do użycia "Z" jako "czas UTC":</span><span class="sxs-lookup"><span data-stu-id="384ce-113">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="384ce-114">Istnieje również format "o", który serializować <xref:System.DateTime> użycie <xref:System.DateTime.Kind%2A> właściwości, która jest poprawnie serializowana bez względu na to, czy wystąpienie jest lokalne, UTC, czy nieokreślone:</span><span class="sxs-lookup"><span data-stu-id="384ce-114">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="384ce-115">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="384ce-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="384ce-116">To zdarzenie MDA nie ma wpływu na środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="384ce-116">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="384ce-117">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="384ce-117">Output</span></span>  
 <span data-ttu-id="384ce-118">W wyniku tego przeprowadzenia operacji MDA nie ma żadnych specjalnych danych wyjściowych. jednak stos wywołań może służyć do określenia lokalizacji <xref:System.DateTime.ToString%2A> wywołania, które aktywuje zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="384ce-118">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="384ce-119">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="384ce-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="384ce-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="384ce-120">Example</span></span>  
 <span data-ttu-id="384ce-121">Rozważmy aplikację, która pośrednio serializacji wartość czasu UTC <xref:System.DateTime> przy <xref:System.Xml.XmlConvert> użyciu klasy or <xref:System.Data.DataSet> , w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="384ce-121">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="384ce-122">Serializacji <xref:System.Xml.XmlConvert> i<xref:System.Data.DataSet> domyślnie używają formatów lokalnych do serializacji.</span><span class="sxs-lookup"><span data-stu-id="384ce-122">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="384ce-123">Do serializacji innych rodzajów <xref:System.DateTime> wartości, takich jak UTC, są wymagane dodatkowe opcje.</span><span class="sxs-lookup"><span data-stu-id="384ce-123">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="384ce-124">Na potrzeby tego konkretnego przykładu `XmlDateTimeSerializationMode.RoundtripKind` Przekaż `ToString` do wywołania `XmlConvert`.</span><span class="sxs-lookup"><span data-stu-id="384ce-124">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="384ce-125">Spowoduje to serializacji danych jako czas UTC.</span><span class="sxs-lookup"><span data-stu-id="384ce-125">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="384ce-126">Jeśli używasz <xref:System.Data.DataSet>, <xref:System.Data.DataColumn.DateTimeMode%2A> <xref:System.Data.DataColumn> Ustaw<xref:System.Data.DataSetDateTime.Utc>właściwość obiektu na.</span><span class="sxs-lookup"><span data-stu-id="384ce-126">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="384ce-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="384ce-127">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="384ce-128">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="384ce-128">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
