---
title: '&lt;msmqIntegrationBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- msmqIntegrationBinding Element
ms.assetid: edf277f3-e3bf-4ed8-9f55-83b5788430a7
ms.openlocfilehash: 1493cb6f9588ee618b085186b3bb63476a9a8930
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48793542"
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
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|closeTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|customDeadLetterQueue|Identyfikator URI, który zawiera lokalizację kolejki utraconych wiadomości dla aplikacji, gdzie umieszcza komunikaty wygasły lub mają niepowodzeniem transferu lub dostarczania.<br /><br /> Kolejka utraconych wiadomości jest kolejką na Menedżer kolejki wysyłania aplikacji dla wygasłe wiadomości, które nie powiodły się do dostarczenia.<br /><br /> Identyfikator URI, który jest określony przez <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> musi używać schematu net.msmq.|  
|deadLetterQueue|A <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>.value określania typu kolejki utraconych wiadomości, aby użyć, jeśli istnieje<br /><br /> Kolejka utraconych wiadomości jest to lokalizacja, w wiadomości, które nie powiodły się dostarczane do aplikacji zostanie przeniesiona.<br /><br /> Komunikaty, które wymagają gwarancji exactlyOnce (czyli `exactlyOnce` ma ustawioną wartość atrybutu `true`), ten atrybut jest domyślnie systemowe kolejki utraconych wiadomości transakcyjnych w usłudze MSMQ.<br /><br /> Komunikaty, które wymagają żadnych zapewnień, ten atrybut są domyślnie `null`.|  
|trwałe|Wartość logiczna wskazująca, czy komunikat jest trwałe lub nietrwała w kolejce. Trwały komunikat przeżyje awarii menedżera kolejki, a komunikat volatile nie. Volatile komunikaty są przydatne, jeśli aplikacje wymagają mniejsze opóźnienia, które mogą tolerować okazjonalne utracone wiadomości. Jeśli `exactlyOnce` ma ustawioną wartość atrybutu `true`, komunikaty muszą być trwałe. Wartość domyślna to `true`.|  
|exactlyOnce|Wartość logiczna wskazująca, czy każdy komunikat zostanie dostarczony tylko raz. Nadawca będą powiadamiani dostarczania błędów. Gdy `durable` jest `false`, ten atrybut jest ignorowany i wiadomości są przekazywane bez zapewnienia dostarczania. Wartość domyślna to `true`. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|maxReceivedMessageSize|Dodatnia liczba całkowita określająca maksymalny rozmiar komunikatu, w bajtach, włącznie z nagłówkami, który jest przetwarzany przez to wiązanie. Nadawca wiadomości przekroczenie tego limitu zostanie wyświetlony błąd protokołu SOAP. Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536. Powiązana rozmiar komunikatu ma to ograniczyć narażenie na ataki przeprowadzenie ataku typu "odmowa usługi" (DoS).|  
|maxRetryCycles|Liczba całkowita, która wskazuje liczbę ponownych prób cyklów używane przez funkcję wykrywania poison komunikatu. Komunikat staje się zarządzanie skażonymi komunikatami, gdy zakończy się niepowodzeniem ze wszystkich prób dostarczenia wszystkich cykli. Wartość domyślna to 2. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|nazwa|Ciąg, który zawiera nazwę konfiguracji powiązania. Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|receiveErrorHandling|A <xref:System.ServiceModel.ReceiveErrorHandling> wartość, która określa sposób obsługi poison i nondispatchable wiadomości.|  
|receiveRetryCount|Liczba całkowita określająca maksymalną liczbę ponownych prób natychmiastowego podjąć Menedżer kolejki w przypadku niepowodzenia przesyłania komunikatów z kolejki aplikacji do aplikacji.<br /><br /> Jeśli zostanie osiągnięta maksymalna liczba prób dostarczenia komunikatu nie jest dostępna przez aplikację, wiadomości są wysyłane w kolejce ponawiania prób dla ponowne dostarczenie w późniejszym czasie. Ilość czasu przed przeniesieniem do kolejki wysyłania komunikatu jest kontrolowany przez `retryCycleDelay`. Jeśli ponawiania cykli zasięg `maxRetryCycles` wartości, a następnie albo wysłać wiadomości do kolejki komunikatów poison lub negatywnego potwierdzenia są wysyłane do nadawcy.|  
|receiveTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:10:00.|  
|receiveContextEnabled|Wartość logiczna określająca, jeśli wyświetlony kontekstu przetwarzanie komunikatów w kolejkach jest włączone. Gdy jest ono ustawione na `true`usługi "wgląd" wiadomość w kolejce rozpoczęcie przetwarzania go i, jeśli nic się nie uda, zgłaszany jest wyjątek pozostaje w kolejce. Usługi można również "zablokować" wiadomości, aby ponowić próbę przetwarzania w dowolnym momencie w czasie. Elementu ReceiveContext udostępnia mechanizm "kończenie" komunikat po przetworzeniu, dzięki czemu może ono zostać usunięte z kolejki. Komunikaty są nie jest już kolejek odczytu i ponownie zapis za pośrednictwem sieci, a poszczególne komunikaty nie są odbijania między wystąpieniami innej usługi podczas przetwarzania.|  
|retryCycleDelay|Wartość przedziału czasu, który określa czas opóźnienia między cykle przy próbie dostarczenia komunikatu, którego nie można dostarczyć natychmiast. Wartość określa tylko minimalny czas oczekiwania, ponieważ rzeczywisty czas może być dłużej. Wartość domyślna to 00:30:00. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|sendTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|serializationFormat|Określa format używany do serializacji w treści wiadomości. Ten atrybut jest typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat>.|  
|timeToLive|Wartość przedziału czasu, który określa, jak długo komunikaty są prawidłowe, zanim wygasną i umieścić w kolejce wiadomości utraconych. Wartość domyślna to 1.00:00:00.<br /><br /> Ten atrybut jest ustawiony, aby upewnić się, że komunikaty zależne od czasu nie staną się przestarzałe zanim zostaną one przetworzone przez aplikacje odbierające. Komunikat w kolejce, który nie jest używane przez aplikację odbierającą w określonym przedziale czasu jest nazywany wygasnąć. Wygasłe komunikaty są wysyłane do kolejki specjalne o nazwie Kolejka utraconych wiadomości. Lokalizacja kolejkę z utraconymi została ustawiona za pomocą `DeadLetterQueue` atrybut lub odpowiednie domyślne na podstawie gwarancji.|  
|useMsmqTracing|Wartość logiczna określająca, czy komunikaty przetwarzane przez to powiązanie powinny być śledzone. Wartość domyślna to `false`. Po włączeniu funkcji śledzenia komunikatów raportów tworzonych i wysyłanych do kolejki raportu za każdym razem wiadomości pozostawia lub dociera do komputera usługi kolejkowania komunikatów.|  
|useSourceJournal|Wartość logiczna, która określa kopie komunikatów przetwarzanych przez to powiązanie powinny być przechowywane w dzienniku źródłowego. Wartość domyślna to `false`.<br /><br /> Umieszczonych w kolejce aplikacji, których chcesz prowadzić rejestr, wiadomości, które pozostało w kolejce wychodzącej komputera można skopiować komunikaty do kolejki dziennika. Gdy wiadomość pozostawia kolejek wychodzących i potwierdzenia otrzymania, czy wiadomość została odebrana na komputerze docelowym, kopia wiadomości są przechowywane w kolejce dziennika systemu komputera wysyłającego.|  
  
## <a name="serializationformat-attribute"></a>{serializationFormat} Atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Xml|XML format|  
|plików binarnych|Format binarny|  
|ActiveX|ActiveX format|  
|ByteArray|Serializuje obiekt jako tablicę bajtów.|  
|Strumień|Treść jest formatowana jako strumienia|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-msmqintegrationbinding.md)|Definiuje ustawienia zabezpieczeń dla wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<powiązania >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element powiązania może służyć do włączenia aplikacji Windows Communication Foundation (WCF) wysyłać i odbierać komunikaty z istniejącej aplikacji usługi MSMQ, które używają COM, natywnych interfejsów API usługi MSMQ lub typów zdefiniowanych w <xref:System.Messaging?displayProperty=nameWithType> przestrzeni nazw użytkownik można użyć tego elementu konfiguracji, aby określić metody rozwiązania kolejki transferu gwarancje, czy komunikaty muszą być trwale przechowywane i jak chronione i uwierzytelnione komunikaty. Aby uzyskać więcej informacji, zobacz [instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami usługi kolejkowania komunikatów](../../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md).  
  
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
 [Konfigurowanie usług i klientów za pomocą powiązań](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Kolejki programu WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
