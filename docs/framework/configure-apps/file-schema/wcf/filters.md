---
title: '&lt;Filtry&gt;'
ms.date: 03/30/2017
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
ms.openlocfilehash: aae70fbe873eee10fcf95dcdd443dfa9ae6efb57
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148971"
---
# <a name="ltfiltersgt"></a>&lt;Filtry&gt;

`filters` Element przetrzymuje kolekcję filtrów XPath używane do kontrolowania, jakiego rodzaju komunikat jest rejestrowany.

Filtry są stosowane tylko w przypadku warstwy transportu, określonej przez `logMessagesAtTransportLevel` jest `true`. Rejestrowanie komunikatów poziomu i źle sformułowane usługi nie dotyczy filtrów.

Aby dodać filtr do kolekcji, należy użyć `add` — słowo kluczowe. Po zdefiniowaniu co najmniej jeden filtr tylko komunikatów spełniających co najmniej jeden z filtrów są rejestrowane. Jeśli nie zdefiniowano żadnego filtru, wszystkie komunikaty przechodzi przez.

Filtry obsługuje pełnej składni XPath i są stosowane w kolejności, w jakiej znajdują się w pliku konfiguracji. Nieprawidłowy filtr powoduje wyjątek konfiguracji.

Oto przykład sposobu konfigurowania filtru, który rejestruje tylko komunikaty, które mają sekcję nagłówek SOAP.
  
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

 <xref:System.ServiceModel.Configuration.DiagnosticSection><xref:System.ServiceModel.Diagnostics>
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>
 <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
 <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
 <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
 [Konfigurowanie rejestrowania komunikatów](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) [ \<messageLogging >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
