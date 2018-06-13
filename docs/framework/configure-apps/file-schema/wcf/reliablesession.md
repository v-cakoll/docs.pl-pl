---
title: '&lt;reliableSession&gt;'
ms.date: 03/30/2017
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
ms.openlocfilehash: 6b8049e2c493a652405a93eed68f05438819aecb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751444"
---
# <a name="ltreliablesessiongt"></a>&lt;reliableSession&gt;
Definiuje ustawienie dla WS-Reliable Messaging. Gdy ten element jest dodawany do niestandardowego powiązania, wynikowy kanał obsługuje dokładnie — raz gwarancje dostarczenia.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<reliableSession >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<reliableSession acknowledgementInterval="TimeSpan"  
        flowControlEnabled="Boolean"   
    inactivityTimeout="TimeSpan"  
    maxPendingChannels="Integer"  
    maxRetryCount="Integer"   
        maxTransferWindowSize="Integer"  
    reliableMessagingVersion="Default/WSReliableMessagingFebruary2005/WSReliableMessaging11"  
    ordered="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|AcknowledgementInterval|A <xref:System.TimeSpan> zawiera maksymalny czas kanału będzie oczekiwał na wysłanie potwierdzenia dla wiadomości otrzymanych do tego punktu. Wartość domyślna to 00:00:0.2.|  
