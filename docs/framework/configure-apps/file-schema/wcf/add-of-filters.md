---
title: <add> dla <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 280c516b17a133930bc4b6621a8c9bc7f4781085
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850567"
---
# <a name="add-of-filters"></a><span data-ttu-id="a66f5-102">\<Dodawanie > \<filtrów ></span><span class="sxs-lookup"><span data-stu-id="a66f5-102">\<add> of \<filters></span></span>
<span data-ttu-id="a66f5-103">Filtr XPath określa rodzaj wiadomości do zarejestrowania.</span><span class="sxs-lookup"><span data-stu-id="a66f5-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
<span data-ttu-id="a66f5-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a66f5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a66f5-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a66f5-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a66f5-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> diagnostyki**](diagnostics.md)</span><span class="sxs-lookup"><span data-stu-id="a66f5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)</span></span>\
<span data-ttu-id="a66f5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<messageLogging >** ](messagelogging.md)</span><span class="sxs-lookup"><span data-stu-id="a66f5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<messageLogging>**](messagelogging.md)</span></span>\
<span data-ttu-id="a66f5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Filtry >** ](filters.md)</span><span class="sxs-lookup"><span data-stu-id="a66f5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters.md)</span></span>\
<span data-ttu-id="a66f5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**</span><span class="sxs-lookup"><span data-stu-id="a66f5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a66f5-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="a66f5-110">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a66f5-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a66f5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a66f5-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a66f5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a66f5-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a66f5-113">Attributes</span></span>  
  
|<span data-ttu-id="a66f5-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a66f5-114">Attribute</span></span>|<span data-ttu-id="a66f5-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a66f5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a66f5-116">filtr</span><span class="sxs-lookup"><span data-stu-id="a66f5-116">filter</span></span>|<span data-ttu-id="a66f5-117">Ciąg określający zapytanie na dokumencie XML zdefiniowanym przez wyrażenie XPath 1,0.</span><span class="sxs-lookup"><span data-stu-id="a66f5-117">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="a66f5-118">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="a66f5-118">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a66f5-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a66f5-119">Child Elements</span></span>  
 <span data-ttu-id="a66f5-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="a66f5-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a66f5-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a66f5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a66f5-122">Element</span><span class="sxs-lookup"><span data-stu-id="a66f5-122">Element</span></span>|<span data-ttu-id="a66f5-123">Opis</span><span class="sxs-lookup"><span data-stu-id="a66f5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a66f5-124">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="a66f5-124">\<filters></span></span>](filters.md)|<span data-ttu-id="a66f5-125">Zawiera kolekcję filtrów XPath używanych do kontroli rodzaju rejestrowanych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a66f5-125">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a66f5-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a66f5-126">Remarks</span></span>  
 <span data-ttu-id="a66f5-127">Filtry są stosowane tylko w warstwie transportowej, określonej `logMessagesAtTransportLevel` przez `true`is.</span><span class="sxs-lookup"><span data-stu-id="a66f5-127">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="a66f5-128">Filtry nie wpływają na poziom usług i źle sformułowane rejestrowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a66f5-128">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="a66f5-129">Aby dodać filtr do kolekcji, użyj `add` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="a66f5-129">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="a66f5-130">Jeśli zdefiniowano co najmniej jeden filtr, rejestrowane są tylko komunikaty zgodne z co najmniej jednym filtrem.</span><span class="sxs-lookup"><span data-stu-id="a66f5-130">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="a66f5-131">Jeśli żaden filtr nie jest zdefiniowany, wszystkie komunikaty są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="a66f5-131">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="a66f5-132">Filtry obsługują pełną składnię XPath i są stosowane w kolejności, w której pojawiają się w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a66f5-132">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="a66f5-133">Składnia nieprawidłowego filtru powoduje wyjątek w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a66f5-133">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="a66f5-134">Poniżej przedstawiono przykład sposobu konfigurowania filtru, który rejestruje tylko komunikaty, które mają sekcję nagłówka SOAP.</span><span class="sxs-lookup"><span data-stu-id="a66f5-134">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a66f5-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="a66f5-135">Example</span></span>  
 <span data-ttu-id="a66f5-136">Poniżej przedstawiono przykład sposobu konfigurowania filtru, który rejestruje tylko komunikaty, które mają sekcję nagłówka SOAP.</span><span class="sxs-lookup"><span data-stu-id="a66f5-136">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="420">
  <filters>
    <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
      /soap:Envelope/soap:Headers
    </add>
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a><span data-ttu-id="a66f5-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a66f5-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="a66f5-138">Konfigurowanie rejestrowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="a66f5-138">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="a66f5-139">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="a66f5-139">\<messageLogging></span></span>](messagelogging.md)
