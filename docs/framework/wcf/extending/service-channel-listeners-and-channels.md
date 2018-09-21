---
title: 'Usługa: Odbiorniki kanałów i kanały'
ms.date: 03/30/2017
ms.assetid: 8ccbe0e8-7e55-441d-80de-5765f67542fa
ms.openlocfilehash: 88bfdc879e4f3c7df6b2c4035c7ed7fdc2b4c41d
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537270"
---
# <a name="service-channel-listeners-and-channels"></a>Usługa: Odbiorniki kanałów i kanały

Istnieją trzy kategorie obiektów kanału: kanały, odbiorniki kanałów i fabryki kanałów. Kanały to interfejs między aplikacją a stosu kanału. Odbiorniki kanałów są odpowiedzialne za tworzenie kanałów po stronie odbioru (lub nasłuchiwania), zwykle w odpowiedzi na nowe wiadomości przychodzących lub połączenia. Fabryki kanałów są odpowiedzialne za tworzenie kanałów na stronie wysyłania w celu zainicjowania komunikacji z punktem końcowym.

## <a name="channel-listeners-and-channels"></a>Odbiorniki kanałów i kanały

Odbiorniki kanałów jest odpowiedzialny za tworzenie kanałów i odbieranie komunikatów z warstwy poniżej lub z sieci. Odebrane komunikaty są dostarczane do warstwy powyżej przy użyciu kanału, który jest tworzony przez odbiornik kanału.

Na poniższym diagramie przedstawiono proces odbierania komunikatów i dostarczanie ich w wyższej warstwie.

![Odbiorniki kanałów i kanały](./media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")

Odbiornik kanału, odbierania wiadomości, a potem dostarczając w warstwie nad za pośrednictwem kanałów.

Proces może koncepcyjnie modelowane jako kolejki wewnątrz każdego kanału, mimo że implementacja nie może faktycznie używać kolejki. Odbiornik kanału jest odpowiedzialna za odbieranie komunikatów z warstwy poniżej lub sieci i umieszczenie ich w kolejce. Kanał jest odpowiedzialny za pobieranie komunikatów z kolejki i przekazywać je do warstwy powyżej po tej warstwy prosi o wiadomości, na przykład przez wywołanie metody `Receive` w kanale.

Usługi WCF zapewnia pomocnicy klasy bazowej dla tego procesu. (Dla diagramu klas pomocniczych kanału omówionych w tym artykule, zobacz [Przegląd modelu kanału](channel-model-overview.md).)

- <xref:System.ServiceModel.Channels.CommunicationObject> Klasy implementuje <xref:System.ServiceModel.ICommunicationObject> oraz wymusza automatu stanów opisany w kroku 2 [kanały rozwijających się](developing-channels.md).

- <xref:System.ServiceModel.Channels.ChannelManagerBase> Klasy implementuje <xref:System.ServiceModel.Channels.CommunicationObject> i zapewnia ujednolicone klasa bazowa dla <xref:System.ServiceModel.Channels.ChannelFactoryBase> i <xref:System.ServiceModel.Channels.ChannelListenerBase>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Klasy działa w połączeniu z <xref:System.ServiceModel.Channels.ChannelBase>, która jest klasą bazową, która implementuje <xref:System.ServiceModel.Channels.IChannel>.

- <xref:System.ServiceModel.Channels.ChannelFactoryBase> Klasy implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> i <xref:System.ServiceModel.Channels.IChannelFactory> i konsoliduje `CreateChannel` przeciążeń w jednym `OnCreateChannel` metody abstrakcyjnej.

- <xref:System.ServiceModel.Channels.ChannelListenerBase> Klasy implementuje <xref:System.ServiceModel.Channels.IChannelListener>. Ta odpowiada za zarządzanie stanem podstawowe.

Następujące dyskusji opiera się na [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.

## <a name="creating-a-channel-listener"></a>Tworzenie odbiornika kanałów

`UdpChannelListener` Że próbki implementuje pochodzi od klasy <xref:System.ServiceModel.Channels.ChannelListenerBase> klasy. Aby otrzymać datagramy używa jedno gniazdo UDP. `OnOpen` Metoda otrzymuje dane przy użyciu gniazda UDP pętlę asynchronicznego. Dane są następnie przekształcana w wiadomości przy użyciu kodowania system komunikatu:

```csharp
message = UdpConstants.MessageEncoder.ReadMessage(
  new ArraySegment<byte>(buffer, 0, count),
  bufferManager
);
```

Ponieważ ten sam kanał datagram reprezentuje komunikaty przychodzące z różnych źródeł, `UdpChannelListener` jest odbiornika pojedynczego wystąpienia. Ma pod najbardziej aktywnych jeden <xref:System.ServiceModel.Channels.IChannel> skojarzony z tym odbiornik naraz. Przykład generuje inny tylko wtedy, gdy kanał, który jest zwracany przez <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> metoda później zostanie usunięty. Gdy wiadomość zostaje odebrana, to umieszczonych w kolejce do tego kanału pojedynczego wystąpienia.

### <a name="udpinputchannel"></a>UdpInputChannel

`UdpInputChannel` Klasy implementuje <xref:System.ServiceModel.Channels.IInputChannel>. Składa się z kolejki wiadomości przychodzących, które jest wypełniana przez `UdpChannelListener`w gniazda. Te komunikaty są usuwane z kolejki przez <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A> metody.
