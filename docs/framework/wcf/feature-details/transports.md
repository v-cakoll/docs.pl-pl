---
title: Transporty w programie Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 077d63d8038b245a68083611897c1e6c68971071
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598674"
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="5a57e-102">Transporty w programie Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="5a57e-102">Transports in Windows Communication Foundation</span></span>
<span data-ttu-id="5a57e-103">Warstwa transportu jest na najniższym poziomie stosu kanału.</span><span class="sxs-lookup"><span data-stu-id="5a57e-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="5a57e-104">Główne transporty używane w Windows Communication Foundation (WCF) to HTTP, HTTPS, TCP i nazwane potoki.</span><span class="sxs-lookup"><span data-stu-id="5a57e-104">The main transports used in Windows Communication Foundation (WCF) are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="5a57e-105">W tematach w tej sekcji omówiono wybór między tymi transportami, Konfigurowanie transportu i Ustawianie właściwości dostrajania.</span><span class="sxs-lookup"><span data-stu-id="5a57e-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 <span data-ttu-id="5a57e-106">Usługa WCF oferuje dodatkowe transporty.</span><span class="sxs-lookup"><span data-stu-id="5a57e-106">WCF includes additional transports.</span></span> <span data-ttu-id="5a57e-107">Aby uzyskać informacje na temat transportu usługi kolejkowania komunikatów (MSMQ), zobacz [kolejki i sesje niezawodne](queues-and-reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="5a57e-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="5a57e-108">Aby uzyskać informacje o transportach równorzędnych, zobacz [sieci peer-to-](peer-to-peer-networking.md)peer.</span><span class="sxs-lookup"><span data-stu-id="5a57e-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5a57e-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="5a57e-109">In This Section</span></span>  
 [<span data-ttu-id="5a57e-110">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="5a57e-110">Choosing a Transport</span></span>](choosing-a-transport.md)  
 <span data-ttu-id="5a57e-111">Opisuje trzy główne transporty i zagadnienia związane z wybraniem jednej z nich.</span><span class="sxs-lookup"><span data-stu-id="5a57e-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="5a57e-112">Wybieranie kodera komunikatów</span><span class="sxs-lookup"><span data-stu-id="5a57e-112">Choosing a Message Encoder</span></span>](choosing-a-message-encoder.md)  
 <span data-ttu-id="5a57e-113">Opisuje czynniki, które należy wziąć pod uwagę podczas wybierania elementu powiązania kodowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="5a57e-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="5a57e-114">Strumieniowy transfer komunikatów</span><span class="sxs-lookup"><span data-stu-id="5a57e-114">Streaming Message Transfer</span></span>](streaming-message-transfer.md)  
 <span data-ttu-id="5a57e-115">Opisuje sposób konfigurowania warstwy transportu na potrzeby przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="5a57e-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="5a57e-116">Konfigurowanie protokołów HTTP i HTTPS</span><span class="sxs-lookup"><span data-stu-id="5a57e-116">Configuring HTTP and HTTPS</span></span>](configuring-http-and-https.md)  
 <span data-ttu-id="5a57e-117">Opisuje sposób konfigurowania elementów powiązania transportu HTTP i HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5a57e-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="5a57e-118">Instrukcje: Zastępowanie rezerwacji adresu URL programu WCF ograniczoną rezerwacją</span><span class="sxs-lookup"><span data-stu-id="5a57e-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="5a57e-119">Opisuje, jak używać rezerwacji z ograniczeniami WCFURL.</span><span class="sxs-lookup"><span data-stu-id="5a57e-119">Describes how to use WCFURL restricted reservations.</span></span>  
  
 [<span data-ttu-id="5a57e-120">Przydziały dla transportu</span><span class="sxs-lookup"><span data-stu-id="5a57e-120">Transport Quotas</span></span>](transport-quotas.md)  
 <span data-ttu-id="5a57e-121">Opisuje zagadnienia dotyczące ustawiania przydziałów dostępnych w warstwie transportowej.</span><span class="sxs-lookup"><span data-stu-id="5a57e-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="5a57e-122">Praca z translatorami adresów sieciowych i zaporami</span><span class="sxs-lookup"><span data-stu-id="5a57e-122">Working with NATs and Firewalls</span></span>](working-with-nats-and-firewalls.md)  
 <span data-ttu-id="5a57e-123">Opisuje sposób konfigurowania warstwy transportu w przypadku, gdy komunikaty są wysyłane lub odbierane za zaporą lub w przypadku obecności translacji adresów sieciowych (NAT).</span><span class="sxs-lookup"><span data-stu-id="5a57e-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="5a57e-124">Współużytkowanie portów w składniku Net.TCP</span><span class="sxs-lookup"><span data-stu-id="5a57e-124">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)  
 <span data-ttu-id="5a57e-125">Opisuje, jak używać składnika do udostępniania portów Net. TCP programu WCF.</span><span class="sxs-lookup"><span data-stu-id="5a57e-125">Describes how to use the Net.TCP Port Sharing component of WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5a57e-126">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="5a57e-126">Reference</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="5a57e-127">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="5a57e-127">Related Sections</span></span>  
 [<span data-ttu-id="5a57e-128">Powiązania</span><span class="sxs-lookup"><span data-stu-id="5a57e-128">Bindings</span></span>](bindings.md)  
  
 [<span data-ttu-id="5a57e-129">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="5a57e-129">Extending Bindings</span></span>](../extending/extending-bindings.md)
