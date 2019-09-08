---
title: Programowanie na poziomie kanału klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: 4f24c558b1d5303b2417416beb14555539f498ea
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797268"
---
# <a name="client-channel-level-programming"></a><span data-ttu-id="fb913-102">Programowanie na poziomie kanału klienta</span><span class="sxs-lookup"><span data-stu-id="fb913-102">Client Channel-Level Programming</span></span>
<span data-ttu-id="fb913-103">W tym temacie opisano sposób pisania aplikacji klienckiej programu Windows Communication Foundation (WCF) bez użycia <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> klasy i skojarzonego z nią modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="fb913-103">This topic describes how to write a Windows Communication Foundation (WCF) client application without using the <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> class and its associated object model.</span></span>  
  
## <a name="sending-messages"></a><span data-ttu-id="fb913-104">Wysyłanie komunikatów</span><span class="sxs-lookup"><span data-stu-id="fb913-104">Sending Messages</span></span>  
 <span data-ttu-id="fb913-105">Aby można było wysyłać wiadomości i odbierać i przetwarzać odpowiedzi, wymagane są następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="fb913-105">To be ready to send messages and receive and process replies, the following steps are required:</span></span>  
  
1. <span data-ttu-id="fb913-106">Utwórz powiązanie.</span><span class="sxs-lookup"><span data-stu-id="fb913-106">Create a binding.</span></span>  
  
2. <span data-ttu-id="fb913-107">Kompiluj fabrykę kanałów.</span><span class="sxs-lookup"><span data-stu-id="fb913-107">Build a channel factory.</span></span>  
  
3. <span data-ttu-id="fb913-108">Utwórz kanał.</span><span class="sxs-lookup"><span data-stu-id="fb913-108">Create a channel.</span></span>  
  
4. <span data-ttu-id="fb913-109">Wyślij żądanie i przeczytaj odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="fb913-109">Send a request and read the reply.</span></span>  
  
5. <span data-ttu-id="fb913-110">Zamknij wszystkie obiekty kanału.</span><span class="sxs-lookup"><span data-stu-id="fb913-110">Close all channel objects.</span></span>  
  
#### <a name="creating-a-binding"></a><span data-ttu-id="fb913-111">Tworzenie powiązania</span><span class="sxs-lookup"><span data-stu-id="fb913-111">Creating a Binding</span></span>  
 <span data-ttu-id="fb913-112">Podobnie jak w przypadku odbioru (zobacz [Programowanie na poziomie kanału usługi](service-channel-level-programming.md)), wysyłanie komunikatów zaczyna się od utworzenia powiązania.</span><span class="sxs-lookup"><span data-stu-id="fb913-112">Similar to the receiving case (see [Service Channel-Level Programming](service-channel-level-programming.md)), sending messages starts by creating a binding.</span></span> <span data-ttu-id="fb913-113">Ten przykład tworzy nowe <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> dodaje do kolekcji elementów.</span><span class="sxs-lookup"><span data-stu-id="fb913-113">This example creates a new <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> and adds an <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> to its Elements collection.</span></span>  
  
#### <a name="building-a-channelfactory"></a><span data-ttu-id="fb913-114">Kompilowanie elementu ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="fb913-114">Building a ChannelFactory</span></span>  
 <span data-ttu-id="fb913-115">Zamiast tworzenia <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, ten czas <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> tworzymy, wywołując <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> na powiązanie, gdzie parametr typu jest <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fb913-115">Instead of creating a <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, this time we create a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> by calling <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> on the binding where the type parameter is <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fb913-116">Gdy Odbiorniki kanałów są używane po stronie, które czekają na komunikaty przychodzące, fabryki kanałów są używane przez stronę, która inicjuje komunikację w celu utworzenia kanału.</span><span class="sxs-lookup"><span data-stu-id="fb913-116">While channel listeners are used by the side that waits for incoming messages, channel factories are used by the side that initiates the communication to create a channel.</span></span> <span data-ttu-id="fb913-117">Podobnie jak w przypadku odbiorników kanału należy najpierw otworzyć fabryki kanałów przed ich użyciem.</span><span class="sxs-lookup"><span data-stu-id="fb913-117">Just like channel listeners, channel factories must be opened first before they can be used.</span></span>  
  
#### <a name="creating-a-channel"></a><span data-ttu-id="fb913-118">Tworzenie kanału</span><span class="sxs-lookup"><span data-stu-id="fb913-118">Creating a Channel</span></span>  
 <span data-ttu-id="fb913-119">Następnie wywołajmy <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> , aby <xref:System.ServiceModel.Channels.IRequestChannel>utworzyć.</span><span class="sxs-lookup"><span data-stu-id="fb913-119">We then call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> to create an <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span> <span data-ttu-id="fb913-120">To wywołanie Pobiera adres punktu końcowego, z którym chcemy się komunikować przy użyciu nowego tworzonego kanału.</span><span class="sxs-lookup"><span data-stu-id="fb913-120">This call takes the address of the endpoint with which we want to communicate using the new channel being created.</span></span> <span data-ttu-id="fb913-121">Gdy będziemy korzystać z kanału, dzwonimy na niego, aby przygotować go w stanie gotowym do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="fb913-121">Once we have a channel, we call Open on it to put it in a state ready for communication.</span></span> <span data-ttu-id="fb913-122">W zależności od rodzaju transportu to wywołanie do otwarcia może inicjować połączenie z docelowym punktem końcowym lub w ogóle nie ma nic w sieci.</span><span class="sxs-lookup"><span data-stu-id="fb913-122">Depending on the nature of the transport, this call to Open may initiate a connection with the target endpoint or may do nothing at all on the network.</span></span>  
  
#### <a name="sending-a-request-and-reading-the-reply"></a><span data-ttu-id="fb913-123">Wysyłanie żądania i odczytywanie odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="fb913-123">Sending a Request and Reading the Reply</span></span>  
 <span data-ttu-id="fb913-124">Po otwarciu kanału można utworzyć komunikat i użyć metody żądania kanału, aby wysłać żądanie i poczekać na powrót odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="fb913-124">Once we have an opened channel, we can create a message and use the channel’s Request method to send the request and wait for the reply to come back.</span></span> <span data-ttu-id="fb913-125">Po powrocie tej metody mamy komunikat odpowiedzi, który możemy przeczytać, aby dowiedzieć się, co to jest odpowiedź punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="fb913-125">When this method returns, we have a reply message that we can read to find out what the endpoint’s reply was.</span></span>  
  
#### <a name="closing-objects"></a><span data-ttu-id="fb913-126">Zamykanie obiektów</span><span class="sxs-lookup"><span data-stu-id="fb913-126">Closing Objects</span></span>  
 <span data-ttu-id="fb913-127">Aby uniknąć przecieków zasobów, należy zamknąć obiekty używane w komunikacji, gdy nie są już wymagane.</span><span class="sxs-lookup"><span data-stu-id="fb913-127">To avoid leaking resources, we close objects used in communications when they are no longer required.</span></span>  
  
 <span data-ttu-id="fb913-128">Poniższy przykład kodu pokazuje klienta podstawowego przy użyciu fabryki kanałów do wysyłania wiadomości i odczytywania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="fb913-128">The following code example shows a basic client using the channel factory to send a message and read the reply.</span></span>  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
