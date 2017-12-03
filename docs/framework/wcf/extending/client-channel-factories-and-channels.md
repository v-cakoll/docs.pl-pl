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
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="0d2c0-102">Klienta: Fabryk kanałów i kanały</span><span class="sxs-lookup"><span data-stu-id="0d2c0-102">Client: Channel Factories and Channels</span></span>
<span data-ttu-id="0d2c0-103">W tym temacie omówiono tworzenie fabryki kanałów i kanały.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-103">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="0d2c0-104">Fabryki kanałów i kanały</span><span class="sxs-lookup"><span data-stu-id="0d2c0-104">Channel Factories and Channels</span></span>  
 <span data-ttu-id="0d2c0-105">Fabryk kanałów, które są odpowiedzialne za tworzenie kanałów.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-105">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="0d2c0-106">Kanałów utworzonych przez fabryk kanałów, które są używane do wysyłania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-106">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="0d2c0-107">Te kanały są zobowiązani do uzyskiwania wiadomości z warstwy powyżej, wykonywania przetwarzania jest wymagane, a następnie wysyła komunikat do warstwy poniżej.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-107">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="0d2c0-108">Poniższa ilustracja przedstawia tego procesu.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-108">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="0d2c0-109">![Fabryki klienta i kanały](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="0d2c0-109">![Client Factories and Channels](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="0d2c0-110">Fabryka kanałów tworzy kanałów.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-110">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="0d2c0-111">Po zamknięciu fabryk kanałów, które są zobowiązani do zamykania kanałów, które są tworzone, które nie są jeszcze zamknięty.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-111">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="0d2c0-112">Należy pamiętać, że model asymetrycznego tutaj ponieważ zamknięcie odbiornika kanałów tylko przestaje akceptować nowych kanałów, ale pozostawia otwartych istniejące kanały, dzięki czemu może nadal otrzymywać wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-112">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="0d2c0-113">udostępnia pomocników klasę podstawową dla tego procesu.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-113"> provides base class helpers for this process.</span></span> <span data-ttu-id="0d2c0-114">(Dla diagramu klas pomocniczych kanału omówione w tym temacie, zobacz [Przegląd modelu kanału](../../../../docs/framework/wcf/extending/channel-model-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="0d2c0-114">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](../../../../docs/framework/wcf/extending/channel-model-overview.md).)</span></span>  
  
-   <span data-ttu-id="0d2c0-115"><xref:System.ServiceModel.Channels.CommunicationObject> Klasa implementuje <xref:System.ServiceModel.ICommunicationObject> i wymusza automatu stanów opisany w kroku 2 [kanały rozwijających się](../../../../docs/framework/wcf/extending/developing-channels.md).</span><span class="sxs-lookup"><span data-stu-id="0d2c0-115">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](../../../../docs/framework/wcf/extending/developing-channels.md).</span></span>  
  
-   <span data-ttu-id="0d2c0-116">"<xref:System.ServiceModel.Channels.ChannelManagerBase> Klasa implementuje <xref:System.ServiceModel.Channels.CommunicationObject> i zapewnia ujednolicone klasa podstawowa dla <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-116">The``<xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0d2c0-117"><xref:System.ServiceModel.Channels.ChannelManagerBase> Klasa działa w połączeniu z <xref:System.ServiceModel.Channels.ChannelBase>, która jest klasy podstawowej, która implementuje <xref:System.ServiceModel.Channels.IChannel>.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
-   <span data-ttu-id="0d2c0-118">"<xref:System.ServiceModel.Channels.ChannelFactoryBase> Klasa implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> i <xref:System.ServiceModel.Channels.IChannelFactory> i konsoliduje `CreateChannel` overloads do jednego `OnCreateChannel` metody abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-118">The``<xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
-   <span data-ttu-id="0d2c0-119">"<xref:System.ServiceModel.Channels.ChannelListenerBase> Klasa implementuje <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-119">The``<xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="0d2c0-120">Odpowiada on za podstawowy zarządzania.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-120">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="0d2c0-121">Następujące dyskusji opiera się na [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-121">The following discussion is based upon the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="0d2c0-122">Tworzenie fabryki kanałów</span><span class="sxs-lookup"><span data-stu-id="0d2c0-122">Creating a Channel Factory</span></span>  
 <span data-ttu-id="0d2c0-123">`UdpChannelFactory` Pochodną <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-123">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="0d2c0-124">Zastępuje próbki <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> zapewniające dostęp do wersji kodera wiadomości wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-124">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="0d2c0-125">Zastępuje również próbki <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> do zerwanie naszych wystąpienie <xref:System.ServiceModel.Channels.BufferManager> podczas przejścia komputera stanu.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-125">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="0d2c0-126">Kanał wyjściowy UDP</span><span class="sxs-lookup"><span data-stu-id="0d2c0-126">The UDP Output Channel</span></span>  
 <span data-ttu-id="0d2c0-127">`UdpOutputChannel` Implementuje <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-127">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="0d2c0-128">Konstruktor sprawdza poprawność argumentów i tworzy miejsce docelowe <xref:System.Net.EndPoint> na podstawie obiektu <xref:System.ServiceModel.EndpointAddress> przekazanego pakietu.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-128">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="0d2c0-129">Zastąpienie z <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> tworzy gniazda, który jest używany do wysyłania wiadomości do tego <xref:System.Net.EndPoint>.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-129">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 `this.socket = new Socket(`  
  
 `this.remoteEndPoint.AddressFamily,`  
  
 `SocketType.Dgram,`  
  
 `ProtocolType.Udp`  
  
 `);`  
  
 <span data-ttu-id="0d2c0-130">Kanał może zostać zamknięty, bezpiecznie lub ungracefully.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-130">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="0d2c0-131">Jeśli bezpiecznie zamknięcie kanału gniazda zostanie zamknięte, a połączenie jest nawiązywane w klasie podstawowej `OnClose` metody.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-131">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="0d2c0-132">Jeśli to zgłasza wyjątek, wywołuje metodę infrastruktury `Abort` zapewnienie kanał jest wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-132">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="0d2c0-133">Implementowanie `Send()` i `BeginSend()` / `EndSend()`.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-133">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="0d2c0-134">To dzieli się na dwóch głównych sekcji.</span><span class="sxs-lookup"><span data-stu-id="0d2c0-134">This breaks down into two main sections.</span></span> <span data-ttu-id="0d2c0-135">Najpierw serializacji komunikatu do tablicy typu byte:</span><span class="sxs-lookup"><span data-stu-id="0d2c0-135">First serialize the message into a byte array:</span></span>  
  
```  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="0d2c0-136">Następnie wysyłania danych w sieci:</span><span class="sxs-lookup"><span data-stu-id="0d2c0-136">Then send the resulting data on the wire:</span></span>  
  
```  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d2c0-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d2c0-137">See Also</span></span>  
 [<span data-ttu-id="0d2c0-138">Opracowywanie kanałów</span><span class="sxs-lookup"><span data-stu-id="0d2c0-138">Developing Channels</span></span>](../../../../docs/framework/wcf/extending/developing-channels.md)
