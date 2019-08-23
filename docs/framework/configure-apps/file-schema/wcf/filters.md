---
title: <filters>
ms.date: 03/30/2017
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
ms.openlocfilehash: e4ce0452cc46a8f29334fa67f51f14b83290b1c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918878"
---
# <a name="filters"></a><span data-ttu-id="6f90a-101">\<Filtry ></span><span class="sxs-lookup"><span data-stu-id="6f90a-101">\<filters></span></span>

<span data-ttu-id="6f90a-102">`filters` Element posiada kolekcję filtrów XPath używanych do kontroli rodzaju rejestrowanych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6f90a-102">The `filters` element holds a collection of XPath filters used to control what kind of message is logged.</span></span>

<span data-ttu-id="6f90a-103">Filtry są stosowane tylko w warstwie transportowej, określonej `logMessagesAtTransportLevel` przez `true`is.</span><span class="sxs-lookup"><span data-stu-id="6f90a-103">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="6f90a-104">Filtry nie wpływają na poziom usług i źle sformułowane rejestrowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6f90a-104">Service level and malformed message logging are not affected by filters.</span></span>

<span data-ttu-id="6f90a-105">Aby dodać filtr do kolekcji, użyj `add` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="6f90a-105">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="6f90a-106">Jeśli zdefiniowano co najmniej jeden filtr, rejestrowane są tylko komunikaty zgodne z co najmniej jednym filtrem.</span><span class="sxs-lookup"><span data-stu-id="6f90a-106">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="6f90a-107">Jeśli żaden filtr nie jest zdefiniowany, wszystkie komunikaty są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="6f90a-107">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="6f90a-108">Filtry obsługują pełną składnię XPath i są stosowane w kolejności, w której pojawiają się w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6f90a-108">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="6f90a-109">Składnia nieprawidłowego filtru powoduje wyjątek w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6f90a-109">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="6f90a-110">Poniżej przedstawiono przykład sposobu konfigurowania filtru, który rejestruje tylko komunikaty, które mają sekcję nagłówka SOAP.</span><span class="sxs-lookup"><span data-stu-id="6f90a-110">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f90a-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f90a-111">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="6f90a-112">Konfigurowanie rejestrowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="6f90a-112">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="6f90a-113">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="6f90a-113">\<messageLogging></span></span>](messagelogging.md)
