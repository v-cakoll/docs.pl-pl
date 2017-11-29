---
title: Transporty w programie Windows Communication Foundation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 115e2a69c7d990c7d4c59634644fb557e83ad405
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="23b16-102">Transporty w programie Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="23b16-102">Transports in Windows Communication Foundation</span></span>
<span data-ttu-id="23b16-103">Warstwa transportu jest na najniższym poziomie stosu kanału.</span><span class="sxs-lookup"><span data-stu-id="23b16-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="23b16-104">Transporty główny używany w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] są HTTP, HTTPS TCP i nazwane potoki.</span><span class="sxs-lookup"><span data-stu-id="23b16-104">The main transports used in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="23b16-105">Tematy w tej sekcji omówiono w nim wybierania tych transportów Konfigurowanie transportu i ustawienie właściwości dostrajania.</span><span class="sxs-lookup"><span data-stu-id="23b16-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="23b16-106">zawiera dodatkowe transportów.</span><span class="sxs-lookup"><span data-stu-id="23b16-106"> includes additional transports.</span></span> <span data-ttu-id="23b16-107">Informacje o transporcie MSMQ (MSMQ), zobacz [kolejki i sesje niezawodne](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="23b16-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="23b16-108">Aby uzyskać informacje o transporcie peer-to-peer, zobacz [sieci Peer-to-Peer](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="23b16-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="23b16-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="23b16-109">In This Section</span></span>  
 [<span data-ttu-id="23b16-110">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="23b16-110">Choosing a Transport</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 <span data-ttu-id="23b16-111">W tym artykule opisano trzy główne transportu i zagadnienia dotyczące wybranie jednego.</span><span class="sxs-lookup"><span data-stu-id="23b16-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="23b16-112">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="23b16-112">Choosing a Message Encoder</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 <span data-ttu-id="23b16-113">Zawiera opis czynników, które należy wziąć pod uwagę podczas wybierania element powiązania Kodowanie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="23b16-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="23b16-114">Strumieniowy Transfer komunikatów</span><span class="sxs-lookup"><span data-stu-id="23b16-114">Streaming Message Transfer</span></span>](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 <span data-ttu-id="23b16-115">Zawiera opis sposobu konfigurowania warstwy transportowej w celu przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="23b16-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="23b16-116">Konfigurowanie protokołów HTTP i HTTPS</span><span class="sxs-lookup"><span data-stu-id="23b16-116">Configuring HTTP and HTTPS</span></span>](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 <span data-ttu-id="23b16-117">Zawiera opis sposobu konfigurowania elementy powiązania transportu HTTP i HTTPS.</span><span class="sxs-lookup"><span data-stu-id="23b16-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="23b16-118">Porady: Zastąp rezerwację adresu URL programu WCF ograniczoną rezerwacją</span><span class="sxs-lookup"><span data-stu-id="23b16-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="23b16-119">Informacje dotyczące używania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zastrzeżenia ograniczone adresu URL.</span><span class="sxs-lookup"><span data-stu-id="23b16-119">Describes how to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]URL restricted reservations.</span></span>  
  
 [<span data-ttu-id="23b16-120">Przydziały dla transportu</span><span class="sxs-lookup"><span data-stu-id="23b16-120">Transport Quotas</span></span>](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 <span data-ttu-id="23b16-121">Zawiera opis zagadnień w Ustawianie przydziałów dostępne w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="23b16-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="23b16-122">Praca z translatorami adresów sieciowych i zapór</span><span class="sxs-lookup"><span data-stu-id="23b16-122">Working with NATs and Firewalls</span></span>](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 <span data-ttu-id="23b16-123">Zawiera opis sposobu konfigurowania warstwy transportowej, gdy komunikaty są wysyłane lub odbierane za zaporą lub w przypadku translatora adresów sieciowych (NAT).</span><span class="sxs-lookup"><span data-stu-id="23b16-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="23b16-124">Udostępniania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="23b16-124">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 <span data-ttu-id="23b16-125">Informacje dotyczące używania składnik Udostępnianie portów Net.TCP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="23b16-125">Describes how to use the Net.TCP Port Sharing component of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="23b16-126">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="23b16-126">Reference</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="23b16-127">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="23b16-127">Related Sections</span></span>  
 [<span data-ttu-id="23b16-128">Powiązania</span><span class="sxs-lookup"><span data-stu-id="23b16-128">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [<span data-ttu-id="23b16-129">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="23b16-129">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
