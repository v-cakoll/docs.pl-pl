---
title: '&lt;add&gt; w &lt;filters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1ca0d5ae73d01e5bbb719f7bcc9a3f5a19fc291
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltfiltersgt"></a><span data-ttu-id="a5877-102">&lt;add&gt; w &lt;filters&gt;</span><span class="sxs-lookup"><span data-stu-id="a5877-102">&lt;add&gt; of &lt;filters&gt;</span></span>
<span data-ttu-id="a5877-103">Filtr XPath określa rodzaj rejestrowanych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a5877-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="a5877-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a5877-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a5877-105">\<diagnostycznych ></span><span class="sxs-lookup"><span data-stu-id="a5877-105">\<diagnostic></span></span>  
<span data-ttu-id="a5877-106">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="a5877-106">\<messageLogging></span></span>  
<span data-ttu-id="a5877-107">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="a5877-107">\<filters></span></span>  
<span data-ttu-id="a5877-108">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="a5877-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5877-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5877-109">Syntax</span></span>  
  
```xml  
<filters>  
   <add filter="String"/>  
</filters>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5877-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a5877-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a5877-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a5877-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5877-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a5877-112">Attributes</span></span>  
  
|<span data-ttu-id="a5877-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a5877-113">Attribute</span></span>|<span data-ttu-id="a5877-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a5877-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a5877-115">filtr</span><span class="sxs-lookup"><span data-stu-id="a5877-115">filter</span></span>|<span data-ttu-id="a5877-116">Ciąg określający zapytanie na dokumencie XML zdefiniowany za pomocą wyrażenia XPath 1.0.</span><span class="sxs-lookup"><span data-stu-id="a5877-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="a5877-117">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="a5877-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5877-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a5877-118">Child Elements</span></span>  
 <span data-ttu-id="a5877-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="a5877-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a5877-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a5877-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a5877-121">Element</span><span class="sxs-lookup"><span data-stu-id="a5877-121">Element</span></span>|<span data-ttu-id="a5877-122">Opis</span><span class="sxs-lookup"><span data-stu-id="a5877-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5877-123">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="a5877-123">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|<span data-ttu-id="a5877-124">Zawiera kolekcję filtrów XPath używane do kontrolowania, jakiego rodzaju komunikat jest rejestrowany.</span><span class="sxs-lookup"><span data-stu-id="a5877-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5877-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5877-125">Remarks</span></span>  
 <span data-ttu-id="a5877-126">Filtry są stosowane tylko w przypadku warstwy transportu, określonej przez `logMessagesAtTransportLevel` jest `true`.</span><span class="sxs-lookup"><span data-stu-id="a5877-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="a5877-127">Usługa rejestrowania komunikatów poziomu i źle sformułowane nie dotyczy filtrów.</span><span class="sxs-lookup"><span data-stu-id="a5877-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="a5877-128">Aby dodać filtr do kolekcji, użyj `add` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="a5877-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="a5877-129">Po zdefiniowaniu co najmniej jeden filtr są rejestrowane tylko komunikatów spełniających co najmniej jeden z filtrów.</span><span class="sxs-lookup"><span data-stu-id="a5877-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="a5877-130">Jeśli nie jest definiować filtru, wszystkie komunikaty przekazywane.</span><span class="sxs-lookup"><span data-stu-id="a5877-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="a5877-131">Filtry obsługuje pełnej składni języka XPath i są stosowane w kolejności, w jakiej znajdują się w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a5877-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="a5877-132">Nieprawidłowy filtr powoduje wyjątek konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a5877-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="a5877-133">Poniżej znajduje się przykład sposobu konfigurowania filtr, który rejestruje tylko komunikaty, które mają sekcji nagłówka SOAP.</span><span class="sxs-lookup"><span data-stu-id="a5877-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5877-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5877-134">Example</span></span>  
 <span data-ttu-id="a5877-135">Poniżej znajduje się przykład sposobu konfigurowania filtr, który rejestruje tylko komunikaty, które mają sekcji nagłówka SOAP.</span><span class="sxs-lookup"><span data-stu-id="a5877-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"  
     logMalformedMessages="true" logMessagesAtServiceLevel="true"  
     logMessagesAtTransportLevel="true" maxMessagesToLog="420">  
     <filters>  
        <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">  
                        /soap:Envelope/soap:Headers  
        </add>  
     </filters>  
</messageLogging>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5877-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5877-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>  
 <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>  
 [<span data-ttu-id="a5877-137">Konfigurowanie rejestrowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="a5877-137">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [<span data-ttu-id="a5877-138">Konfigurowanie rejestrowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="a5877-138">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [<span data-ttu-id="a5877-139">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="a5877-139">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
