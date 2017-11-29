---
title: dateTimeInvalidLocalFormat MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3181acec440f2d01e928bb051b297fba75de1e2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="83b6c-102">dateTimeInvalidLocalFormat MDA</span><span class="sxs-lookup"><span data-stu-id="83b6c-102">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="83b6c-103">`dateTimeInvalidLocalFormat` MDA została aktywowana po <xref:System.DateTime> wystąpienie, które są przechowywane jako uniwersalny czas koordynowany (UTC) sformatowany przy użyciu formatu, który ma być używana tylko w przypadku lokalnego <xref:System.DateTime> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="83b6c-103">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="83b6c-104">To zdarzenie MDA nie została aktywowana dla nieokreślonych lub domyślna <xref:System.DateTime> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="83b6c-104">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="83b6c-105">Objaw</span><span class="sxs-lookup"><span data-stu-id="83b6c-105">Symptom</span></span>  
 <span data-ttu-id="83b6c-106">Aplikacja jest ręcznie serializacji UTC <xref:System.DateTime> wystąpienia przy użyciu lokalnego formatu:</span><span class="sxs-lookup"><span data-stu-id="83b6c-106">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="83b6c-107">Przyczyna</span><span class="sxs-lookup"><span data-stu-id="83b6c-107">Cause</span></span>  
 <span data-ttu-id="83b6c-108">Format 'z' <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> metoda zawiera przesunięcie strefy czasu lokalnego, na przykład "10:00" dla czasu Sydney.</span><span class="sxs-lookup"><span data-stu-id="83b6c-108">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="83b6c-109">W efekcie powoduje tylko wygenerowanie znaczącego wyniku Jeśli wartość <xref:System.DateTime> jest lokalny.</span><span class="sxs-lookup"><span data-stu-id="83b6c-109">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="83b6c-110">Jeśli wartość jest czas UTC <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> obejmuje czas lokalny przesunięcia strefy, ale nie wyświetlanie lub Dostosuj specyfikator strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="83b6c-110">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="83b6c-111">Rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="83b6c-111">Resolution</span></span>  
 <span data-ttu-id="83b6c-112">Czas UTC <xref:System.DateTime> wystąpień powinien być sformatowany w taki sposób, który wskazuje, że są one w formacie UTC.</span><span class="sxs-lookup"><span data-stu-id="83b6c-112">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="83b6c-113">Zalecanym formatem dla czasu UTC do użycia Z określający czas UTC:</span><span class="sxs-lookup"><span data-stu-id="83b6c-113">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="83b6c-114">Istnieje również format "e", który serializuje <xref:System.DateTime> korzystające z <xref:System.DateTime.Kind%2A> właściwości, który serializuje prawidłowo, niezależnie od tego, czy wystąpienie lokalne, UTC, lub nieokreślona:</span><span class="sxs-lookup"><span data-stu-id="83b6c-114">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="83b6c-115">Wpływ na środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="83b6c-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="83b6c-116">To zdarzenie MDA nie ma wpływu na środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="83b6c-116">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="83b6c-117">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="83b6c-117">Output</span></span>  
 <span data-ttu-id="83b6c-118">Brak żadne specjalne dane wyjściowe w wyniku tego aktywowanie MDA., jednak stos wywołań może służyć do określenia lokalizacji <xref:System.DateTime.ToString%2A> wywołaniu, które są aktywowane MDA.</span><span class="sxs-lookup"><span data-stu-id="83b6c-118">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="83b6c-119">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="83b6c-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="83b6c-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="83b6c-120">Example</span></span>  
 <span data-ttu-id="83b6c-121">Należy wziąć pod uwagę aplikacji, która wykonuje serializację pośrednio UTC <xref:System.DateTime> wartość przy użyciu <xref:System.Xml.XmlConvert> lub <xref:System.Data.DataSet> klasy, w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="83b6c-121">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="83b6c-122"><xref:System.Xml.XmlConvert> i <xref:System.Data.DataSet> serializations użyć lokalnego formatów serializacji domyślnie.</span><span class="sxs-lookup"><span data-stu-id="83b6c-122">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="83b6c-123">Dodatkowe opcje są wymagane do serializacji innymi rodzajami z <xref:System.DateTime> wartości, takich jak czas UTC.</span><span class="sxs-lookup"><span data-stu-id="83b6c-123">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="83b6c-124">W tym przykładzie określonych przekazywanie `XmlDateTimeSerializationMode.RoundtripKind` do `ToString` wywołać `XmlConvert`.</span><span class="sxs-lookup"><span data-stu-id="83b6c-124">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="83b6c-125">To serializuje dane jako czas UTC.</span><span class="sxs-lookup"><span data-stu-id="83b6c-125">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="83b6c-126">Jeśli przy użyciu <xref:System.Data.DataSet>ustaw <xref:System.Data.DataColumn.DateTimeMode%2A> właściwość <xref:System.Data.DataColumn> do obiektu <xref:System.Data.DataSetDateTime.Utc>.</span><span class="sxs-lookup"><span data-stu-id="83b6c-126">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="83b6c-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83b6c-127">See Also</span></span>  
 <xref:System.Globalization.DateTimeFormatInfo>  
 [<span data-ttu-id="83b6c-128">Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="83b6c-128">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
