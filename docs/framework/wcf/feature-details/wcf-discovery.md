---
title: Odnajdywanie w programie WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0c9b083180870e451816b54dddc10068ca7ec5db
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-discovery"></a><span data-ttu-id="2c279-102">Odnajdywanie w programie WCF</span><span class="sxs-lookup"><span data-stu-id="2c279-102">WCF Discovery</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="2c279-103">Umożliwia włączenie usług będzie wykrywalny w czasie wykonywania w sposób interoperacyjne za pomocą protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="2c279-103"> provides support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2c279-104">usługi można poinformować o ich dostępności sieci za pomocą komunikatu multiemisji lub serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="2c279-104"> services can announce their availability to the network using a multicast message or to a discovery proxy server.</span></span> <span data-ttu-id="2c279-105">Aplikacje klienckie można znaleźć sieci lub serwera proxy odnajdywania można znaleźć usługi, które spełniają określone kryteria.</span><span class="sxs-lookup"><span data-stu-id="2c279-105">Client applications can search the network or a discovery proxy server to find services that meet a set of criteria.</span></span> <span data-ttu-id="2c279-106">Tematy w tej sekcji omówiono i modelu programowania dla tej funkcji, które szczegółowo opisano.</span><span class="sxs-lookup"><span data-stu-id="2c279-106">The topics in this section provide an overview and describe the programming model for this feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c279-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2c279-107">In This Section</span></span>  
 [<span data-ttu-id="2c279-108">Omówienie odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="2c279-108">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 <span data-ttu-id="2c279-109">Zawiera omówienie pomocy technicznej usługi WS-Discovery [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2c279-109">Provides an overview of WS-Discovery support provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="2c279-110">Model obiektów odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="2c279-110">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)  
 <span data-ttu-id="2c279-111">Zawiera opis klas w modelu obiektów i rozszerzalność obsługi protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="2c279-111">Describes the classes in the object model and extensibility of WS-Discovery support.</span></span>  
  
 [<span data-ttu-id="2c279-112">Porady: programowane Dodawanie możliwości odnajdywania do usługi WCF i klienta</span><span class="sxs-lookup"><span data-stu-id="2c279-112">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 <span data-ttu-id="2c279-113">Pokazuje, jak utworzyć [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] wykrywalny usługi.</span><span class="sxs-lookup"><span data-stu-id="2c279-113">Shows how to make a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service discoverable.</span></span>  
  
 [<span data-ttu-id="2c279-114">Wdrażanie serwera Proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="2c279-114">Implementing a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 <span data-ttu-id="2c279-115">W tym artykule opisano kroki wymagane do wdrożenia serwera proxy odnajdywania, wykrywalnej usługi, który rejestruje przy użyciu serwera proxy odnajdywania i klienta, który używa serwera proxy odnajdywania można znaleźć wykrywalnej usługi.</span><span class="sxs-lookup"><span data-stu-id="2c279-115">Describes the steps required to implement a discovery proxy, a discoverable service that registers with the discovery proxy, and a client that uses the discovery proxy to find the discoverable service.</span></span>  
  
 [<span data-ttu-id="2c279-116">Przechowywanie wersji odnajdywania</span><span class="sxs-lookup"><span data-stu-id="2c279-116">Discovery Versioning</span></span>](../../../../docs/framework/wcf/feature-details/discovery-versioning.md)  
 <span data-ttu-id="2c279-117">Krótki przegląd prototypu stosowania niektórych nowych funkcji odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="2c279-117">Provides a brief overview of a prototype implementation of some new discovery features.</span></span> <span data-ttu-id="2c279-118">Również zawiera omówienie dotyczące wybierz wersję odnajdywania do użycia.</span><span class="sxs-lookup"><span data-stu-id="2c279-118">It also gives an overview on how to select the discovery version to use.</span></span>  
  
 [<span data-ttu-id="2c279-119">Konfigurowanie odnajdywania w pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2c279-119">Configuring Discovery in a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md)  
 <span data-ttu-id="2c279-120">Pokazano, jak skonfigurować odnajdywanie w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2c279-120">Shows how to configure Discovery in configuration.</span></span>  
  
 [<span data-ttu-id="2c279-121">Za pomocą kanału klienta odnajdywania</span><span class="sxs-lookup"><span data-stu-id="2c279-121">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 <span data-ttu-id="2c279-122">Przedstawia sposób korzystania z kanału klienta odnajdowania, podczas zapisywania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="2c279-122">Shows how to use a Discovery Client Channel when writing a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application.</span></span>
