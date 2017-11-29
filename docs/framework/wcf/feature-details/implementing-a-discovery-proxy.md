---
title: Implementowanie serwera proxy odnajdywania
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5ddea7bf69f697c5b9ecd9d41021bff2407522a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-a-discovery-proxy"></a><span data-ttu-id="ff5b9-102">Implementowanie serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="ff5b9-102">Implementing a Discovery Proxy</span></span>
<span data-ttu-id="ff5b9-103">W tej sekcji opisano kroki wymagane do wdrożenia serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="ff5b9-103">This section describes the steps required to implement a discovery proxy.</span></span> <span data-ttu-id="ff5b9-104">Serwer proxy odnajdywania jest usługi autonomicznej, który zawiera repozytorium usług.</span><span class="sxs-lookup"><span data-stu-id="ff5b9-104">A discovery proxy is a standalone service that contains a repository of services.</span></span> <span data-ttu-id="ff5b9-105">Klienci mogą wykonywać kwerendę serwera proxy odnajdywania można znaleźć wykrywalny usługi Serwer proxy jest znane.</span><span class="sxs-lookup"><span data-stu-id="ff5b9-105">Clients can query a discovery proxy to find discoverable services that the proxy is aware of.</span></span> <span data-ttu-id="ff5b9-106">Jak serwer proxy jest wypełniane przy użyciu usługi jest implementujący.</span><span class="sxs-lookup"><span data-stu-id="ff5b9-106">How a proxy is populated with services is up to the implementer.</span></span> <span data-ttu-id="ff5b9-107">Na przykład serwera proxy odnajdywania można połączyć się z istniejącą repozytorium usługi i stał się wykrywalny, administrator może użyć interfejsu API zarządzania, aby dodać wykrywalny usługi na serwerze proxy lub serwera proxy odnajdywania może używać funkcji anonsu do tych informacji Zaktualizuj swojej wewnętrznej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="ff5b9-107">For example, a discovery proxy can connect to an existing service repository and make that information discoverable, an administrator can use a management API to add discoverable services to a proxy, or a discovery proxy can use the announcement functionality to update its internal cache.</span></span>  
  
 <span data-ttu-id="ff5b9-108">Implementacja WCF udostępnia klas podstawowych, które umożliwiają łatwe tworzenie serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="ff5b9-108">The WCF implementation provides base classes that allow you to easily build a proxy.</span></span> <span data-ttu-id="ff5b9-109">Mogą wykorzystywać te interfejsy API do tworzenia serwera Proxy odnajdywania na podstawie istniejących repozytorium.</span><span class="sxs-lookup"><span data-stu-id="ff5b9-109">You can utilize these APIs to build a Discovery Proxy on top of your existing repository.</span></span>  
  
 <span data-ttu-id="ff5b9-110">Serwera proxy odnajdywania zaimplementowana w tym miejscu jest podobnie jak inne usługi WCF, możesz również ustawić serwera proxy odnajdywania wykrywalny, a klienci mogą zlokalizować jego punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="ff5b9-110">The discovery proxy implemented here is like any other WCF services, in that you can also make the discovery proxy discoverable and have the clients locate its endpoints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ff5b9-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ff5b9-111">In This Section</span></span>  
 [<span data-ttu-id="ff5b9-112">Porady: Implementowanie serwera Proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="ff5b9-112">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 <span data-ttu-id="ff5b9-113">Opisuje sposób wdrożenia serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="ff5b9-113">Describes how to implement a discovery proxy.</span></span>  
  
 [<span data-ttu-id="ff5b9-114">Porady: Implementowanie wykrywalnej usługi, który rejestruje przy użyciu serwera Proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="ff5b9-114">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 <span data-ttu-id="ff5b9-115">Opisuje sposób wdrożenia wykrywalny [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, która rejestruje z serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="ff5b9-115">Describes how to implement a discoverable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that registers with the discovery proxy.</span></span>  
  
 [<span data-ttu-id="ff5b9-116">Porady: Wdrażanie aplikacji klienta, który używa serwera Proxy odnajdywania można znaleźć usługi</span><span class="sxs-lookup"><span data-stu-id="ff5b9-116">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 <span data-ttu-id="ff5b9-117">Opisuje sposób wdrożenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji klienckiej, która używa serwera proxy odnajdywania do wyszukiwania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="ff5b9-117">Describes how to implement a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses the discovery proxy to search for a service.</span></span>  
  
 [<span data-ttu-id="ff5b9-118">Porady: testowanie serwera Proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="ff5b9-118">How to: Test the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 <span data-ttu-id="ff5b9-119">Opisuje sposoby testowania kod napisany w poprzednim trzy tematy.</span><span class="sxs-lookup"><span data-stu-id="ff5b9-119">Describes how to test the code written in the previous three topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff5b9-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff5b9-120">See Also</span></span>  
 [<span data-ttu-id="ff5b9-121">Odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="ff5b9-121">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [<span data-ttu-id="ff5b9-122">Porady: programowane Dodawanie możliwości odnajdywania do usługi WCF i klienta</span><span class="sxs-lookup"><span data-stu-id="ff5b9-122">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
