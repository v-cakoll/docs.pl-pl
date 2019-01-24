---
title: '&lt;Filtry&gt;'
ms.date: 03/30/2017
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
ms.openlocfilehash: 5f50b1ad4abfa77022a17d6497b614721382ec1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600196"
---
# <a name="ltfiltersgt"></a><span data-ttu-id="41a54-102">&lt;Filtry&gt;</span><span class="sxs-lookup"><span data-stu-id="41a54-102">&lt;filters&gt;</span></span>

<span data-ttu-id="41a54-103">`filters` Element przetrzymuje kolekcję filtrów XPath używane do kontrolowania, jakiego rodzaju komunikat jest rejestrowany.</span><span class="sxs-lookup"><span data-stu-id="41a54-103">The `filters` element holds a collection of XPath filters used to control what kind of message is logged.</span></span>

<span data-ttu-id="41a54-104">Filtry są stosowane tylko w przypadku warstwy transportu, określonej przez `logMessagesAtTransportLevel` jest `true`.</span><span class="sxs-lookup"><span data-stu-id="41a54-104">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="41a54-105">Rejestrowanie komunikatów poziomu i źle sformułowane usługi nie dotyczy filtrów.</span><span class="sxs-lookup"><span data-stu-id="41a54-105">Service level and malformed message logging are not affected by filters.</span></span>

<span data-ttu-id="41a54-106">Aby dodać filtr do kolekcji, należy użyć `add` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="41a54-106">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="41a54-107">Po zdefiniowaniu co najmniej jeden filtr tylko komunikatów spełniających co najmniej jeden z filtrów są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="41a54-107">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="41a54-108">Jeśli nie zdefiniowano żadnego filtru, wszystkie komunikaty przechodzi przez.</span><span class="sxs-lookup"><span data-stu-id="41a54-108">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="41a54-109">Filtry obsługuje pełnej składni XPath i są stosowane w kolejności, w jakiej znajdują się w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="41a54-109">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="41a54-110">Nieprawidłowy filtr powoduje wyjątek konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="41a54-110">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="41a54-111">Oto przykład sposobu konfigurowania filtru, który rejestruje tylko komunikaty, które mają sekcję nagłówek SOAP.</span><span class="sxs-lookup"><span data-stu-id="41a54-111">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="41a54-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41a54-112">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="41a54-113">Konfigurowanie rejestrowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="41a54-113">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="41a54-114">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="41a54-114">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
