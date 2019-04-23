---
title: <add> dla <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 399fc4e22a9253469a5494af61dac862e33814a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59128703"
---
# <a name="add-of-filters"></a><span data-ttu-id="0584e-102">\<Dodaj > z \<Filtry ></span><span class="sxs-lookup"><span data-stu-id="0584e-102">\<add> of \<filters></span></span>
<span data-ttu-id="0584e-103">Filtr XPath określa rodzaj rejestrowanych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0584e-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="0584e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0584e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0584e-105">\<diagnostyczne ></span><span class="sxs-lookup"><span data-stu-id="0584e-105">\<diagnostic></span></span>  
<span data-ttu-id="0584e-106">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="0584e-106">\<messageLogging></span></span>  
<span data-ttu-id="0584e-107">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="0584e-107">\<filters></span></span>  
<span data-ttu-id="0584e-108">\<add></span><span class="sxs-lookup"><span data-stu-id="0584e-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0584e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="0584e-109">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0584e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0584e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0584e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0584e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0584e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0584e-112">Attributes</span></span>  
  
|<span data-ttu-id="0584e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0584e-113">Attribute</span></span>|<span data-ttu-id="0584e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="0584e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0584e-115">filtr</span><span class="sxs-lookup"><span data-stu-id="0584e-115">filter</span></span>|<span data-ttu-id="0584e-116">Ciąg określający zapytanie na dokumencie XML, który jest zdefiniowany przez wyrażenie XPath 1.0.</span><span class="sxs-lookup"><span data-stu-id="0584e-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="0584e-117">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="0584e-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0584e-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0584e-118">Child Elements</span></span>  
 <span data-ttu-id="0584e-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="0584e-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0584e-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0584e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0584e-121">Element</span><span class="sxs-lookup"><span data-stu-id="0584e-121">Element</span></span>|<span data-ttu-id="0584e-122">Opis</span><span class="sxs-lookup"><span data-stu-id="0584e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0584e-123">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="0584e-123">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|<span data-ttu-id="0584e-124">Zawiera kolekcję filtrów XPath używane do kontrolowania, jakiego rodzaju komunikat jest rejestrowany.</span><span class="sxs-lookup"><span data-stu-id="0584e-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0584e-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0584e-125">Remarks</span></span>  
 <span data-ttu-id="0584e-126">Filtry są stosowane tylko w przypadku warstwy transportu, określonej przez `logMessagesAtTransportLevel` jest `true`.</span><span class="sxs-lookup"><span data-stu-id="0584e-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="0584e-127">Rejestrowanie komunikatów poziomu i źle sformułowane usługi nie dotyczy filtrów.</span><span class="sxs-lookup"><span data-stu-id="0584e-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="0584e-128">Aby dodać filtr do kolekcji, należy użyć `add` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="0584e-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="0584e-129">Po zdefiniowaniu co najmniej jeden filtr tylko komunikatów spełniających co najmniej jeden z filtrów są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="0584e-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="0584e-130">Jeśli nie zdefiniowano żadnego filtru, wszystkie komunikaty przechodzi przez.</span><span class="sxs-lookup"><span data-stu-id="0584e-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="0584e-131">Filtry obsługuje pełnej składni XPath i są stosowane w kolejności, w jakiej znajdują się w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0584e-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="0584e-132">Nieprawidłowy filtr powoduje wyjątek konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0584e-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="0584e-133">Oto przykład sposobu konfigurowania filtru, który rejestruje tylko komunikaty, które mają sekcję nagłówek SOAP.</span><span class="sxs-lookup"><span data-stu-id="0584e-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0584e-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="0584e-134">Example</span></span>  
 <span data-ttu-id="0584e-135">Oto przykład sposobu konfigurowania filtru, który rejestruje tylko komunikaty, które mają sekcję nagłówek SOAP.</span><span class="sxs-lookup"><span data-stu-id="0584e-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0584e-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0584e-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="0584e-137">Konfigurowanie rejestrowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="0584e-137">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="0584e-138">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="0584e-138">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
