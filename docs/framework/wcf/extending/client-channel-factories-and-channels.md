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
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="2f29c-102">Klient: Fabryki kanałów i kanały</span><span class="sxs-lookup"><span data-stu-id="2f29c-102">Client: Channel Factories and Channels</span></span>
<span data-ttu-id="2f29c-103">W tym temacie omówiono tworzenie fabryk kanałów i kanałów.</span><span class="sxs-lookup"><span data-stu-id="2f29c-103">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="2f29c-104">Fabryki kanałów i kanały</span><span class="sxs-lookup"><span data-stu-id="2f29c-104">Channel Factories and Channels</span></span>  
 <span data-ttu-id="2f29c-105">Fabryki kanałów są odpowiedzialne za tworzenie kanałów.</span><span class="sxs-lookup"><span data-stu-id="2f29c-105">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="2f29c-106">Kanały utworzone przez fabryki kanałów są używane do wysyłania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2f29c-106">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="2f29c-107">Te kanały są odpowiedzialne za uzyskanie wiadomości z powyższej warstwy, wykonywanie dowolnego przetwarzania jest konieczne, a następnie wysłanie wiadomości do warstwy poniżej.</span><span class="sxs-lookup"><span data-stu-id="2f29c-107">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="2f29c-108">Poniższa grafika ilustruje ten proces.</span><span class="sxs-lookup"><span data-stu-id="2f29c-108">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="2f29c-109">![Fabryki i kanały klientów](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="2f29c-109">![Client Factories and Channels](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="2f29c-110">Fabryka kanałów tworzy kanały.</span><span class="sxs-lookup"><span data-stu-id="2f29c-110">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="2f29c-111">Po zamknięciu fabryki kanałów są odpowiedzialne za zamykanie utworzonych kanałów, które nie zostały jeszcze zamknięte.</span><span class="sxs-lookup"><span data-stu-id="2f29c-111">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="2f29c-112">Należy zauważyć, że model jest asymetryczny w tym miejscu, ponieważ gdy odbiornik kanału jest zamknięty, zatrzymuje tylko akceptowanie nowych kanałów, ale pozostawia istniejące kanały otwarte, dzięki czemu mogą kontynuować odbieranie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2f29c-112">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 <span data-ttu-id="2f29c-113">WCF zapewnia pomocników klasy podstawowej dla tego procesu.</span><span class="sxs-lookup"><span data-stu-id="2f29c-113">WCF provides base class helpers for this process.</span></span> <span data-ttu-id="2f29c-114">(Aby uzyskać diagram klas pomocnika kanału omówione w tym temacie, zobacz [Omówienie modelu kanału](channel-model-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="2f29c-114">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](channel-model-overview.md).)</span></span>  
  
- <span data-ttu-id="2f29c-115">Klasa <xref:System.ServiceModel.Channels.CommunicationObject> implementuje <xref:System.ServiceModel.ICommunicationObject> i wymusza maszynę stanu opisaną w kroku 2 [rozwijających się kanałów](developing-channels.md).</span><span class="sxs-lookup"><span data-stu-id="2f29c-115">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](developing-channels.md).</span></span>  
  
- <span data-ttu-id="2f29c-116">Klasa <xref:System.ServiceModel.Channels.ChannelManagerBase> implementuje <xref:System.ServiceModel.Channels.CommunicationObject> i zapewnia ujednoliconą klasę podstawową dla <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2f29c-116">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2f29c-117">Klasa <xref:System.ServiceModel.Channels.ChannelManagerBase> działa w <xref:System.ServiceModel.Channels.ChannelBase>połączeniu z , który jest <xref:System.ServiceModel.Channels.IChannel>klasą podstawową, która implementuje .</span><span class="sxs-lookup"><span data-stu-id="2f29c-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>
  
- <span data-ttu-id="2f29c-118">Klasa <xref:System.ServiceModel.Channels.ChannelFactoryBase> implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> <xref:System.ServiceModel.Channels.IChannelFactory> i konsoliduje `CreateChannel` przeciążenia `OnCreateChannel` w jedną metodę abstrakcyjną.</span><span class="sxs-lookup"><span data-stu-id="2f29c-118">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>
  
