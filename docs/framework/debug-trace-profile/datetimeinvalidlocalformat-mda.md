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
ms.openlocfilehash: b01f030c474e426cb87fb907f99f241eeb76a7fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174761"
---
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="95289-102">dateTimeInvalidLocalFormat MDA</span><span class="sxs-lookup"><span data-stu-id="95289-102">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="95289-103">MdA `dateTimeInvalidLocalFormat` jest aktywowany, <xref:System.DateTime> gdy wystąpienie, które jest przechowywane jako uniwersalny czas skoordynowany (UTC) jest <xref:System.DateTime> sformatowany przy użyciu formatu, który jest przeznaczony do użycia tylko dla wystąpień lokalnych.</span><span class="sxs-lookup"><span data-stu-id="95289-103">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="95289-104">To narzędzie MDA nie jest aktywowane <xref:System.DateTime> dla wystąpienia nieokreślone lub domyślne.</span><span class="sxs-lookup"><span data-stu-id="95289-104">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="95289-105">Objaw</span><span class="sxs-lookup"><span data-stu-id="95289-105">Symptom</span></span>  
 <span data-ttu-id="95289-106">Aplikacja ręcznie serializuje wystąpienie <xref:System.DateTime> UTC przy użyciu formatu lokalnego:</span><span class="sxs-lookup"><span data-stu-id="95289-106">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="95289-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="95289-107">Cause</span></span>  
 <span data-ttu-id="95289-108">Format "z" dla <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metody zawiera przesunięcie lokalnej strefy czasowej, na przykład "+10:00" dla czasu Sydney.</span><span class="sxs-lookup"><span data-stu-id="95289-108">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="95289-109">Jako takie będzie produkować znaczący wynik tylko <xref:System.DateTime> wtedy, gdy wartość jest lokalny.</span><span class="sxs-lookup"><span data-stu-id="95289-109">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="95289-110">Jeśli wartość jest czas <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> UTC, zawiera przesunięcie lokalnej strefy czasowej, ale nie wyświetla ani nie dostosowuje specyfikatora strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="95289-110">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="95289-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="95289-111">Resolution</span></span>  
 <span data-ttu-id="95289-112">Wystąpienia <xref:System.DateTime> UTC powinny być sformatowane w sposób, który wskazuje, że są one UTC.</span><span class="sxs-lookup"><span data-stu-id="95289-112">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="95289-113">Zalecany format czasu UTC do używania "Z" do oznaczania czasu UTC:</span><span class="sxs-lookup"><span data-stu-id="95289-113">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="95289-114">Istnieje również format "o", który serializuje <xref:System.DateTime> korzystanie <xref:System.DateTime.Kind%2A> z właściwości, która serializuje poprawnie, niezależnie od tego, czy wystąpienie jest lokalne, UTC lub nieokreślony:</span><span class="sxs-lookup"><span data-stu-id="95289-114">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="95289-115">Wpływ na czas działania</span><span class="sxs-lookup"><span data-stu-id="95289-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="95289-116">Ten mda nie wpływa na środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="95289-116">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="95289-117">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="95289-117">Output</span></span>  
 <span data-ttu-id="95289-118">Nie ma żadnych specjalnych danych wyjściowych w wyniku tego aktywowania MDA., Jednak stos <xref:System.DateTime.ToString%2A> wywołań może służyć do określenia lokalizacji wywołania, które aktywowało MDA.</span><span class="sxs-lookup"><span data-stu-id="95289-118">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="95289-119">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="95289-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="95289-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="95289-120">Example</span></span>  
 <span data-ttu-id="95289-121">Należy wziąć pod uwagę aplikację, która <xref:System.DateTime> jest pośrednio serializacji wartości UTC przy użyciu <xref:System.Xml.XmlConvert> lub <xref:System.Data.DataSet> klasy, w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="95289-121">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="95289-122">I <xref:System.Xml.XmlConvert> <xref:System.Data.DataSet> serializacji używać formatów lokalnych do serializacji domyślnie.</span><span class="sxs-lookup"><span data-stu-id="95289-122">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="95289-123">Dodatkowe opcje są wymagane do serializacji innych rodzajów <xref:System.DateTime> wartości, takich jak UTC.</span><span class="sxs-lookup"><span data-stu-id="95289-123">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="95289-124">W tym konkretnym `XmlDateTimeSerializationMode.RoundtripKind` przykładzie `ToString` przekaż `XmlConvert`do wywołania na .</span><span class="sxs-lookup"><span data-stu-id="95289-124">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="95289-125">To serializuje dane jako czas UTC.</span><span class="sxs-lookup"><span data-stu-id="95289-125">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="95289-126">Jeśli <xref:System.Data.DataSet>używasz , <xref:System.Data.DataColumn.DateTimeMode%2A> ustaw <xref:System.Data.DataColumn> właściwość <xref:System.Data.DataSetDateTime.Utc>na obiekcie na .</span><span class="sxs-lookup"><span data-stu-id="95289-126">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="95289-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95289-127">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="95289-128">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="95289-128">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
