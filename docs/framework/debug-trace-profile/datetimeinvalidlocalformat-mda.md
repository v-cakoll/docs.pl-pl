---
title: dateTimeInvalidLocalFormat MDA
description: Zapoznaj się z asystentem debugowania zarządzanego dateTimeInvalidLocalFormat (MDA), który jest uaktywniany, gdy wartość daty/godziny przechowywanej przez czas UTC pobiera tylko lokalny format DateTime.
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
ms.openlocfilehash: d092b93af55d2cdf14e9284d8cffcdc8440cbf81
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415995"
---
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="ba5b8-103">dateTimeInvalidLocalFormat MDA</span><span class="sxs-lookup"><span data-stu-id="ba5b8-103">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="ba5b8-104">`dateTimeInvalidLocalFormat`Zdarzenie MDA jest uaktywniane, gdy <xref:System.DateTime> wystąpienie, które jest przechowywane jako uniwersalny czas koordynowany (UTC) jest sformatowane przy użyciu formatu, który jest przeznaczony do użycia tylko dla <xref:System.DateTime> wystąpień lokalnych.</span><span class="sxs-lookup"><span data-stu-id="ba5b8-104">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="ba5b8-105">Ta wartość MDA nie została aktywowana dla wystąpień nieokreślonych lub domyślnych <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="ba5b8-105">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="ba5b8-106">Objaw</span><span class="sxs-lookup"><span data-stu-id="ba5b8-106">Symptom</span></span>  
 <span data-ttu-id="ba5b8-107">Aplikacja ręcznie Serializowanie wystąpienia czasu UTC <xref:System.DateTime> przy użyciu formatu lokalnego:</span><span class="sxs-lookup"><span data-stu-id="ba5b8-107">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="ba5b8-108">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="ba5b8-108">Cause</span></span>  
 <span data-ttu-id="ba5b8-109">Format "z" dla <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metody obejmuje przesunięcie lokalnej strefy czasowej, na przykład "+ 10:00" dla czasu Sydney.</span><span class="sxs-lookup"><span data-stu-id="ba5b8-109">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="ba5b8-110">W związku z tym zostanie wygenerowane znaczące wyniki tylko wtedy, gdy wartość <xref:System.DateTime> jest lokalna.</span><span class="sxs-lookup"><span data-stu-id="ba5b8-110">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="ba5b8-111">Jeśli wartość jest czasu UTC, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> uwzględnia przesunięcie strefy czasowej, ale nie wyświetla ani nie dostosowuje specyfikatora strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="ba5b8-111">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="ba5b8-112">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="ba5b8-112">Resolution</span></span>  
 <span data-ttu-id="ba5b8-113">Wystąpienia czasu UTC <xref:System.DateTime> powinny być sformatowane w taki sposób, aby wskazywały czas UTC.</span><span class="sxs-lookup"><span data-stu-id="ba5b8-113">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="ba5b8-114">Zalecany format czasu UTC do użycia "Z" jako "czas UTC":</span><span class="sxs-lookup"><span data-stu-id="ba5b8-114">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="ba5b8-115">Istnieje również format "o", który serializować <xref:System.DateTime> użycie <xref:System.DateTime.Kind%2A> właściwości, która jest poprawnie serializowana bez względu na to, czy wystąpienie jest lokalne, UTC, czy nieokreślone:</span><span class="sxs-lookup"><span data-stu-id="ba5b8-115">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ba5b8-116">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="ba5b8-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="ba5b8-117">To zdarzenie MDA nie ma wpływu na środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="ba5b8-117">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ba5b8-118">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="ba5b8-118">Output</span></span>  
 <span data-ttu-id="ba5b8-119">W wyniku tego przeprowadzenia operacji MDA nie ma żadnych specjalnych danych wyjściowych. jednak stos wywołań może służyć do określenia lokalizacji <xref:System.DateTime.ToString%2A> wywołania, które aktywuje zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="ba5b8-119">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="ba5b8-120">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ba5b8-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="ba5b8-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="ba5b8-121">Example</span></span>  
 <span data-ttu-id="ba5b8-122">Rozważmy aplikację, która pośrednio serializacji wartość czasu UTC przy <xref:System.DateTime> użyciu <xref:System.Xml.XmlConvert> <xref:System.Data.DataSet> klasy or, w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="ba5b8-122">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="ba5b8-123"><xref:System.Xml.XmlConvert>Serializacji i <xref:System.Data.DataSet> domyślnie używają formatów lokalnych do serializacji.</span><span class="sxs-lookup"><span data-stu-id="ba5b8-123">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="ba5b8-124">Do serializacji innych rodzajów <xref:System.DateTime> wartości, takich jak UTC, są wymagane dodatkowe opcje.</span><span class="sxs-lookup"><span data-stu-id="ba5b8-124">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="ba5b8-125">Na potrzeby tego konkretnego przykładu Przekaż `XmlDateTimeSerializationMode.RoundtripKind` do `ToString` wywołania `XmlConvert` .</span><span class="sxs-lookup"><span data-stu-id="ba5b8-125">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="ba5b8-126">Spowoduje to serializacji danych jako czas UTC.</span><span class="sxs-lookup"><span data-stu-id="ba5b8-126">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="ba5b8-127">Jeśli używasz <xref:System.Data.DataSet> , ustaw <xref:System.Data.DataColumn.DateTimeMode%2A> Właściwość <xref:System.Data.DataColumn> obiektu na <xref:System.Data.DataSetDateTime.Utc> .</span><span class="sxs-lookup"><span data-stu-id="ba5b8-127">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba5b8-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ba5b8-128">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="ba5b8-129">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="ba5b8-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
