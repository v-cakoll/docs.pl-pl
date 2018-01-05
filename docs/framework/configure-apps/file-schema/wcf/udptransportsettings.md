---
title: '&lt;udpTransportSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 842d92e9-6199-4ec5-b2d1-58533054e1f0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88b38fc7c67c404446000ca79d2c6191bfc7eed5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltudptransportsettingsgt"></a>&lt;udpTransportSettings&gt;
Ten element konfiguracji udostępnia ustawienia transportu UDP [ \<udpDiscoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md).  
  
\<System. ServiceModel >  
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
|duplicateMessageHistoryLength|Liczba całkowita określająca maksymalną liczbę wartości skrótu wiadomości w celu zidentyfikowania zduplikowanych komunikatów używany przez transport.  Wykrywanie duplikatów zostaną wykonane na poziomie Obiekt TransportManager. Ustawienie tej właściwości na wartość 0 powoduje wyłączenie wykrywania duplikatów.<br /><br /> Ten atrybut umożliwia administratorom systemu lub deweloperom wyłączyć algorytmy wykrywania zduplikowanych komunikatów. Może to być pożądane, aby wdrożyć własny algorytm wykrywania duplikatów.<br /><br /> Wartość domyślna to 4112.|  
|MaxBufferPoolSize|Liczba całkowita określająca maksymalny rozmiar pulami buforu, używany przez transport.|  
|maxMulticastRetransmitCount|Liczba całkowita określająca maksymalną liczbę razy (oprócz pierwszego wysyłania) powinny zostać ponownie wysłane wiadomości.<br /><br /> Wartość domyślna to 2.|  
|maxPendingMessageCount|Liczba całkowita określająca maksymalną liczbę wiadomości, które zostały odebrane, ale jeszcze nie zostały usunięte z obiektu InputQueue dla wystąpienia kanałów.  Jeśli obiektu InputQueue osiągnęła swój limit liczby oczekujących komunikatów, komunikat zostanie usunięty.<br /><br /> Wartość domyślna to 32.|  
|MaxReceivedMessageSize|Liczba całkowita określająca maksymalny rozmiar komunikatu, który może przetworzyć wiązanie.<br /><br /> Wartość domyślna to 65507.|  
|maxUnicastRetransmitCount|Liczba całkowita określająca maksymalną liczbę razy (oprócz pierwszego wysyłania) powinny zostać ponownie wysłane wiadomości.  Jeśli komunikat jest wysyłany do adresu emisji pojedynczej, odebrano komunikat odpowiedzi odpowiedniego nagłówka RelatesTo retransmisji może zakończyć się wcześniej (przed zainicjowaniu o skonfigurowaną liczbę razy).<br /><br /> Wartość domyślna to 1.|  
|multicastInterfaceId|Ciąg unikatowo identyfikujący karty sieciowej, które mają być używane podczas wysyłania i odbierania multiemisji na maszynach wieloadresowych. W czasie wykonywania, transport użyje ta wartość atrybutu do wyszukiwania indeksu interfejsu, który jest następnie używana do ustawiania `IP_MULTICAST_IF` i `IPV6_MULTICAST_IF` gniazda opcje.  Ten sam indeks interfejsu będą używane podczas dołączanie do grupy multiemisji, jeśli ma to zastosowanie.<br /><br /> Wartość domyślna to `null`.|  
|socketReceiveBufferSize|Liczba całkowita określająca rozmiar buforów odbioru na podstawowym gniazda interfejsu WinSock.<br /><br /> Użytkownik odbierający kanału można użyć tego atrybutu w powiązaniu do kontroli zachowania systemu odbiera dane.  Na przykład mając aplikacji, która zajmuje przychodzących komunikatów usługi WCF na maksymalną wartość progową, za pomocą większej wartości tego atrybutu umożliwia komunikaty, aby zająć w buforze WinSock podczas oczekiwania na aplikacji można było je przetworzyć.  Przy użyciu niższą wartość w tej samej sytuacji spowoduje wiadomości porzucane. Ten atrybut przedstawia podstawowy WinSock `SO_RCVBUF` gniazda opcji. Wartość tego atrybutu musi być co najmniej rozmiar `maxReceivedMessageSize`.   Ustawienie jej na wartość mniejszą niż `maxReceivedMessageSize` spowodują wyjątek czasu wykonywania.<br /><br /> Wartość domyślna to 65536.|  
|Wartość TimeToLive|Liczba całkowita określająca liczbę przeskoków sieciowych segmentu, przechodzących pakiety multiemisji.  Ten atrybut dostęp do funkcji skojarzonych z `IP_MULTICAST_TTL` i `IP_TTL` gniazda opcje.<br /><br /> Wartość domyślna to 1.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<udpDiscoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)|Standardowy punkt końcowy ze stałym odnajdywania powiązania transportu kontraktu i UDP.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Discovery.UdpTransportSettings>
