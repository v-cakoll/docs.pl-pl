---
title: 'Usługa: Odbiorniki kanałów i kanały'
ms.date: 03/30/2017
ms.assetid: 8ccbe0e8-7e55-441d-80de-5765f67542fa
ms.openlocfilehash: 4367d844867db7fdad013e30d047f9385addbce5
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834802"
---
# <a name="service-channel-listeners-and-channels"></a>Usługa: Odbiorniki kanałów i kanały

Istnieją trzy kategorie obiektów kanału: kanały, odbiorniki kanałów i fabryki kanałów. Kanały to interfejs między aplikacją a stosem kanału. Odbiorniki kanałów są odpowiedzialne za tworzenie kanałów na stronie odbierania (lub nasłuchiwania), zazwyczaj w odpowiedzi na nowy komunikat przychodzący lub połączenie. Fabryki kanałów są odpowiedzialne za tworzenie kanałów po stronie wysyłania w celu zainicjowania komunikacji z punktem końcowym.

## <a name="channel-listeners-and-channels"></a>Odbiorniki kanałów i kanały

Odbiorniki kanałów są odpowiedzialne za tworzenie kanałów i otrzymywanie komunikatów z warstwy poniżej lub z sieci. Odebrane komunikaty są dostarczane do warstwy powyżej przy użyciu kanału, który jest tworzony przez odbiornik kanału.

Na poniższym diagramie przedstawiono proces otrzymywania komunikatów i dostarczania ich do warstwy powyżej.

![Odbiorniki kanałów i kanały](./media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")

Odbiornik kanału odbiera komunikaty i dostarcza do warstwy powyżej za pośrednictwem kanałów.

Ten proces może być koncepcyjnie modelowany jako kolejka w każdym kanale, chociaż implementacja nie może w rzeczywistości korzystać z kolejki. Odbiornik kanału jest odpowiedzialny za otrzymywanie komunikatów z warstwy poniżej lub z sieci i umieszczanie ich w kolejce. Kanał jest odpowiedzialny za pobieranie komunikatów z kolejki i umieszczanie ich w powyższej warstwie, gdy ta warstwa pyta o komunikat, na przykład przez wywołanie `Receive` w kanale.

Funkcja WCF udostępnia pomocników klasy bazowej dla tego procesu. Aby zapoznać się z diagramem klas pomocnika kanału omawianych w tym artykule, zobacz [Omówienie modelu kanału](channel-model-overview.md).

- Klasa <xref:System.ServiceModel.Channels.CommunicationObject> implementuje <xref:System.ServiceModel.ICommunicationObject> i wymusza komputer stanu opisany w kroku 2 [tworzenia kanałów](developing-channels.md).

- Klasa <xref:System.ServiceModel.Channels.ChannelManagerBase> implementuje <xref:System.ServiceModel.Channels.CommunicationObject> i zapewnia ujednoliconą klasę bazową dla <xref:System.ServiceModel.Channels.ChannelFactoryBase> i <xref:System.ServiceModel.Channels.ChannelListenerBase>. Klasa <xref:System.ServiceModel.Channels.ChannelManagerBase> działa w połączeniu z <xref:System.ServiceModel.Channels.ChannelBase>, która jest klasą bazową implementującą <xref:System.ServiceModel.Channels.IChannel>.

- Klasa <xref:System.ServiceModel.Channels.ChannelFactoryBase> implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> i <xref:System.ServiceModel.Channels.IChannelFactory> i konsoliduje przeciążenia `CreateChannel` do jednej metody abstrakcyjnej `OnCreateChannel`.

- Klasa <xref:System.ServiceModel.Channels.ChannelListenerBase> implementuje <xref:System.ServiceModel.Channels.IChannelListener>. Dział IT zajmuje się podstawowym zarządzaniem stanem.

Następująca dyskusja jest oparta na przykładowej [transportowej: UDP](../samples/transport-udp.md) .

## <a name="creating-a-channel-listener"></a>Tworzenie odbiornika kanału

@No__t-0 implementacja próbki pochodzi od klasy <xref:System.ServiceModel.Channels.ChannelListenerBase>. Do odbierania datagramów jest stosowane pojedyncze gniazdo UDP. Metoda `OnOpen` odbiera dane przy użyciu gniazda UDP w pętli asynchronicznej. Dane są następnie konwertowane na komunikaty przy użyciu systemu kodowania komunikatów:

```csharp
message = UdpConstants.MessageEncoder.ReadMessage(
  new ArraySegment<byte>(buffer, 0, count),
  bufferManager
);
```

Ponieważ ten sam kanał datagramu reprezentuje komunikaty przychodzące z kilku źródeł, `UdpChannelListener` jest pojedynczym odbiornikiem. Istnieje co najwyżej jedna aktywna <xref:System.ServiceModel.Channels.IChannel> skojarzona z tym odbiornikiem. Przykład generuje inny, tylko wtedy, gdy kanał zwracany przez metodę <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> jest następnie usuwany. Po odebraniu komunikatu jest on dodawany do kolejki pojedynczego tego kanału.

### <a name="udpinputchannel"></a>UdpInputChannel

Klasa `UdpInputChannel` implementuje <xref:System.ServiceModel.Channels.IInputChannel>. Składa się z kolejki komunikatów przychodzących wypełnianych przez gniazdo `UdpChannelListener`. Te komunikaty są dekolejkowane przez metodę <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A>.
