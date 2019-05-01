---
title: 'Instrukcje: testowanie serwera proxy odnajdywania'
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 856b86241299585b80d58c6d37582463736a5935
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972916"
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="8f27c-102">Instrukcje: testowanie serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="8f27c-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="8f27c-103">Jest to czwarta cztery tematy, pokazujący sposób wdrażania serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="8f27c-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="8f27c-104">W poprzednim temacie [jak: Wdrażanie aplikacji klienta, który używa serwera Proxy odnajdywania można znaleźć usługi](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), zaimplementować aplikację kliencką usługi WCF, która używa serwera proxy odnajdywania można znaleźć usługi, a następnie wywołuje usługę.</span><span class="sxs-lookup"><span data-stu-id="8f27c-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), you implemented a WCF client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="8f27c-105">W tym temacie opisano sposób weryfikacji serwera proxy odnajdywania, usługi i klienta aplikacji działają zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="8f27c-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="8f27c-106">Uruchamianie serwera Proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="8f27c-106">Run the Discovery Proxy</span></span>  
  
1. <span data-ttu-id="8f27c-107">Otwórz wiersz polecenia jako administrator.</span><span class="sxs-lookup"><span data-stu-id="8f27c-107">Open a command prompt as an administrator.</span></span>  
  
2. <span data-ttu-id="8f27c-108">Może pojawić się okno dialogowe, które jest wyświetlany komunikat: Zapora Windows zablokowała niektórych funkcji tego programu.</span><span class="sxs-lookup"><span data-stu-id="8f27c-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="8f27c-109">Jeśli ten komunikat jest wyświetlony, kliknij przycisk **odblokowanie** przycisku.</span><span class="sxs-lookup"><span data-stu-id="8f27c-109">If you see this message, click the **Unblock** button.</span></span>  
  
3. <span data-ttu-id="8f27c-110">W wierszu polecenia Uruchom serwera proxy odnajdywania DiscoveryProxy.exe.</span><span class="sxs-lookup"><span data-stu-id="8f27c-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4. <span data-ttu-id="8f27c-111">Aplikacja powinna wyświetlić następujący tekst: `Proxy started. Hit Enter to exit`.</span><span class="sxs-lookup"><span data-stu-id="8f27c-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="8f27c-112">Uruchom usługę wykrywalny</span><span class="sxs-lookup"><span data-stu-id="8f27c-112">Run the Discoverable Service</span></span>  
  
1. <span data-ttu-id="8f27c-113">Otwórz wiersz polecenia jako administrator.</span><span class="sxs-lookup"><span data-stu-id="8f27c-113">Open a command prompt as an administrator.</span></span>  
  
2. <span data-ttu-id="8f27c-114">W wierszu polecenia Uruchom Service.exe odnajdywanej usługi.</span><span class="sxs-lookup"><span data-stu-id="8f27c-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3. <span data-ttu-id="8f27c-115">DiscoveryProxy.exe powinien być wyświetlany następujący tekst: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="8f27c-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="8f27c-116">Uruchom aplikację klienta</span><span class="sxs-lookup"><span data-stu-id="8f27c-116">Run the Client Application</span></span>  
  
1. <span data-ttu-id="8f27c-117">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="8f27c-117">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="8f27c-118">W wierszu polecenia Uruchom aplikację client.exe.</span><span class="sxs-lookup"><span data-stu-id="8f27c-118">Within the command prompt, run the client.exe application.</span></span>  
  
3. <span data-ttu-id="8f27c-119">Po kilku sekundach aplikacja kliencka wyświetla następujący tekst: Łączenie [punktu końcowego usługi].</span><span class="sxs-lookup"><span data-stu-id="8f27c-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4. <span data-ttu-id="8f27c-120">Service.exe należy następnie wyświetl następujący tekst: Umożliwia pozdrowienia Odebrano żądanie, czy będzie odpowiadać.</span><span class="sxs-lookup"><span data-stu-id="8f27c-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5. <span data-ttu-id="8f27c-121">Client.exe należy następnie wyświetl następujący tekst: Klient Hello!</span><span class="sxs-lookup"><span data-stu-id="8f27c-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="8f27c-122">Zamknij aplikacje</span><span class="sxs-lookup"><span data-stu-id="8f27c-122">Shut Down the Applications</span></span>  
  
1. <span data-ttu-id="8f27c-123">Zamykanie aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="8f27c-123">Shut down the client application.</span></span>  
  
2. <span data-ttu-id="8f27c-124">Wyłączenie usługi.</span><span class="sxs-lookup"><span data-stu-id="8f27c-124">Shut down the service.</span></span> <span data-ttu-id="8f27c-125">Serwera proxy odnajdywania wyświetla następujący tekst: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span><span class="sxs-lookup"><span data-stu-id="8f27c-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3. <span data-ttu-id="8f27c-126">Zamknij serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="8f27c-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f27c-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f27c-127">See also</span></span>

- [<span data-ttu-id="8f27c-128">Omówienie odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="8f27c-128">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="8f27c-129">Instrukcje: Wdrażanie serwera Proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="8f27c-129">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="8f27c-130">Instrukcje: Implementowanie Odnajdywanej usługi rejestrowanej za pomocą serwera Proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="8f27c-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="8f27c-131">Instrukcje: Wdrażanie aplikacji klienta, który używa serwera Proxy odnajdywania można znaleźć usługi</span><span class="sxs-lookup"><span data-stu-id="8f27c-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
