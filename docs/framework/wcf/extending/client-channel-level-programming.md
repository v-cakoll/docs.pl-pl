---
title: Programowanie na poziomie kanału klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: ea56c99d7d122dd20fc217f8ecb2937bcf81bec3
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324136"
---
# <a name="client-channel-level-programming"></a><span data-ttu-id="a9684-102">Programowanie na poziomie kanału klienta</span><span class="sxs-lookup"><span data-stu-id="a9684-102">Client Channel-Level Programming</span></span>
<span data-ttu-id="a9684-103">W tym temacie opisano sposób pisania aplikacji klienckiej Windows Communication Foundation (WCF) bez użycia <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> klasy i jego skojarzonego obiektu modelu.</span><span class="sxs-lookup"><span data-stu-id="a9684-103">This topic describes how to write a Windows Communication Foundation (WCF) client application without using the <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> class and its associated object model.</span></span>  
  
## <a name="sending-messages"></a><span data-ttu-id="a9684-104">Wysyłanie wiadomości</span><span class="sxs-lookup"><span data-stu-id="a9684-104">Sending Messages</span></span>  
 <span data-ttu-id="a9684-105">Gotowość wysyłać i odbierać i przetwarzać odpowiedzi, wymagane są następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="a9684-105">To be ready to send messages and receive and process replies, the following steps are required:</span></span>  
  
1. <span data-ttu-id="a9684-106">Tworzenie powiązania.</span><span class="sxs-lookup"><span data-stu-id="a9684-106">Create a binding.</span></span>  
  
2. <span data-ttu-id="a9684-107">Tworzenie fabryki kanałów.</span><span class="sxs-lookup"><span data-stu-id="a9684-107">Build a channel factory.</span></span>  
  
3. <span data-ttu-id="a9684-108">Utwórz kanał.</span><span class="sxs-lookup"><span data-stu-id="a9684-108">Create a channel.</span></span>  
  
4. <span data-ttu-id="a9684-109">Wyślij żądanie i odpowiedź do odczytu.</span><span class="sxs-lookup"><span data-stu-id="a9684-109">Send a request and read the reply.</span></span>  
  
5. <span data-ttu-id="a9684-110">Zamknij wszystkie obiekty kanału.</span><span class="sxs-lookup"><span data-stu-id="a9684-110">Close all channel objects.</span></span>  
  
