---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: 79fadb422a2330677bc5d8c64c81931615b6be91
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289773"
---
# <a name="messagelogging"></a>\<messageLogging>
Ten element definiuje ustawienia dla możliwości rejestrowania komunikatów Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<diagnostyczne >  
\<messageLogging>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`logEntireMessage`|Wartość logiczna określająca, czy cały komunikat (nagłówek i treść wiadomości) jest rejestrowane. Wartość domyślna to `false`, co oznacza, że tylko nagłówek wiadomości jest rejestrowane. To ustawienie ma wpływ na wszystkie poziomy rejestrowania komunikatu (usługi, transport i jest źle sformułowane).|  
|`logMalformedMessages`|Wartość logiczna określająca czy wadliwe komunikaty są rejestrowane. Źle sformułowane komunikaty nie są uwzględniane w kierunku `maxMessagesToLog`. Wartość domyślna to `false`.|  
|`logMessagesAtServiceLevel`|Wartość logiczna określająca, czy komunikaty są śledzone na poziomie usługi (przed szyfrowania — i transformacjami związanymi z transportem). Wartość domyślna to `false`.|  
|`logMessagesAtTransportLevel`|Wartość logiczna określająca, czy komunikaty są śledzone na poziomie transportu. Filtry w pliku konfiguracyjnym zostały zastosowane, a tylko te komunikaty, które pasują do filtrów są śledzone. Wartość domyślna to `false`.|  
|`maxMessagesToLog`|Dodatnia liczba całkowita, określająca maksymalną liczbę wiadomości rejestrowaną w dzienniku. Wartość domyślna to 1000.|  
|`maxSizeOfMessageToLog`|Dodatnia liczba całkowita, która określa maksymalny rozmiar w bajtach, komunikat do zarejestrowania. Większy niż limit komunikaty nie zostaną zarejestrowane. To ustawienie ma wpływ na wszystkie poziomy śledzenia. Wartość domyślna to 262144(0x4000).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|filtry|`filters` Element przetrzymuje kolekcję filtrów XPath. Po włączeniu rejestrowania komunikatów transportu (`logMessagesAtTransportLevel` jest `true`), będą rejestrowane tylko wiadomości pasujące do filtrów.<br /><br /> Filtry są stosowane tylko w warstwie transportowej. Rejestrowanie komunikatów poziomu i źle sformułowane usługi nie dotyczy filtrów.<br /><br /> To jedyny atrybut dla tego elementu `filter`, to obiekt XpathFilter.<br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|diagnostyka|Definiuje ustawienia WCF dla środowiska uruchomieniowego kontroli i kontroli dla administratora.|  
  
## <a name="remarks"></a>Uwagi  
 Komunikaty są rejestrowane na trzech różnych poziomach w stosie: usługa, transport i jest nieprawidłowo sformułowany. Każdy poziom można aktywować oddzielnie.  
  
 Filtrach XPath można dodać do logowania określonego wiadomości na poziomie transportu i usług. Jeśli zdefiniowano żadnych filtrów, wszystkie komunikaty są rejestrowane. Filtry są stosowane tylko do nagłówków wiadomości. Treść jest ignorowany. Usługi WCF ignoruje treść wiadomości, aby zwiększyć wydajność. Jeśli chcesz filtrować na podstawie zawartości treści, można utworzyć odbiornika niestandardowych za pomocą filtru, która wykonuje.  
  
 Należy utworzyć odbiornik śledzenia, aby uaktywnić śledzenie wiadomości. Odbiornik, sama może być dowolnym odbiornik, który współdziała z <xref:System.Diagnostics> architektury śledzenia. Poniższy przykład przedstawia sposób tworzenia takie odbiornik.  
  
```xml  
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel"
            switchValue="Verbose">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="ServiceModel Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
    <source name="System.ServiceModel.MessageLogging">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="MessageLogging Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
  </sources>
  <sharedListeners>
    <add initializeData="C:\ItProTools\TraceLog.xml"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="ServiceModel Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
    <add initializeData="C:\ItProTools\MessageLog.log"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="MessageLogging Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
  </sharedListeners>
</system.diagnostics>
```  
  
## <a name="example"></a>Przykład  
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="42"
                maxSizeOfMessageToLog="42">
  <filters>
    <clear />
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [Konfigurowanie rejestrowania komunikatów](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
