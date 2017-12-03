---
title: Propagacja
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a993ec836417906229e47b7f415f4aee8b1a9eb1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="propagation"></a>Propagacja
W tym temacie opisano działanie propagacją [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] śledzenie modelu.  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a>Przy użyciu propagacji służące do skorelowania działań w obrębie punktów końcowych  
 Propagacja zapewnia użytkownikowi bezpośredni korelacji błędu śledzi w tej samej jednostce przetwarzania przez punkty końcowe aplikacji, na przykład żądania. Błędy emitowane na różnych punktów końcowych w tej samej jednostce przetwarzania są pogrupowane w to samo działanie nawet w różnych domenach aplikacji. Jest to realizowane za pośrednictwem Propagacja identyfikatora działania w nagłówkach wiadomości. W związku z tym jeśli upłynie limit czasu klienta z powodu wewnętrznego błędu serwera, oba błędy są wyświetlane w to samo działanie do bezpośredniego korelacji.  
  
 Aby to zrobić, użyj `ActivityTracing` ustawienie, jak pokazano w poprzednim przykładzie. Ponadto ustawić `propagateActivity` atrybutu dla `System.ServiceModel` źródła śledzenia na wszystkich punktów końcowych.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 Propagacja działania jest konfigurowalne możliwości, który powoduje, że [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] można dodać nagłówka do wiadomości wychodzących, takich jak identyfikator działania na TLS. Jeśli dołączysz to na kolejnych ślady po stronie serwera, firma Microsoft skorelowania działania klienta i serwera.  
  
## <a name="propagation-definition"></a>Propagacji definicji  
 GAId M działania jest propagowana do działania N, jeśli wszystkie następujące warunki.  
  
-   N została utworzona, ponieważ M  
  
-   W M gAId jest znana N  
  
-   W N gAId jest równa gAId M firmy.  
  
 GAId są propagowane za pomocą identyfikatora nagłówek komunikatu, jak pokazano na poniższej schematu XML.  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 Poniżej przedstawiono przykładowy nagłówek komunikatu.  
  
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
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous  
          </a:Address>  
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
 Gdy identyfikator działania są propagowane w obrębie punktów końcowych, odbiorcy wiadomości emituje rozpoczęcia i zatrzymania śledzi z tym identyfikatorem działania (propagowany). W związku z tym jest rozpoczęcie i zakończenie śledzenia z tym gAId z każdego źródła śledzenia. Jeśli punkty końcowe w ramach tego samego procesu, użyj takiej samej nazwy źródła śledzenia są tworzone wielu rozpoczęcie i zakończenie o tej samej sekcji (tego samego gAId, tego samego źródła śledzenia, sam proces).  
  
## <a name="synchronization"></a>Synchronizacja  
 Aby zsynchronizować zdarzenia przez punkty końcowe, które działają na różnych maszynach, CorrelationId jest dodawana do nagłówka identyfikatora, który są propagowane w wiadomości. Narzędzia można użyć tego Identyfikatora zsynchronizować zdarzeń na komputerach z rozbieżność zegara. W szczególności narzędzia podglądu śledzenia usługi używa tego Identyfikatora wyświetlania przepływów wiadomości między punktami końcowymi.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [Przy użyciu przeglądarki śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Scenariusze śledzenia end-To-End](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [Narzędzie podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
