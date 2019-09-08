---
title: 'Usługa: Odbiorniki kanałów i kanały'
ms.date: 03/30/2017
ms.assetid: 8ccbe0e8-7e55-441d-80de-5765f67542fa
ms.openlocfilehash: 0a740f5dcf682c3c140adb9c4c7c9678c4eae132
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797181"
---
# <a name="service-channel-listeners-and-channels"></a>Usługa: Odbiorniki kanałów i kanały

Istnieją trzy kategorie obiektów kanału: kanały, odbiorniki kanałów i fabryki kanałów. Kanały to interfejs między aplikacją a stosem kanału. Odbiorniki kanałów są odpowiedzialne za tworzenie kanałów na stronie odbierania (lub nasłuchiwania), zazwyczaj w odpowiedzi na nowy komunikat przychodzący lub połączenie. Fabryki kanałów są odpowiedzialne za tworzenie kanałów po stronie wysyłania w celu zainicjowania komunikacji z punktem końcowym.

## <a name="channel-listeners-and-channels"></a>Odbiorniki kanałów i kanały

Odbiorniki kanałów są odpowiedzialne za tworzenie kanałów i otrzymywanie komunikatów z warstwy poniżej lub z sieci. Odebrane komunikaty są dostarczane do warstwy powyżej przy użyciu kanału, który jest tworzony przez odbiornik kanału.

Na poniższym diagramie przedstawiono proces otrzymywania komunikatów i dostarczania ich do warstwy powyżej.

![Odbiorniki kanałów i kanały](./media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")

Odbiornik kanału odbiera komunikaty i dostarcza do warstwy powyżej za pośrednictwem kanałów.

Ten proces może być koncepcyjnie modelowany jako kolejka w każdym kanale, chociaż implementacja nie może w rzeczywistości korzystać z kolejki. Odbiornik kanału jest odpowiedzialny za otrzymywanie komunikatów z warstwy poniżej lub z sieci i umieszczanie ich w kolejce. Kanał jest odpowiedzialny za pobieranie komunikatów z kolejki i umieszczanie ich w powyższej warstwie, gdy ta warstwa pyta o komunikat, na przykład przez wywołanie `Receive` kanału.

Funkcja WCF udostępnia pomocników klasy bazowej dla tego procesu. (Aby zapoznać się z diagramem klas pomocnika kanału omawianych w tym artykule, zobacz temat [model kanału — Omówienie](channel-model-overview.md)).

- Klasa implementuje <xref:System.ServiceModel.ICommunicationObject> i wymusza komputer stanu opisany w kroku 2 [tworzenia kanałów.](developing-channels.md) <xref:System.ServiceModel.Channels.CommunicationObject>

- Klasa implementuje <xref:System.ServiceModel.Channels.CommunicationObject> i udostępnia ujednoliconą klasę bazową dla <xref:System.ServiceModel.Channels.ChannelFactoryBase> i <xref:System.ServiceModel.Channels.ChannelListenerBase>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Klasa działa w połączeniu z <xref:System.ServiceModel.Channels.ChannelBase>, która jest klasą bazową implementującą <xref:System.ServiceModel.Channels.IChannel>. <xref:System.ServiceModel.Channels.ChannelManagerBase>

- <xref:System.ServiceModel.Channels.ChannelFactoryBase> Klasa implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> i<xref:System.ServiceModel.Channels.IChannelFactory> konsoliduje przeciążeniaw`OnCreateChannel` jedną metodę abstrakcyjną. `CreateChannel`

- <xref:System.ServiceModel.Channels.ChannelListenerBase> Klasa implementuje<xref:System.ServiceModel.Channels.IChannelListener>. Dział IT zajmuje się podstawowym zarządzaniem stanem.

Następująca dyskusja jest oparta [na transporcie: Przykład](../samples/transport-udp.md) protokołu UDP.

## <a name="creating-a-channel-listener"></a>Tworzenie odbiornika kanału

To, że Przykładowa implementacja jest pochodną <xref:System.ServiceModel.Channels.ChannelListenerBase> klasy. `UdpChannelListener` Do odbierania datagramów jest stosowane pojedyncze gniazdo UDP. `OnOpen` Metoda odbiera dane przy użyciu gniazda UDP w pętli asynchronicznej. Dane są następnie konwertowane na komunikaty przy użyciu systemu kodowania komunikatów:

```csharp
message = UdpConstants.MessageEncoder.ReadMessage(
  new ArraySegment<byte>(buffer, 0, count),
  bufferManager
);
```

Ponieważ ten sam kanał datagramu reprezentuje komunikaty, które docierają do różnych źródeł `UdpChannelListener` , jest to pojedynczy odbiornik. W danym momencie istnieje najwyżej <xref:System.ServiceModel.Channels.IChannel> jedna aktywna skojarzona z tym odbiornikiem. Przykład generuje inny, tylko wtedy, gdy kanał, który jest zwracany przez <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> metodę, zostaje następnie usunięty. Po odebraniu komunikatu jest on dodawany do kolejki pojedynczego tego kanału.

### <a name="udpinputchannel"></a>UdpInputChannel

`UdpInputChannel` Klasa implementuje<xref:System.ServiceModel.Channels.IInputChannel>. Składa się z kolejki komunikatów przychodzących wypełnianych przez `UdpChannelListener`gniazdo. Te komunikaty są dekolejkowane przez <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A> metodę.
