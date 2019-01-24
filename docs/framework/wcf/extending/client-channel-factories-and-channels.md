---
title: 'Klient: Fabryki kanałów i kanały'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: 71ed9f9cbef35d14597ce6452d65bfca994dc23e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720317"
---
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="0291f-102">Klient: Fabryki kanałów i kanały</span><span class="sxs-lookup"><span data-stu-id="0291f-102">Client: Channel Factories and Channels</span></span>
<span data-ttu-id="0291f-103">W tym temacie opisano tworzenie fabryki kanałów i kanały.</span><span class="sxs-lookup"><span data-stu-id="0291f-103">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="0291f-104">Fabryki kanałów i kanały</span><span class="sxs-lookup"><span data-stu-id="0291f-104">Channel Factories and Channels</span></span>  
 <span data-ttu-id="0291f-105">Fabryki kanałów są odpowiedzialne za tworzenie kanałów.</span><span class="sxs-lookup"><span data-stu-id="0291f-105">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="0291f-106">Kanałów utworzonych przez fabryki kanałów są używane do wysyłania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0291f-106">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="0291f-107">Te kanały są odpowiedzialni za pobieranie wiadomości z warstwy powyżej, wykonanie dowolnego przetwarzanie danych jest konieczne, a następnie wysyłania komunikatu do niższej warstwy.</span><span class="sxs-lookup"><span data-stu-id="0291f-107">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="0291f-108">Poniższa ilustracja przedstawia ten proces.</span><span class="sxs-lookup"><span data-stu-id="0291f-108">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="0291f-109">![Fabryk klienta i kanałów](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="0291f-109">![Client Factories and Channels](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="0291f-110">Fabryka kanałów tworzy kanałów.</span><span class="sxs-lookup"><span data-stu-id="0291f-110">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="0291f-111">Po zamknięciu fabryki kanałów jest odpowiedzialny za zamykania kanałów, które zostały utworzone, które jeszcze nie zostały zamknięte.</span><span class="sxs-lookup"><span data-stu-id="0291f-111">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="0291f-112">Należy pamiętać, że model asymetrycznego w tym miejscu, ponieważ po zamknięciu odbiornika kanałów tylko przestaje akceptować nowych kanałów, ale pozostawia otwartych istniejących kanałów, dzięki czemu może nadal otrzymywać wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0291f-112">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 <span data-ttu-id="0291f-113">Usługi WCF zapewnia pomocnicy klasy bazowej dla tego procesu.</span><span class="sxs-lookup"><span data-stu-id="0291f-113">WCF provides base class helpers for this process.</span></span> <span data-ttu-id="0291f-114">(Dla diagramu klas pomocniczych kanału omówione w tym temacie, zobacz [Przegląd modelu kanału](../../../../docs/framework/wcf/extending/channel-model-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="0291f-114">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](../../../../docs/framework/wcf/extending/channel-model-overview.md).)</span></span>  
  
-   <span data-ttu-id="0291f-115"><xref:System.ServiceModel.Channels.CommunicationObject> Klasy implementuje <xref:System.ServiceModel.ICommunicationObject> oraz wymusza automatu stanów opisany w kroku 2 [kanały rozwijających się](../../../../docs/framework/wcf/extending/developing-channels.md).</span><span class="sxs-lookup"><span data-stu-id="0291f-115">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](../../../../docs/framework/wcf/extending/developing-channels.md).</span></span>  
  
-   <span data-ttu-id="0291f-116"><xref:System.ServiceModel.Channels.ChannelManagerBase> Klasy implementuje <xref:System.ServiceModel.Channels.CommunicationObject> i zapewnia ujednolicone klasa bazowa dla <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0291f-116">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0291f-117"><xref:System.ServiceModel.Channels.ChannelManagerBase> Klasy działa w połączeniu z <xref:System.ServiceModel.Channels.ChannelBase>, która jest klasą bazową, która implementuje <xref:System.ServiceModel.Channels.IChannel>.</span><span class="sxs-lookup"><span data-stu-id="0291f-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>
  
