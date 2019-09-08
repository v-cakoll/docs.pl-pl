---
title: 'Klient: Fabryki kanałów i kanały'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: 3dfcca0d5492a3fa376ec184f4bdd9bfa03b53c0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795861"
---
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="0a020-102">Klient: Fabryki kanałów i kanały</span><span class="sxs-lookup"><span data-stu-id="0a020-102">Client: Channel Factories and Channels</span></span>
<span data-ttu-id="0a020-103">W tym temacie omówiono tworzenie fabryk kanałów i kanałów.</span><span class="sxs-lookup"><span data-stu-id="0a020-103">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="0a020-104">Fabryki kanałów i kanały</span><span class="sxs-lookup"><span data-stu-id="0a020-104">Channel Factories and Channels</span></span>  
 <span data-ttu-id="0a020-105">Fabryki kanałów są odpowiedzialne za tworzenie kanałów.</span><span class="sxs-lookup"><span data-stu-id="0a020-105">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="0a020-106">Kanały utworzone za pomocą fabryk kanałów są używane do wysyłania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="0a020-106">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="0a020-107">Kanały te są odpowiedzialne za pobieranie wiadomości z warstwy powyżej, wykonując niezależnie od tego, co jest konieczne, a następnie wysyłając komunikat do poniższej warstwy.</span><span class="sxs-lookup"><span data-stu-id="0a020-107">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="0a020-108">Poniższy rysunek ilustruje ten proces.</span><span class="sxs-lookup"><span data-stu-id="0a020-108">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="0a020-109">![Fabryki i kanały klienta](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="0a020-109">![Client Factories and Channels](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="0a020-110">Fabryka kanałów tworzy kanały.</span><span class="sxs-lookup"><span data-stu-id="0a020-110">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="0a020-111">Po zamknięciu fabryki kanałów są odpowiedzialne za zamknięcie wszelkich utworzonych przez siebie kanałów, które nie zostały jeszcze zamknięte.</span><span class="sxs-lookup"><span data-stu-id="0a020-111">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="0a020-112">Należy zauważyć, że model jest asymetryczny w tym miejscu, ponieważ gdy odbiornik kanału jest zamknięty, nie akceptuje tylko nowych kanałów, ale pozostawia otwarte kanały, aby mogły nadal otrzymywać komunikaty.</span><span class="sxs-lookup"><span data-stu-id="0a020-112">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 <span data-ttu-id="0a020-113">Funkcja WCF udostępnia pomocników klasy bazowej dla tego procesu.</span><span class="sxs-lookup"><span data-stu-id="0a020-113">WCF provides base class helpers for this process.</span></span> <span data-ttu-id="0a020-114">(Aby zapoznać się z diagramem klas pomocnika kanału omawianych w tym temacie, zobacz temat [model kanału — Omówienie](channel-model-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="0a020-114">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](channel-model-overview.md).)</span></span>  
  
- <span data-ttu-id="0a020-115">Klasa implementuje <xref:System.ServiceModel.ICommunicationObject> i wymusza komputer stanu opisany w kroku 2 [tworzenia kanałów.](developing-channels.md) <xref:System.ServiceModel.Channels.CommunicationObject></span><span class="sxs-lookup"><span data-stu-id="0a020-115">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](developing-channels.md).</span></span>  
  
- <span data-ttu-id="0a020-116">Klasa implementuje <xref:System.ServiceModel.Channels.CommunicationObject> i udostępnia ujednoliconą klasę bazową dla <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>. <xref:System.ServiceModel.Channels.ChannelManagerBase></span><span class="sxs-lookup"><span data-stu-id="0a020-116">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0a020-117">Klasa działa w połączeniu z <xref:System.ServiceModel.Channels.ChannelBase>, która jest klasą bazową implementującą <xref:System.ServiceModel.Channels.IChannel>. <xref:System.ServiceModel.Channels.ChannelManagerBase></span><span class="sxs-lookup"><span data-stu-id="0a020-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>
  
- <span data-ttu-id="0a020-118"><xref:System.ServiceModel.Channels.ChannelFactoryBase> Klasa implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> i<xref:System.ServiceModel.Channels.IChannelFactory> konsoliduje przeciążeniaw`OnCreateChannel` jedną metodę abstrakcyjną. `CreateChannel`</span><span class="sxs-lookup"><span data-stu-id="0a020-118">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>
  
- <span data-ttu-id="0a020-119"><xref:System.ServiceModel.Channels.ChannelListenerBase> Klasa implementuje<xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="0a020-119">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="0a020-120">Dział IT zajmuje się podstawowym zarządzaniem stanem.</span><span class="sxs-lookup"><span data-stu-id="0a020-120">It takes care of basic state management.</span></span> 
  
 <span data-ttu-id="0a020-121">Następująca dyskusja jest oparta [na transporcie: Przykład](../samples/transport-udp.md) protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="0a020-121">The following discussion is based upon the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="0a020-122">Tworzenie fabryki kanałów</span><span class="sxs-lookup"><span data-stu-id="0a020-122">Creating a Channel Factory</span></span>  
 <span data-ttu-id="0a020-123">`UdpChannelFactory` Pochodzi od<xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="0a020-123">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="0a020-124">Przykłady zastąpień <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> w celu zapewnienia dostępu do wersji komunikatu kodera wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0a020-124">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="0a020-125">Przykład przesłonił <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> również, aby wypróbować <xref:System.ServiceModel.Channels.BufferManager> nasze wystąpienie po przeniesieniu automatu Stanów.</span><span class="sxs-lookup"><span data-stu-id="0a020-125">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="0a020-126">Kanał wyjściowy UDP</span><span class="sxs-lookup"><span data-stu-id="0a020-126">The UDP Output Channel</span></span>  
 <span data-ttu-id="0a020-127">`UdpOutputChannel` Implementacja .<xref:System.ServiceModel.Channels.IOutputChannel></span><span class="sxs-lookup"><span data-stu-id="0a020-127">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="0a020-128">Konstruktor sprawdza poprawność argumentów i konstruuje obiekt <xref:System.Net.EndPoint> docelowy na podstawie <xref:System.ServiceModel.EndpointAddress> przekazanego elementu.</span><span class="sxs-lookup"><span data-stu-id="0a020-128">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="0a020-129">Przesłonięcie <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> tworzenia gniazda, które jest używane do wysyłania komunikatów do tego <xref:System.Net.EndPoint>obiektu.</span><span class="sxs-lookup"><span data-stu-id="0a020-129">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 ```csharp 
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 <span data-ttu-id="0a020-130">Kanał może być zamknięty bezpiecznie lub bezproblemowo.</span><span class="sxs-lookup"><span data-stu-id="0a020-130">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="0a020-131">Jeśli kanał zostanie zamknięty bezpiecznie, gniazdo jest zamknięte i zostanie wykonane wywołanie metody klasy `OnClose` bazowej.</span><span class="sxs-lookup"><span data-stu-id="0a020-131">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="0a020-132">W przypadku zgłaszania wyjątku, infrastruktura wywołuje `Abort` , aby upewnić się, że kanał jest czyszczony.</span><span class="sxs-lookup"><span data-stu-id="0a020-132">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="0a020-133">Implementuj `Send()` i `BeginSend()`. / `EndSend()`</span><span class="sxs-lookup"><span data-stu-id="0a020-133">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="0a020-134">Ten podział jest podzielony na dwie główne sekcje.</span><span class="sxs-lookup"><span data-stu-id="0a020-134">This breaks down into two main sections.</span></span> <span data-ttu-id="0a020-135">Najpierw serializować komunikat do tablicy bajtowej:</span><span class="sxs-lookup"><span data-stu-id="0a020-135">First serialize the message into a byte array:</span></span>  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="0a020-136">Następnie Wyślij dane uzyskane z sieci:</span><span class="sxs-lookup"><span data-stu-id="0a020-136">Then send the resulting data on the wire:</span></span>  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a020-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a020-137">See also</span></span>

- [<span data-ttu-id="0a020-138">Opracowywanie kanałów</span><span class="sxs-lookup"><span data-stu-id="0a020-138">Developing Channels</span></span>](developing-channels.md)
