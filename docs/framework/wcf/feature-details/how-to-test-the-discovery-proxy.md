---
title: 'Porady: testowanie serwera Proxy odnajdywania'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55a7fe72b34fc8c099d921e7e295c184817825a3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="7b47f-102">Porady: testowanie serwera Proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="7b47f-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="7b47f-103">Jest to czwarty cztery tematów, pokazujący sposób wdrożenia serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="7b47f-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="7b47f-104">W poprzednim temacie [porady: Wdrażanie aplikacji klienta, który używa serwera Proxy odnajdywania można znaleźć usługi](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), zostanie zaimplementowana [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji klienckiej, która używa serwera proxy odnajdywania można znaleźć usługi, a następnie wywołuje Usługa.</span><span class="sxs-lookup"><span data-stu-id="7b47f-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), you implemented a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="7b47f-105">W tym temacie opisano sposób weryfikacji serwera proxy odnajdywania, usługi i klienta aplikacji działają zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="7b47f-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="7b47f-106">Uruchamianie serwera Proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="7b47f-106">Run the Discovery Proxy</span></span>  
  
1.  <span data-ttu-id="7b47f-107">Otwórz wiersz polecenia jako administrator.</span><span class="sxs-lookup"><span data-stu-id="7b47f-107">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="7b47f-108">Okno dialogowe z informacją, może zostać wyświetlony: Zapora systemu Windows zablokowała niektóre funkcje tego programu.</span><span class="sxs-lookup"><span data-stu-id="7b47f-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="7b47f-109">Jeśli ten komunikat zostanie wyświetlony, kliknij przycisk **Odblokuj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="7b47f-109">If you see this message, click the **Unblock** button.</span></span>  
  
3.  <span data-ttu-id="7b47f-110">W wierszu polecenia Uruchom serwera proxy odnajdywania DiscoveryProxy.exe.</span><span class="sxs-lookup"><span data-stu-id="7b47f-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4.  <span data-ttu-id="7b47f-111">Aplikacja powinna wyświetl następujący tekst: `Proxy started. Hit Enter to exit`.</span><span class="sxs-lookup"><span data-stu-id="7b47f-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="7b47f-112">Uruchom wykrywalnej usługi</span><span class="sxs-lookup"><span data-stu-id="7b47f-112">Run the Discoverable Service</span></span>  
  
1.  <span data-ttu-id="7b47f-113">Otwórz wiersz polecenia jako administrator.</span><span class="sxs-lookup"><span data-stu-id="7b47f-113">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="7b47f-114">W wierszu polecenia Uruchom Service.exe wykrywalnej usługi.</span><span class="sxs-lookup"><span data-stu-id="7b47f-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3.  <span data-ttu-id="7b47f-115">DiscoveryProxy.exe powinien być wyświetlany następujący tekst: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="7b47f-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="7b47f-116">Uruchom aplikację klienta</span><span class="sxs-lookup"><span data-stu-id="7b47f-116">Run the Client Application</span></span>  
  
1.  <span data-ttu-id="7b47f-117">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="7b47f-117">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="7b47f-118">W wierszu polecenia Uruchom aplikację client.exe.</span><span class="sxs-lookup"><span data-stu-id="7b47f-118">Within the command prompt, run the client.exe application.</span></span>  
  
3.  <span data-ttu-id="7b47f-119">Po kilku sekundach aplikacja kliencka będzie wyświetlony następujący tekst: nawiązywanie [punktu końcowego usługi].</span><span class="sxs-lookup"><span data-stu-id="7b47f-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4.  <span data-ttu-id="7b47f-120">Service.exe należy następnie wyświetl następujący tekst: pozdrowienia Odebrano żądanie, I będzie odpowiadać.</span><span class="sxs-lookup"><span data-stu-id="7b47f-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5.  <span data-ttu-id="7b47f-121">Client.exe należy następnie wyświetl następujący tekst: Hello klienta!</span><span class="sxs-lookup"><span data-stu-id="7b47f-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="7b47f-122">Zamknij aplikacje</span><span class="sxs-lookup"><span data-stu-id="7b47f-122">Shut Down the Applications</span></span>  
  
1.  <span data-ttu-id="7b47f-123">Zamknij aplikację klienta.</span><span class="sxs-lookup"><span data-stu-id="7b47f-123">Shut down the client application.</span></span>  
  
2.  <span data-ttu-id="7b47f-124">Zatrzymania usługi.</span><span class="sxs-lookup"><span data-stu-id="7b47f-124">Shut down the service.</span></span> <span data-ttu-id="7b47f-125">Serwera proxy odnajdywania wyświetla następujący tekst: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span><span class="sxs-lookup"><span data-stu-id="7b47f-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3.  <span data-ttu-id="7b47f-126">Zamknij serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="7b47f-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b47f-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b47f-127">See Also</span></span>  
 [<span data-ttu-id="7b47f-128">Omówienie odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="7b47f-128">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="7b47f-129">Porady: Implementowanie serwera Proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="7b47f-129">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [<span data-ttu-id="7b47f-130">Porady: Implementowanie wykrywalnej usługi, który rejestruje przy użyciu serwera Proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="7b47f-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [<span data-ttu-id="7b47f-131">Porady: Wdrażanie aplikacji klienta, który używa serwera Proxy odnajdywania można znaleźć usługi</span><span class="sxs-lookup"><span data-stu-id="7b47f-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
