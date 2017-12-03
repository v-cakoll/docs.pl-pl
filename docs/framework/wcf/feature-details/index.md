---
title: "Szczegóły funkcji WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- features [WCF]
- WCF, features
- Windows Communication Foundation, features
ms.assetid: 9b4368ca-0bd3-40dc-a539-bcd5779cee5f
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fbf351f0d71893457419d3b8b0e2cfb9c96ad0b0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-feature-details"></a><span data-ttu-id="993c6-102">Szczegóły funkcji WCF</span><span class="sxs-lookup"><span data-stu-id="993c6-102">WCF Feature Details</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="993c6-103">zapewnia szeroką gamę kontrolę nad funkcji obsługi wiadomości w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="993c6-103"> allows extensive control over the messaging functions of an application.</span></span> <span data-ttu-id="993c6-104">Tematy w tej sekcji, przejdź do szczegółów dotyczących dostępnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="993c6-104">The topics in this section go into detail about the available features.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="993c6-105">podstawowe programowania, zobacz [podstawowe programowania WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="993c6-105"> basic programming, see [Basic WCF Programming](../../../../docs/framework/wcf/basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="993c6-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="993c6-106">In This Section</span></span>  
 [<span data-ttu-id="993c6-107">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="993c6-107">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 <span data-ttu-id="993c6-108">Opisuje sposób tworzenia i konfigurowania usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="993c6-108">Describes how to create and configure workflow services.</span></span>  
  
 [<span data-ttu-id="993c6-109">Punkty końcowe: Adresy powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="993c6-109">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 <span data-ttu-id="993c6-110">Zawiera opis sposobu kontrolowania wiele aspektów usługi.</span><span class="sxs-lookup"><span data-stu-id="993c6-110">Describes how to control multiple aspects of your service.</span></span>  
  
 [<span data-ttu-id="993c6-111">Transfer i serializacja danych</span><span class="sxs-lookup"><span data-stu-id="993c6-111">Data Transfer and Serialization</span></span>](../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)  
 <span data-ttu-id="993c6-112">W tym artykule opisano, jak współdziałanie lub przyszłe zgodności umożliwia dostosowanie serializacji danych.</span><span class="sxs-lookup"><span data-stu-id="993c6-112">Describes how serialization of data can be tailored for interoperation or future compatibility.</span></span>  
  
 [<span data-ttu-id="993c6-113">Sesje, tworzenie wystąpień i współbieżność</span><span class="sxs-lookup"><span data-stu-id="993c6-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 <span data-ttu-id="993c6-114">W tym artykule opisano tryby wystąpień i sesji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oraz sposobu wybierania prawo tryb aplikacji.</span><span class="sxs-lookup"><span data-stu-id="993c6-114">Describes the instancing and session modes of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and how to select the right mode for your application.</span></span>  
  
 [<span data-ttu-id="993c6-115">Transporty</span><span class="sxs-lookup"><span data-stu-id="993c6-115">Transports</span></span>](../../../../docs/framework/wcf/feature-details/transports.md)  
 <span data-ttu-id="993c6-116">Zawiera opis sposobu konfigurowania warstwy transportowej najniższy poziom stosu kanału.</span><span class="sxs-lookup"><span data-stu-id="993c6-116">Describes how to configure the transport layer, the lowest level of the channel stack.</span></span>  
  
 [<span data-ttu-id="993c6-117">Kolejki i sesje niezawodne</span><span class="sxs-lookup"><span data-stu-id="993c6-117">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)  
 <span data-ttu-id="993c6-118">Zawiera opis kolejki, które przechowują wiadomości z aplikacja wysyłająca imieniu aplikację i później przekazywanie tych wiadomości do aplikacji odbierającej.</span><span class="sxs-lookup"><span data-stu-id="993c6-118">Describes queues, which store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span>  
  
 [<span data-ttu-id="993c6-119">Transakcje</span><span class="sxs-lookup"><span data-stu-id="993c6-119">Transactions</span></span>](../../../../docs/framework/wcf/feature-details/transactions-in-wcf.md)  
 <span data-ttu-id="993c6-120">Wyjaśnia sposób tworzenia Operacje transakcyjne, które można wycofać ponownie, jeśli jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="993c6-120">Explains how to create transacted operations that can be rolled back if needed.</span></span>  
  
 [<span data-ttu-id="993c6-121">Zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="993c6-121">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
 <span data-ttu-id="993c6-122">Opisuje sposób [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczeń ułatwia tworzenie aplikacji, które mają poufności i integralności.</span><span class="sxs-lookup"><span data-stu-id="993c6-122">Describes how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security helps you to create applications that have confidentiality and integrity.</span></span> <span data-ttu-id="993c6-123">Uwierzytelnianie i autoryzacja są również dostępne, ponieważ funkcje inspekcji.</span><span class="sxs-lookup"><span data-stu-id="993c6-123">Authentication and authorization are also available, as are auditing features.</span></span>  
  
 [<span data-ttu-id="993c6-124">Sieci peer-to-Peer</span><span class="sxs-lookup"><span data-stu-id="993c6-124">Peer-to-Peer Networking</span></span>](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 <span data-ttu-id="993c6-125">Zawiera szczegóły dotyczące sposobu tworzenia elementów równorzędnych, usług i klientów.</span><span class="sxs-lookup"><span data-stu-id="993c6-125">Details how to create peer services and clients.</span></span>  
  
 [<span data-ttu-id="993c6-126">Metadane</span><span class="sxs-lookup"><span data-stu-id="993c6-126">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 <span data-ttu-id="993c6-127">Zawiera opis architektury metadanych i formaty.</span><span class="sxs-lookup"><span data-stu-id="993c6-127">Describes metadata architecture and formats.</span></span>  
  
 [<span data-ttu-id="993c6-128">Klienci</span><span class="sxs-lookup"><span data-stu-id="993c6-128">Clients</span></span>](../../../../docs/framework/wcf/feature-details/clients.md)  
 <span data-ttu-id="993c6-129">Opisuje sposób tworzenia różnych klientów uzyskujących dostęp do usług.</span><span class="sxs-lookup"><span data-stu-id="993c6-129">Describes how to create a variety of clients that access services.</span></span>  
  
 [<span data-ttu-id="993c6-130">Hosting</span><span class="sxs-lookup"><span data-stu-id="993c6-130">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)  
 <span data-ttu-id="993c6-131">Opisuje hosting.</span><span class="sxs-lookup"><span data-stu-id="993c6-131">Describes hosting.</span></span> <span data-ttu-id="993c6-132">Usługa może być obsługiwany przez inną aplikację, lub może być hostowanie Samoobsługowe.</span><span class="sxs-lookup"><span data-stu-id="993c6-132">A service can be hosted by another application, or it can be self-hosted.</span></span>  
  
 [<span data-ttu-id="993c6-133">Współdziałanie i integracja</span><span class="sxs-lookup"><span data-stu-id="993c6-133">Interoperability and Integration</span></span>](../../../../docs/framework/wcf/feature-details/interoperability-and-integration.md)  
 <span data-ttu-id="993c6-134">Informacje dotyczące używania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rozszerzyć istniejącą logiki zamiast konieczności ponownego zapisania go, jeśli masz znaczących inwestycji w logice na podstawie składnika aplikacji hostowanej w modelu COM +.</span><span class="sxs-lookup"><span data-stu-id="993c6-134">Describes how to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to extend your existing logic rather than having to rewrite it if you have a substantial investment in component-based application logic hosted in COM+.</span></span>  
  
 [<span data-ttu-id="993c6-135">Model programowania protokołu HTTP sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="993c6-135">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 <span data-ttu-id="993c6-136">Opisuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programowania modelu sieci Web, dzięki której deweloperzy mogą uwidaczniać [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] operacje punktów końcowych SOAP z systemem innym niż usługi.</span><span class="sxs-lookup"><span data-stu-id="993c6-136">Describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Programming Model that allows developers to expose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service operations to non-SOAP endpoints.</span></span>  
  
 [<span data-ttu-id="993c6-137">Syndykacja programu WCF</span><span class="sxs-lookup"><span data-stu-id="993c6-137">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)  
 <span data-ttu-id="993c6-138">W tym artykule opisano umożliwiają łatwe udostępnianie zespolonego źródła [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="993c6-138">Describes support to easily expose syndication feeds from a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 [<span data-ttu-id="993c6-139">Integracji AJAX i obsługi JSON</span><span class="sxs-lookup"><span data-stu-id="993c6-139">AJAX Integration and JSON Support</span></span>](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 <span data-ttu-id="993c6-140">W tym artykule opisano obsługę asynchronicznych języka JavaScript ASP.NET i XML (AJAX) i format danych JavaScript Object Notation (JSON), umożliwia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług do udostępnienia operacji klientom AJAX.</span><span class="sxs-lookup"><span data-stu-id="993c6-140">Describes support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format to allow [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to expose operations to AJAX clients.</span></span>  
  
 [<span data-ttu-id="993c6-141">Odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="993c6-141">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 <span data-ttu-id="993c6-142">Informacje pomocy technicznej, aby włączyć usługi będzie wykrywalny w czasie wykonywania w sposób interoperacyjne za pomocą protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="993c6-142">Describes support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span>  
  
 [<span data-ttu-id="993c6-143">Routing</span><span class="sxs-lookup"><span data-stu-id="993c6-143">Routing</span></span>](../../../../docs/framework/wcf/feature-details/routing.md)  
 <span data-ttu-id="993c6-144">Zawiera opis usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="993c6-144">Describes the routing service.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="993c6-145">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="993c6-145">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.ServiceModel.Routing>  
  
## <a name="related-sections"></a><span data-ttu-id="993c6-146">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="993c6-146">Related Sections</span></span>  
 [<span data-ttu-id="993c6-147">Programowanie podstawowe usługi WCF</span><span class="sxs-lookup"><span data-stu-id="993c6-147">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)
