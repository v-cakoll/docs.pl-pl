---
title: <reliableSession>
ms.date: 03/30/2017
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
ms.openlocfilehash: 95f6646041dc2dd7bae7691a0a9f748c844f50b6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738747"
---
# \<reliableSession>
Definiuje ustawienie dla obsługi komunikatów w usłudze WS-niezawodny. Gdy ten element zostanie dodany do niestandardowego powiązania, otrzymany kanał może obsługiwać tylko jednokrotne gwarancje dostarczania.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<reliableSession>**  
  
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
|acknowledgementInterval|A <xref:System.TimeSpan> , który zawiera maksymalny czas oczekiwania kanału na wysłanie potwierdzenia dla wiadomości otrzymanych do tego punktu. Wartość domyślna to 00:00:0,2.|  
|flowControlEnabled|Wartość logiczna wskazująca, czy jest uaktywniana Zaawansowana kontrola przepływów — implementacja sterowania przepływem dla usługi WS-niezawodny. Wartość domyślna to `true`.|  
|inactivityTimeout|<xref:System.TimeSpan>Określa maksymalny czas, przez który kanał będzie zezwalał innej stronie komunikacyjnej, aby nie wysyłał żadnych komunikatów przed awarią kanału. Wartość domyślna to 00:10:00.<br /><br /> Działanie w kanale jest zdefiniowane jako otrzymywanie komunikatów aplikacji lub infrastruktury. Ta właściwość określa maksymalny czas utrzymywania aktywnej sesji. Jeśli dłuższy czas upłynie bez aktywności, sesja zostanie przerwana przez infrastrukturę i błędy kanałów. **Uwaga:**  Nie jest konieczne, aby aplikacja okresowo wysyłał komunikaty w celu utrzymania aktywności połączenia.|  
|maxPendingChannels|Liczba całkowita określająca maksymalną liczbę kanałów, które mogą oczekiwać na zaakceptowanie odbiornika. Ta wartość powinna należeć do zakresu od 1 do 16384 włącznie. Wartość domyślna to 4.<br /><br /> Kanały oczekują na zatwierdzenie. Po osiągnięciu tego limitu nie są tworzone żadne kanały. Zamiast tego są one umieszczane w trybie oczekiwania, dopóki ta liczba nie przejdzie w dół (akceptując kanały oczekujące). Jest to limit dla poszczególnych fabryk.<br /><br /> Po osiągnięciu progu, gdy aplikacja zdalna podejmie próbę nawiązania nowej niezawodnej sesji, żądanie zostanie odrzucone i zostanie otwarta operacja, która monituje o te błędy. Ten limit nie ma zastosowania do liczby oczekujących kanałów wychodzących.|  
|Wartość MaxRetryCount|Liczba całkowita określająca maksymalną liczbę prób ponownego przesłania przez niezawodny kanał komunikatu, dla którego nie otrzymano potwierdzenia, przez wywołanie metody send w kanale źródłowym.<br /><br /> Ta wartość powinna być większa od zera. Wartość domyślna to 8.<br /><br /> Ta wartość powinna być liczbą całkowitą większą od zera. Jeśli potwierdzenie nie zostanie odebrane po ostatniej ponownej transmisji, wystąpią błędy kanałów.<br /><br /> Wiadomość jest uznawana za przetransferowaną, jeśli jej dostarczenie w odbiorcy zostało potwierdzone przez adresata.<br /><br /> Jeśli potwierdzenie nie zostało odebrane w określonym czasie przez komunikat, który został przesłany, infrastruktura automatycznie ponownie przesyła komunikat. Infrastruktura próbuje ponownie wysłać komunikat przez maksymalnie liczbę razy określony przez tę właściwość. Jeśli potwierdzenie nie zostanie odebrane po ostatniej ponownej transmisji, wystąpią błędy kanałów.<br /><br /> Infrastruktura używa algorytmu wycofywania wykładniczego, aby określić, kiedy należy ponownie przesłać, w oparciu o obliczony średni czas błądzenia. Czas początkowo rozpoczyna się o 1 sekundę przed ponownym przesłaniem i Podwajanie opóźnienia przy każdej próbie, co powoduje około 8,5 minut przekazywania między pierwszą próbą transmisji a ostatnią ponowną transmisją. Czas pierwszej próby ponownej transmisji jest dostosowywany zgodnie z obliczonym czasem błądzenia i wynikowym rozciągnięciem czasu, który podejmuje te próby. Umożliwia to czas ponownej transmisji, który dynamicznie dostosowuje się do różnych warunków sieciowych.|  
|maxTransferWindowSize|Liczba całkowita określająca maksymalny rozmiar buforu. Prawidłowe wartości to od 1 do 4096 włącznie.<br /><br /> Ten atrybut określa maksymalny rozmiar buforu używany przez niezawodny kanał do przechowywania komunikatów, które nie zostały jeszcze potwierdzone przez odbiornik. Jednostka przydziału jest komunikatem. Jeśli bufor jest pełny, dalsze operacje wysyłania są blokowane.<br /><br /> W odniesieniu do odbiorcy ten atrybut definiuje maksymalny rozmiar buforu używany przez kanał do przechowywania przychodzących komunikatów, które nie zostały jeszcze wysłane do aplikacji. Jeśli bufor jest pełny, dalsze komunikaty są dyskretnie usuwane przez odbiornik i wymagają ponownej transmisji przez klienta.|  
|uporządkowany|Wartość logiczna określająca, czy komunikaty są gwarantowane w kolejności, w jakiej zostały wysłane. Jeśli to ustawienie ma wartość `false` , komunikaty mogą dotrzeć poza kolejnością. Wartość domyślna to `true`.|  
|ReliableMessagingVersion określająca|Prawidłowa wartość <xref:System.ServiceModel.ReliableMessagingVersion> określająca, czy wersja protokołu WS-ReliableMessaging ma być używana.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Definiuje wszystkie możliwości powiązań niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Niezawodne sesje zapewniają funkcje niezawodnej obsługi komunikatów i sesji. Niezawodna komunikacja w celu komunikacji przy niepowodzeń i pozwala na określenie gwarancji dostarczania, takich jak wysyłanie komunikatów. Sesje utrzymują stan dla klientów między wywołaniami. Ten element również opcjonalnie udostępnia uporządkowane dostarczanie komunikatów. Ta zaimplementowana sesja może przekroczyć pośredniki SOAP i transportu.  
  
 Każdy element powiązania reprezentuje etap przetwarzania podczas wysyłania lub otrzymywania wiadomości. W czasie wykonywania elementy powiązania tworzą fabryki kanałów i odbiorniki, które są niezbędne do tworzenia stosów kanałów wychodzących i przychodzących wymaganych do wysyłania i odbierania wiadomości. `reliableSession`Zapewnia opcjonalną warstwę w stosie, która może nawiązywać niezawodne sesje między punktami końcowymi i skonfigurować zachowanie tej sesji.  
  
 Aby uzyskać więcej informacji, zobacz [niezawodne sesje](../../../wcf/feature-details/reliable-sessions.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób konfigurowania powiązania niestandardowego z różnymi elementami transportu i transportem komunikatów, szczególnie w przypadku włączania niezawodnych sesji, które utrzymują stan klienta i określa gwarancje dostarczania w kolejności. Ta funkcja jest konfigurowana w plikach konfiguracji aplikacji dla klienta i usługi. W przykładzie przedstawiono konfigurację usługi.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc -->
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
          <textMessageEncoding messageVersion="Soap12WSAddressing10"
                               writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous"
                         bypassProxyOnLocal="false"
                         hostNameComparisonMode="StrongWildcard"
                         proxyAuthenticationScheme="Anonymous"
                         realm=""
                         useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ReliableSessionElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
- [Niezawodne sesje](../../../wcf/feature-details/reliable-sessions.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
