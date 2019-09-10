---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: 9291c38af28c18d20e23e34e8316b4a9fe523123
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855124"
---
# <a name="messagelogging"></a>\<messageLogging >
Ten element definiuje ustawienia dla możliwości rejestrowania komunikatów Windows Communication Foundation (WCF).  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> diagnostyki**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<messageLogging >**  
  
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
|`logEntireMessage`|Wartość logiczna określająca, czy cały komunikat (nagłówek i treść wiadomości) jest rejestrowany. Wartość domyślna to `false`, co oznacza, że rejestrowany jest tylko nagłówek komunikatu. To ustawienie ma wpływ na wszystkie poziomy rejestrowania komunikatów (usługa, transport i nieprawidłowo sformułowane).|  
|`logMalformedMessages`|Wartość logiczna określająca, czy źle sformułowane komunikaty są rejestrowane. Źle sformułowane wiadomości nie są wliczane do `maxMessagesToLog`. Wartość domyślna to `false`.|  
|`logMessagesAtServiceLevel`|Wartość logiczna określająca, czy komunikaty są śledzone na poziomie usługi (przed szyfrowaniem i transformami związanymi z transportem). Wartość domyślna to `false`.|  
|`logMessagesAtTransportLevel`|Wartość logiczna określająca, czy komunikaty są śledzone na poziomie transportu. Wszystkie filtry określone w pliku konfiguracyjnym są stosowane i śledzone są tylko komunikaty zgodne z filtrami. Wartość domyślna to `false`.|  
|`maxMessagesToLog`|Dodatnia liczba całkowita, która określa maksymalną liczbę komunikatów do zarejestrowania. Wartość domyślna to 1000.|  
|`maxSizeOfMessageToLog`|Dodatnia liczba całkowita, która określa maksymalny rozmiar komunikatu do zarejestrowania w bajtach. Komunikaty przekraczające limit nie będą rejestrowane. To ustawienie ma wpływ na wszystkie poziomy śledzenia. Wartość domyślna to 262 144 (0x4000).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|filtry|`filters` Element przechowuje kolekcję filtrów XPath. Gdy rejestrowanie komunikatów transportu jest włączone (`logMessagesAtTransportLevel` is `true`), rejestrowane będą tylko komunikaty pasujące do filtrów.<br /><br /> Filtry są stosowane tylko w warstwie transportowej. Filtry nie wpływają na poziom usług i źle sformułowane rejestrowanie komunikatów.<br /><br /> Jedynym atrybutem dla tego elementu `filter`,,, jest obiekt XPathFilter.<br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|diagnostyka|Definiuje ustawienia WCF na potrzeby inspekcji i kontroli środowiska uruchomieniowego dla administratora.|  
  
## <a name="remarks"></a>Uwagi  
 Komunikaty są rejestrowane na trzech różnych poziomach w stosie: Service, transport i źle sformułowane. Każdy poziom można aktywować osobno.  
  
 Filtry XPath można dodawać do rejestrowania określonych komunikatów na poziomie transportu i usług. Jeśli żadne filtry nie są zdefiniowane, wszystkie komunikaty są rejestrowane. Filtry są stosowane tylko do nagłówków wiadomości. Treść jest ignorowana. Funkcja WCF ignoruje treść komunikatu w celu zwiększenia wydajności. Jeśli chcesz filtrować w oparciu o zawartość treści, możesz utworzyć niestandardowy odbiornik z filtrem, który to robi.  
  
 Musisz utworzyć odbiornik śledzenia, aby aktywować śledzenie komunikatów. Odbiornik może być dowolnym odbiornikiem, który współpracuje z <xref:System.Diagnostics> architekturą śledzenia. W poniższym przykładzie pokazano, jak utworzyć taki odbiornik.  
  
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
- [Konfigurowanie rejestrowania komunikatów](../../../wcf/diagnostics/configuring-message-logging.md)
