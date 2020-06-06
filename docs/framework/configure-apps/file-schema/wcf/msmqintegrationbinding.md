---
title: <msmqIntegrationBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- msmqIntegrationBinding Element
ms.assetid: edf277f3-e3bf-4ed8-9f55-83b5788430a7
ms.openlocfilehash: ba28a81dd2ea0684ed863821afd3a8f31c0fb064
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140767"
---
# \<msmqIntegrationBinding>
Definiuje powiązanie, które zapewnia obsługę kolejkowania przez kierowanie komunikatów za pośrednictwem usługi MSMQ.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqIntegrationBinding>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<msmqIntegrationBinding>
  <binding closeTimeout="TimeSpan"
           customDeadLetterQueue="Uri"
           deadLetterQueue="Uri"
           durable="Boolean"
           exactlyOnce="Boolean"
           maxReceivedMessageSize="Integer"
           maxRetryCycles="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveContextEnabled="Boolean"
           receiveErrorHandling="Drop/Fault/Move/Reject"
           receiveTimeout="TimeSpan"
           receiveRetryCount="Integer"
           retryCycleDelay="TimeSpan"
           sendTimeout="TimeSpan"
           serializationFormat="XML/Binary/ActiveX/ByteArray/Stream"
           timeToLive="TimeSpan"
           useMsmqTracing="Boolean"
           useSourceJournal="Boolean">
  </binding>
</msmqIntegrationBinding>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|closeTimeout|<xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|  
|customDeadLetterQueue|Identyfikator URI, który zawiera lokalizację kolejki utraconych wiadomości dla aplikacji, w której znajdują się komunikaty, które wygasły lub które nie zostały przesłane.<br /><br /> Kolejka utraconych wiadomości jest kolejką w Menedżerze kolejek aplikacji wysyłającej dla wygasłych komunikatów, których dostarczenie nie powiodło się.<br /><br /> Identyfikator URI określony przez <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> musi używać schematu net. MSMQ.|  
|deadLetterQueue|A <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> . wartość określająca typ używanej kolejki utraconych wiadomości, jeśli istnieje<br /><br /> Kolejka utraconych wiadomości to lokalizacja, w której zostaną przesłane komunikaty, które nie zostały dostarczone do aplikacji.<br /><br /> W przypadku komunikatów, które wymagają gwarancji exactlyOnce (tj. `exactlyOnce` atrybut jest ustawiony na `true` ), ten atrybut domyślnie jest kolejką utraconych wiadomości transakcyjnych w całej systemie w usłudze MSMQ.<br /><br /> W przypadku wiadomości, które nie wymagają żadnych gwarancji, ten atrybut domyślnie przyjmuje wartość `null` .|  
|służąc|Wartość logiczna wskazująca, czy komunikat jest trwały, czy nietrwały w kolejce. Trwały komunikat przeżyje awarię Menedżera kolejki, podczas gdy nietrwały komunikat nie jest. Komunikaty nietrwałe są przydatne, gdy aplikacje wymagają mniejszych opóźnień i mogą tolerować sporadycznie utracone komunikaty. Jeśli `exactlyOnce` atrybut jest ustawiony na `true` , komunikaty muszą być trwałe. Wartość domyślna to `true`.|  
|exactlyOnce|Wartość logiczna wskazująca, czy każdy komunikat jest dostarczany tylko raz. Nadawca zostanie powiadomiony o błędach dostawy. Gdy `durable` jest `false` , ten atrybut jest ignorowany i komunikaty są przesyłane bez gwarancji dostarczania. Wartość domyślna to `true`. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|maxReceivedMessageSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar komunikatu (w bajtach, włącznie z nagłówkami) przetwarzanych przez to powiązanie. Nadawca komunikatu przekraczającego ten limit otrzyma błąd protokołu SOAP. Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536. Ta wartość związana z rozmiarem komunikatu jest przeznaczona do ograniczania narażenia na ataki typu "odmowa usługi" (DoS).|  
|maxRetryCycles|Liczba całkowita, która wskazuje liczbę ponownych prób używanych przez funkcję wykrywania skażonych komunikatów. Komunikat jest skażony komunikatem, gdy nie powiedzie się wszystkie próby dostarczenia wszystkich cykli. Wartość domyślna to 2. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|name|Ciąg zawierający nazwę konfiguracji powiązania. Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania. Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy. Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|<xref:System.TimeSpan>Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|  
|receiveErrorHandling|Wartość określająca <xref:System.ServiceModel.ReceiveErrorHandling> sposób obsługi komunikatów trujących i niewysyłających.|  
|receiveRetryCount|Liczba całkowita określająca maksymalną liczbę natychmiastowych ponownych prób, która powinna zostać podjęta przez Menedżera kolejki, jeśli transmisja komunikatu z kolejki aplikacji do aplikacji zakończy się niepowodzeniem.<br /><br /> Jeśli zostanie osiągnięta maksymalna liczba prób dostarczenia, a wiadomość nie jest używana przez aplikację, komunikat jest wysyłany do kolejki ponownych prób w celu ponownego dostarczenia w późniejszym czasie. Czas, po którym komunikat jest przesyłany z powrotem do kolejki wysyłania jest kontrolowany przez `retryCycleDelay` . Jeśli cykle ponawiania docierają do `maxRetryCycles` wartości, komunikat jest wysyłany do kolejki trujących komunikatów lub zostanie wysłane potwierdzenie negatywne do nadawcy.|  
|receiveTimeout|Wartość określająca <xref:System.TimeSpan> interwał czasu podanego do ukończenia operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:10:00.|  
|receiveContextEnabled|Wartość logiczna określająca, czy jest włączony kontekst odbioru dla komunikatów przetwarzanych w kolejkach. Gdy ta wartość jest ustawiona na `true` , usługa może "wgląd" w kolejkę wiadomości, aby rozpocząć przetwarzanie, i, jeśli coś się nie dzieje i zostanie zgłoszony wyjątek, pozostaje w kolejce. Usługi mogą również "blokować" komunikaty, aby ponowić próbę przetwarzania w późniejszym czasie. Element ReceiveContext oferuje mechanizm "uzupełniania" komunikatu po przetworzeniu, aby można go było usunąć z kolejki. Komunikaty nie są już odczytywane i zapisywane w kolejkach za pośrednictwem sieci, a poszczególne komunikaty nie przeodbijają się w różnych wystąpieniach usługi podczas przetwarzania.|  
|retryCycleDelay|Wartość TimeSpan określająca czas opóźnienia między kolejnymi próbami dostarczenia komunikatu, którego nie można było dostarczyć natychmiast. Wartość definiuje tylko minimalny czas oczekiwania, ponieważ rzeczywisty czas oczekiwania może być dłuższy. Wartość domyślna to 00:30:00. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|Właściwości SendTimeout|<xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|  
|serializationFormat|Definiuje format używany do serializacji treści komunikatu. Ten atrybut jest typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat> .|  
|timeToLive|Wartość TimeSpan określająca czas ważności komunikatów przed ich wygaśnięciem i umieszczona w kolejce utraconych wiadomości. Wartość domyślna to 1,00:00:00.<br /><br /> Ten atrybut jest ustawiony w celu zapewnienia, że komunikaty zależne od czasu nie stają się nieodświeżone przed przetworzeniem przez aplikacje do odebrania. Wiadomość w kolejce, która nie jest używana przez aplikację otrzymującą w określonym przedziale czasu, jest uznawana za wygasłą. Wygasłe komunikaty są wysyłane do kolejki specjalnej zwanej kolejką utraconych wiadomości. Lokalizacja kolejki utraconych wiadomości jest ustawiana z `DeadLetterQueue` atrybutem lub z odpowiednim ustawieniem domyślnym w oparciu o gwarancje.|  
|useMsmqTracing|Wartość logiczna określająca, czy komunikaty przetwarzane przez to powiązanie powinny być śledzone. Wartość domyślna to `false`. Gdy śledzenie jest włączone, wiadomości raportów są tworzone i wysyłane do kolejki raportu za każdym razem, gdy komunikat opuszcza lub dociera do komputera usługi kolejkowania komunikatów.|  
|useSourceJournal|Wartość logiczna określająca kopie komunikatów przetwarzanych przez to powiązanie powinny być przechowywane w dzienniku źródłowym. Wartość domyślna to `false`.<br /><br /> W kolejce aplikacje, które chcą zachować rekord komunikatów, które zostały pozostawione przez kolejkę wychodzącą komputera, mogą kopiować komunikaty do kolejki dziennika. Gdy wiadomość opuszcza kolejkę wychodzącą i otrzyma potwierdzenie odebrania komunikatu na komputerze docelowym, kopia komunikatu jest przechowywana w kolejce dziennika systemowego komputera wysyłającego.|  
  
