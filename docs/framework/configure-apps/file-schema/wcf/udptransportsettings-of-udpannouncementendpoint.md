---
title: <udpTransportSettings> dla <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: a7ddff1a-5eed-4bbc-8580-b95ef8890e1f
ms.openlocfilehash: 901b7e1429c3afc19e9b609026dc632730c35024
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148333"
---
# <a name="udptransportsettings-of-udpannouncementendpoint"></a>\<udpTransportSettings > z \<udpAnnouncementEndpoint >
Ten element konfiguracji udostępnia ustawienia transportu UDP [ \<udpAnnouncementEndpoint >](udpannouncementendpoint.md).  
  
\<system.ServiceModel>  
\<standardEndpoints>  
\<udpAnnouncementEndpoint>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpAnnouncementEndpoint>
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
    </udpAnnouncementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|duplicateMessageHistoryLength|Liczba całkowita określająca maksymalną liczbę wartości skrótu wiadomości używane przez transportu do identyfikowania zduplikowanych komunikatów.  Wykrywanie duplikatów, zostanie wykonane na poziomie elementu TransportManager. Ustawienie tej właściwości na wartość 0 powoduje wyłączenie wykrywania duplikatów.<br /><br /> Ten atrybut umożliwia administratorom systemu lub deweloperów, aby wyłączyć algorytmy wykrywania duplikatów wiadomości. Może to być pożądane, jeśli chcesz zaimplementować algorytm wykrywania duplikatów.<br /><br /> Wartość domyślna to 4112.|  
|maxBufferPoolSize|Liczba całkowita określająca maksymalny rozmiar żadnych pul buforu używany przez transportu.|  
|maxMulticastRetransmitCount|Liczba całkowita określająca maksymalną liczbę przypadków, gdy komunikat powinien zostać ponownie wysłane (oprócz pierwszego wysyłania).<br /><br /> Wartość domyślna to 2.|  
|maxPendingMessageCount|Liczba całkowita określająca maksymalną liczbę wiadomości, które zostały przyjęte, ale nie zostały jeszcze usunięte z InputQueue wystąpienia pojedynczy kanał.  Jeśli InputQueue osiągnie swój limit liczby oczekujących komunikatów, komunikat zostanie usunięty.<br /><br /> Wartość domyślna to 32.|  
|maxReceivedMessageSize|Liczba całkowita określająca maksymalny rozmiar komunikatu, który może przetworzyć wiązanie.<br /><br /> Wartość domyślna to 65507.|  
|maxUnicastRetransmitCount|Liczba całkowita określająca maksymalną liczbę przypadków, gdy komunikat powinien zostać ponownie wysłane (oprócz pierwszego wysyłania).  Jeśli komunikat jest wysyłany na adres emisji pojedynczej, odebraniu komunikatu odpowiedzi za pomocą odpowiedniego nagłówka RelatesTo retransmisji może rozwiązać niniejszą wcześnie (przed zainicjowaniu skonfigurowaną liczbę razy).<br /><br /> Wartość domyślna to 1.|  
|multicastInterfaceId|Ciąg, który unikatowo identyfikuje kartę sieciową, które mają być używane podczas wysyłania i odbierania ruchu multiemisji w przypadku komputerów wieloadresowych. W czasie wykonywania, transport ta wartość zostanie użyta atrybutów do wyszukiwania indeks interfejsu, który jest następnie używana do ustawiania `IP_MULTICAST_IF` i `IPV6_MULTICAST_IF` gniazda opcje.  Tego samego indeksu interfejsu będzie używany podczas dołączania do grupy multiemisji, jeśli ma to zastosowanie.<br /><br /> Wartość domyślna to `null`.|  
|socketReceiveBufferSize|Liczba całkowita określająca rozmiar buforów odbioru na podstawowej gniazda interfejsu WinSock.<br /><br /> Użytkownik odbieranie kanału, można użyć tego atrybutu w powiązaniu do kontrolowania, jak system zachowuje się po odebraniu danych.  Na przykład biorąc pod uwagę aplikację, która zużywa wiadomości przychodzące usługi WCF w osiągnie maksymalny próg, przy użyciu większej wartości tego atrybutu będzie Zezwalaj na wiadomości wypadasz w buforze WinSock podczas oczekiwania na aplikację można było je przetworzyć.  Korzystanie z niższą wartość w tej samej sytuacji spowodowałaby wprowadzenie porzucone komunikaty. Ten atrybut udostępnia podstawowe WinSock `SO_RCVBUF` gniazda opcji. Ta wartość atrybutu musi być co najmniej rozmiar `maxReceivedMessageSize`.   Ustawienie na wartość mniejszą niż `maxReceivedMessageSize` spowodują wyjątek czasu wykonywania.<br /><br /> Wartość domyślna to 65536.|  
|timeToLive|Liczba całkowita określająca liczbę przeskoków sieciowych segmentu, przechodzących pakiety multiemisji.  Ten atrybut uwidacznia funkcje skojarzone z `IP_MULTICAST_TTL` i `IP_TTL` gniazda opcje.<br /><br /> Wartość domyślna to 1.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<udpAnnouncementEndpoint>](udpannouncementendpoint.md)|Standardowy punkt końcowy ze stałym anons, kontrakt i protokołu UDP transportu powiązania.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Discovery.UdpTransportSettings>