- <span data-ttu-id="2f29c-119">Klasa <xref:System.ServiceModel.Channels.ChannelListenerBase> implementuje <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="2f29c-119">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="2f29c-120">Zajmuje się podstawowym zarządzaniem państwem.</span><span class="sxs-lookup"><span data-stu-id="2f29c-120">It takes care of basic state management.</span></span>
  
 <span data-ttu-id="2f29c-121">Następująca dyskusja jest oparta na [transport: próbka UDP.](../samples/transport-udp.md)</span><span class="sxs-lookup"><span data-stu-id="2f29c-121">The following discussion is based upon the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="2f29c-122">Tworzenie fabryki kanałów</span><span class="sxs-lookup"><span data-stu-id="2f29c-122">Creating a Channel Factory</span></span>  
 <span data-ttu-id="2f29c-123">Pochodzi `UdpChannelFactory` z <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="2f29c-123">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="2f29c-124">Przykładowe <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> zastąpienia, aby zapewnić dostęp do wersji wiadomości kodera wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2f29c-124">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="2f29c-125">Przykład również zastępuje, <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> aby zniszczyć <xref:System.ServiceModel.Channels.BufferManager> nasze wystąpienie, gdy przechodzi maszyny stanu.</span><span class="sxs-lookup"><span data-stu-id="2f29c-125">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="2f29c-126">Kanał wyjściowy UDP</span><span class="sxs-lookup"><span data-stu-id="2f29c-126">The UDP Output Channel</span></span>  
 <span data-ttu-id="2f29c-127">Implements `UdpOutputChannel` <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="2f29c-127">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="2f29c-128">Konstruktor sprawdza poprawność argumentów <xref:System.Net.EndPoint> i konstruuje obiekt docelowy na podstawie <xref:System.ServiceModel.EndpointAddress> tego, który jest przekazywany w.</span><span class="sxs-lookup"><span data-stu-id="2f29c-128">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="2f29c-129">Zastąpienie <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> tworzy gniazdo, które jest używane do wysyłania wiadomości do tego <xref:System.Net.EndPoint>.</span><span class="sxs-lookup"><span data-stu-id="2f29c-129">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 ```csharp
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 <span data-ttu-id="2f29c-130">Kanał można zamknąć z gracją lub bezgrawych.</span><span class="sxs-lookup"><span data-stu-id="2f29c-130">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="2f29c-131">Jeśli kanał jest zamknięty bezpiecznie gniazdo jest zamknięty i wywołanie `OnClose` metody klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="2f29c-131">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="2f29c-132">Jeśli to zgłasza wyjątek, `Abort` infrastruktury wywołuje, aby upewnić się, że kanał jest czyszczone.</span><span class="sxs-lookup"><span data-stu-id="2f29c-132">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="2f29c-133">Wdrożenie `Send()` `BeginSend()` / `EndSend()`i .</span><span class="sxs-lookup"><span data-stu-id="2f29c-133">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="2f29c-134">To dzieli się na dwie główne sekcje.</span><span class="sxs-lookup"><span data-stu-id="2f29c-134">This breaks down into two main sections.</span></span> <span data-ttu-id="2f29c-135">Najpierw serializuj wiadomość do tablicy bajtów:</span><span class="sxs-lookup"><span data-stu-id="2f29c-135">First serialize the message into a byte array:</span></span>  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="2f29c-136">Następnie wyślij wynikowe dane na przewodzie:</span><span class="sxs-lookup"><span data-stu-id="2f29c-136">Then send the resulting data on the wire:</span></span>  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,
  messageBuffer.Offset,
  messageBuffer.Count,
  SocketFlags.None,
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f29c-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f29c-137">See also</span></span>

- [<span data-ttu-id="2f29c-138">Opracowywanie kanałów</span><span class="sxs-lookup"><span data-stu-id="2f29c-138">Developing Channels</span></span>](developing-channels.md)
