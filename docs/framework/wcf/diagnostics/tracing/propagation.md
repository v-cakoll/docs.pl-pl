---
title: Propagacja
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: faa0e6ecb53963587e3fc253cd8beae1dc2c4bf5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154040"
---
# <a name="propagation"></a>Propagacja
W tym temacie opisano Propagacja działania w modelu śledzenia usług Windows Communication Foundation (WCF).  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a>Korelowanie działania punktów końcowych przy użyciu propagacji  
 Propagacja zapewnia użytkownikowi bezpośrednia korelacja błąd ślady dla tej samej jednostki przetwarzania między punktami końcowymi aplikacji, na przykład żądania. Emitowane na różne punkty końcowe dla tej samej jednostki przetwarzania, błędy są grupowane w tym samym działaniu, nawet w różnych domenach aplikacji. Jest to realizowane za pośrednictwem Propagacja identyfikatora działania w nagłówkach wiadomości. W związku z tym jeśli upłynie limit czasu klienta z powodu wewnętrznego błędu serwera, oba błędy są wyświetlane w tym samym działaniu dla bezpośrednia korelacja.  
  
 Aby to zrobić, należy użyć `ActivityTracing` ustawienia, jak pokazano w poprzednim przykładzie. Dodatkowo, ustawienia `propagateActivity` atrybutu dla `System.ServiceModel` źródła śledzenia w wszystkie punkty końcowe.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 Propagacja działania jest konfigurowalnych możliwości, który powoduje, że WCF można dodać nagłówka do wiadomości wychodzących, która zawiera identyfikator działania na TLS. Jeśli dołączysz to na kolejne ślady po stronie serwera, firma Microsoft skorelować działania klienta i serwera.  
  
## <a name="propagation-definition"></a>Propagacji definicji  
 GAId M działania jest propagowana do działania N, jeśli wszystkie następujące warunki zastosowania.  
  
-   N jest tworzony z powodu M  
  
-   Wiadomo gAId firmy M, N  
  
-   GAId firmy N jest równy gAId firmy M.  
  
 GAId są propagowane przez identyfikator nagłówka wiadomości, jak pokazano w poniższym schematu XML.  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 Oto przykład nagłówka komunikatu.  
  
```xml  
<MessageLogTraceRecord>  
  <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"
                      xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      <a:Action s:mustUnderstand="1">http://Microsoft.ServiceModel.Samples/ICalculator/Subtract  
      </a:Action>  
      <a:MessageID>urn:uuid:f0091eae-d339-4c7e-9408-ece34602f1ce  
      </a:MessageID>  
      <ActivityId CorrelationId="f94c6af1-7d5d-4295-b693-4670a8a0ce34"
               xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">  
        17f59a29-b435-4a15-bf7b-642ffc40eac8  
      </ActivityId>  
      <a:ReplyTo>  
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
      </a:ReplyTo>  
      <a:To s:mustUnderstand="1">net.tcp://localhost/servicemodelsamples/service</a:To>  
   </s:Header>  
   <s:Body>  
     <Subtract xmlns="http://Microsoft.ServiceModel.Samples">  
       <n1>145</n1>  
       <n2>76.54</n2>  
     </Subtract>  
   </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
## <a name="propagation-and-activity-boundaries"></a>Propagacja i granice działania  
 Po identyfikator działania są propagowane w obrębie punktów końcowych, odbiorcom wiadomości emituje jest rozpoczęcie i zatrzymanie ślady za pomocą tego identyfikatora działania (propagowany). Dlatego jest uruchamianie i zatrzymywanie śledzenia przy użyciu tego gAId z każdego źródła śledzenia. Jeśli punkty końcowe są w tym samym procesie, użyj tej samej nazwy źródła śledzenia wielu uruchamianie i zatrzymywanie, o tej samej sekcji (tego samego gAId, tego samego źródła śledzenia, ten sam proces) są tworzone.  
  
## <a name="synchronization"></a>Synchronizacja  
 Aby zsynchronizować zdarzenia różnych punktów końcowych, które działają na różnych maszynach, CorrelationId jest dodawany do nagłówka ActivityId, która jest propagowana do wiadomości. Narzędzia można użyć tego Identyfikatora synchronizacji zdarzeń na komputerach z rozbieżność zegara. W szczególności narzędzia przeglądarki danych śledzenia usługi używa tego Identyfikatora do wyświetlania komunikatu przepływów między punktami końcowymi.  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Scenariusze kompleksowego śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
