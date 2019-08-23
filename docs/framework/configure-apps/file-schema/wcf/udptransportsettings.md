---
title: <udpTransportSettings>
ms.date: 03/30/2017
ms.assetid: 842d92e9-6199-4ec5-b2d1-58533054e1f0
ms.openlocfilehash: ed87db92bcbfa0aa9016e36f391d707c5b17bf2b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934493"
---
# <a name="udptransportsettings"></a>\<udpTransportSettings>
Ten element konfiguracji udostępnia ustawienia transportu UDP dla [ \<udpDiscoveryEndpoint >](udpdiscoveryendpoint.md).  
  
\<system.ServiceModel>  
\<standardEndpoints >  
\<udpDiscoveryEndpoint >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint>
        <updTransportSettings duplicateMessageHistoryLength="Integer"
                              maxBufferPoolSize="Integer"
                              maxMulticastRetransmitCount="Integer"
                              maxPendingMessageCount="Integer"
                              maxReceivedMessageSize="Integer"
                              maxUnicastRetransmitCount="Integer"
                              multicastInterfaceId="String"
                              socketReceiveBufferSize="Integer"
                              timeToLive="Integer" />
      </standardEndpoint>
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|duplicateMessageHistoryLength|Liczba całkowita określająca maksymalną liczbę skrótów komunikatów używanych przez transport do identyfikowania zduplikowanych komunikatów.  Wykrywanie duplikatów zostanie wykonane na poziomie TransportManager. Ustawienie dla tej właściwości wartości 0 powoduje wyłączenie wykrywania duplikatów.<br /><br /> Ten atrybut pozwala administratorom systemu lub deweloperom wyłączyć używanie zduplikowanych algorytmów wykrywania komunikatów. Może to być pożądane, jeśli chcesz zaimplementować własny algorytm wykrywania duplikatów.<br /><br /> Wartość domyślna to 4112.|  
|maxBufferPoolSize|Liczba całkowita określająca maksymalny rozmiar wszystkich pul buforów używanych przez transport.|  
|maxMulticastRetransmitCount|Liczba całkowita określająca maksymalną liczbę ponownych transmisji wiadomości (oprócz pierwszego wysłania).<br /><br /> Wartość domyślna to 2.|  
|maxPendingMessageCount|Liczba całkowita określająca maksymalną liczbę komunikatów, które zostały odebrane, ale nie zostały jeszcze usunięte z InputQueue dla pojedynczego wystąpienia kanału.  Jeśli InputQueue osiągnął limit liczby komunikatów oczekujących, komunikat zostanie porzucony.<br /><br /> Wartość domyślna to 32.|  
|maxReceivedMessageSize|Liczba całkowita określająca maksymalny rozmiar wiadomości, która może być przetwarzana przez powiązanie.<br /><br /> Wartość domyślna to 65507.|  
|maxUnicastRetransmitCount|Liczba całkowita określająca maksymalną liczbę ponownych transmisji wiadomości (oprócz pierwszego wysłania).  Jeśli komunikat jest wysyłany do adresu emisji pojedynczej, a komunikat odpowiedzi zostanie odebrany z odpowiadającym mu nagłówkiem relatesta, wówczas retransmisja może zakończyć się wczesnie (przed ponownym przesłaniem skonfigurowanej liczby razy).<br /><br /> Wartość domyślna to 1.|  
|multicastInterfaceId|Ciąg unikatowo identyfikujący kartę sieciową, która ma być używana podczas wysyłania i otrzymywania ruchu multiemisji na maszynach wieloadresowych. W czasie wykonywania transport użyje tej wartości atrybutu do wyszukania indeksu interfejsu, który jest następnie używany do ustawiania `IP_MULTICAST_IF` opcji i `IPV6_MULTICAST_IF` gniazda.  Ten sam indeks interfejsu będzie używany podczas dołączania do grupy multiemisji, jeśli ma zastosowanie.<br /><br /> Wartość domyślna to `null`.|  
|socketReceiveBufferSize|Liczba całkowita określająca rozmiar buforu odbioru w źródłowym gnieździe WinSock.<br /><br /> Użytkownik kanału odbiorczego może użyć tego atrybutu na oprawie, aby kontrolować sposób zachowania systemu po odebraniu danych.  Na przykład dana aplikacja, która zużywa przychodzące komunikaty WCF przy maksymalnym progu, przy użyciu wyższej wartości tego atrybutu zezwoli na komunikaty stosujące się w buforze WinSock podczas oczekiwania na aplikację, która będzie mogła je przetworzyć.  Użycie niższej wartości w tej samej sytuacji spowoduje porzucenie komunikatów. Ten atrybut uwidacznia opcję powiązane z `SO_RCVBUF` gniazdem Winsock. Wartość atrybutu musi być równa co najmniej `maxReceivedMessageSize`.   Ustawienie go na wartość mniejszą niż `maxReceivedMessageSize` spowoduje wyjątek czasu wykonania.<br /><br /> Wartość domyślna to 65536.|  
|timeToLive|Liczba całkowita określająca liczbę przeskoków segmentu sieci, które mogą przechodzić przez pakiet multiemisji.  Ten atrybut uwidacznia funkcje skojarzone z `IP_MULTICAST_TTL` opcjami i `IP_TTL` gniazdem.<br /><br /> Wartość domyślna to 1.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<udpDiscoveryEndpoint >](udpdiscoveryendpoint.md)|Standardowy punkt końcowy ze stałym kontraktem odnajdowania i powiązaniem transportu UDP.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Discovery.UdpTransportSettings>
