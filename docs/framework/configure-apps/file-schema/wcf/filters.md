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
# <a name="filters"></a>\<Filtry >

`filters` Element posiada kolekcję filtrów XPath używanych do kontroli rodzaju rejestrowanych komunikatów.

Filtry są stosowane tylko w warstwie transportowej, określonej `logMessagesAtTransportLevel` przez `true`is. Filtry nie wpływają na poziom usług i źle sformułowane rejestrowanie komunikatów.

Aby dodać filtr do kolekcji, użyj `add` słowa kluczowego. Jeśli zdefiniowano co najmniej jeden filtr, rejestrowane są tylko komunikaty zgodne z co najmniej jednym filtrem. Jeśli żaden filtr nie jest zdefiniowany, wszystkie komunikaty są przekazywane.

Filtry obsługują pełną składnię XPath i są stosowane w kolejności, w której pojawiają się w pliku konfiguracji. Składnia nieprawidłowego filtru powoduje wyjątek w konfiguracji.

Poniżej przedstawiono przykład sposobu konfigurowania filtru, który rejestruje tylko komunikaty, które mają sekcję nagłówka SOAP.
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [Konfigurowanie rejestrowania komunikatów](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging >](messagelogging.md)
