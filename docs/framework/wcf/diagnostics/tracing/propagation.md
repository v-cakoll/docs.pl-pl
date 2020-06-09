---
title: Propagacja
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: 732ae5cb1ce311b78728f8d5de0fd9102bf32499
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578958"
---
# <a name="propagation"></a>Propagacja
W tym temacie opisano propagację działań w modelu śledzenia Windows Communication Foundation (WCF).  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a>Używanie propagacji do skorelowania działań w punktach końcowych  
 Propagacja udostępnia użytkownikowi bezpośrednią korelację śladów błędów dla tej samej jednostki przetwarzania między punktami końcowymi aplikacji, na przykład żądania. Błędy emitowane w różnych punktach końcowych dla tej samej jednostki przetwarzania są pogrupowane w tym samym działaniu, nawet w różnych domenach aplikacji. Jest to realizowane przez propagację identyfikatora działania w nagłówkach wiadomości. W związku z tym, jeśli klient przeprowadzi limit czasu z powodu błędu wewnętrznego na serwerze, oba błędy pojawiają się w tym samym działaniu dla bezpośredniej korelacji.  
  
 Aby to zrobić, użyj `ActivityTracing` Ustawienia, jak pokazano w poprzednim przykładzie. Ponadto należy ustawić `propagateActivity` atrybut dla `System.ServiceModel` źródła śledzenia we wszystkich punktach końcowych.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 Propagacja działań to konfigurowalna funkcja, która powoduje, że program WCF dodaje nagłówek do komunikatów wychodzących, który obejmuje identyfikator działania w protokole TLS. W tym celu w przypadku kolejnych śladów po stronie serwera można skorelować działania klientów i serwerów.  
  
## <a name="propagation-definition"></a>Definicja propagacji  
 Podczas działania gAId M jest propagowany do działania N, jeśli spełnione są wszystkie poniższe warunki.  
  
- N jest tworzony z powodu M  
  
- GAId M jest znany jako N  
  
- GAId N jest równe gAId M.  
  
 GAId jest propagowany za pomocą nagłówka komunikatu ActivityId, jak pokazano w poniższym schemacie XML.  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 Poniżej znajduje się przykład nagłówka komunikatu.  
  
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
  
## <a name="propagation-and-activity-boundaries"></a>Propagowanie i granice działania  
 Gdy identyfikator działania jest propagowany między punktami końcowymi, odbiorca komunikatów emituje uruchomienie i zatrzymanie śladów z tym (propagowanym) IDENTYFIKATORem działania. W związku z tym istnieje rozpoczęcie i zatrzymanie śledzenia z tym gAId z każdego źródła śledzenia. Jeśli punkty końcowe są w tym samym procesie i używają tej samej nazwy źródła śledzenia, są tworzone wiele operacji uruchamiania i zatrzymywania z tymi samymi (gAId, tym samym źródłem śladów).  
  
## <a name="synchronization"></a>Synchronizacja  
 Aby synchronizować zdarzenia między punktami końcowymi, które działają na różnych komputerach, identyfikator korelacji jest dodawany do nagłówka ActivityId, który jest propagowany w komunikatach. Narzędzia mogą używać tego identyfikatora do synchronizowania zdarzeń między maszynami z niezgodnością zegara. Narzędzie Podgląd śledzenia usług używa tego identyfikatora do wyświetlania przepływów komunikatów między punktami końcowymi.  
  
## <a name="see-also"></a>Zobacz też

- [Konfigurowanie śledzenia](configuring-tracing.md)
- [Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Scenariusze kompleksowego śledzenia](end-to-end-tracing-scenarios.md)
- [Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md)
