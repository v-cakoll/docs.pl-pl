---
title: '&lt;msmqIntegrationBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- msmqIntegrationBinding Element
ms.assetid: edf277f3-e3bf-4ed8-9f55-83b5788430a7
ms.openlocfilehash: bae6b4e6bd11074b47c55bf310215f296394c90d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltmsmqintegrationbindinggt"></a>&lt;msmqIntegrationBinding&gt;
Definiuje powiązanie, które dostarcza obsługę kolejki poprzez wiadomości routingu za pomocą usługi MSMQ.  
  
 \<system.ServiceModel>  
\<powiązania >  
msmqIntegrationBinding  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<msmqIntegrationBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       customDeadLetterQueue="Uri"  
       deadLetterQueue="Uri"  
       durable="Boolean"  
       exactlyOnce="Boolean"   
       maxReceivedMessageSize"Integer"  
       maxRetryCycles="Integer"   
       name="string"   
       openTimeout="TimeSpan"        receiveContextEnabled="Boolean"  
       receiveErrorHandling="Drop/Fault/Move/Reject"  
       receiveTimeout="TimeSpan"   
       receiveRetryCount="Integer"  
       retryCycleDelay="TimeSpan"    
       sendTimeout="TimeSpan"   
       serializationFormat="XML/Binary/ActiveX/ByteArray/Stream">  
       timeToLive="TimeSpan"    
       useMsmqTracing="Boolean  
       useSourceJournal="Boolean"  
   </binding>  
</msmqIntegrationBinding>   
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|closeTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|customDeadLetterQueue|Identyfikator URI zawiera lokalizację kolejki utraconych wiadomości dla każdej aplikacji, gdzie umieścić są komunikaty wygasłe, lub które nie przeszły przesłanie bądź dostarczenie.<br /><br /> Kolejki utraconych wiadomości jest kolejką na aplikację wysyłającą wygasłych komunikatów, które nie można dostarczyć do menedżera kolejki.<br /><br /> Identyfikator URI, który jest określony przez <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> musi być stosowany schemat net.msmq.|  
|deadLetterQueue|A <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>.value określenie typu kolejki utraconych wiadomości, aby użyć, jeśli istnieje<br /><br /> Kolejki utraconych wiadomości jest lokalizacja zostanie przeniesiona wiadomości, które nie powiodły się do dostarczenia do aplikacji.<br /><br /> Komunikaty, które wymagają gwarancji exactlyOnce (tj. `exactlyOnce` atrybut ma ustawioną `true`), ten atrybut domyślnie systemowe kolejki utraconych wiadomości transakcyjnych w usłudze MSMQ.<br /><br /> Komunikaty, które wymagają nie zapewnień, domyślna tego atrybutu `null`.|  
|trwałe|Wartość logiczna wskazująca, czy komunikat jest trwałe lub zmienne w kolejce. Trwałe komunikat przeżyje awarii menedżera kolejki, a komunikat nietrwałe nie. Volatile wiadomości są przydatne, gdy aplikacje wymagają mniejsze opóźnienia i może tolerować okazjonalne utratą komunikatów. Jeśli `exactlyOnce` atrybut ma ustawioną `true`, komunikaty muszą być trwałe. Wartość domyślna to `true`.|  
|ExactlyOnce|Wartość logiczna wskazująca, czy każdy komunikat jest dostarczany tylko raz. Nadawca będą powiadamiani niepowodzeń dostarczania. Gdy `durable` jest `false`, ten atrybut jest ignorowany i wiadomości są przekazywane bez gwarancji dostarczenia. Wartość domyślna to `true`. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|maxReceivedMessageSize|Dodatnia liczba całkowita określająca maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami, które są przetwarzane przez to powiązanie. Nadawcy wiadomości przekracza ten limit, zostanie wyświetlony błąd protokołu SOAP. Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536. To powiązana rozmiar wiadomości ma na celu ograniczenia narażenia na ataki przeprowadzenie ataku typu "odmowa usługi" (DoS).|  
|MaxRetryCycles|Liczba całkowita, która wskazuje liczbę cykli ponownych prób używane przez funkcję wykrywania poison wiadomości. Komunikat staje się Trująca wiadomość po błędzie wszystkich kolejnymi próbami dostarczenia wszystkich cykli. Wartość domyślna to 2. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|nazwa|Ciąg zawierający nazwę konfiguracji powiązania. Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|ReceiveErrorHandling|A <xref:System.ServiceModel.ReceiveErrorHandling> wartość, która określa sposób obsługi poison i nondispatchable wiadomości.|  
|ReceiveRetryCount|Liczba całkowita określająca maksymalną liczbę ponownych prób natychmiastowego menedżera kolejek powinny podejmować Jeśli transmisję wiadomości z kolejki aplikacji do aplikacji nie powiedzie się.<br /><br /> Jeśli zostanie osiągnięta maksymalna liczba prób dostarczenia komunikatu nie jest dostępna przez aplikację, komunikat jest wysyłany w do kolejki ponawiania ponowne dostarczenie w późniejszym czasie. Ilość czasu przed przeniesieniem do kolejki wysyłania komunikatu jest kontrolowany przez `retryCycleDelay`. Jeśli ponawiania cykli reach `maxRetryCycles` wartości, a następnie albo wysłać komunikatu do kolejki wiadomości poison lub negatywna są wysyłane do nadawcy.|  
|receiveTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:10:00.|  
|receiveContextEnabled|Wartość logiczna określająca, czy kontekstu odbierania, przetwarzanie komunikatów w kolejkach jest włączona. Jeśli to jest równa `true`, usługi mogą "wgląd" wiadomości w kolejce jego przetwarzanie i niczego nieprawidłowość, wyjątek pozostaje w kolejce. Usługi można również "lock" wiadomości, aby ponowić próbę przetworzenia w późniejszym czasie, w czasie. ReceiveContext zapewnia mechanizm "kończenia" komunikat po przetworzeniu, może ono zostać usunięte z kolejki. Komunikaty są nie jest już kolejki odczytu i ponownie zapisane za pośrednictwem sieci, a poszczególne wiadomości nie są odbijania w wystąpieniach innej usługi podczas przetwarzania.|  
|RetryCycleDelay|Wartość TimeSpan określający czas opóźnienia między kolejnymi próbami dostarczenia komunikatu, którego nie można było dostarczyć natychmiast. Wartość określa tylko minimalny czas oczekiwania, czas oczekiwania rzeczywiste mogą być dłuższe. Wartość domyślna to 00:30:00. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|sendTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|Wartości właściwości SerializationFormat|Określa format używany do serializacji w treści wiadomości. Ten atrybut jest typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat>.|  
|timeToLive|Wartość TimeSpan Określa, jak długo komunikaty są prawidłowe, zanim wygasną i umieścić w kolejce wiadomości utraconych. Wartość domyślna to 1.00:00:00.<br /><br /> Ten atrybut ma ustawioną upewnij się, że komunikaty o określonym terminie ważności nie nieodświeżone przetworzenia przez aplikacje odbierające. Wiadomości w kolejce, który nie jest używane przez aplikację odbierającą w określonym przedziale czasu jest określany wygasło. Wygasłe komunikaty są wysyłane do specjalnego kolejki o nazwie Kolejka utraconych wiadomości. Ustawiono lokalizację kolejki utraconych wiadomości `DeadLetterQueue` atrybut lub odpowiednie domyślne oparte na gwarancji.|  
|useMsmqTracing|Wartość logiczna określająca, czy komunikaty przetwarzane przez to powiązanie powinny być śledzone. Wartość domyślna to `false`. Gdy śledzenie jest włączone, wiadomości raportów tworzonych i wysyłanych do kolejki raportu za każdym razem wiadomość opuszcza lub dociera do komputera usługi kolejkowania komunikatów.|  
|useSourceJournal|Wartość logiczna, która określa kopie komunikatów przetwarzanych przez to powiązanie powinny być przechowywane w dzienniku źródłowego. Wartość domyślna to `false`.<br /><br /> W kolejce aplikacji, które chcesz rejestrować komunikatów, które zostały zwolnione kolejki wychodzącej komputera można skopiować wiadomości do kolejki dziennika. Po komunikat pozostawia kolejek wychodzących i potwierdzenia otrzymania, czy wiadomość została odebrana na komputerze docelowym, kopia wiadomości jest przechowywana w kolejce dziennika systemu komputera wysyłającego.|  
  