## <a name="serializationformat-attribute"></a>{serializationFormat} Przypisane  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Xml|XML format|  
|Binarne|Format binarny|  
|ActiveX|Format ActiveX|  
|ByteArray|Serializacja obiektu do tablicy bajtów.|  
|Strumień|Treść sformatowana jako strumień|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<security>](security-of-msmqintegrationbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement> .|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|Ten element zawiera kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element powiązania może służyć do włączania aplikacji Windows Communication Foundation (WCF) do wysyłania komunikatów do i odbierania komunikatów z istniejących aplikacji MSMQ, które korzystają z natywnych interfejsów API COM, MSMQ lub typów zdefiniowanych w <xref:System.Messaging?displayProperty=nameWithType> przestrzeni nazw, można użyć tego elementu konfiguracji, aby określić sposoby rozwiązania kolejki, gwarancje transferu, czy komunikaty muszą być przechowywane i uwierzytelniane. Aby uzyskać więcej informacji, zobacz [jak: wymienianie komunikatów z punktami końcowymi WCF i aplikacjami usługi kolejkowania komunikatów](../../../wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md).  
  
## <a name="example"></a>Przykład  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <msmqIntegrationBinding>
        <binding closeTimeout="00:00:10"
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
      </msmqIntegrationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>
- [\<binding>](bindings.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [Kolejki programu WCF](../../../wcf/feature-details/queues-in-wcf.md)
