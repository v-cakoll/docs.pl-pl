---
title: <reliableSession>
ms.date: 03/30/2017
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
ms.openlocfilehash: 324c46d88d084605dc2b873c65d2a7e7c7a2c4fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783152"
---
# <a name="reliablesession"></a>\<reliableSession >
Definiuje ustawienie dla WS-Reliable Messaging. Gdy ten element jest dodawany do niestandardowego powiązania, dokładnie obsługuje wynikowy kanału — gdy gwarancje dostarczenia.  
  
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
|acknowledgementInterval|Element <xref:System.TimeSpan> zawierający maksymalny interwał kanał przechodzi do oczekiwania na wysłanie potwierdzenia dla wiadomości otrzymanych do tego punktu. Wartość domyślna to 00:00:0.2.|  
|flowControlEnabled|Wartość logiczna wskazująca, czy Zaawansowane sterowanie przepływem, implementacja specyficzna dla Microsoft sterowanie przepływem dla protokołu WS-Reliable messaging jest aktywowana. Wartość domyślna to `true`.|  
|Limit czasu nieaktywności|Element <xref:System.TimeSpan> , który określa maksymalny czas, przez który kanał umożliwi innemu uczestnikowi komunikacji nie na niewysyłanie komunikatów przed spowodowaniem błędu kanału. Wartość domyślna to 00:10:00.<br /><br /> Działań w kanale jest zdefiniowany jako odbieranie aplikacji lub infrastruktury komunikatów. Ta właściwość określa maksymalną ilość czasu, aby utrzymać aktywność sesji nieaktywne. Za pomocą działania nie przeszedł przez dłuższy czas, sesja zostanie przerwany przez infrastruktury i usterek kanału. **Uwaga:**  Nie jest wymagane dla aplikacji, które okresowo wysyłają komunikaty, aby utrzymać aktywność połączenia.|  
|maxPendingChannels|Liczba całkowita określająca maksymalną liczbę kanałów oczekujących na akceptację detektora. Ta wartość powinna należeć do zakresu od 1 do 16384 (włącznie). Wartość domyślna to 4.<br /><br /> Kanały oczekują od tego, kiedy są oczekuje na zatwierdzenie. Po osiągnięciu tego limitu tworzone są kanałów. Zamiast ich umieszczeniem oczekujące tryb dopóki ta liczba zbliża się w dół (akceptując oczekujące kanałów). Jest to limit dla fabryki.<br /><br /> Po osiągnięciu progu i zdalna aplikacja próbuje utworzyć nowy niezawodnej sesji, żądanie zostanie odrzucone i otwórz operacji, która zostanie wyświetlony monit tej usterki. To ograniczenie nie dotyczy liczby oczekujących wychodzących kanałów.|  
|maxRetryCount|Liczba całkowita określająca maksymalną liczbę razy niezawodny kanał podejmuje próbę przesłania wiadomości przez nie otrzymano potwierdzenia, poprzez wywoływanie metody Send dla kanału źródłowego.<br /><br /> Ta wartość powinna być większa od zera. Wartość domyślna to 8.<br /><br /> Ta wartość powinna być liczbą całkowitą większą niż zero. Jeśli potwierdzenie nie zostanie odebrany po ostatnim retransmisji, błędy kanału.<br /><br /> Komunikat jest uważany za przesłane, jeśli jego dostarczenia u odbiorcy została potwierdzona przez odbiorcę.<br /><br /> Jeśli nie otrzymano potwierdzenia w ramach określoną ilość czasu dla wiadomości, które zostały przekazane, infrastruktury automatycznie ponownie wysyła wiadomości. Infrastruktura próbuje ponownie wysłać wiadomość do co najwyżej liczba określona przez tę właściwość. Jeśli potwierdzenie nie zostanie odebrany po ostatnim retransmisji, błędy kanału.<br /><br /> Infrastruktury używa wykładniczego wycofywania algorytmu do określenia, kiedy ponowne przesłanie, oparte na obliczanej Średni czas błądzenia. Czas początkowo rozpoczyna się od 1 sekundy przed retransmisji i podwajając opóźnienie w każdej próby, co powoduje przekazanie między pierwszej próby transmisji i ostatnia próba retransmisji około 8,5 minut. Podczas pierwszej próby retransmisji jest dostosowywany zgodnie z obliczony czas błądzenia i wynikowy stretch czas, przez który te próby podjęcia zmienia się odpowiednio. Dzięki temu czas retransmisji dynamicznie dostosowywana do zmiennych warunkach sieciowych.|  
|maxTransferWindowSize|Liczba całkowita określająca maksymalny rozmiar buforu. Prawidłowe wartości to od 1 do 4096 (włącznie).<br /><br /> Na komputerze klienckim ten atrybut określa maksymalny rozmiar buforu używany przez niezawodny kanał do przechowywania wiadomości nie została jeszcze potwierdzona przez odbiorcę. Jednostka limitu przydziału jest wiadomość. Jeśli bufor jest pełna, są blokowane dalszych operacji WYSYŁANIA.<br /><br /> Na odbiornik ten atrybut określa maksymalny rozmiar buforu używany przez kanał do przechowywania wiadomości przychodzących, które jeszcze nie zostało wysłane do aplikacji. Jeśli bufor jest pełna, dalsze komunikaty dyskretnie są odrzucane przez odbiornik i wymagają retransmisji przez klienta.|  
|uporządkowany|Wartość logiczna określająca, czy komunikaty dotrą do celu w kolejności wysłania. Jeśli to ustawienie jest `false`, komunikaty mogą pojawić się poza kolejnością. Wartość domyślna to `true`.|  
|ReliableMessagingVersion|Prawidłowa wartość z <xref:System.ServiceModel.ReliableMessagingVersion> określająca wersję WS-ReliableMessaging ma być używany.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie funkcje powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Niezawodne sesje oferują funkcje dla niezawodna obsługa komunikatów i sesji. Niezawodna obsługa komunikatów ponawia próbę komunikacji w przypadku niepowodzenia i umożliwia gwarancje dostarczenia, np. w kolejności przybycia komunikaty, aby określić. Sesje zarządzania stanem dla klientów między wywołaniami. Ten element udostępnia również opcjonalnie dostarczanie uporządkowanych komunikatów. Ta sesja zaimplementowano mogą przechodzić pośredników SOAP i mechanizm transportu.  
  
 Każdy element powiązania reprezentuje krok przetwarzania podczas wysyłania lub odbierania komunikatów. W czasie wykonywania elementy powiązania tworzenie fabryki kanałów i odbiorników, które są niezbędne do utworzenia przychodzących i wychodzących stosów kanału wymagane do wysyłania i odbierania komunikatów. `reliableSession` Zapewnia opcjonalne warstwę stosu, który można utworzyć niezawodnej sesji między punktami końcowymi i skonfiguruj zachowanie tej sesji.  
  
 Aby uzyskać więcej informacji, zobacz [sesje niezawodnej](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak skonfigurować powiązania niestandardowego z różnymi transportu i komunikat kodowania elementów, szczególnie umożliwiające niezawodne sesje, które przechowuje stan klienta i określa gwarancje dostarczenia w określonej kolejności. Ta funkcja jest konfigurowana w plikach konfiguracji aplikacji dla klienta i usługi. Pokaż przykład konfiguracji usługi.  
  
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
- [Niezawodne sesje](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