#### <a name="creating-a-binding"></a><span data-ttu-id="a9684-111">Tworzenie powiązania</span><span class="sxs-lookup"><span data-stu-id="a9684-111">Creating a Binding</span></span>  
 <span data-ttu-id="a9684-112">Podobnie jak w przypadku odbieranego (zobacz [programowania na poziomie kanału usługi](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), wysyłanie komunikatów rozpoczyna się przez utworzenie powiązania.</span><span class="sxs-lookup"><span data-stu-id="a9684-112">Similar to the receiving case (see [Service Channel-Level Programming](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), sending messages starts by creating a binding.</span></span> <span data-ttu-id="a9684-113">W tym przykładzie tworzy nowy <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> i dodaje <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> do swojej kolekcji elementów.</span><span class="sxs-lookup"><span data-stu-id="a9684-113">This example creates a new <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> and adds an <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> to its Elements collection.</span></span>  
  
#### <a name="building-a-channelfactory"></a><span data-ttu-id="a9684-114">Tworzenie elementu ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="a9684-114">Building a ChannelFactory</span></span>  
 <span data-ttu-id="a9684-115">Zamiast tworzyć <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, tym razem możemy utworzyć <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> przez wywołanie metody <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> w powiązaniu, gdzie parametr typu jest <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a9684-115">Instead of creating a <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, this time we create a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> by calling <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> on the binding where the type parameter is <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a9684-116">Odbiorniki kanałów są używane przez stronę, która czeka na komunikaty przychodzące, fabryki kanałów są używane przez strony, która inicjuje komunikację, próba utworzenia kanału.</span><span class="sxs-lookup"><span data-stu-id="a9684-116">While channel listeners are used by the side that waits for incoming messages, channel factories are used by the side that initiates the communication to create a channel.</span></span> <span data-ttu-id="a9684-117">Podobnie jak odbiorniki kanałów fabryki kanałów najpierw należy otworzyć zanim będzie można ich użyć.</span><span class="sxs-lookup"><span data-stu-id="a9684-117">Just like channel listeners, channel factories must be opened first before they can be used.</span></span>  
  
#### <a name="creating-a-channel"></a><span data-ttu-id="a9684-118">Tworzenie kanału</span><span class="sxs-lookup"><span data-stu-id="a9684-118">Creating a Channel</span></span>  
 <span data-ttu-id="a9684-119">Następnie wywołaj <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> utworzyć <xref:System.ServiceModel.Channels.IRequestChannel>.</span><span class="sxs-lookup"><span data-stu-id="a9684-119">We then call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> to create an <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span> <span data-ttu-id="a9684-120">To wywołanie pobiera adres punktu końcowego za pomocą którego chcemy, aby komunikować się za pomocą nowego kanału tworzona.</span><span class="sxs-lookup"><span data-stu-id="a9684-120">This call takes the address of the endpoint with which we want to communicate using the new channel being created.</span></span> <span data-ttu-id="a9684-121">Gdy będziemy już mieć kanał, nazywamy otwórz go, aby umieścić ją w stanie gotowy do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="a9684-121">Once we have a channel, we call Open on it to put it in a state ready for communication.</span></span> <span data-ttu-id="a9684-122">W zależności od charakteru transportu tego wywołania do otworzenia może zainicjować połączenia z punktem końcowym docelowego lub mogą nic w ogóle w sieci.</span><span class="sxs-lookup"><span data-stu-id="a9684-122">Depending on the nature of the transport, this call to Open may initiate a connection with the target endpoint or may do nothing at all on the network.</span></span>  
  
#### <a name="sending-a-request-and-reading-the-reply"></a><span data-ttu-id="a9684-123">Wysyłanie żądania i odpowiedzi do czytania</span><span class="sxs-lookup"><span data-stu-id="a9684-123">Sending a Request and Reading the Reply</span></span>  
 <span data-ttu-id="a9684-124">Gdy będziemy już mieć otwarty kanał, firma Microsoft Utwórz wiadomość, a następnie wysłać żądanie i oczekiwania na odpowiedź, aby wrócić do tego za pomocą metody żądania tego kanału.</span><span class="sxs-lookup"><span data-stu-id="a9684-124">Once we have an opened channel, we can create a message and use the channel’s Request method to send the request and wait for the reply to come back.</span></span> <span data-ttu-id="a9684-125">Gdy metoda zwróci wartość, mamy komunikat odpowiedzi, który firma Microsoft może odczytać, aby dowiedzieć się, jaka była odpowiedzi punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a9684-125">When this method returns, we have a reply message that we can read to find out what the endpoint’s reply was.</span></span>  
  
#### <a name="closing-objects"></a><span data-ttu-id="a9684-126">Zamykanie obiektów</span><span class="sxs-lookup"><span data-stu-id="a9684-126">Closing Objects</span></span>  
 <span data-ttu-id="a9684-127">Aby uniknąć wyciek zasobów, możemy zamknąć obiekty używane podczas komunikacji, gdy nie są już wymagane.</span><span class="sxs-lookup"><span data-stu-id="a9684-127">To avoid leaking resources, we close objects used in communications when they are no longer required.</span></span>  
  
 <span data-ttu-id="a9684-128">Poniższy przykład kodu pokazuje podstawowe klienta za pomocą fabryki kanałów, aby wysłać wiadomość i odczytać odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a9684-128">The following code example shows a basic client using the channel factory to send a message and read the reply.</span></span>  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
