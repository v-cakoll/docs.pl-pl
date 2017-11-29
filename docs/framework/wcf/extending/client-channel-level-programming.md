---
title: "Programowanie na poziomie kanału klienta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a6ffe482c8d04314b79ee5bb7029d2583c56c363
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="client-channel-level-programming"></a><span data-ttu-id="d16b8-102">Programowanie na poziomie kanału klienta</span><span class="sxs-lookup"><span data-stu-id="d16b8-102">Client Channel-Level Programming</span></span>
<span data-ttu-id="d16b8-103">W tym temacie opisano sposób zapisania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji klienckiej bez użycia <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> klasy i jego skojarzony obiekt modelu.</span><span class="sxs-lookup"><span data-stu-id="d16b8-103">This topic describes how to write a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client application without using the <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> class and its associated object model.</span></span>  
  
## <a name="sending-messages"></a><span data-ttu-id="d16b8-104">Wysyłanie wiadomości</span><span class="sxs-lookup"><span data-stu-id="d16b8-104">Sending Messages</span></span>  
 <span data-ttu-id="d16b8-105">Aby mógł wysyłać i odbierać i przetwarzać odpowiedzi, wymagane są następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="d16b8-105">To be ready to send messages and receive and process replies, the following steps are required:</span></span>  
  
1.  <span data-ttu-id="d16b8-106">Utwórz powiązanie.</span><span class="sxs-lookup"><span data-stu-id="d16b8-106">Create a binding.</span></span>  
  
2.  <span data-ttu-id="d16b8-107">Tworzenie fabryki kanałów.</span><span class="sxs-lookup"><span data-stu-id="d16b8-107">Build a channel factory.</span></span>  
  
3.  <span data-ttu-id="d16b8-108">Tworzenie kanału.</span><span class="sxs-lookup"><span data-stu-id="d16b8-108">Create a channel.</span></span>  
  
4.  <span data-ttu-id="d16b8-109">Wyślij żądanie i odpowiedź do odczytu.</span><span class="sxs-lookup"><span data-stu-id="d16b8-109">Send a request and read the reply.</span></span>  
  
5.  <span data-ttu-id="d16b8-110">Zamknij wszystkie obiekty kanału.</span><span class="sxs-lookup"><span data-stu-id="d16b8-110">Close all channel objects.</span></span>  
  
#### <a name="creating-a-binding"></a><span data-ttu-id="d16b8-111">Tworzenie powiązania</span><span class="sxs-lookup"><span data-stu-id="d16b8-111">Creating a Binding</span></span>  
 <span data-ttu-id="d16b8-112">Podobnie jak w przypadku odbierania (zobacz [programowania na poziomie kanału usługi](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), wysyłanie wiadomości rozpoczyna się przez utworzenie powiązania.</span><span class="sxs-lookup"><span data-stu-id="d16b8-112">Similar to the receiving case (see [Service Channel-Level Programming](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), sending messages starts by creating a binding.</span></span> <span data-ttu-id="d16b8-113">Tworzy nową klasę w tym przykładzie <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> i dodaje <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> do swojej kolekcji elementów.</span><span class="sxs-lookup"><span data-stu-id="d16b8-113">This example creates a new <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> and adds an <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> to its Elements collection.</span></span>  
  
#### <a name="building-a-channelfactory"></a><span data-ttu-id="d16b8-114">Tworzenie elementu ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="d16b8-114">Building a ChannelFactory</span></span>  
 <span data-ttu-id="d16b8-115">Zamiast tworzyć <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, utworzymy teraz <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> przez wywołanie metody <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> w powiązaniu, gdzie parametr typu jest <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d16b8-115">Instead of creating a <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, this time we create a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> by calling <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> on the binding where the type parameter is <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d16b8-116">Odbiorniki kanałów są używane przez stronę oczekiwania dla komunikatów przychodzących, fabryk kanałów, które są używane przez strony, która inicjuje komunikację, aby utworzyć kanał.</span><span class="sxs-lookup"><span data-stu-id="d16b8-116">While channel listeners are used by the side that waits for incoming messages, channel factories are used by the side that initiates the communication to create a channel.</span></span> <span data-ttu-id="d16b8-117">Podobnie jak odbiorniki kanałów fabryk kanałów, które należy otworzyć przed ich użyciem.</span><span class="sxs-lookup"><span data-stu-id="d16b8-117">Just like channel listeners, channel factories must be opened first before they can be used.</span></span>  
  
#### <a name="creating-a-channel"></a><span data-ttu-id="d16b8-118">Tworzenie kanału</span><span class="sxs-lookup"><span data-stu-id="d16b8-118">Creating a Channel</span></span>  
 <span data-ttu-id="d16b8-119">Następnie wywołaj <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> do utworzenia <xref:System.ServiceModel.Channels.IRequestChannel>.</span><span class="sxs-lookup"><span data-stu-id="d16b8-119">We then call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> to create an <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span> <span data-ttu-id="d16b8-120">To wywołanie pobiera adres punktu końcowego, z którą chcemy, aby komunikować się za pomocą nowego kanału tworzona.</span><span class="sxs-lookup"><span data-stu-id="d16b8-120">This call takes the address of the endpoint with which we want to communicate using the new channel being created.</span></span> <span data-ttu-id="d16b8-121">Gdy mamy kanału Open nazywa się na niej umieszcza je w stanie gotowy do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="d16b8-121">Once we have a channel, we call Open on it to put it in a state ready for communication.</span></span> <span data-ttu-id="d16b8-122">W zależności od charakteru transportu to wywołanie do otworzenia mogą inicjować połączenia z punktem końcowym docelowej lub może nic nie rób w ogóle w sieci.</span><span class="sxs-lookup"><span data-stu-id="d16b8-122">Depending on the nature of the transport, this call to Open may initiate a connection with the target endpoint or may do nothing at all on the network.</span></span>  
  
#### <a name="sending-a-request-and-reading-the-reply"></a><span data-ttu-id="d16b8-123">Wysyłanie żądania i odczytywanie odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="d16b8-123">Sending a Request and Reading the Reply</span></span>  
 <span data-ttu-id="d16b8-124">Po mamy kanał otwarty możemy utworzyć wiadomości i używać metody żądania kanału do wysyłania żądania i oczekiwania na odpowiedź, aby wrócić do.</span><span class="sxs-lookup"><span data-stu-id="d16b8-124">Once we have an opened channel, we can create a message and use the channel’s Request method to send the request and wait for the reply to come back.</span></span> <span data-ttu-id="d16b8-125">Po powrocie z tej metody mamy komunikat odpowiedzi, który firma Microsoft może być odczytany Aby dowiedzieć się, została odpowiedzi punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="d16b8-125">When this method returns, we have a reply message that we can read to find out what the endpoint’s reply was.</span></span>  
  
#### <a name="closing-objects"></a><span data-ttu-id="d16b8-126">Zamykanie obiektów</span><span class="sxs-lookup"><span data-stu-id="d16b8-126">Closing Objects</span></span>  
 <span data-ttu-id="d16b8-127">Aby uniknąć przeciek zasobów, możemy zamknąć obiekty używane podczas komunikacji, gdy nie są już wymagane.</span><span class="sxs-lookup"><span data-stu-id="d16b8-127">To avoid leaking resources, we close objects used in communications when they are no longer required.</span></span>  
  
 <span data-ttu-id="d16b8-128">Poniższy przykładowy kod przedstawia podstawowe klienta przy użyciu fabryki kanału do wysyłania wiadomości i odczytu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="d16b8-128">The following code example shows a basic client using the channel factory to send a message and read the reply.</span></span>  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
