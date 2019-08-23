---
title: <add> dla <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: e7975bea1435abdb77528628e7b96c65a72cbbc2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926698"
---
# <a name="add-of-filters"></a><span data-ttu-id="cf67c-102">\<Dodawanie > \<filtrów ></span><span class="sxs-lookup"><span data-stu-id="cf67c-102">\<add> of \<filters></span></span>
<span data-ttu-id="cf67c-103">Filtr XPath określa rodzaj wiadomości do zarejestrowania.</span><span class="sxs-lookup"><span data-stu-id="cf67c-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="cf67c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cf67c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cf67c-105">\<> diagnostyki</span><span class="sxs-lookup"><span data-stu-id="cf67c-105">\<diagnostic></span></span>  
<span data-ttu-id="cf67c-106">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="cf67c-106">\<messageLogging></span></span>  
<span data-ttu-id="cf67c-107">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="cf67c-107">\<filters></span></span>  
<span data-ttu-id="cf67c-108">\<add></span><span class="sxs-lookup"><span data-stu-id="cf67c-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf67c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf67c-109">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf67c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cf67c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cf67c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cf67c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf67c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cf67c-112">Attributes</span></span>  
  
|<span data-ttu-id="cf67c-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cf67c-113">Attribute</span></span>|<span data-ttu-id="cf67c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="cf67c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cf67c-115">filtr</span><span class="sxs-lookup"><span data-stu-id="cf67c-115">filter</span></span>|<span data-ttu-id="cf67c-116">Ciąg określający zapytanie na dokumencie XML zdefiniowanym przez wyrażenie XPath 1,0.</span><span class="sxs-lookup"><span data-stu-id="cf67c-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="cf67c-117">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="cf67c-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf67c-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cf67c-118">Child Elements</span></span>  
 <span data-ttu-id="cf67c-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="cf67c-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf67c-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cf67c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="cf67c-121">Element</span><span class="sxs-lookup"><span data-stu-id="cf67c-121">Element</span></span>|<span data-ttu-id="cf67c-122">Opis</span><span class="sxs-lookup"><span data-stu-id="cf67c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf67c-123">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="cf67c-123">\<filters></span></span>](filters.md)|<span data-ttu-id="cf67c-124">Zawiera kolekcję filtrów XPath używanych do kontroli rodzaju rejestrowanych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="cf67c-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf67c-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cf67c-125">Remarks</span></span>  
 <span data-ttu-id="cf67c-126">Filtry są stosowane tylko w warstwie transportowej, określonej `logMessagesAtTransportLevel` przez `true`is.</span><span class="sxs-lookup"><span data-stu-id="cf67c-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="cf67c-127">Filtry nie wpływają na poziom usług i źle sformułowane rejestrowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="cf67c-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="cf67c-128">Aby dodać filtr do kolekcji, użyj `add` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="cf67c-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="cf67c-129">Jeśli zdefiniowano co najmniej jeden filtr, rejestrowane są tylko komunikaty zgodne z co najmniej jednym filtrem.</span><span class="sxs-lookup"><span data-stu-id="cf67c-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="cf67c-130">Jeśli żaden filtr nie jest zdefiniowany, wszystkie komunikaty są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="cf67c-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="cf67c-131">Filtry obsługują pełną składnię XPath i są stosowane w kolejności, w której pojawiają się w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cf67c-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="cf67c-132">Składnia nieprawidłowego filtru powoduje wyjątek w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cf67c-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="cf67c-133">Poniżej przedstawiono przykład sposobu konfigurowania filtru, który rejestruje tylko komunikaty, które mają sekcję nagłówka SOAP.</span><span class="sxs-lookup"><span data-stu-id="cf67c-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf67c-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf67c-134">Example</span></span>  
 <span data-ttu-id="cf67c-135">Poniżej przedstawiono przykład sposobu konfigurowania filtru, który rejestruje tylko komunikaty, które mają sekcję nagłówka SOAP.</span><span class="sxs-lookup"><span data-stu-id="cf67c-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cf67c-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf67c-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="cf67c-137">Konfigurowanie rejestrowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="cf67c-137">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="cf67c-138">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="cf67c-138">\<messageLogging></span></span>](messagelogging.md)
