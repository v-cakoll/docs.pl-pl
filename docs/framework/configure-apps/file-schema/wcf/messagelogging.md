---
title: '&lt;messageLogging&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d2febd8582ded47827794762bf0fb842c8131666
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltmessagelogginggt"></a>&lt;messageLogging&gt;
Ten element definiuje ustawienia dla możliwości rejestrowania komunikatów Windows Communication Foundation (WCF).  
  
 \<System. ServiceModel >  
\<diagnostycznych >  
\<messageLogging >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <messageLogging logEntireMessage="Boolean"  
          logMalformedMessages="Boolean"  
          logMessagesAtServiceLevel="Boolean"  
          logMessagesAtTransportLevel="Boolean"  
                    maxMessagesToLog="Integer"  
          maxSizeOfMessageToLog="Integer" >  
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
|`logEntireMessage`|Wartość logiczna określająca, czy cały komunikat (nagłówek i treść wiadomości) jest zarejestrowany. Wartość domyślna to `false`, co oznacza, że tylko nagłówek komunikatu jest rejestrowane. To ustawienie ma wpływ na wszystkie poziomy rejestrowania komunikatów (usługi, transport i źle sformułowane).|  
|`logMalformedMessages`|Wartość logiczna określająca, czy wadliwe komunikaty są rejestrowane. Wadliwe komunikaty nie są wliczane do `maxMessagesToLog`. Wartość domyślna to `false`.|  
|`logMessagesAtServiceLevel`|Wartość logiczna określająca, czy komunikaty są śledzone na poziomie usługi (przed szyfrowania - i transformacjami związanymi z transportem). Wartość domyślna to `false`.|  
|`logMessagesAtTransportLevel`|Wartość logiczna określająca, czy komunikaty są śledzone na poziomie transportu. Wszystkie filtry w pliku konfiguracyjnym są stosowane, a tylko komunikaty zgodne z filtrami są śledzone. Wartość domyślna to `false`.|  
|`maxMessagesToLog`|Dodatnia liczba całkowita, która określa maksymalną liczbę komunikatów do zarejestrowania. Wartość domyślna to 1000.|  
|`maxSizeOfMessageToLog`|Dodatnia liczba całkowita, która określa maksymalny rozmiar w bajtach komunikatu do dziennika. Wiadomości przekracza limit nie będą rejestrowane. To ustawienie ma wpływ na wszystkie poziomy śledzenia. Wartość domyślna to 262144(0x4000).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|filtry|`filters` Element przetrzymuje kolekcję filtrów XPath. Po włączeniu rejestrowania komunikatów transportu (`logMessagesAtTransportLevel` jest `true`), będą rejestrowane tylko komunikatów spełniających kryteria filtrów.<br /><br /> Filtry są stosowane tylko w przypadku warstwy transportu. Usługa rejestrowania komunikatów poziomu i źle sformułowane nie dotyczy filtrów.<br /><br /> Atrybut tylko dla tego elementu `filter`, jest obiekt XpathFilter.<br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|diagnostyka|Definiuje ustawienia WCF dla środowiska uruchomieniowego inspekcji i kontroli administratora.|  
  
## <a name="remarks"></a>Uwagi  
 Komunikaty są rejestrowane w trzech różnych poziomów w stosie: usługi, transport i jest nieprawidłowo sformułowany. Każdy poziom można aktywować oddzielnie.  
  
 Filtrach XPath można dodać do logowania określonego wiadomości na poziomie transportu i usługi. Jeśli filtry nie są zdefiniowane, wszystkie komunikaty są rejestrowane. Filtry są stosowane tylko do nagłówków wiadomości. Treść jest ignorowana. Usługi WCF ignoruje treść wiadomości, aby zwiększyć wydajność. Jeśli chcesz filtrować na podstawie zawartości treści, można utworzyć niestandardowe odbiornika z filtrem to.  
  
 Musisz utworzyć odbiornik śledzenia, aby uaktywnić śledzenie wiadomości. Odbiornik sam może być żadnych odbiornika, który działa z <xref:System.Diagnostics> architektura śledzenia. W poniższym przykładzie pokazano, jak utworzyć takie odbiornika.  
  
```xml  
<system.diagnostics>  
    <sources>  
          <source name="System.ServiceModel" switchValue="Verbose">  
              <listeners>  
                    <clear />  
                    <add type="System.Diagnostics.DefaultTraceListener" name="Default"  
                        traceOutputOptions="None" />  
                    <add name="ServiceModel Listener" traceOutputOptions="None" />  
               </listeners>  
        </source>  
            <source name="System.ServiceModel.MessageLogging">  
                <listeners>  
                    <clear />  
                    <add type="System.Diagnostics.DefaultTraceListener" name="Default"  
                        traceOutputOptions="None" />  
                    <add name="MessageLogging Listener" traceOutputOptions="None"/>  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 [Konfigurowanie rejestrowania komunikatów](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
