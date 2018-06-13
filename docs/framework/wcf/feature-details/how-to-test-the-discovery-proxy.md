---
title: 'Porady: testowanie serwera Proxy odnajdywania'
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 35edbd03e912ae2d9c491afb28dee1c4a3055d14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491225"
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="83e61-102">Porady: testowanie serwera Proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="83e61-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="83e61-103">Jest to czwarty cztery tematów, pokazujący sposób wdrożenia serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="83e61-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="83e61-104">W poprzednim temacie [porady: Wdrażanie aplikacji klienta, który używa serwera Proxy odnajdywania można znaleźć usługi](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), zaimplementowana aplikacji klienta WCF, która używa serwera proxy odnajdywania można znaleźć usługi, a następnie wywołuje usługę.</span><span class="sxs-lookup"><span data-stu-id="83e61-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), you implemented a WCF client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="83e61-105">W tym temacie opisano sposób weryfikacji serwera proxy odnajdywania, usługi i klienta aplikacji działają zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="83e61-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="83e61-106">Uruchamianie serwera Proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="83e61-106">Run the Discovery Proxy</span></span>  
  
1.  <span data-ttu-id="83e61-107">Otwórz wiersz polecenia jako administrator.</span><span class="sxs-lookup"><span data-stu-id="83e61-107">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="83e61-108">Okno dialogowe z informacją, może zostać wyświetlony: Zapora systemu Windows zablokowała niektóre funkcje tego programu.</span><span class="sxs-lookup"><span data-stu-id="83e61-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="83e61-109">Jeśli ten komunikat zostanie wyświetlony, kliknij przycisk **Odblokuj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="83e61-109">If you see this message, click the **Unblock** button.</span></span>  
  
3.  <span data-ttu-id="83e61-110">W wierszu polecenia Uruchom serwera proxy odnajdywania DiscoveryProxy.exe.</span><span class="sxs-lookup"><span data-stu-id="83e61-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4.  <span data-ttu-id="83e61-111">Aplikacja powinna wyświetl następujący tekst: `Proxy started. Hit Enter to exit`.</span><span class="sxs-lookup"><span data-stu-id="83e61-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="83e61-112">Uruchom wykrywalnej usługi</span><span class="sxs-lookup"><span data-stu-id="83e61-112">Run the Discoverable Service</span></span>  
  
1.  <span data-ttu-id="83e61-113">Otwórz wiersz polecenia jako administrator.</span><span class="sxs-lookup"><span data-stu-id="83e61-113">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="83e61-114">W wierszu polecenia Uruchom Service.exe wykrywalnej usługi.</span><span class="sxs-lookup"><span data-stu-id="83e61-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3.  <span data-ttu-id="83e61-115">DiscoveryProxy.exe powinien być wyświetlany następujący tekst: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="83e61-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="83e61-116">Uruchom aplikację klienta</span><span class="sxs-lookup"><span data-stu-id="83e61-116">Run the Client Application</span></span>  
  
1.  <span data-ttu-id="83e61-117">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="83e61-117">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="83e61-118">W wierszu polecenia Uruchom aplikację client.exe.</span><span class="sxs-lookup"><span data-stu-id="83e61-118">Within the command prompt, run the client.exe application.</span></span>  
  
3.  <span data-ttu-id="83e61-119">Po kilku sekundach aplikacja kliencka będzie wyświetlony następujący tekst: nawiązywanie [punktu końcowego usługi].</span><span class="sxs-lookup"><span data-stu-id="83e61-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4.  <span data-ttu-id="83e61-120">Service.exe należy następnie wyświetl następujący tekst: pozdrowienia Odebrano żądanie, I będzie odpowiadać.</span><span class="sxs-lookup"><span data-stu-id="83e61-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5.  <span data-ttu-id="83e61-121">Client.exe należy następnie wyświetl następujący tekst: Hello klienta!</span><span class="sxs-lookup"><span data-stu-id="83e61-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="83e61-122">Zamknij aplikacje</span><span class="sxs-lookup"><span data-stu-id="83e61-122">Shut Down the Applications</span></span>  
  
1.  <span data-ttu-id="83e61-123">Zamknij aplikację klienta.</span><span class="sxs-lookup"><span data-stu-id="83e61-123">Shut down the client application.</span></span>  
  
2.  <span data-ttu-id="83e61-124">Zatrzymania usługi.</span><span class="sxs-lookup"><span data-stu-id="83e61-124">Shut down the service.</span></span> <span data-ttu-id="83e61-125">Serwera proxy odnajdywania wyświetla następujący tekst: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span><span class="sxs-lookup"><span data-stu-id="83e61-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3.  <span data-ttu-id="83e61-126">Zamknij serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="83e61-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83e61-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83e61-127">See Also</span></span>  
 [<span data-ttu-id="83e61-128">Omówienie odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="83e61-128">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="83e61-129">Instrukcje: wdrażanie serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="83e61-129">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [<span data-ttu-id="83e61-130">Instrukcje: implementowanie odnajdywanej usługi rejestrowanej za pomocą serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="83e61-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [<span data-ttu-id="83e61-131">Instrukcje: wdrażanie aplikacji klienta znajdującej usługę przy użyciu serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="83e61-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
