---
title: <filters>
ms.date: 03/30/2017
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
ms.openlocfilehash: e4ce0452cc46a8f29334fa67f51f14b83290b1c8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "69918878"
---
# \<filters>

<span data-ttu-id="43306-101">`filters`Element posiada kolekcję filtrów XPath używanych do kontroli rodzaju rejestrowanych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="43306-101">The `filters` element holds a collection of XPath filters used to control what kind of message is logged.</span></span>

<span data-ttu-id="43306-102">Filtry są stosowane tylko w warstwie transportowej, określonej przez `logMessagesAtTransportLevel` is `true` .</span><span class="sxs-lookup"><span data-stu-id="43306-102">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="43306-103">Filtry nie wpływają na poziom usług i źle sformułowane rejestrowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="43306-103">Service level and malformed message logging are not affected by filters.</span></span>

<span data-ttu-id="43306-104">Aby dodać filtr do kolekcji, użyj `add` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="43306-104">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="43306-105">Jeśli zdefiniowano co najmniej jeden filtr, rejestrowane są tylko komunikaty zgodne z co najmniej jednym filtrem.</span><span class="sxs-lookup"><span data-stu-id="43306-105">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="43306-106">Jeśli żaden filtr nie jest zdefiniowany, wszystkie komunikaty są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="43306-106">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="43306-107">Filtry obsługują pełną składnię XPath i są stosowane w kolejności, w której pojawiają się w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="43306-107">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="43306-108">Składnia nieprawidłowego filtru powoduje wyjątek w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="43306-108">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="43306-109">Poniżej przedstawiono przykład sposobu konfigurowania filtru, który rejestruje tylko komunikaty, które mają sekcję nagłówka SOAP.</span><span class="sxs-lookup"><span data-stu-id="43306-109">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="43306-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43306-110">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="43306-111">Konfigurowanie rejestrowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="43306-111">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](messagelogging.md)