-   <span data-ttu-id="0291f-118"><xref:System.ServiceModel.Channels.ChannelFactoryBase> Klasy implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> i <xref:System.ServiceModel.Channels.IChannelFactory> i konsoliduje `CreateChannel` przeciążeń w jednym `OnCreateChannel` metody abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="0291f-118">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>
  
-   <span data-ttu-id="0291f-119"><xref:System.ServiceModel.Channels.ChannelListenerBase> Klasy implementuje <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="0291f-119">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="0291f-120">Ta odpowiada za zarządzanie stanem podstawowe.</span><span class="sxs-lookup"><span data-stu-id="0291f-120">It takes care of basic state management.</span></span> 
  
 <span data-ttu-id="0291f-121">Następujące dyskusji opiera się na [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="0291f-121">The following discussion is based upon the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="0291f-122">Tworzenie fabryki kanałów</span><span class="sxs-lookup"><span data-stu-id="0291f-122">Creating a Channel Factory</span></span>  
 <span data-ttu-id="0291f-123">`UdpChannelFactory` Pochodzi od klasy <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="0291f-123">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="0291f-124">Przykład zastępuje <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> zapewnienie dostępu do wersji wiadomości koder komunikatów.</span><span class="sxs-lookup"><span data-stu-id="0291f-124">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="0291f-125">Zastępuje również próbki <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> do zatrzymywania naszych wystąpienie <xref:System.ServiceModel.Channels.BufferManager> podczas przejścia automatu stanów.</span><span class="sxs-lookup"><span data-stu-id="0291f-125">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="0291f-126">Kanał danych wyjściowych UDP</span><span class="sxs-lookup"><span data-stu-id="0291f-126">The UDP Output Channel</span></span>  
 <span data-ttu-id="0291f-127">`UdpOutputChannel` Implementuje <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="0291f-127">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="0291f-128">Konstruktor weryfikuje argumentów i tworzy miejsce docelowe <xref:System.Net.EndPoint> na podstawie obiektu <xref:System.ServiceModel.EndpointAddress> który jest przekazywany w.</span><span class="sxs-lookup"><span data-stu-id="0291f-128">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="0291f-129">Zastępowania metody <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> tworzy gniazdo, który jest używany do wysyłania wiadomości do tego <xref:System.Net.EndPoint>.</span><span class="sxs-lookup"><span data-stu-id="0291f-129">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 ```csharp 
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 <span data-ttu-id="0291f-130">Kanał może zostać zamknięty, bez problemu zmieniała lub ungracefully.</span><span class="sxs-lookup"><span data-stu-id="0291f-130">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="0291f-131">Jeśli kanał jest zamknięta bez problemu zmieniała gniazda zostanie zamknięte, a wywołanie klasy bazowej `OnClose` metody.</span><span class="sxs-lookup"><span data-stu-id="0291f-131">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="0291f-132">Jeśli to zgłasza wyjątek, wywołuje metodę infrastruktury `Abort` zapewnienie kanał jest czyszczony.</span><span class="sxs-lookup"><span data-stu-id="0291f-132">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="0291f-133">Implementowanie `Send()` i `BeginSend()` / `EndSend()`.</span><span class="sxs-lookup"><span data-stu-id="0291f-133">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="0291f-134">To dzieli się na dwóch głównych sekcji.</span><span class="sxs-lookup"><span data-stu-id="0291f-134">This breaks down into two main sections.</span></span> <span data-ttu-id="0291f-135">Najpierw należy serializować komunikatu do tablicy typu byte:</span><span class="sxs-lookup"><span data-stu-id="0291f-135">First serialize the message into a byte array:</span></span>  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="0291f-136">Następnie Wyślij dane wynikowe w sieci:</span><span class="sxs-lookup"><span data-stu-id="0291f-136">Then send the resulting data on the wire:</span></span>  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="0291f-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0291f-137">See also</span></span>
- [<span data-ttu-id="0291f-138">Opracowywanie kanałów</span><span class="sxs-lookup"><span data-stu-id="0291f-138">Developing Channels</span></span>](../../../../docs/framework/wcf/extending/developing-channels.md)
