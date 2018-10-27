---
title: 'Klient: Fabryki kanałów i kanały'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: 3f045f56f7b73c5416e7a21a3afde29d22212d68
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182440"
---
# <a name="client-channel-factories-and-channels"></a>Klient: Fabryki kanałów i kanały
W tym temacie opisano tworzenie fabryki kanałów i kanały.  
  
## <a name="channel-factories-and-channels"></a>Fabryki kanałów i kanały  
 Fabryki kanałów są odpowiedzialne za tworzenie kanałów. Kanałów utworzonych przez fabryki kanałów są używane do wysyłania wiadomości. Te kanały są odpowiedzialni za pobieranie wiadomości z warstwy powyżej, wykonanie dowolnego przetwarzanie danych jest konieczne, a następnie wysyłania komunikatu do niższej warstwy. Poniższa ilustracja przedstawia ten proces.  
  
 ![Fabryk klienta i kanałów](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")  
Fabryka kanałów tworzy kanałów.  
  
 Po zamknięciu fabryki kanałów jest odpowiedzialny za zamykania kanałów, które zostały utworzone, które jeszcze nie zostały zamknięte. Należy pamiętać, że model asymetrycznego w tym miejscu, ponieważ po zamknięciu odbiornika kanałów tylko przestaje akceptować nowych kanałów, ale pozostawia otwartych istniejących kanałów, dzięki czemu może nadal otrzymywać wiadomości.  
  
 Usługi WCF zapewnia pomocnicy klasy bazowej dla tego procesu. (Dla diagramu klas pomocniczych kanału omówione w tym temacie, zobacz [Przegląd modelu kanału](../../../../docs/framework/wcf/extending/channel-model-overview.md).)  
  
-   <xref:System.ServiceModel.Channels.CommunicationObject> Klasy implementuje <xref:System.ServiceModel.ICommunicationObject> oraz wymusza automatu stanów opisany w kroku 2 [kanały rozwijających się](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
-   <xref:System.ServiceModel.Channels.ChannelManagerBase> Klasy implementuje <xref:System.ServiceModel.Channels.CommunicationObject> i zapewnia ujednolicone klasa bazowa dla <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Klasy działa w połączeniu z <xref:System.ServiceModel.Channels.ChannelBase>, która jest klasą bazową, która implementuje <xref:System.ServiceModel.Channels.IChannel>.
  
-   <xref:System.ServiceModel.Channels.ChannelFactoryBase> Klasy implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> i <xref:System.ServiceModel.Channels.IChannelFactory> i konsoliduje `CreateChannel` przeciążeń w jednym `OnCreateChannel` metody abstrakcyjnej.
  
-   <xref:System.ServiceModel.Channels.ChannelListenerBase> Klasy implementuje <xref:System.ServiceModel.Channels.IChannelListener>. Ta odpowiada za zarządzanie stanem podstawowe. 
  
 Następujące dyskusji opiera się na [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.  
  
### <a name="creating-a-channel-factory"></a>Tworzenie fabryki kanałów  
 `UdpChannelFactory` Pochodzi od klasy <xref:System.ServiceModel.Channels.ChannelFactoryBase>. Przykład zastępuje <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> zapewnienie dostępu do wersji wiadomości koder komunikatów. Zastępuje również próbki <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> do zatrzymywania naszych wystąpienie <xref:System.ServiceModel.Channels.BufferManager> podczas przejścia automatu stanów.  
  
#### <a name="the-udp-output-channel"></a>Kanał danych wyjściowych UDP  
 `UdpOutputChannel` Implementuje <xref:System.ServiceModel.Channels.IOutputChannel>. Konstruktor weryfikuje argumentów i tworzy miejsce docelowe <xref:System.Net.EndPoint> na podstawie obiektu <xref:System.ServiceModel.EndpointAddress> który jest przekazywany w.  
  
 Zastępowania metody <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> tworzy gniazdo, który jest używany do wysyłania wiadomości do tego <xref:System.Net.EndPoint>.  
  
 ```csharp 
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 Kanał może zostać zamknięty, bez problemu zmieniała lub ungracefully. Jeśli kanał jest zamknięta bez problemu zmieniała gniazda zostanie zamknięte, a wywołanie klasy bazowej `OnClose` metody. Jeśli to zgłasza wyjątek, wywołuje metodę infrastruktury `Abort` zapewnienie kanał jest czyszczony.  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 Implementowanie `Send()` i `BeginSend()` / `EndSend()`. To dzieli się na dwóch głównych sekcji. Najpierw należy serializować komunikatu do tablicy typu byte:  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Następnie Wyślij dane wynikowe w sieci:  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opracowywanie kanałów](../../../../docs/framework/wcf/extending/developing-channels.md)
