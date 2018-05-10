---
title: 'Usługa: Odbiorniki kanałów i kanały'
ms.date: 03/30/2017
ms.assetid: 8ccbe0e8-7e55-441d-80de-5765f67542fa
ms.openlocfilehash: eca7061243fa7f006079d19c3eaaf86ba906bca2
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="service-channel-listeners-and-channels"></a>Usługa: Odbiorniki kanałów i kanały
Istnieją trzy kategorie obiektów kanału: kanały, odbiorniki kanałów i fabryk kanałów. Kanały to interfejs pomiędzy aplikacją i stosu kanału. Odbiorniki kanałów są zobowiązani do tworzenia kanałów po stronie odbioru (lub nasłuchiwania), zwykle w odpowiedzi na połączenie lub nowy komunikat przychodzący. Fabryk kanałów, które są odpowiedzialne za tworzenie kanałów po stronie wysyłającej można zainicjować komunikacji z punktem końcowym.  
  
## <a name="channel-listeners-and-channels"></a>Odbiorniki kanałów i kanały  
 Odbiorniki kanałów są odpowiedzialne za tworzenie kanałów i odbieranie wiadomości z warstwy poniżej lub z sieci. Odebrane komunikaty są dostarczane do warstwy powyżej przy użyciu kanału, który jest tworzony przez odbiornik kanału.  
  
 Na poniższym diagramie przedstawiono proces odbieranie wiadomości oraz dostarczania ich do warstwy powyżej.  
  
 ![Odbiorniki kanałów i kanały](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")  
Odbiornik kanału odbierania komunikatów i dostarczanie do warstwy powyżej za pośrednictwem kanałów.  
  
 Proces można koncepcyjnie modelowane jako kolejki wewnątrz każdego kanału, mimo że implementacji nie mogą faktycznie używać kolejki. Odbiornik kanału jest odpowiedzialny za odbieranie wiadomości z warstwy poniżej lub sieci i umieszczania ich w kolejce. Kanał jest odpowiedzialny za pobieranie wiadomości z kolejki i przekazywanie ich do warstwy powyżej po tej warstwy komunikatu z pytaniem wiadomości, na przykład wywołując `Receive` w kanale.  
  
 WCF udostępnia pomocników klasę podstawową dla tego procesu. (Dla diagramu klas pomocniczych kanału omówione w tym temacie, zobacz [Przegląd modelu kanału](../../../../docs/framework/wcf/extending/channel-model-overview.md).)  
  
-   <xref:System.ServiceModel.Channels.CommunicationObject> Klasa implementuje <xref:System.ServiceModel.ICommunicationObject> i wymusza automatu stanów opisany w kroku 2 [kanały rozwijających się](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
-   <xref:System.ServiceModel.Channels.ChannelManagerBase> Klasa implementuje <xref:System.ServiceModel.Channels.CommunicationObject> i zapewnia ujednolicone klasa podstawowa dla <xref:System.ServiceModel.Channels.ChannelFactoryBase> i <xref:System.ServiceModel.Channels.ChannelListenerBase>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Klasa działa w połączeniu z <xref:System.ServiceModel.Channels.ChannelBase>, która jest klasy podstawowej, która implementuje <xref:System.ServiceModel.Channels.IChannel>.  
  
-   "<xref:System.ServiceModel.Channels.ChannelFactoryBase> Klasa implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> i <xref:System.ServiceModel.Channels.IChannelFactory> i konsoliduje `CreateChannel` overloads do jednego `OnCreateChannel` metody abstrakcyjnej.  
  
-   <xref:System.ServiceModel.Channels.ChannelListenerBase> Klasa implementuje <xref:System.ServiceModel.Channels.IChannelListener>. Odpowiada on za podstawowy zarządzania.  
  
 Następujące dyskusji opiera się na [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.  
  
## <a name="creating-a-channel-listener"></a>Tworzenie odbiornika kanałów  
 "UdpChannelListener implementujący próbki jest pochodną <xref:System.ServiceModel.Channels.ChannelListenerBase> klasy. Użyto jednego gniazda UDP do odbierania datagramów. `OnOpen` Metody odbiera dane przy użyciu gniazda UDP w pętli asynchronicznego. Dane są następnie konwertowane na komunikaty przy użyciu kodowania systemu komunikatu:  
  
```  
message = UdpConstants.MessageEncoder.ReadMessage(  
  new ArraySegment<byte>(buffer, 0, count),   
  bufferManager  
);  
```  
  
 Ponieważ ten sam kanał datagram reprezentuje komunikaty przychodzące z różnych źródeł, `UdpChannelListener` odbiornik singleton. W większości jeden aktywny jest <xref:System.ServiceModel.Channels.IChannel>'' skojarzone z tym odbiorniku naraz. Przykład generuje kolejnego tylko wtedy, gdy kanału, który jest zwracany przez <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> metody później został usunięty. Po otrzymaniu komunikatu jest dodawanych do kolejki w tym kanale singleton.  
  
### <a name="udpinputchannel"></a>UdpInputChannel  
 `UdpInputChannel` Klasa implementuje <xref:System.ServiceModel.Channels.IInputChannel>. Składa się z kolejki wiadomości przychodzących, które jest wypełniana `UdpChannelListener`do gniazda. Komunikaty te są usuniętej przez <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A> metody.
