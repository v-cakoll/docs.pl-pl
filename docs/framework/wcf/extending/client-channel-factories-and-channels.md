---
title: "Klienta: Fabryk kanałów i kanały"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4a841fec01b3a0ef29cd836cccf3f337f29ddb6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="client-channel-factories-and-channels"></a>Klienta: Fabryk kanałów i kanały
W tym temacie omówiono tworzenie fabryki kanałów i kanały.  
  
## <a name="channel-factories-and-channels"></a>Fabryki kanałów i kanały  
 Fabryk kanałów, które są odpowiedzialne za tworzenie kanałów. Kanałów utworzonych przez fabryk kanałów, które są używane do wysyłania wiadomości. Te kanały są zobowiązani do uzyskiwania wiadomości z warstwy powyżej, wykonywania przetwarzania jest wymagane, a następnie wysyła komunikat do warstwy poniżej. Poniższa ilustracja przedstawia tego procesu.  
  
 ![Fabryki klienta i kanały](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")  
Fabryka kanałów tworzy kanałów.  
  
 Po zamknięciu fabryk kanałów, które są zobowiązani do zamykania kanałów, które są tworzone, które nie są jeszcze zamknięty. Należy pamiętać, że model asymetrycznego tutaj ponieważ zamknięcie odbiornika kanałów tylko przestaje akceptować nowych kanałów, ale pozostawia otwartych istniejące kanały, dzięki czemu może nadal otrzymywać wiadomości.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]udostępnia pomocników klasę podstawową dla tego procesu. (Dla diagramu klas pomocniczych kanału omówione w tym temacie, zobacz [Przegląd modelu kanału](../../../../docs/framework/wcf/extending/channel-model-overview.md).)  
  
-   <xref:System.ServiceModel.Channels.CommunicationObject> Klasa implementuje <xref:System.ServiceModel.ICommunicationObject> i wymusza automatu stanów opisany w kroku 2 [kanały rozwijających się](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
-   "<xref:System.ServiceModel.Channels.ChannelManagerBase> Klasa implementuje <xref:System.ServiceModel.Channels.CommunicationObject> i zapewnia ujednolicone klasa podstawowa dla <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Klasa działa w połączeniu z <xref:System.ServiceModel.Channels.ChannelBase>, która jest klasy podstawowej, która implementuje <xref:System.ServiceModel.Channels.IChannel>.  
  
-   "<xref:System.ServiceModel.Channels.ChannelFactoryBase> Klasa implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> i <xref:System.ServiceModel.Channels.IChannelFactory> i konsoliduje `CreateChannel` overloads do jednego `OnCreateChannel` metody abstrakcyjnej.  
  
-   "<xref:System.ServiceModel.Channels.ChannelListenerBase> Klasa implementuje <xref:System.ServiceModel.Channels.IChannelListener>. Odpowiada on za podstawowy zarządzania.  
  
 Następujące dyskusji opiera się na [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.  
  
### <a name="creating-a-channel-factory"></a>Tworzenie fabryki kanałów  
 `UdpChannelFactory` Pochodną <xref:System.ServiceModel.Channels.ChannelFactoryBase>. Zastępuje próbki <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> zapewniające dostęp do wersji kodera wiadomości wiadomości. Zastępuje również próbki <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> do zerwanie naszych wystąpienie <xref:System.ServiceModel.Channels.BufferManager> podczas przejścia komputera stanu.  
  
#### <a name="the-udp-output-channel"></a>Kanał wyjściowy UDP  
 `UdpOutputChannel` Implementuje <xref:System.ServiceModel.Channels.IOutputChannel>. Konstruktor sprawdza poprawność argumentów i tworzy miejsce docelowe <xref:System.Net.EndPoint> na podstawie obiektu <xref:System.ServiceModel.EndpointAddress> przekazanego pakietu.  
  
 Zastąpienie z <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> tworzy gniazda, który jest używany do wysyłania wiadomości do tego <xref:System.Net.EndPoint>.  
  
 `this.socket = new Socket(`  
  
 `this.remoteEndPoint.AddressFamily,`  
  
 `SocketType.Dgram,`  
  
 `ProtocolType.Udp`  
  
 `);`  
  
 Kanał może zostać zamknięty, bezpiecznie lub ungracefully. Jeśli bezpiecznie zamknięcie kanału gniazda zostanie zamknięte, a połączenie jest nawiązywane w klasie podstawowej `OnClose` metody. Jeśli to zgłasza wyjątek, wywołuje metodę infrastruktury `Abort` zapewnienie kanał jest wyczyszczone.  
  
```  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 Implementowanie `Send()` i `BeginSend()` / `EndSend()`. To dzieli się na dwóch głównych sekcji. Najpierw serializacji komunikatu do tablicy typu byte:  
  
```  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Następnie wysyłania danych w sieci:  
  
```  
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
