---
title: 'Klient: Fabryki kanałów i kanały'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: 25e2c034d1fefc7728667231040a97c3aeecabbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185693"
---
# <a name="client-channel-factories-and-channels"></a>Klient: Fabryki kanałów i kanały
W tym temacie omówiono tworzenie fabryk kanałów i kanałów.  
  
## <a name="channel-factories-and-channels"></a>Fabryki kanałów i kanały  
 Fabryki kanałów są odpowiedzialne za tworzenie kanałów. Kanały utworzone przez fabryki kanałów są używane do wysyłania wiadomości. Te kanały są odpowiedzialne za uzyskanie wiadomości z powyższej warstwy, wykonywanie dowolnego przetwarzania jest konieczne, a następnie wysłanie wiadomości do warstwy poniżej. Poniższa grafika ilustruje ten proces.  
  
 ![Fabryki i kanały klientów](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")  
Fabryka kanałów tworzy kanały.  
  
 Po zamknięciu fabryki kanałów są odpowiedzialne za zamykanie utworzonych kanałów, które nie zostały jeszcze zamknięte. Należy zauważyć, że model jest asymetryczny w tym miejscu, ponieważ gdy odbiornik kanału jest zamknięty, zatrzymuje tylko akceptowanie nowych kanałów, ale pozostawia istniejące kanały otwarte, dzięki czemu mogą kontynuować odbieranie wiadomości.  
  
 WCF zapewnia pomocników klasy podstawowej dla tego procesu. (Aby uzyskać diagram klas pomocnika kanału omówione w tym temacie, zobacz [Omówienie modelu kanału](channel-model-overview.md).)  
  
- Klasa <xref:System.ServiceModel.Channels.CommunicationObject> implementuje <xref:System.ServiceModel.ICommunicationObject> i wymusza maszynę stanu opisaną w kroku 2 [rozwijających się kanałów](developing-channels.md).  
  
- Klasa <xref:System.ServiceModel.Channels.ChannelManagerBase> implementuje <xref:System.ServiceModel.Channels.CommunicationObject> i zapewnia ujednoliconą klasę podstawową dla <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>. Klasa <xref:System.ServiceModel.Channels.ChannelManagerBase> działa w <xref:System.ServiceModel.Channels.ChannelBase>połączeniu z , który jest <xref:System.ServiceModel.Channels.IChannel>klasą podstawową, która implementuje .
  
- Klasa <xref:System.ServiceModel.Channels.ChannelFactoryBase> implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> <xref:System.ServiceModel.Channels.IChannelFactory> i konsoliduje `CreateChannel` przeciążenia `OnCreateChannel` w jedną metodę abstrakcyjną.
  
- Klasa <xref:System.ServiceModel.Channels.ChannelListenerBase> implementuje <xref:System.ServiceModel.Channels.IChannelListener>. Zajmuje się podstawowym zarządzaniem państwem.
  
 Następująca dyskusja jest oparta na [transport: próbka UDP.](../samples/transport-udp.md)  
  
### <a name="creating-a-channel-factory"></a>Tworzenie fabryki kanałów  
 Pochodzi `UdpChannelFactory` z <xref:System.ServiceModel.Channels.ChannelFactoryBase>. Przykładowe <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> zastąpienia, aby zapewnić dostęp do wersji wiadomości kodera wiadomości. Przykład również zastępuje, <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> aby zniszczyć <xref:System.ServiceModel.Channels.BufferManager> nasze wystąpienie, gdy przechodzi maszyny stanu.  
  
#### <a name="the-udp-output-channel"></a>Kanał wyjściowy UDP  
 Implements `UdpOutputChannel` <xref:System.ServiceModel.Channels.IOutputChannel>. Konstruktor sprawdza poprawność argumentów <xref:System.Net.EndPoint> i konstruuje obiekt docelowy na podstawie <xref:System.ServiceModel.EndpointAddress> tego, który jest przekazywany w.  
  
 Zastąpienie <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> tworzy gniazdo, które jest używane do wysyłania wiadomości do tego <xref:System.Net.EndPoint>.  
  
 ```csharp
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 Kanał można zamknąć z gracją lub bezgrawych. Jeśli kanał jest zamknięty bezpiecznie gniazdo jest zamknięty i wywołanie `OnClose` metody klasy podstawowej. Jeśli to zgłasza wyjątek, `Abort` infrastruktury wywołuje, aby upewnić się, że kanał jest czyszczone.  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 Wdrożenie `Send()` `BeginSend()` / `EndSend()`i . To dzieli się na dwie główne sekcje. Najpierw serializuj wiadomość do tablicy bajtów:  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Następnie wyślij wynikowe dane na przewodzie:  
  
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

- [Opracowywanie kanałów](developing-channels.md)