## <a name="serializationformat-attribute"></a>{serializationFormat} Atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Xml|XML format|  
|plików binarnych|Format binarny|  
|ActiveX|ActiveX format|  
|ByteArray|Serializuje obiekt na tablicę bajtów.|  
|Strumień|Treść sformatowane jako strumienia|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-msmqintegrationbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<powiązania >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element powiązania można wysyłać i odbierać wiadomości z istniejących aplikacji usługi MSMQ, które używają modelu COM, macierzystych interfejsów API usługi MSMQ lub typów zdefiniowanych w aplikacji Windows Communication Foundation (WCF) <xref:System.Messaging?displayProperty=nameWithType> przestrzeni nazw użytkownik można użyć tego elementu konfiguracji, aby określić metody rozwiązania kolejki transfer gwarancji, czy komunikaty muszą być trwale przechowywane i jak chronione i uwierzytelnione komunikaty. Aby uzyskać więcej informacji, zobacz [porady: wymiany komunikatów z punktami końcowymi WCF i aplikacji usługi kolejkowania komunikatów](../../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md).  
  
## <a name="example"></a>Przykład  
  
```xml  
<configuration>  
<system.ServiceModel>  
    <bindings>  
       <msmqIntegrationBinding>  
           <binding   
                    closeTimeout="00:00:10"   
                    openTimeout="00:00:20"   
                    receiveTimeout="00:00:30"   
                    sendTimeout="00:00:40"   
                    deadLetterQueue="net.msmq://localhost/blah"   
                    durable="true"   
                    exactlyOnce="true"   
                    maxReceivedMessageSize="1000"   
                    maxImmediateRetries="11"   
                    maxRetryCycles="12"  
                    poisonMessageHandling="Disabled"   
                    rejectAfterLastRetry="false"   
                    retryCycleDelay="00:05:55"   
                    timeToLive="00:11:11"   
                    useSourceJournal="true"   
                    useMsmqTracing="true"   
                    serializationFormat="Binary">  
                    <security mode="None" />  
           </binding>  
       </msmqIntegrationBinding  
   </bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [Kolejki programu WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
