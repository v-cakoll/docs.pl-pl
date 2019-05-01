---
title: Transporty w programie Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 6bb8e8b90c26533661684bd403b9ec439f1bb37e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933734"
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="4118e-102">Transporty w programie Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="4118e-102">Transports in Windows Communication Foundation</span></span>
<span data-ttu-id="4118e-103">Warstwa transportu jest na najniższym poziomie stosu kanału.</span><span class="sxs-lookup"><span data-stu-id="4118e-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="4118e-104">Główne transportów używane w Windows Communication Foundation (WCF) są HTTP, HTTPS, TCP i nazwane potoki.</span><span class="sxs-lookup"><span data-stu-id="4118e-104">The main transports used in Windows Communication Foundation (WCF) are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="4118e-105">Tematy w tej sekcji omówiono wybierania tych transportu, konfigurowanie transportu i ustawienie właściwości dostrajania.</span><span class="sxs-lookup"><span data-stu-id="4118e-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 <span data-ttu-id="4118e-106">Usługi WCF zawiera dodatkowe transportów.</span><span class="sxs-lookup"><span data-stu-id="4118e-106">WCF includes additional transports.</span></span> <span data-ttu-id="4118e-107">Aby uzyskać informacji na temat transportu MSMQ (MSMQ), zobacz [kolejki i sesje niezawodne](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="4118e-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="4118e-108">Aby uzyskać informacje o transporcie peer-to-peer, zobacz [sieci Peer-to-Peer](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="4118e-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4118e-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="4118e-109">In This Section</span></span>  
 [<span data-ttu-id="4118e-110">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="4118e-110">Choosing a Transport</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 <span data-ttu-id="4118e-111">W tym artykule opisano trzy główne transportu i zagadnienia dotyczące wybierania go.</span><span class="sxs-lookup"><span data-stu-id="4118e-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="4118e-112">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="4118e-112">Choosing a Message Encoder</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 <span data-ttu-id="4118e-113">Zawiera opis czynników, które należy wziąć pod uwagę podczas wybierania element powiązania Kodowanie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="4118e-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="4118e-114">Strumieniowy transfer komunikatów</span><span class="sxs-lookup"><span data-stu-id="4118e-114">Streaming Message Transfer</span></span>](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 <span data-ttu-id="4118e-115">W tym artykule opisano sposób konfigurowania warstwy transportowej w celu przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="4118e-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="4118e-116">Konfigurowanie protokołów HTTP i HTTPS</span><span class="sxs-lookup"><span data-stu-id="4118e-116">Configuring HTTP and HTTPS</span></span>](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 <span data-ttu-id="4118e-117">W tym artykule opisano sposób konfigurowania elementów wiązania transportu HTTP i HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4118e-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="4118e-118">Instrukcje: Zastępowanie rezerwacji adresu URL programu WCF ograniczoną rezerwacją</span><span class="sxs-lookup"><span data-stu-id="4118e-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="4118e-119">Opisuje sposób używania rezerwacje WCFURL z ograniczeniami.</span><span class="sxs-lookup"><span data-stu-id="4118e-119">Describes how to use WCFURL restricted reservations.</span></span>  
  
 [<span data-ttu-id="4118e-120">Przydziały dla transportu</span><span class="sxs-lookup"><span data-stu-id="4118e-120">Transport Quotas</span></span>](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 <span data-ttu-id="4118e-121">W tym artykule opisano zagadnienia dotyczące ustawiania przydziałów, które są dostępne w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="4118e-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="4118e-122">Praca z translatorami adresów sieciowych i zaporami</span><span class="sxs-lookup"><span data-stu-id="4118e-122">Working with NATs and Firewalls</span></span>](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 <span data-ttu-id="4118e-123">W tym artykule opisano sposób konfigurowania warstwy transportowej, gdy komunikaty są wysyłane lub odbierane za zaporą lub w przypadku, gdy występuje translatora adresów sieciowych (NAT).</span><span class="sxs-lookup"><span data-stu-id="4118e-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="4118e-124">Współużytkowanie portów w składniku Net.TCP</span><span class="sxs-lookup"><span data-stu-id="4118e-124">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 <span data-ttu-id="4118e-125">Opisuje sposób używania składnika współużytkowania portów Net.TCP funkcji WCF.</span><span class="sxs-lookup"><span data-stu-id="4118e-125">Describes how to use the Net.TCP Port Sharing component of WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4118e-126">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="4118e-126">Reference</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="4118e-127">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="4118e-127">Related Sections</span></span>  
 [<span data-ttu-id="4118e-128">Powiązania</span><span class="sxs-lookup"><span data-stu-id="4118e-128">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [<span data-ttu-id="4118e-129">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="4118e-129">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
