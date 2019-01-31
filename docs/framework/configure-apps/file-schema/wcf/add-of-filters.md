---
title: <add> z <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 0e42766cd94b58562bc5728d517e65e80f558cda
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288798"
---
# <a name="add-of-filters"></a><span data-ttu-id="4d56b-102">\<Dodaj > z \<Filtry ></span><span class="sxs-lookup"><span data-stu-id="4d56b-102">\<add> of \<filters></span></span>
<span data-ttu-id="4d56b-103">Filtr XPath określa rodzaj rejestrowanych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4d56b-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="4d56b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4d56b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4d56b-105">\<diagnostyczne ></span><span class="sxs-lookup"><span data-stu-id="4d56b-105">\<diagnostic></span></span>  
<span data-ttu-id="4d56b-106">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="4d56b-106">\<messageLogging></span></span>  
<span data-ttu-id="4d56b-107">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="4d56b-107">\<filters></span></span>  
<span data-ttu-id="4d56b-108">\<add></span><span class="sxs-lookup"><span data-stu-id="4d56b-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d56b-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d56b-109">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d56b-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4d56b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4d56b-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4d56b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d56b-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4d56b-112">Attributes</span></span>  
  
|<span data-ttu-id="4d56b-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4d56b-113">Attribute</span></span>|<span data-ttu-id="4d56b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4d56b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d56b-115">filtr</span><span class="sxs-lookup"><span data-stu-id="4d56b-115">filter</span></span>|<span data-ttu-id="4d56b-116">Ciąg określający zapytanie na dokumencie XML, który jest zdefiniowany przez wyrażenie XPath 1.0.</span><span class="sxs-lookup"><span data-stu-id="4d56b-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="4d56b-117">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="4d56b-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d56b-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4d56b-118">Child Elements</span></span>  
 <span data-ttu-id="4d56b-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="4d56b-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d56b-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4d56b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4d56b-121">Element</span><span class="sxs-lookup"><span data-stu-id="4d56b-121">Element</span></span>|<span data-ttu-id="4d56b-122">Opis</span><span class="sxs-lookup"><span data-stu-id="4d56b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d56b-123">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="4d56b-123">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|<span data-ttu-id="4d56b-124">Zawiera kolekcję filtrów XPath używane do kontrolowania, jakiego rodzaju komunikat jest rejestrowany.</span><span class="sxs-lookup"><span data-stu-id="4d56b-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d56b-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d56b-125">Remarks</span></span>  
 <span data-ttu-id="4d56b-126">Filtry są stosowane tylko w przypadku warstwy transportu, określonej przez `logMessagesAtTransportLevel` jest `true`.</span><span class="sxs-lookup"><span data-stu-id="4d56b-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="4d56b-127">Rejestrowanie komunikatów poziomu i źle sformułowane usługi nie dotyczy filtrów.</span><span class="sxs-lookup"><span data-stu-id="4d56b-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="4d56b-128">Aby dodać filtr do kolekcji, należy użyć `add` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="4d56b-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="4d56b-129">Po zdefiniowaniu co najmniej jeden filtr tylko komunikatów spełniających co najmniej jeden z filtrów są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="4d56b-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="4d56b-130">Jeśli nie zdefiniowano żadnego filtru, wszystkie komunikaty przechodzi przez.</span><span class="sxs-lookup"><span data-stu-id="4d56b-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="4d56b-131">Filtry obsługuje pełnej składni XPath i są stosowane w kolejności, w jakiej znajdują się w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4d56b-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="4d56b-132">Nieprawidłowy filtr powoduje wyjątek konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4d56b-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="4d56b-133">Oto przykład sposobu konfigurowania filtru, który rejestruje tylko komunikaty, które mają sekcję nagłówek SOAP.</span><span class="sxs-lookup"><span data-stu-id="4d56b-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d56b-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d56b-134">Example</span></span>  
 <span data-ttu-id="4d56b-135">Oto przykład sposobu konfigurowania filtru, który rejestruje tylko komunikaty, które mają sekcję nagłówek SOAP.</span><span class="sxs-lookup"><span data-stu-id="4d56b-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4d56b-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d56b-136">See also</span></span>
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="4d56b-137">Konfigurowanie rejestrowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="4d56b-137">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="4d56b-138">Konfigurowanie rejestrowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="4d56b-138">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="4d56b-139">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="4d56b-139">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