|FlowControlEnabled|Wartość logiczna wskazująca, czy Zaawansowane sterowanie przepływem, implementacja specyficzna dla Microsoft kontroli przepływu dla obsługi wiadomości WS-Reliable, jest aktywowana. Wartość domyślna to `true`.|  
|Limit czasu nieaktywności|A <xref:System.TimeSpan> , który określa maksymalny czas, który będzie kanał zezwoli innemu uczestnikowi komunikacji nie na niewysyłanie komunikatów przed spowodowaniem błędu kanału. Wartość domyślna to 00:10:00.<br /><br /> Działań w kanale jest zdefiniowany jako odbieranie aplikacji lub infrastruktury komunikatów. Ta właściwość kontroluje maksymalną ilość czasu podtrzymywania nieaktywnych sesji. Jeśli dłużej zakończy się pomyślnie bez żadnych działań, sesji został przerwany przez infrastrukturę i usterek kanału. **Uwaga:** nie jest niezbędna dla aplikacji, aby okresowo wysyłania komunikatów podtrzymywania połączenia.|  
|MaxPendingChannels|Liczba całkowita określająca maksymalną liczbę kanałów oczekujących na akceptację odbiornika. Ta wartość może zawierać od 1 do 16384 włącznie. Wartość domyślna to 4.<br /><br /> Kanały oczekują na kiedy są oczekuje na zatwierdzenie. Po osiągnięciu tego limitu tworzone są Brak kanałów. Zamiast wprowadzeniem oczekujących tryb dopóki liczba osiąga w dół (akceptując oczekujących kanałów). Jest to limit dla fabryki.<br /><br /> Po osiągnięciu progu i aplikacji zdalnej próbuje utworzyć nowe niezawodnej sesji, żądanie zostanie odrzucone i otwórz operację, która zostanie wyświetlony monit tej usterki. To ograniczenie nie dotyczy liczby oczekujących kanałów wychodzących.|  
|Wartość MaxRetryCount|Liczba całkowita określająca maksymalną liczbę razy niezawodny kanał prób ponownego przesłania wiadomości nie otrzymano potwierdzenia, poprzez wywoływanie metody Send kanału źródłowego.<br /><br /> Ta wartość powinna być większa niż zero. Wartość domyślna to 8.<br /><br /> Ta wartość powinna być liczbą całkowitą większą niż zero. Jeśli potwierdzenie nie zostanie odebrana po ostatnim retransmisji, błędów kanału.<br /><br /> Komunikat jest uznawany za do przeniesienia, jeśli potwierdzenia dostarczenia po stronie odbiorcy przez odbiorcę.<br /><br /> Jeśli nie otrzymano potwierdzenia w ciągu pewnego czasu dla wiadomości, które zostały przesłane, infrastruktury automatycznie ponownie wysyła wiadomość. Infrastruktura próbuje ponownie wysłać wiadomość co najwyżej liczbę powtórzeń przez tę właściwość. Jeśli potwierdzenie nie zostanie odebrana po ostatnim retransmisji, błędów kanału.<br /><br /> Infrastruktura używa algorytm wykładnicze wycofania do określenia, kiedy ponownego przesłania, oparte na obliczona średnia czasu rundy. Czas początkowo rozpoczyna się od 1 sekundy przed retransmisji i podwajając opóźnienie co nieudanej próby podania, co prowadzi do przekazywania między przy pierwszej próbie transmisji i ostatnią próbę retransmisji około 8,5 minut. Podczas pierwszej próby retransmisji jest dostosowane według czasu Rundy obliczeniowej i odcinek wynikowy czas trwania tymi próbami różni odpowiednio. Dzięki temu czas retransmisji dynamicznie dostosowywana w zmiennych warunkach sieciowych.|  
|MaxTransferWindowSize|Liczba całkowita określająca maksymalny rozmiar buforu. Prawidłowe są wartości z zakresu od 1 do 4096 włącznie.<br /><br /> Na komputerze klienckim ten atrybut określa maksymalny rozmiar bufora używanego przez kanał niezawodny do przechowywania komunikatów potwierdzonych nie została jeszcze przez odbiornik. Jednostki przydziału jest komunikat. Jeśli bufor jest pełna, dodatkowe operacje WYSYŁANIA są zablokowane.<br /><br /> Odbiornika ten atrybut określa maksymalny rozmiar bufora używanego przez kanał do przechowywania wiadomości przychodzących, które nie zostały jeszcze wysłane do aplikacji. Jeśli bufor jest pełna, dalsze komunikaty dyskretnie są usuwane przez odbiornik i wymagają retransmisji przez klienta.|  
|uporządkowany|Wartość logiczna określająca, czy komunikaty dotrą do celu w kolejności wysłania. Jeśli to ustawienie jest `false`, można odebraniu komunikatów poza kolejnością. Wartość domyślna to `true`.|  
|ReliableMessagingVersion|Prawidłowa wartość z <xref:System.ServiceModel.ReliableMessagingVersion> określająca wersję WS-ReliableMessaging do użycia.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie możliwości powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Niezawodne sesje zapewniają funkcje dla niezawodna obsługa komunikatów i sesji. Niezawodna obsługa komunikatów ponowi próbę komunikacji w przypadku niepowodzenia i umożliwia gwarancje dostarczenia, takich jak otrzymanie wiadomości, można określić w kolejności. Sesje przechowywania stanu dla klientów między wywołaniami. Ten element zawiera również opcjonalnie dostarczanie komunikatów uporządkowanej. Ta sesja zaimplementowanym mogą przechodzić pośredników SOAP i transportu.  
  
 Każdy element powiązania reprezentuje krok przetwarzania przy wysyłaniu lub odbieraniu wiadomości. W czasie wykonywania elementy powiązania utworzyć fabryk kanałów i odbiorników, które są niezbędne do utworzenia wychodzące i przychodzące stosy kanału wymagane do wysyłania i odbierania wiadomości. `reliableSession` Zapewnia opcjonalne warstwę stosu, który można utworzyć niezawodnej sesji między punktami końcowymi i skonfigurować działanie tej sesji.  
  
 Aby uzyskać więcej informacji, zobacz [sesji niezawodnej](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób konfigurowania niestandardowego powiązania z różnymi transportu i wiadomości kodowania elementów, szczególnie Włączanie niezawodnej sesji, która przechowuje stan klienta i określa gwarancje dostarczenia w kolejności. Ta funkcja jest skonfigurowany w plikach konfiguracji aplikacji dla klienta i usługi. Pokaż przykład konfiguracji usługi.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
        <!-- specify customBinding binding and a binding configuration to use -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <reliableSession />  
          <security authenticationMode="SecureConversation"  
                     requireSecurityContextCancellation="true">  
          </security>  
          <compositeDuplex />  
          <oneWay />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />  
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"  
                        hostNameComparisonMode="StrongWildcard"   
                        proxyAuthenticationScheme="Anonymous" realm=""   
                        useDefaultWebProxy="true" />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ReliableSessionElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>  
 [Niezawodne sesje](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
